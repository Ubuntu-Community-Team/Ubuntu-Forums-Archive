---
title: "[SOLVED] A few concerns"
date: 2007-09-21
forum: General Help
---

### Post by Eagle2005 on 2007-09-21
First let me start by saying that i just recently installed Ubuntu possibly server version on my computer at work earlier this week.  Now i am having a few problems, the computer is running slow as molasses.  My first question to you is how do i speed it up?

Secondly where i work have specialty software for furthering our employees education and that third-party software requires a certain screen resolution so my question to you is how do i adjust the screen resolution?

---

### Post by PmDematagoda on 2007-09-21
What's the video card you have?

---

### Post by mojoman on 2007-09-21
> **Eagle2005 said:**
> First let me start by saying that i just recently installed Ubuntu possibly server version on my computer at work earlier this week.  Now i am having a few problems, the computer is running slow as molasses.  My first question to you is how do i speed it up?

Secondly where i work have specialty software for furthering our employees education and that third-party software requires a certain screen resolution so my question to you is how do i adjust the screen resolution?

There is a configuration file for X server, /etc/X11/xorg.conf. You can adjust the resolution in that file. There are usually several resolutions stated but If I remember correctly the first stated resolution is used by default. 

There are other ways to change this as well but I think they differ between different desktop so you'll have to give more info on what you're running if you want more specific answers.

---

### Post by Eagle2005 on 2007-09-25
Some NVidia Card, i'm not sure where to look to find the exact card information.  I'm a noob to linux.

I've been so used to using windows and then overnight my workplace changes over to linux and user computers are now Ubuntu.

---

### Post by PmDematagoda on 2007-09-25
Try mojoman's advice, an nvidia card will very usually work properly with Ubuntu, as long a it isn't a "Just released" card because then it will take some time for the Linux driver to come out but not long.

---

### Post by Eagle2005 on 2007-09-25
Additionally i'd like to know how to access a command-line interface from within Ubuntu's GUI.

---

### Post by Eagle2005 on 2007-09-25
Additionally we're having trouble installing Sun Java Runtime Environment 6.0 or later

---

### Post by PmDematagoda on 2007-09-25
> **Eagle2005 said:**
> Additionally i'd like to know how to access a command-line interface from within Ubuntu's GUI.

Open up a terminal. That's your CLI.

---

### Post by PmDematagoda on 2007-09-25
> **Eagle2005 said:**
> Additionally we're having trouble installing Sun Java Runtime Environment 6.0 or later

I'm not very sure on the installation of Java, since I used Ubuntu Ultimate which installs it automatically.

---

