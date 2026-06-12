---
title: "Inconsistant downloads ?"
date: 2022-03-30
forum: General Help
---

### Post by IRQsRFun on 2022-03-30
I have been trying to download a very large file (71.9GB) and I am unable to get a consistent MD5 sum for the file. None of the downloaded files have the correct MD5 sum.

**~/Downloads$ md5sum Xilinx_Unified_2021.2_1021_0703.tar.gz
991ae1928f7917c0c5ceac23ff943428  Xilinx_Unified_2021.2_1021_0703.tar.gz
**~/Downloads$ md5sum 'Xilinx_Unified_2021.2_1021_0703(1).tar.gz'
dadf2c536177e8451bbdf2aaf2b3a8a8  Xilinx_Unified_2021.2_1021_0703(1).tar.gz
**~/Downloads$ 
**~/Downloads$ md5sum 'Xilinx_Unified_2021.2_1021_0703(2).tar.gz'
d627effeaee8025d948eea3e765fa00f  Xilinx_Unified_2021.2_1021_0703(2).tar.gz
**~/Downloads$

Wen I tried to download the file using my Windows 10 virtual machine, I twice got  a download failed message less than 5 minutes before the download is complete.


Any suggestions would be appreciated.  I have tried resetting my router and modem as well as a hard reboot of the computer.

---

### Post by ActionParsnip on 2022-03-31
[http://ew-dev.physi.uni-heidelberg.de/~rubio/software/FPGAs/](http://ew-dev.physi.uni-heidelberg.de/~rubio/software/FPGAs/)

a 72Gb file.....Daaaaamn

---

### Post by coffeecat on 2022-03-31
Try using wget from the terminal. If you use the -c flag, you can continue an interrupted download and (usually) end up with a uncorrupted file. I've found that useful in the past.

---

### Post by IRQsRFun on 2022-04-20
I was able to download the file with a raspberry PI B+ with an external hard drive.  

The PI downloaded at about 10MB/s which is about 30% slower than everywhere else.  My router is a little dated and perhaps a buffer filled up that was handled properly.

Thank you to everyone who tried to help.

---

### Post by ActionParsnip on 2022-04-20
Rebooting your router may help

---

### Post by HermanAB on 2022-04-20
Can your file system handle a 75 GB file? Otherwise, wget -c is the way to go as suggested above.

---

### Post by IRQsRFun on 2022-04-24
I have some confounding evidence to my issue.  

I ran the following from an ubuntu terminal:

**:/media/kevin/No Label/bigfiletest$ sudo cat /dev/random > testFile
^C
**:/media/kevin/No Label/bigfiletest$ ls -l testFile
-rw-rw-r-- 1 kevin kevin 30529683456 Apr 24 08:05 testFile
**/media/kevin/No Label/bigfiletest$ md5sum testFile
91964b1d1a0014f57b1d77205c1747e4  testFile
**:/media/kevin/No Label/bigfiletest$ cp testFile testFile2
**:/media/kevin/No Label/bigfiletest$ md5sum testFile2
2c1ef7524e6a0908d8646713147aaa4b  testFile2
 

Basically, I am checking that a copy of a file should have the same md5sum as the original.  the copy does not.  Therefore copy does not work with extremely large files.  My hardware is a recent Ryzen B550 system.

When I have time, I will fix my accounts stuff so that I have an Ubuntu One Account so that I can submit a bug report.

---

