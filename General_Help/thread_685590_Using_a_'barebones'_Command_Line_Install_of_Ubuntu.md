---
title: "Using a 'barebones' Command Line Install of Ubuntu Gutsy on a Laptop"
date: 2008-02-02
forum: General Help
---

### Post by pelikan555 on 2008-02-02
Hi,

I am not an absolute beginner, having used various graphical Linux distros (and Mac and Windows) for a couple of years now so I know my way around the non-technical side of Linux pretty well and am quite adept at copying and pasting commands into the terminal :P,  but I am looking for some help regarding a couple of things I want to try and can't quite find the right information I need due to the vast multitude of information around the web! I am no programmer, so my knowledge of under-the-hood Linux is extremely basic &#8211; but I can do a lot of standard things like chmod, moving files, copying, wget etc etc.

What I am trying to do is achieve a state of simplicity on an oldish laptop I have &#8211; a Dell Inspiron 1300. I have installed a basic command-line version of Ubuntu with a view to using it as an everyday desktop system for simple word-processing (maybe Nano), web browsing (elinks probably), email (looking at Alpine) and reading .txt & .html files. I don't want anything graphical on it &#8211; the reasons being (a) save space, (b) save battery power, ( c) I want a distraction free non-fancy thingy just to type peacefully and research on the web. I am triple-booting with XP, Gnome Ubuntu and this CLI Ubuntu &#8211; so I have graphical interfaces if I desperately need.

Some questions:

1)The CLI screen is a black background with white text &#8211; can I reverse this? I have heard that it takes up more power to make a dark pixel than a white one and would prefer black text as a matter of personal preference anyway.
2)Are there any online resources about using a CLI Linux for everyday non-programming uses like I want to do? Just thought someone may have made a guide for people who don't know that much about Linux CLI.
3)Power-saving: How can I minimise power wastage and maximise battery life through the command line? The battery is very poorly &#8211; it says it has about 1 hour charge when 100%. One handy thing I do know is how to check battery life using &#8220;sudo acpi -b&#8221;. As many extra minutes as possible will be handy.
4)Is there a way to sort of hibernate or suspend in CLI?
5)Are there any specific Linux distributions for this sort of thing (with good repositories preferably) other than CLI Ubuntu? I rather prefer Debian-based distros but it doesn't really matter.
6)Any program suggestions, tips and links regarding CLI email, text/word processing, file browsing, or anything you can think of would be much appreciated too.

I am doing as much research as I can via search engines etc. &#8211; and may have further questions to add later &#8211; but thought I may get some of these questions answered more efficiently here. Sorry for the long post &#8211; thanks for any help. Ubuntuforums.org is a veritable gold-mine of information!

---

### Post by teacher bai on 2008-02-24
I have no clue about your questions pertaining to laptops - my knowledge doesn't extend that far, but I think this thread answers some of your questions about command line applications. Based on how you described your level of knowledge, this may be old news to you.

[http://ubuntuforums.org/showthread.php?t=387598&highlight=ubuntu+command+line+edition](http://ubuntuforums.org/showthread.php?t=387598&highlight=ubuntu+command+line+edition)

As for which distro to use, for a command line system, you might want to consider installing Debian itself. 

Also, I know you said you didn't want a GUI, but have you ever tried Damn Small Linux (DSL)? It does a lot and you can install it fast. Plus you still have the command line if you want it. Also, it is Debian based. They have 3.x and 4.x branches currently. You may wish to try both.

---

### Post by Yellow Pasque on 2008-02-24
I'd recommend Arch Linux for this sort of thing. It's all about elegant minimalism; the base install doesn't come with a window manager, it's optimized for PentiumII/i686 or later, it has a great package management system (pacman), it's very customizable, it uses a rolling-release system so you always have the latest stable packages with one command... I could go on.

---

### Post by kerry_s on 2008-02-24
mc= file manger & editor
links2= web browser

mc= sudo apt-get install mc
to use type " mc "

links2= sudo apt-get install links2
to use type " links2 -g google.com "

in debian you only have to do the mouse with->
dpkg-statoverride --update --add root root 4755 /usr/bin/links2

check your /etc/doc/links2 if it's the same for ubuntu.

if you want the mouse to use on mc, install " gpm "
sudo apt-get install gpm

it's not really needed, but some like the mouse

---

