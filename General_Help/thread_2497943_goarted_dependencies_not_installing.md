---
title: "goarted dependencies not installing"
date: 2024-05-23
forum: General Help
---

### Post by mark allyn on 2024-05-23
Hello anyone,


I have been away from ubuntu for several years.  A lot must have happened in the meantime!  I have been trying to install gparted but there are dependencies that won't install.  I hope there is an apt command that will pull them in.  Anyone knowing such a command will receive my unbounded thanks.  Here are the error reports:

```

Err:1 http://us.archive.ubuntu.com/ubuntu yakkety/main amd64 libgtkmm-2.4-1v5 amd64 1:2.24.5-1
  404  Not Found
Err:2 http://us.archive.ubuntu.com/ubuntu yakkety/main amd64 libparted-fs-resize0 amd64 3.2-15build1
  404  Not Found
Unable to correct missing packages.
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1v5_2.24.5-1_amd64.deb  404  Not Found
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/parted/libparted-fs-resize0_3.2-15build1_amd64.deb  404  Not Found
E: Aborting install.

```

BTW, I HAVE searched the web and this forum.

Thanks,

Mark Allyn

---

### Post by #&amp;thj^% on 2024-05-23
Just to remind you, /ubuntu yakkety is well out of support; currently 22.04LTS and 24.04 are the new LTS releases.

---

### Post by Rubi1200 on 2024-05-23
Ubuntu 16.10 reached EOL on July 20, 2017.

I cannot stress enough what the security risks are of running such an outdated version.

Backup your important data and install a more recent version.

---

### Post by grahammechanical on 2024-05-23
The fact that 16.10 is out of support is the reason you are getting those "failed to fetch" messages. The internet addresses to those repositories are wrong because the 16.10 repositories have been 
moved to another internet address.

Regards

---

### Post by mark allyn on 2024-05-24
Hi everyone,

Thanks for clarifying.  I thought I was running ubuntu version 22.  I'm not.  I'm running 16.10.  Got to track down my 22.04.  It's around somewhere.  

Mark Allyn

---

