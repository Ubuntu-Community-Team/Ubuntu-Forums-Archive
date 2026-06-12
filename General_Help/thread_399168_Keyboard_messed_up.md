---
title: "Keyboard messed up"
date: 2007-04-02
forum: General Help
---

### Post by FrustratedGuy on 2007-04-02
Hello, it´s been a long time since the last time I tried to put Kubuntu on. I have to say, I like the fact that this time around, my ra0 was automatically configured. Last time, being unable to get online was the main reason I (for a while) scrapped my Linux install in favor of Windows XP.

Now, I have a dual-boot XP-Kubuntu system I´m thrilled with -- for the most part. Right now, it´s probably obvious, but: I can´t type quotes, single or double. There may be other problems, but I haven´t found any yet.

If I hit the quote key twice, I get what you´ve been seeing: the ´. If I Shift-quote twice, I get this: ¨ Pressing this key once and another key can give me ö, é, á ä, etc.

Much as that can be useful, I kinda need quotes for, if nothing else, writing code. I don´t want to think about how a C++ compiler will puke all over any attempt at a string or file access. :(

I think I did this by mistake when setting up Linux, but I want to know how I can possibly fix this.

Thanks,

Timothy

---

### Post by epdp14 on 2007-04-02
When I switched from XP to Ubuntu, I had problems with keyboards as well. I suggest trying keytouch, it allows you to change key bindings graphically and there are many pre-made keyboard setups available that enable the extra keys on many higher end keyboards.

---

### Post by FrustratedGuy on 2007-04-02
> timothy@ubuntu:~$ sudo dpkg -i keytouch_2.2.99+2.3.0beta5-0ubuntu1_i386.deb
(Reading database ... 81057 files and directories currently installed.)
Preparing to replace keytouch 2.2.99+2.3.0beta5-0ubuntu1 (using keytouch_2.2.99+2.3.0beta5-0ubuntu1_i386.deb) ...
Unpacking replacement keytouch ...
Setting up keytouch (2.2.99+2.3.0beta5-0ubuntu1) ...

timothy@ubuntu:~$

It appears to have installed, but I can´t find it. I apologize, I am a total newbie at this. :)

EDIT: I found it, but I have a problem: KeyTouch doesn´t support a Kensington. :(

---

### Post by FrustratedGuy on 2007-04-02
Figured it out. Regional Settings on my keyboard somehow got disabled between installation and that "oem-config-prepare" business. :)

" ' ' " '''' """" They work. :)

---

