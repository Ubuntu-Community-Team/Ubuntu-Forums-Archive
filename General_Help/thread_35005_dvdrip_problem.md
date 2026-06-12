---
title: "dvd:rip problem"
date: 2005-05-17
forum: General Help
---

### Post by vaskark on 2005-05-17
I'm trying to rip a dvd. The encoding looked to be going fine but then I was given an error about 'multiplexing' and it aborted. The process did create 2 output files, for video and audio (I think!) but were never combined into one file. Can anyone help? Thanks. Here's the end of the log file:

 > Tue May 17 08:00:58 2005 Successfully finished job (1): Transcoding video - title #2, single pass
Tue May 17 08:00:58 2005 Starting job (2): Multiplexing MPEG - title #2
Tue May 17 08:00:58 2005 Executing command: dr_exec mplex -f 1 -o /home/jason/.dvdrip/Futurama/avi/002/Futurama-002-%d.mpg /home/jason/.dvdrip/Futurama/avi/002/Futurama-002.m1v /home/jason/.dvdrip/Futurama/avi/002/Futurama-002.mpa && echo DVDRIP_SUCCESS
Tue May 17 08:00:59 2005 Job has PID 1776
Tue May 17 08:00:59 2005 Aborting command. Sending signal 1 to PID 1776...
Tue May 17 08:00:59 2005 Aborting job: Multiplexing MPEG - title #2
Tue May 17 08:00:59 2005 You should analyze the last output of this job to see what's going wrong here:
Tue May 17 08:00:59 2005 ---- job output start ----
Tue May 17 08:00:59 2005 ---- job output end ----

---

