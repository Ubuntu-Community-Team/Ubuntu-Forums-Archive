---
title: "Can I install Java Virtual Machine?"
date: 2007-05-04
forum: General Help
---

### Post by jester805 on 2007-05-04
Hey guys-
I just installed Feisty on my Dell laptop.  We have a Cisco CallManager phone system at work that requires me to use Internet Explorer and have Java Virtual Machine installed.  Is there a way that I can install the Java VM on Feisty??

If not, could this be done in Wine?  If it can, could someone please post instructions for me?

Any help is appreciated! :) 
Thanks a lot!

---

### Post by Steven_B on 2007-05-04
You can install Java natively using apt:
```
sudo apt-get install sun-java6-jre
```
You can also install the sun-java6-jre package via synaptic, if you prefer.  You can't run IE natively, so you may also have to run Java via wine for IE to be able to use it.

---

### Post by jfinkels on 2007-05-04
And once you install wine, IE should be pretty simple. Here's one place you can get it in a jiffy [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by jester805 on 2007-05-04
Thanks for the quick replies.

I did download and install Java.  I also downloaded and installed the **IEs4Linux** and it works great.  However, I still get the error message on the web page telling me that I must install the Java Virtual Machine.

I will attach a screenshot of the IE window so you can see it.

---

### Post by jester805 on 2007-05-05
Any thoughts?  :confused: :confused: :confused:

---

### Post by Steven_B on 2007-05-12
Do you have Java installed on Wine?  IE is blind to anything outside of ~/.wine/drive_c .

---

### Post by jester805 on 2007-05-14
When I try to install the Java VM (**msjavx86.exe**) using WINE, I get a prompt asking if I want to install it and I click on **Yes**.  After that, nothing happens.  :( :confused:

---

### Post by cypress.cynthia on 2007-08-13
Hello, I think I have found the solution to your problem. According to [this site,]("http://packages.ubuntu.com/feisty/virtual/java-virtual-machine") the following packages provide Java Virtual Machine for Ubuntu Linux: jamvm, sablevm. After you download and install them, please let me know if you can now use the application that requires the Java Virtual Machine program to be installed.

---

### Post by cypress.cynthia on 2007-09-29
Hello again, to install Java Virtual Machine in Ubuntu please follow the instructions posted [here]("http://ubuntuforums.org/showthread.php?p=3447377#post3447377"). Hope they work for you! :) ;)

---

