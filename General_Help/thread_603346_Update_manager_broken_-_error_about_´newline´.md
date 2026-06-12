---
title: "Update manager broken - error about ´newline´"
date: 2007-11-05
forum: General Help
---

### Post by phi1ip on 2007-11-05
Hello, I am trying to use the update manager. but have problem.

I get an error  message. I am now at 144 updates...I am still on 7.04. The problem was here 4 months ago at least, but there was only about 9 updates at that time. so its not related to the fact there are 144 i think.

The updates are downloaded no problem. but when i try to install them i get the message below.

[I][B]E: /var/cache/apt/archives/bsdutils_1%3a2.12r-17ubuntu2.1_i386.deb: files list file for package `perl-modules' is missing final newline
[/B][/I]

suggestions?

---

### Post by dcstar on 2007-11-05
> **phi1ip said:**
> Hello, I am trying to use the update manager. but have problem.

I get an error  message. I am now at 144 updates...I am still on 7.04. The problem was here 4 months ago at least, but there was only about 9 updates at that time. so its not related to the fact there are 144 i think.

The updates are downloaded no problem. but when i try to install them i get the message below.

[I][B]E: /var/cache/apt/archives/bsdutils_1%3a2.12r-17ubuntu2.1_i386.deb: files list file for package `perl-modules' is missing final newline
[/B][/I]

suggestions?

Try deleting/renaming that particular file as it could be a corrupt download, it should be downloaded again.

---

### Post by Maestro23 on 2007-11-05
> **phi1ip said:**
> Hello, I am trying to use the update manager. but have problem.

I get an error  message. I am now at 144 updates...I am still on 7.04. The problem was here 4 months ago at least, but there was only about 9 updates at that time. so its not related to the fact there are 144 i think.

The updates are downloaded no problem. but when i try to install them i get the message below.

[I][B]E: /var/cache/apt/archives/bsdutils_1%3a2.12r-17ubuntu2.1_i386.deb: files list file for package `perl-modules' is missing final newline
[/B][/I]

suggestions?

Go into **/var/cache/apt/archives** and try and delete the .deb in question.

---

### Post by phi1ip on 2007-11-05
i went into the synaptic package manager and it wanted to uninstall half my system because of the dependencies on the perl-module from other stuff. was worried would lose xwindows. so going for second option of deleting the file
....hold on....

---

### Post by phi1ip on 2007-11-05
how do i downloadit again

***sudo apt-get perl-modules install***

the above is my guess, is that right?

---

### Post by Maestro23 on 2007-11-05
> **phi1ip said:**
> how do i downloadit again

***sudo apt-get perl-modules install***

the above is my guess, is that right?

Were you able to delete the .deb from archives?

To try and install it again:

> sudo apt-get install perl-modules

---

### Post by phi1ip on 2007-11-05
Hi, i notice i have deleted the perl-modules file. not the actual file with the error message.

how do i download the file again?

bsdutils_1%3a2.12r-17ubuntu2.1_i386.deb

---

### Post by phi1ip on 2007-11-05
i tried this.....   sudo apt-get install perl-modules

but it said it was already up to date. i only removed the file from the archives with ¨rm¨

---

### Post by phi1ip on 2007-11-05
Ok, i have a slightly better understanding now if someone could be so kind as to suggest how to solve the problem

seems var/cache/apt/archive is where apt-get and the update manager store downloads before they are installed.

i think i will keep getting this problem.....

i have done 

sudo apt-get clean

and this has deleted all the downloads. downloading all 144 again. but when it is finished i think i will get the newline error messages again.

Is there a problem with the download manager where it does not check for errors when downloading?

or is this an indication of many bad spots on my hard disk?

other problem people already know about? another bug?

thanks if u know.....my download will take an hour or so, so i&#314;l still be here.....

;-)

---

