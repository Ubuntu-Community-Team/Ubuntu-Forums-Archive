---
title: "Error occurred while extracting files- Error setting owner: Operation not permitted"
date: 2013-11-04
forum: General Help
---

### Post by Grimace78 on 2013-11-04
Trying to extract makemkv files from download folder and got this message: 

> Error occurred while extracting files- Error setting owner: Operation not permitted

First thought corrupt file, I downloaded twice more on two different days; problem persists. Also checked permissions (no previous problems with this), and r/w permissions are enabled.

Reading this thread to try to troubleshoot issue:

[http://ubuntuforums.org/showthread.php?t=1847573](http://ubuntuforums.org/showthread.php?t=1847573)

Was inputting terminal commands (whoami, etc.) before mod shut down old thread. This was my output:

> donald@d-z77m:~$ whoami
donald
donald@d-z77m:~$ ls -ld ~/Desktop
drwxr-xr-x 2 donald donald 4096 Nov  4 10:22 /home/donald/Desktop
donald@d-z77m:~$ cd ~/Desktop; ls -l
total 0
donald@d-z77m:~/Desktop$ 

Can someone help me finish troubleshooting this problem?

---

### Post by Grimace78 on 2013-11-04
Just extracted conky tarball, no issues.

---

### Post by Grimace78 on 2013-11-04
Instead of using the archive manager, I got the folders unzipped using > [COLOR=#333333][FONT=UbuntuMono]tar -xzvf tarballname.tar.gz[/FONT][/COLOR], but would still like to know what was going on if anyone knows and has a minute. I don't want to run into the issue in the future and think it would be good to know information regardless.

---

