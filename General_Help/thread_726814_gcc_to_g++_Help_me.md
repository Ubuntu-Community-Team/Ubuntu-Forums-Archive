---
title: "gcc to g++ Help me"
date: 2008-03-17
forum: General Help
---

### Post by chathu on 2008-03-17
hi!,
I installed Ubuntu v 7.04  today...wow! nice and coool...But  i have a problem because i want to compile and run in  C++..but i saw g++ command is not working... and gcc command working..but i wanted to work in g++ command in vieditor... i download some g++ packages..but they are not compatible and during the installation stage they shows me a error!... My computer runs on Intel Dualcore 3.0 processor and ubuntu 7.04.. which version of g++ package is suitable for me? I need help hurryup!
bye
Chathu

---

### Post by lloyd_b on 2008-03-17
> **chathu said:**
> hi!,
I installed Ubuntu v 7.04  today...wow! nice and coool...But  i have a problem because i want to compile and run in  C++..but i saw g++ command is not working... and gcc command working..but i wanted to work in g++ command in vieditor... i download some g++ packages..but they are not compatible and during the installation stage they shows me a error!... My computer runs on Intel Dualcore 3.0 processor and ubuntu 7.04.. which version of g++ package is suitable for me? I need help hurryup!
bye
Chathu

Start by running (in a terminal window) "sudo apt-get install build-essential".  This will install all of the tools required to compile programs, either in C or C++.

The g++ version will be selected based on the gcc version - the two are parts of the same project...

Lloyd B.

---

### Post by chathu on 2008-03-17
I download g++ package from [http://packages.ubuntu.com/dapper/i386/g++/download](http://packages.ubuntu.com/dapper/i386/g++/download) here and trying to install it..but during the installation step this error shown...(see Attached Screenshot).. Plese guide me how to do this

[IMG]http://images.cjb.net/0d1dd.png[/IMG]

I download above package from [http://packages.ubuntu.com/dapper/i386/g++/download]("http://packages.ubuntu.com/dapper/i386/g++/download")
bye
Chathu

---

### Post by mc4man on 2008-03-17
Why not search gcc and g++ in synaptic and get what you need in compatible versions

---

