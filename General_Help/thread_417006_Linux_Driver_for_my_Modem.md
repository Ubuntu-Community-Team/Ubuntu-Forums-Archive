---
title: "Linux Driver for my Modem"
date: 2007-04-21
forum: General Help
---

### Post by s3a on 2007-04-21
I have a Conexant Modem with Chipset ESS 2838. I am using the Desktop Edition (32-bit) of Dapper Drake (6.0.6.1). Someone please help me choose which driver I need from this page ([http://www.linuxant.com/drivers/hcf/full/downloads-ubuntu-x86.php)](http://www.linuxant.com/drivers/hcf/full/downloads-ubuntu-x86.php)). From what I know, the kernel version of Dapper Drake is 2.6.15.

Thanks in advance!

P.S.
Please help me! I've been waiting sooo long for this!

---

### Post by helmut_hed on 2007-05-02
Hi s3a,

I don't believe any of the Linuxant drivers will support your ESS 2838 modem.  Normally those drivers are for Conexant modems.  I'm afraid I don't know of any source for ESS 2838 linux drivers.

Some types of PCTel and Lucent modems are known to work under Linux, as are the ESS 2898 modems.  You may be able to get one secondhand quite cheaply.

Good luck,
Jeff

---

### Post by orange2k on 2007-05-02
If it is a adsl modem that connects via USB then you are probably in trouble.
If you have the option to connect the modem via ethernet card then that`s the option to choose...

I have a Kasda external USB/ethernet modem that I used to connect via USB cable and it used to work just fine in windows and in Dapper Drake. But once I installed Feisty I couldn`t make it work no matter what I do. There are no drivers available for Linux. Then I read the help file in Feisty and it pointed me in the right direction: I had to plug a network card and connect the modem with the RJ-45 cable. Had to reinstall Feisty for my ethernet card to be recognized correctly and voila - everything works fine ever since.

---

