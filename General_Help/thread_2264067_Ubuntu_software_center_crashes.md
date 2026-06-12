---
title: "Ubuntu software center crashes"
date: 2015-02-05
forum: General Help
---

### Post by faneleshezitiger on 2015-02-05
every time I want to open the Ubuntu software center it starts loading the just crashes. Pleas help.

---

### Post by Elfy on 2015-02-05
*Thread moved to **General Help**.*

Before anyone is likely to be able to help, try running a few things from a terminal to help them.

First run it from terminal to see if that gives any clue.

```
software-center
```

See if there are apt issues causing it 

```
sudo apt-get update
```



> [B]Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.[/B]

---

### Post by faneleshezitiger on 2015-02-05
its still doing the same thing dont know what the problem is im not good with the terminal.

---

### Post by slickymaster on 2015-02-05
> **faneleshezitiger said:**
> its still doing the same thing dont know what the problem is im not good with the terminal.
All you have to do is to open a terminal window and run the code, one at a time, you were already provided. As you do it please copy the output you get from each command and past it here in the thread, using [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect.

Without that output we'll be unable to provide you any assistance regarding the issue you're facing.

---

### Post by oldrocker99 on 2015-02-05
If you can open a terminal and type this```
sudo apt-get install synaptic
```you'll be able to use it to install software a lot more easily and more quickly than the Software Center.

---

### Post by faneleshezitiger on 2015-02-13
i did that in my terminal 
but the i got this as a resolt 

fantheboos1@fanele-Q1742:~$ sudo apt-get install synaptic
[sudo] password for fantheboos1: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en%5fZA
E: The package lists or status file could not be parsed or opened.
fantheboos1@fanele-Q1742:~$ ^C
fantheboos1@fanele-Q1742:~$ sudo apt-get install synaptic

---

### Post by slickymaster on 2015-02-13
> **faneleshezitiger said:**
> i did that in my terminal 
but the i got this as a resolt 

fantheboos1@fanele-Q1742:~$ sudo apt-get install synaptic
[sudo] password for fantheboos1: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en%5fZA
E: The package lists or status file could not be parsed or opened.
fantheboos1@fanele-Q1742:~$ ^C
fantheboos1@fanele-Q1742:~$ sudo apt-get install synaptic
Let's try to remove the Merge List. Open a terminal window and run the following```
sudo rm /var/lib/apt/lists/* -vf
```After that generate a new one by running a simple update. Again in the terminal```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by faneleshezitiger on 2015-02-20
yeay it works thax all :D

---

### Post by slickymaster on 2015-02-20
> **faneleshezitiger said:**
> yeay it works thax all :D

Great.

Please mark your thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution.

---

