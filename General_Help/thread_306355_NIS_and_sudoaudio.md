---
title: "NIS and sudo/audio"
date: 2006-11-24
forum: General Help
---

### Post by wolfgangpauli on 2006-11-24
Hi,

I just installed kubuntu with NIS support. I can successfully log in with NIS accounts but I have two problems: (1) sudo does not work and (2) I don't get permission to access /dev/dsp

If I type 'groups', I get my groups listed: 'admin' for sudoers and 'audio' for /dev/dsp, but for some reason that I am not recognized as sudoer and am not allowed to access the audio device.

Any ideas?

---

### Post by wolfgangpauli on 2006-11-24
Hey,

I found the problem. had to delete the group entries for audio and admin in the /etc/group file. 

wolfgang

---

### Post by vtripolitakis on 2006-11-26
Hello,

can your NIS users start firefox and openoffice 2.0 ?

My local users contrary to nis can !!!

---

