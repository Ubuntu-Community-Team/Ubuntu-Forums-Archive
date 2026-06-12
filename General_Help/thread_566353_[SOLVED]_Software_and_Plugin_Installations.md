---
title: "[SOLVED] Software and Plugin Installations"
date: 2007-10-03
forum: General Help
---

### Post by Eagle2005 on 2007-10-03
I am having trouble installing Java as well as installing skype on Ubuntu.

Additionally how do i find out what version of Ubuntu i'm running?

---

### Post by gautada on 2007-10-03
> **Eagle2005 said:**
> I am having trouble installing Java as well as installing skype on Ubuntu.

Additionally how do i find out what version of Ubuntu i'm running?

For Java I use the blackdown JVM which I installed via synaptic.  Sorry, but I run an amd64 and my skype install is different from a 32 bit machine which I assume you have.

---

### Post by Seisen on 2007-10-03
To find out what version of Ubuntu you are using just go to System>About Ubuntu and it should state their what version you have. To install Java go here

[https://help.ubuntu.com/community/Java?highlight=%28Java%29]("https://help.ubuntu.com/community/Java?highlight=%28Java%29")

for Skype 

[https://help.ubuntu.com/community/Skype?highlight=%28Skype%29]("https://help.ubuntu.com/community/Skype?highlight=%28Skype%29")

---

### Post by FuturePilot on 2007-10-03
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```
Restart Firefox when done.

---

### Post by divague on 2007-10-03
Go to system menu and choose about ubuntu, there shouldb e the version taht you're running

---

### Post by Eagle2005 on 2007-10-03
> **Seisen said:**
> To find out what version of Ubuntu you are using just go to System>About Ubuntu and it should state their what version you have. To install Java go here

[https://help.ubuntu.com/community/Java?highlight=%28Java%29]("https://help.ubuntu.com/community/Java?highlight=%28Java%29")

for Skype 

[https://help.ubuntu.com/community/Skype?highlight=%28Skype%29]("https://help.ubuntu.com/community/Skype?highlight=%28Skype%29")

Thanks to the post made by Seisen i was able to figure out the version of Ubuntu

"Thank you for your interest in Ubuntu 6.06 LTS
                - the Dapper Drake - released in June 2006."

However the Skype Documentation that I was linked to didn't tell me anything new that i didn't already know.  The problem i'm having with skype is that when I download and attempt to install the debian package it generates an error message: Error: Dependency is not satisfiable: libasound2

---

### Post by Eagle2005 on 2007-10-03
> **FuturePilot said:**
> ```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```
Restart Firefox when done.

This command doesn't work for me in the terminal

---

### Post by Eagle2005 on 2007-10-03
> **gautada said:**
> For Java I use the blackdown JVM which I installed via synaptic.  Sorry, but I run an amd64 and my skype install is different from a 32 bit machine which I assume you have.

I need JRE not JVM

---

### Post by por100pre1 on 2007-10-03
> **Eagle2005 said:**
> This command doesn't work for me in the terminal

Please try [this]("https://help.ubuntu.com/community/Java").

---

### Post by Eagle2005 on 2007-10-05
> **por100pre1 said:**
> Please try [this]("https://help.ubuntu.com/community/Java").

That doesn't help me any.

---

### Post by Eagle2005 on 2007-10-05
I'm looking for a way to load Sun Java Runtime Environment 6.x onto Ubuntu 6.06, preferably without having to do command line.

---

### Post by gautada on 2007-10-08
> **Eagle2005 said:**
> I need JRE not JVM

The Java Runtime Environment (JRE) is roughly equivalent to the Java Virtual Machine (JVM).

---

### Post by FuturePilot on 2007-10-08
> **FuturePilot said:**
> ```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```
Restart Firefox when done.

> **Eagle2005 said:**
> This command doesn't work for me in the terminal

> **Eagle2005 said:**
> I'm looking for a way to load Sun Java Runtime Environment 6.x onto Ubuntu 6.06, preferably without having to do command line.
This command will only work if you have the backport repo enabled. Java 6 was backported to Dapper a while ago.
Go System>Administration>Software Properties. I can't remember where exactly, I think it might be under the Updates Tab, but somewhere there is a check box to enable the backports. It will says something like Unsupported Updates(Backports) or similar. Then when it asks you click the Reload button. Then that command will work.

---

### Post by Eagle2005 on 2007-10-15
I just got so fedup that i decided it was better just to reinstall with Feisty Fawn, alot less bugs seem to be in Feisty Fawn than in 6.06, thanks anyways.

---

