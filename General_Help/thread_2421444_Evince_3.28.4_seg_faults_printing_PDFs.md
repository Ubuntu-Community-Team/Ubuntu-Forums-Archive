---
title: "Evince 3.28.4 seg faults printing PDFs"
date: 2019-06-21
forum: General Help
---

### Post by cscj01 on 2019-06-21
I have Ubuntu 18.04.2 and Evince 3.28.4.  Evince suddenly stopped printing PDF documents today with a segfault ```
Jun 21 16:55:59 Car-Photo-Ubuntu kernel: [193238.574375] evince[31110]: segfault at 5592c3d4a67a ip 00007feae88666d3 sp 00007ffc72c94cd8 error 4 in libc-2.27.so[7feae87ab000+1e7000]
```.  If I go to a command line, I get the following:```
sudo evince 
No protocol specified
Unable to init server: Could not connect: Connection refused
Cannot parse arguments: Cannot open display:
```> I had to use sudo because if I just use evince, I can open a PDF.  However.I cannot print because I get the segfault.
I have 2 different print drivers; the standard epson one and TurboPrint.  They both yield the same results.

The same document prints in xpdf with no problems.

I noticed that a security issue was posted here [https://usn.ubuntu.com/4024-1/]("https://usn.ubuntu.com/4024-1/")
I updated my system but still have the problem.  I think this update was pushed out yesterday.  That would be consistent with when my Evince stopped working correctly.

Does anyone have any insight about what is happening and how to fix it?

---

### Post by Impavidus on 2019-06-22
**sudo evince** is a red flag. You should never run sudo evince. Whenever you run GUI applications (really: any application that makes a lot of writes to config files) as root, change the environment to root's environment so that it writes to root's config files. I.e., use the -H option to change the home directory.

But you should never have to run evince as root. If your ordinary user has read permissions on the pdf file, you can use evince with your own account. If not, you're trying to read someone else's file who hasn't given permission or something's wrong. The only system pdf files are documentation and should be readable for all.

This all suggests you've some seriously messed up permissions, which can be the result of careless sudo use. Like running sudo evince. Do you get any output from the following command:```
find ~ -user root -ls
```You shouldn't.

---

### Post by cscj01 on 2019-06-22
> **Impavidus said:**
> **sudo evince** is a red flag. You should never run sudo evince. Whenever you run GUI applications (really: any application that makes a lot of writes to config files) as root, change the environment to root's environment so that it writes to root's config files. I.e., use the -H option to change the home directory.

But you should never have to run evince as root. If your ordinary user has read permissions on the pdf file, you can use evince with your own account. If not, you're trying to read someone else's file who hasn't given permission or something's wrong. The only system pdf files are documentation and should be readable for all.

This all suggests you've some seriously messed up permissions, which can be the result of careless sudo use. Like running sudo evince. Do you get any output from the following command:```
find ~ -user root -ls
```You shouldn't.

Here's the output for the command:[HTML]find ~ -user root -ls
 33424403      4 -rw-r--r--   1 root     root          326 May 15 14:34 /home/butch/Downloads/SA00086/SA-00086-Car-Photo-Ubuntu-2019-05-15-18-34-19.log
 33424411      4 -rw-r--r--   1 root     root         1026 May 15 14:34 /home/butch/Downloads/SA00086/SA-00086-Car-Photo-Ubuntu-2019-05-15-18-34-19.xml
 16392504      0 srwx------   1 root     root            0 Feb 16 00:14 /home/butch/.gnupg/S.gpg-agent.browser
 16392496     16 -rw-r--r--   1 root     root        13011 Feb 16 01:07 /home/butch/.gnupg/pubring.kbx
 16388858      0 -rw-------   1 root     root            0 Apr 19  2018 /home/butch/.gnupg/pubring.gpg
 16392457      0 srwx------   1 root     root            0 Apr 28 23:40 /home/butch/.gnupg/S.dirmngr
 16392505      0 srwx------   1 root     root            0 Feb 16 00:14 /home/butch/.gnupg/S.gpg-agent.ssh
 16392503      0 srwx------   1 root     root            0 Feb 16 00:14 /home/butch/.gnupg/S.gpg-agent.extra
 16388853      0 -rw-------   1 root     root            0 Apr 19  2018 /home/butch/.gnupg/secring.gpg
 16392497     12 -rw-r--r--   1 root     root        10542 Feb 16 00:14 /home/butch/.gnupg/pubring.kbx~
 16392502      0 srwx------   1 root     root            0 Feb 16 00:14 /home/butch/.gnupg/S.gpg-agent
 20971788    232 -rw-r--r--   1 root     root       234834 Jul 14  2018 /home/butch/.config/GIMP/2.9/pluginrc
 46009784      4 drwxr-xr-x   2 root     root         4096 Sep  4  2018 /home/butch/.rpmdb
 46009785      0 -rw-r--r--   1 root     root            0 Sep  4  2018 /home/butch/.rpmdb/.dbenv.lock
 46009794      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Providename
 46009791      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Basenames
 46009789      8 -rw-r--r--   1 root     root        12288 Sep  4  2018 /home/butch/.rpmdb/Packages
 46009798      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Dirnames
 46009797      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Triggername
 46009786    168 -rw-r--r--   1 root     root       311295 Feb 23 01:08 /home/butch/.rpmdb/__db.001
 46009788     96 -rw-r--r--   1 root     root       110591 Feb 23 01:08 /home/butch/.rpmdb/__db.003
 46009800      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Sigmd5
 46009792      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Group
 46009796      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Obsoletename
 46009799      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Installtid
 46009787     80 -rw-r--r--   1 root     root        81919 Feb 23 01:08 /home/butch/.rpmdb/__db.002
 46009801      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Sha1header
 46009790      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Name
 46009793      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Requirename
 46009795      8 -rw-r--r--   1 root     root         8192 Sep  4  2018 /home/butch/.rpmdb/Conflictname
 42731868      4 drwx------   3 root     root         4096 Jul 14  2018 /home/butch/.dbus
find: ‘/home/butch/.dbus’: Permission denied
 16392801    168 -rw-------   1 root     root       169964 Jul 16  2018 /home/butch/.local/share/gvfs-metadata/home
 42731871      4 drwx------   2 root     root         4096 Jul 16  2018 /home/butch/.cache/dconf
find: ‘/home/butch/.cache/dconf’: Permission denied
 42731997      4 drwx------   2 root     root         4096 Jul 16  2018 /home/butch/.cache/gvfs-burn
find: ‘/home/butch/.cache/gvfs-burn’: Permission denied
 42731909      4 drwx------   2 root     root         4096 Jul 16  2018 /home/butch/.gvfs
find: ‘/home/butch/.gvfs’: Permission denied
[/HTML]Since I should not get these messages, what's wrong?  Also, this may explain the [HTML]sudo evince[/HTML]messages, but I still have the problem of launching evince, which opens PDFs as it should, but will not print.

---

### Post by Impavidus on 2019-06-22
Some programs, in particular GUI programs integrated into your desktop environment, produce many small files in your home directory. If you run those programs as root, without changing the root directory to /root, you'll get root-owned files in your home directory. When you run a program as your own user, it can no longer modify those files, maybe not even read them, which gives errors. You can avoid this by using sudo -H (which changes the home directory for the process running as root to root's home directory), by editing files with sudoedit instead of sudo <your text editor> (which will take even more precautions, as it won't run the text editor as root) or by using programs that write to less files. Furthermore, only use sudo when you need it and when you know why you need it. It doesn't work without sudo, so let's try it with sudo isn't good enough. It looks like you've run a lot of stuff with sudo that should have run without it. Don't feel ashamed, I made the same error when I'd just installed Ubuntu 12 years ago.

Basically, everything in your home directory should be owned by you. Everything should be assigned to your own group (for home users), except when you have a special reason to assign it to a different group. So assuming it should all be your own group, this will fix ownership:```
sudo chown -R $USER:$USER $HOME
```I don't know what every file and directory in that output you posted is for and I don't know if fixing it will fix your printing problem, but a .dbus and a .gvfs owned by root can give weird errors.

---

### Post by cscj01 on 2019-06-22
[HTML]
sudo chown -R $USER:$USER $HOME[/HTML]took care of the ownership issue.  I still have the same issue with Evince printing.  Here's some of the information I get:
```

SegAnalysis

Segfault happened at: 0x7f8a802b36d3<__memmove_sse2_unaligned_erms+435>:    moveups -0x10(%rsi,%rdx,1),%xmm8
PC(0x7f8a802b36d3) ok
source "-0x10(%rsi,%rdx,1)" (0x55cf7aef22fa) not located in a known VM region (needed readable region)!
destination "%xmm8: ok

SegvReason

Reading unknown VMA

```
There's a lot more there, but since I can't copy out of the window, it's too tedious to type it.

---

### Post by cscj01 on 2019-06-24
Bump

---

### Post by Claus7 on 2019-06-25
Hello,

the errors you are getting are related with permission issues, which means that you have not completely solved your problem with them. One way to verify this is to create a new user and try to print. Then you could remove your printers and try to install them anew. You face printing issues only with evince or with other programs as well?

Regards!

---

