---
title: "HTS speech synthesis problem"
date: 2017-09-16
forum: General Help
---

### Post by na2 on 2017-09-16
Hi everyone,

I'm using the HTS-demo_CMU-ARCTIC-SLT for speech synthesis, i'm training it with my own data (raw files, label files and questions files), in the begining everything seems ok but after a while a problem come out which is: 

/usr/local/bin/HHEd -A -B -C /home/nadia/syn/HTS-demo_CMU-ARCTIC-SLT/configs/qst001/ver1/trn.cnf -D -T 1 -p -i -H /home/nadia/syn/HTS-demo_CMU-ARCTIC-SLT/gv/qst001/ver1/clustered.mmf -m -a 1.0 -w /home/nadia/syn/HTS-demo_CMU-ARCTIC-SLT/gv/qst001/ver1/clustered.mmf /home/nadia/syn/HTS-demo_CMU-ARCTIC-SLT/gv/qst001/ver1/cxc_mgc.hed /home/nadia/syn/HTS-demo_CMU-ARCTIC-SLT/gv/qst001/ver1/gv.list


HTK Configuration Parameters[8]
  Module/Tool     Parameter                  Value
#                 MINDUR                         5
#                 MAXSTDDEVCOEF                 10
#                 APPLYDURVARFLOOR              TRUE
#                 DURVARFLOORPERCENTILE          1.000000
#                 VFLOORSCALESTR  Vector 4 0.01 0.01 0.01 0.01
#                 NATURALWRITEORDER              TRUE
#                 NATURALREADORDER              TRUE
#                 APPLYVFLOOR                 TRUE


HHEd
 16/16 Models Loaded [3 states max, 1 mixes max]
  ERROR [+5010]  InitSource: Cannot open source file /home/nadia/syn/HTS-demo_CMU-ARCTIC-SLT/gv/qst001/ver1/cxc_mgc.hed
  ERROR [+2610]  DoEdit: Can't open file /home/nadia/syn/HTS-demo_CMU-ARCTIC-SLT/gv/qst001/ver1/cxc_mgc.hed
 FATAL ERROR - Terminating program /usr/local/bin/HHEd

All the other files were created except cxc_mgc.hed and i can't understand from where this problem come. Please help me solve it and thanks in advance.

---

