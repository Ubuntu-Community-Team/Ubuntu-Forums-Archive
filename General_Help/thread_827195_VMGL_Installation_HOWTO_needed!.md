---
title: "VMGL Installation HOWTO needed!"
date: 2008-06-12
forum: General Help
---

### Post by nemesis93 on 2008-06-12
I really need a VMGL installation guide that is noob-friendly.
I do not have any knowledge on how to install anything on Ubuntu as I am knew to Ubuntu.
I currently writing this on Ubuntu 8.04 running on VMware. I am testing out Ubuntu and testing to see if i really like it, Hopefully in the future i will like it a lot and will switch to making my Primary OS Ubuntu instead of Windows XP.

I tryed to follow the instructions on the VMGL homepage which is:
[http://www.cs.toronto.edu/~andreslc/xen-gl/](http://www.cs.toronto.edu/~andreslc/xen-gl/)
I do not understand not one of the Steps that they give on that Webpage!
Please help me!

Thanks.

---

### Post by kdcoetzee on 2008-06-12
I have no idea what VMGL is, but ubuntuguide.org is a very handy site.
it will help you setup your Ubuntu. 

if you have a package name of VMGL 

the normal routine for installing stuff on Ubuntu/Debian is APT
sudo apt-get install packagename.

It seems you need to compile the package, extract it;./configure;make;make install.

there is usally a README in the tar file that explains how to install the package.

I found a yahoo answer that says VMware does not support VMGL. [http://answers.yahoo.com/question/index?qid=20080612111412AAtwNEd]("http://answers.yahoo.com/question/index?qid=20080612111412AAtwNEd")

Hope I said something that will help you.

---

### Post by nemesis93 on 2008-06-12
OMG LOL! That same question you found on Yahoo! Answers was mine once again!
I've been searching all over the net on how to install this program.
Basically what this does is it allows some OpenGL Applications to run on VMware. 
Now VMware is a a virtual Machine tool which is commonly used for testing operating systems.
It supports All windows, Mac, Most Linux distros, etc. 
On the other hand, VMGL is a new project that trys to integrate OpenGL into virtual machines, In other words im trying to see if i could get the Visual Effects to work on a Virtual Machine. 
I unfortunately cannot find the way to install ubuntu on my desktop SO i have to run it through virtual Machine software so i am trying to configure VMGL to work so i could get the most out of Ubuntu even if it is running on a virtual machine.
And by the way VMware does Support VMGL says it on the VMGL website here:
[http://www.cs.toronto.edu/~andreslc/xen-gl/](http://www.cs.toronto.edu/~andreslc/xen-gl/)
This is my other unsolved question that i posted on this forum trying to get an answer:
[http://ubuntuforums.org/showthread.php?p=5173797#post5173797](http://ubuntuforums.org/showthread.php?p=5173797#post5173797)

Note: I have been trying to install Ubuntu on my computer for a week now!

---

### Post by kdcoetzee on 2008-06-13
I now how you feel i search high and low for a way to connect to a Microsoft SQL server thru Linux without using a virtual machine or wine. But never found anything.

Your cd worked fine when installing Ubuntu on VMware, but when you try it on the machine self it does not work. ?

OK there is two paths we can take. The one is to compile the tar.gz file or you can install a program named alien , and convert the rpm file to deb. 
so you can install it normally.

Have you already installed the program ? how far are you ? I just want to know so we are on the same level.

---

### Post by Dedoimedo on 2009-01-14
Hi,

Maybe this is a bit late ... but I was going through posts tags this or that ... I thought you deserve an answer.

I did not manage to successfully run vmgl, for a simple reason: the packages are broken ... In addition to that, quite a bit of what needs to be done is not said or mentioned ... You're in for a lot of guesswork trying to hack a 6+ years old vnc server.

I've written about it, if you're interested (probably not):
[http://ubuntuforums.org/showthread.php?t=1029367](http://ubuntuforums.org/showthread.php?t=1029367)

Here's you answer, fealls :(

Cheers,
Dedoimedo

---

