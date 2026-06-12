---
title: "antivirus"
date: 2007-06-01
forum: General Help
---

### Post by pardesi on 2007-06-01
is there any antivirus inbuilt or rather comes with the ubuntu CD or do we have to download .i already have a norton on my XP as i dual boot them

---

### Post by bmartin on 2007-06-01
I don't know anyone who has ever had a virus in Linux. Nevertheless, there is such a program: ClamAV.
```
sudo apt-get install clamav
```

I've never used it. You'll be very, very safe without it, especially if most of the things you install are from the repositories.

---

### Post by pardesi on 2007-06-01
thanks but i am new to linux so where should i write this code:confused:

---

### Post by tszanon on 2007-06-01
> **pardesi said:**
> is there any antivirus inbuilt or rather comes with the ubuntu CD or do we have to download .i already have a norton on my XP as i dual boot them
I don't know if there's an antivirus in the repositories, but I'm thinking about downloading Avast, so I can check my Windows partition for viruses once in a while.

---

### Post by pardesi on 2007-06-01
also how do i find the things installed .i instaled python but couldn't find that nywhere

---

### Post by loathsome on 2007-06-01
> **pardesi said:**
> thanks but i am new to linux so where should i write this code:confused:
In the terminal.

Press ALT+F2 and write «gnome-terminal»

---

### Post by bmartin on 2007-06-01
Sorry, my mistake.

You can use the **add/remove programs** menu item in Gnome. Search in there for a program called ClamAV.

You can also use the command I posted above, but you have to open a terminal and enter it into there. I wish I had a Linux PC in front of me right now so I could give you better directions :(

The terminal should be under your accessories menu. I don't use Gnome or KDE. It shouldn't be too hard to find the terminal program. If and when you get used to the terminal, you'll find that it's a great tool for doing most maintenance on your computer, especially adding and removing software.

---

### Post by pardesi on 2007-06-01
thanks8) but do you know where to find these installed programs after installing

---

### Post by bmartin on 2007-06-01
They're usually installed in an intuitive location in your menus. Python is an interpreter; it probably isn't in your menu, as it's not something you normally run directly. If you're looking to write python programs, there might be something to help you in if you click on **add/remove software**. Do a search for **python** in there and it should bring up the related packages.

---

### Post by pardesi on 2007-06-01
sorry to disturb u yes i did that but that simply showed that python is installed and not where...:(

---

### Post by bmartin on 2007-06-01
If you want to know where on your hard drive it's installed, the command you want is:
```
which python
```

If you want to load up the python interpreter, you could open a terminal and simply type **python** into it.

---

### Post by pardesi on 2007-06-01
after doing that it shows
/usr/bin/python what does that mean

---

### Post by pardesi on 2007-06-01
yes i got it but the python folder there is not opening like all others .
[B]
P.S.[/B] where did you get to know all these commands.

---

### Post by bmartin on 2007-06-01
That's where it is on your hard drive.

If you're asking "Where's the icon?", then the answer is that there isn't one. Python is a programming language. The **python** program is an interpreter. You use it to run python programs. There isn't a GUI.

The same goes for **gcc**, the most common C compiler found on Linux systems. It's used to compile programs, and as such, only needs to be used from the command line. There is no GUI with gcc.

Why are you trying to run Python?

---

### Post by pardesi on 2007-06-01
thanks that was a misconception

---

### Post by bmartin on 2007-06-01
> **pardesi said:**
> P.S.[/B] where did you get to know all these commands.
Most of them I learned while in college. We compiled our Java and C++ programs on a Solaris machine. Solaris and Linux are both [POSIX-compliant]("http://en.wikipedia.org/wiki/POSIX") operating systems; for all intensive purposes, that means that they have a bunch of commands that can be used on either system.

I also used Linux (Fedora Core 4) extensively at my former college for development. The computers at my workplace were set up for development reasons, but I like to listen to music while I write code and I took a break every once in a while to watch homestarrunner.com, which I still enjoy in my mid-20s. In order to get these programs installed, I had to install them for a single user (i.e., I wasn't the system admin), so I had to compile programs myself and install things (like Flash) manually. I learned Linux gradually.

There are a lot of resources on the web to help you learn the commands. Do a Google search for **common unix commands**. One of the most useful commands is **man**; it displays a page that tells you all about a certain command. For more information, go to a terminal and type **man man**. If you type **man cd**, it'll tell you all about the cd command, which is used to change your working directory.

I could go on for pages, but I want to post this soon so you don't think I abandoned you :D

---

### Post by pardesi on 2007-06-01
thanks:cool:

---

### Post by loathsome on 2007-06-01
Btw, anti-virus for Linux?


:lolflag:

Don't even bother,

---

### Post by shijirou on 2007-06-03
Good thing I found this thread. I need an anti virus because I'm on a network. The machine I'm on is the fileserver so I need an antivirus to scan files I've downloaded over the net so I can make sure that its safe before I pass them over to my windows machines on the network. lol...

---

### Post by coolzgeek on 2007-06-03
> **pardesi said:**
> yes i got it but the python folder there is not opening like all others .
[B]
P.S.[/B] where did you get to know all these commands.

Go to your local computer bookstore and get a beginner's linux codebook/phrasebook.

---

### Post by curts on 2007-06-07
> **bmartin said:**
> I don't know anyone who has ever had a virus in Linux. Nevertheless, there is such a program: ClamAV.

FYI, ClamAV doesn't install successfully on Ubuntu 7.04 for AMD 64.  I just tried it last night.

---

### Post by bmartin on 2007-06-07
I'm assuming you used apt-get or aptitude to install it. What error did you get?

---

### Post by pardesi on 2007-06-07
Never thought that my first thread here would get so long:D.But one problem though out of the context bu still everything is same for a newbie.My computer says that i have been connected but i don't get my webpage .I use ethernet

---

