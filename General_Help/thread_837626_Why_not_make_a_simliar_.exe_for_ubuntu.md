---
title: "Why not make a simliar .exe for ubuntu?"
date: 2008-06-22
forum: General Help
---

### Post by Hamstermerc on 2008-06-22
I'm new to the linux world so please hold the laughter as this is probably a stupid question. Nevertheless why not make a general installer for linux like windows' .exe? I understand there is a difference between the different distrubutions but surely there must be a simple way to install a program on any linux distro avoiding much use of terminal and code. 

Installation problems have been my big learning curve so far and is probably what holds a lot of people back. So why isn't there one?

Also i've just installed americas army through a .run file and it was so simple. Once i got past the little bit of code to get it going it felt comfortable and easy. Is this not possible for all programs?

---

### Post by damis648 on 2008-06-22
Ubuntu is based on Debian, and uses the Debian standard package, *.deb
All you have to do is download a deb and double click to install. Is this what you meant? But keep in mind we have synaptic and "Add/Remove" from the applications menu. Isn't that easier than either of these anyway?

PS. for debs try getdeb.net

---

### Post by Anzan on 2008-06-22
While there are a number of ways to install programs, almost everything you could need is found in the repositories. 

Using APT through Synaptic, aptitude, apt-get, or the simplified Add/Remove programs menu is unparalleled for its simplicity and its grace in handling dependencies.

It is Windows that needs a unified installation process.

---

### Post by damis648 on 2008-06-22
> **Anzan said:**
> 
Using APT through Synaptic, aptitude, apt-get, or the simplified Add/Remove programs menu is unparalleled for its simplicity and its grace in handling dependencies.

It is Windows that needs a unified installation process.

+1 Where is the Windows unified process? Try the repositories! Applications>Add/Remove has all the software you could ever need!

---

### Post by steveneddy on 2008-06-22
So we are comparing to Windows again?

[COLOR="Blue"]**This is not Windows, it is Linux**[/COLOR].

If you don't like code, look for .deb files.

Open **Synaptic Package Manager** and search for the application you want:

> 
System --> Administration --> Synaptic Package Manager


Or in the [COLOR="Blue"]Application[/COLOR] menu, choose [COLOR="Blue"]Add/Remove Programs[/COLOR] option.

Or if you DL source code, just unpack it, read the "[COLOR="Red"]Read Me[/COLOR]" file and follow the instructions.

Installing from source is the preferred method, and all the cool kids are doing it this year.

Maybe [read this]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_packages_.28programs.29_and_libraries"). It will help you understand it a little better.

---

### Post by Pjotr123 on 2008-06-22
Read here a bit about the various ways of installing software:
[http://ubuntutip.googlepages.com/installingapplications](http://ubuntutip.googlepages.com/installingapplications)

---

### Post by issih on 2008-06-22
Basically, its what you are used to, Windows seems simple because you know how to do it, not because it actually easier.

That said the fractured nature of linux distributions means that it isn't simply a case of being able to have one simple installation mechanism. Too many people use different kernels, and have different supporting programs installed. Because the exact nature of the os environment can vary from one pc to another, never mind one distribution to another, its impossible to have just one way of installing things that will work on any "linux" pc.

In essence linux is too broad and varied for that to happen without massive unprecedented cooperation between all the different source distros. Windows can get away with it because they make everyone wear the same clothes. Linux gives you a choice, but if you try and wear sandals with your suit its up to you to make the look work.

If you use a debian based distro (ubuntu) stick to .deb packages and ideally repositories and things will all be very smooth.

If you use an rpm one, again life is easiest if you stay within your ecosystem, although tools do exist to allow people to convert things.

Finally, when it comes to building from source, it can seem confusing, but you just have to get your head around it, or wait for someone kind to do the build for you and package it up nicely in a .deb for you.

It seems confusing because you are used to downloading one file and clicking it. Its no harder to tick a box in synaptic and have something installed. You only have trouble when you want something a bit more esoteric that isn't in the repositories, and then its only the relative sizes of linux vs windows userbases that means windows is any better. For windows there will virtually always be someone who has paved the way before you, because there are so very many users. That is probably also true for linux, but finding the guide can be much much harder...

---

### Post by Hamstermerc on 2008-06-23
Thanks for answering my question. I'm slowly getting used to different installation codes and the various package managers but thankyou for explaining why there isn't one unified installation method. I am not afraid to learn and these forums are a fantastic help so thanks again :)

---

### Post by brett123 on 2008-06-23
Installing applications is/was one of the hardest things for me to comprehend having come across from Windows. Please don't forget that all mighty advanced users. ;)

Sure, now I have no problem, but in the beginning it was incredibly frustrating - maybe **the** most frustrating part of making the change?!?!?

---

### Post by Zorael on 2008-06-23
> **issih said:**
> Basically, its what you are used to, Windows seems simple because you know how to do it, not because it actually easier.
This sentence is made of distilled truth in its purest form, and earns a thanks from me for its empirical clarity.

---

### Post by amdlintuxos on 2008-06-23
[COLOR="DarkGreen"][B]linux way is the easiest and simplest way to install SW.
Just need to understand this way, using sinaptic. 
The terminal is not necessery at all[/B][/COLOR]

---

### Post by easybake on 2008-06-23
While we're at it, why don't we make more malware and spyware for linux. I really miss that stuff.

---

