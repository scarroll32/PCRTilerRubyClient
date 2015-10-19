Several convenient functions to interact with the
`PCRTiler servlet <http://pcrtiler.alaingervais.org:8080/PCRTiler/>`_.

Create job
----------

::

  require 'pcr_tiler_client'

  PCRTiler_BASE_URL = 'http://pcrtiler.alaingervais.org:8080/PCRTiler'

  params = {
    'sequence' => 'ACCAATGGTGGCGCGATGTAACACGAGAAAGCACATACCAAGGCCACCACACACCACCTGTCCAAAAAGGCCTTCGATACGGGATAATCCTATTTATTACCTCAGAAGTTTTTTTCTTCGCAGGATTTTTCTGAGCCTTTTACCACTCCAGCCTAGCCCCTACCCCCCAACTAGGAGGGCACTGGCCCCCAACAGGCATCAACCAATGGTGGCGCGATGTAACACGAGAAAGCACATACCAAGGCCACCACACACCACCTGTCCAAAAAGGCCTTCGATACGGGATAATCCTATTTATTACCTCAGAAGTTTTTTTCTTCGCAGGATTTTTCTGAGCCTTTTACCACTCCAGCCTAGCCCCTACCCCCCAACTAGGAGGGCACTGGCCCCCAACAGGCATCAACCAATGGTGGCGCGATGTAACACGAGAAAGCACATACCAAGGCCACCACACACCACCTGTCCAAAAAGGCCTTCGATACGGGATAATCCTATTTATTACCTCAGAAGTTTTTTTCTTCGCAGGATTTTTCTGAGCCTTTTACCACTCCAGCCTAGCCCCTACCCCCCAACTAGGAGGGCACTGGCCCCCAACAGGCATCA',
    'organism' => 'Homo_sapiens'
  }
  id = PCRTiler.post_job(PCRTiler_BASE_URL, params)

If you don't specify other params, they will take default values:

::

  job_name=PCRTilerRubyClient

  minimum_tm=60
  maximum_tm=63
  minimum_length=100
  maximum_length=150

  segmentation_type=primer_pair_count
  primer_pair_count=20
  primer_target_length=200

  filter=

  total_mismatches=4
  three_prime_mismatches=2
  number_of_candidates=1000
  distance_threshold=3000

  program=blastn

  email=

Check job result
----------------

::

  result = PCRTiler.check_job(PCRTiler_BASE_URL, id)

``result`` examples:

* {:status => 'queued'}
* {:status => 'doing', :done => 10, :total => 16}
* {:status => 'done', :txt => 'Oligos for job No name...'}
