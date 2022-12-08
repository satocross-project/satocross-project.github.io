# New code coverage criteria for industrial users

The project started with a review of code coverage criteria from the perspective of the needs of industry, in terms of bug detection, certifiability and acceptability for industrial users of tests generated automatically to satisfy the criteria. The results highlighted two aspects that have not received much attention in the literature: boundary coverage and output-guided criteria. Indeed, boundary coverage is often applied in practice and even demanded by industrial norms but rarely precisely defined, even though criteria must be formally defined in order to be handled by automatic tools. We proposed a new output-guided criterion in which tests are paired according to coverage or non-coverage of a given label, with the observable outputs of the two tests being different. We decided to study the formalization of these criteria using Frama-C Ltest hyper-labels, based on our preliminary investigation of the expression and treatment of dataflow criteria, which require similar treatment to output-guided criteria, and then adding the concepts of boundary testing and output visibility in order to extend Ltest to efficiently treat the SATOCROSS criteria.

# Elimination of polluting test objectives

Another result of the review of industrial needs was the problem of infeasible test objectives. Indeed, a criterion may demand coverage of a test objective that is in fact unreachable and so cannot be covered. It is difficult and time-consuming for testers to manually identify such objectives and so this is an important function of automatic tools. Infeasible objectives are one case of the more general problem of polluting test objectives which hamper efficient test generation and test assessment and are prevalent in MC/DC, boundary testing, dataflow coverage criteria and also mutation testing. The problem of polluting test objectives was extensively addressed by the project in several ways:
<br>
* Extending and optimizing the Frama-C Ltest plugins in order to use dataflow analysis to eliminate non-applicable and equivalent objectives in dataflow and other similar criteria during their definition;
* Using different static analyses at various points in the test process to detect some infeasible and redundant objectives;
* The Cerebro tool uses machine learning to statically select high utility mutants, i.e., mutants that subsume almost all other mutants, thereby allowing the application of mutation testing in a best-effort basis;
* A key problem with mutation testing is the large number of low utility mutants it introduces. To deal with issue, we developed µBERT, a mutation testing tool that leverages the power of pre-trained language models when generating mutants in order to generate strong and natural mutants;
* Using exhaustive test generation in Frama-C PathCrawler to demonstrate that any remaining infeasible objectives cannot be covered. We showed that efficient generation of tests to cover branches or Ltest labels in PathCrawler depends on early coverage of reachable objectives followed by exhaustive exploration of potential ways to cover remaining objectives.

# Continous Development

Finally, we also addressed the industrial need for integration of coverage-based testing into a Continuous Development process. We proposed solutions for test generation based on symbolic execution to two alternative formulations of this problem, both of which seemed to us to be relevant to industrial users:
<br>
1. The DeltaTG test generation tool was developed to generate tests to cover just the differences between two versions of the source code;
2. Using PathCrawler to maintain complete coverage of a new version of the code while reusing as many as possible of the tests generated to cover the previous version.
