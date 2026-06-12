---
title: "[SOLVED] How can I not use a hardcoded password in a cron job"
date: 2008-01-01
forum: General Help
---

### Post by rml00 on 2008-01-01
Hi all,

I have a problem and I cannot find the answer on the net.

I have a shell script that gets some files from a secure website. I use wget and specify my username and password on the command line. I want to run this shell script from a cron job. All the exemples I saw hardcoded the password either directly in the shell script or by using an environment variable set in the crontab. I do not want to hardcode any password because, if the computer gets stolen, anybody can easily get the password from the file.

I would like for the password to reside in ram somewhere so that if the computer is powered off, the password dies with it. Of course, the password could be retrieved directly from the computer but I am more worried about somebody retrieving the password after the computer has been stolen. Any ideas?

Thanks a lot.

---

### Post by dcstar on 2008-01-02
> **rml00 said:**
> Hi all,

I have a problem and I cannot find the answer on the net.

I have a shell script that gets some files from a secure website. I use wget and specify my username and password on the command line. I want to run this shell script from a cron job. All the exemples I saw hardcoded the password either directly in the shell script or by using an environment variable set in the crontab. I do not want to hardcode any password because, if the computer gets stolen, anybody can easily get the password from the file.

I would like for the password to reside in ram somewhere so that if the computer is powered off, the password dies with it. Of course, the password could be retrieved directly from the computer but I am more worried about somebody retrieving the password after the computer has been stolen. Any ideas?

Thanks a lot.

Have the password stored in a file on an encrypted drive, and have the script access it from that drive.

---

### Post by rml00 on 2008-01-02
Great idea. I should have thaught of it myself. Thank you.

---

