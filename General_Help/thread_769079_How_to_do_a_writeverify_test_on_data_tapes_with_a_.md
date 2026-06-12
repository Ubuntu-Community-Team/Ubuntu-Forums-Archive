---
title: "How to do a write/verify test on data tapes with a Storagetek L700e robotic library"
date: 2008-04-26
forum: General Help
---

### Post by pyrotherm on 2008-04-26
Ok, I know this is a very specialized question, but i figured someone might have an idea here.

I'm trying to figure out what software would be able to give me this capability.

I have a Storagetek L700e Robotic tape library with 10 Quantum SuperDLT drives in it, along with a computer running Ubuntu 8.04LTS with 3 Adaptec 3944 Dual-channel SCSI Cards.

What I would like to do is be able to:
1. put a bunch of unlabeled tapes into the library's storage silo's slots

2. write a bunch of data to each tape and verify it through the use of a checksum, etc. using any of the drives which are not currently being used (not using library for anything but testing tapes)
2a. possibly be able to script in the ability to define how much data/ how long the test will run for each tape

3. have the program give a report of which tapes are good/bad with slot #'s from the library

4. be able to export bad tapes through the library's access portal at the end of the batch job, either automatically or manually (i'm sure i can figure out the scripting for most of this stuff once i have a platform to work with)

My ultimate goal here, is to use linux and my tape library to do a write/read test to tapes, so that i can sell re-certified media to my customers. My employer is currently using a very bad dos-ported program to do this that has absolutely no flexibility or tape library support.

Any tips, suggestions, feedback of any kind (please don't flame me for this one) are welcome.

Best Regards to all of you purveyors/distributors of knowledge in the Linux community, have a great day!

---

