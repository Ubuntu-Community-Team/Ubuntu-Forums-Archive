---
title: "Moving to ubuntu on a tablet"
date: 2013-08-30
forum: General Help
---

### Post by Los Frijoles on 2013-08-30
I am eventually going to be replacing my netbook computer with a tablet once the fan fails (it stops occasionally, causing overheating and sudden shutdowns, and replacements are more than the value of the computer). However, I want to essentially have the tablet take over the function of my netbook which is mostly note taking and web browsing for classes. However, I also am taking several programming and engineering courses and it would be quite handy to still be able to complete the assignments for those classes which use applications not normally available for android.

Here is my question: What sort of support for not-so-regular applications (let's say Dia, Sublime Text, gcc, make, tomboy notes, and latex) would Ubuntu for tablets have? Does it have a normal build system and such or is it just a shell around android and actually just runs the same things? Does it have a bash console?

I guess what I am really asking is, how does it work underneath? Is it simply linux compiled for whatever processor is used in the tablet or is it more like android in terms of what it can run? I am having a hard time wording the question since I am not entirely familiar with android or tablets in general, not actually owning one as of yet.

I've had a difficult time finding out what exactly it supports doing other than taglines like "All the applications you normally use". I get the impression it really is a separate operating system which makes me wonder if it is just like things like the operating systems for the Raspberry Pi which are simply linux and everything else just compiled for arm. That would actually be the ideal for me, if it were simply ubuntu and its applications compiled for the processor of the tablet, but still retaining the features I commonly use such as the build system and the console.

A description of the netbook I might replace with a tablet running Ubuntu:
- Runs Arch Linux with the XFCE desktop environment using lots of gnome applications
- Used for web browsing, notes (tomboy right now, but I am not particularly attached to tomboy), word processing, and writing latex documents most of the time
- Used for programming/compiling things in C, C++, Java for completing assignments for my courses
- Used for messing with scripting things in Python and Bash for when I am bored

---

### Post by Maheriano on 2013-08-30
As far as I know Ubuntu can only be installed on specific tablets:
- those with x86 architectures
- those with ARMv7 chips
- Nexus tablets

---

### Post by Los Frijoles on 2013-08-30
I was planning on using a Nexus 7 or 10.

---

### Post by grahammechanical on 2013-08-30
You really need to read up on Ubuntu Touch. Get the facts from the right source. Do not go by rumour and speculation. Which, with all respect, can be available on a forum. There is also a section on this forum set aside for mobile discussions.

[https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install)

Ubuntu touch is not a separate operating system. The intention is for one Ubuntu platform that will run on Phones, Tablets and PCs with a core set of phone/tablet applications that will scale according to the screen size and when the phone/tablet is connected to a monitor it will run the Ubuntu Desktop with the usual set of applications that come with the Ubuntu distribution. It will be one Ubuntu platform in the code base. Touch is the user Interface for mobile. Unity 8 is the user interface for the desktop. This is what is meant by the term "convergence."  It is an OS for a mobile phone/tablet/PC in one device.

A lot will depend upon the hardware specification of any mobile device. Especially storage because it will be possible to install applications like we do right now on the desktop as well as apps developed especially for mobile devices.

The Ubuntu specification is for a quad core Arm Cortext-A9 CPU but many developers are working on porting Ubuntu Touch to other CPUs. Raspberry Pi does not fit the specification.

Regards.

---

