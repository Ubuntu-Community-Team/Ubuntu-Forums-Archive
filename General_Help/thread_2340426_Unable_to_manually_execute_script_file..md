---
title: "Unable to manually execute script file."
date: 2016-10-18
forum: General Help
---

### Post by Douglas_H_Campbell on 2016-10-18
To give you some background the solution to a  bug report which I needed to fix a sound  
 problem, was the following:   

 
 
 > Thank you for your attention. The bug is not critical. The can be a
> workaround with adding the script during the system startup.
> hda-verb /dev/snd/hwC0D2 0x20 SET_COEF_INDEX 0x07
> hda-verb /dev/snd/hwC0D2 0x20 SET_PROC_COEF 0x7cb0 So, my script “foo.sh” is as follows:
 
 
 #!/bin/sh -e
 hda-verb /dev/snd/hwC0D2 0x20 SET_COEF_INDEX 0x07
 hda-verb /dev/snd/hwC0D2 0x20 SET_PROC_COEF 0x7cb0
 exit 0
 
 
 When I use the terminal to check it out I get:
 
 
 doug@doug-Ubuntu:~$  cd /home/doug/bin
 doug@doug-Ubuntu:~/bin$ ls -l foo.sh
 -rwxrwxr-x 1 doug doug 121 Oct 15 14:59 foo.sh
 doug@doug-Ubuntu:~/bin$ sudo su
 [sudo] password for doug:  
 root@doug-Ubuntu:/home/doug/bin# ./ foo.sh
 bash: ./: Is a directory
 root@doug-Ubuntu:/home/doug/bin# 
 
 
 Any suggestion for manually running the script to see if it works?  Thanks.

---

### Post by Impavidus on 2016-10-18
To execute the script, run```
./foo.sh
```In other words, don't type a space between ./ and foo.sh

---

### Post by Douglas_H_Campbell on 2016-10-18
Thanks for the reply.

Here's what I get using ./foo.sh:

root@doug-Ubuntu:/home/doug/bin# ./foo.sh
open: No such file or directory
root@doug-Ubuntu:/home/doug/bin# 


Any suggestion?  Thanks

---

### Post by Habitual on 2016-10-18
```
sh /home/doug/bin/foo.sh
```

---

### Post by Douglas_H_Campbell on 2016-10-18
Here's latest try:

ug@doug-Ubuntu:~$ cd /home/doug/bin
doug@doug-Ubuntu:~/bin$ ls -l
total 4
-rwxrwxr-x 1 doug doug 121 Oct 15 14:59 foo.sh
doug@doug-Ubuntu:~/bin$ sudo su
[sudo] password for doug: 
root@doug-Ubuntu:/home/doug/bin# sh /home/doug/bin/foo.sh
open: No such file or directory
open: No such file or directory
root@doug-Ubuntu:/home/doug/bin#

---

### Post by steeldriver on 2016-10-18
What exactly are the contents of the foo.sh file, and how did you create it? please post the output of the following commands

```

file foo.sh

cat foo.sh

```

(from the directory in which foo.sh resides).

---

### Post by Douglas_H_Campbell on 2016-10-18
doug@doug-Ubuntu:~$ cd /home/doug/bin
doug@doug-Ubuntu:~/bin$ ls -l
total 4
-rwxrwxr-x 1 doug doug 121 Oct 15 14:59 foo.sh
doug@doug-Ubuntu:~/bin$ file foo.sh
foo.sh: POSIX shell script, ASCII text executable
doug@doug-Ubuntu:~/bin$ cat foo.sh
#!/bin/sh -e
hda-verb /dev/snd/hwC0D2 0x20 SET_COEF_INDEX 0x07
hda-verb /dev/snd/hwC0D2 0x20 SET_PROC_COEF 0x7cb0
exit 0
doug@doug-Ubuntu:~/bin$

---

### Post by steeldriver on 2016-10-18
OK so having looked into the hda-verb utility a little, I suspect it means you don't actually have a /dev/snd/hwC0D2 device - what is the output of

```

ls /dev/snd

```

---

### Post by Douglas_H_Campbell on 2016-10-19
Interesting!

Here's output:

doug@doug-Ubuntu:~$ ls /dev/snd
by-path    hwC0D0  pcmC0D0c  pcmC1D10p  pcmC1D8p  pcmC2D1c  seq
controlC0  hwC1D0  pcmC0D0p  pcmC1D11p  pcmC1D9p  pcmC2D1p  timer
controlC1  hwC2D1  pcmC0D1p  pcmC1D3p   pcmC2D0c  pcmC2D2c
controlC2  hwC2D2  pcmC0D2c  pcmC1D7p   pcmC2D0p  pcmC2D4c
doug@doug-Ubuntu:~$

Thanks for your help.

---

