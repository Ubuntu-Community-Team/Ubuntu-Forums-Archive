---
title: "problem with the terminal (su)"
date: 2008-01-10
forum: General Help
---

### Post by *Sid* on 2008-01-10
Hi,

I have just installed linux xubuntu on my powerpc g4. I am trying to install the software for my printer (samsung ML-2010 series)... but before i run the setup file, it asks me to become the super user

i went to the terminal and typed su and it asked me for my password, i typed my password but it said authentication failure... i have tried dozens of times... thinking i might be typing the password wrong... but i am convinced that there is something else wrong ( i am sure that i am typing my password correctly... i don't know why it is not accepting it)

is there any way to fix this problem or bypass it


Thanks in advance,
Sid

---

### Post by MartynA on 2008-01-10
Use sudo su

---

### Post by *Sid* on 2008-01-10
what is sudo su?? another application like terminal

sorry i don't know anything about linux... i am new to all this

---

### Post by Craigus on 2008-01-10
Does it ask for your password ?

Edit: type > sudo su

in a terminal window

---

### Post by MartynA on 2008-01-10
Yes sorry, type sudo su in a terminal window.

---

### Post by *Sid* on 2008-01-10
i did.. and then it told me to give my passoword and i did and then it gives me this

root@siddharth-desktop:/home/siddharth#



what do i type there...

---

### Post by MartynA on 2008-01-10
You're now the root user. You mentioned you were going to run a setup file? You could drag the file onto the terminal window and then press enter to execute it.

---

### Post by manimal347 on 2008-01-10
blanked for double-post- sorry, community

---

### Post by manimal347 on 2008-01-10
"sudo" is another way to become root. "Root" simply means you're escalated to the role of system administrator, and allows you to change essentially *anything* on the system. Be careful as root, and NEVER run Gnome or any other form of xwindows (the GUI) like that until you feel very comfortable with Linux. su also makes you root, but unlike sudo, su changes the whole terminal session to full privileges, instead of just doing one command as root. 

"su" may be causing problems because you never set a root password? You see, linux has many passwords, one for the root, or administrator (you when things need tweaking), and ones for the users, in your case, whatever you personally type when you login. The password you use to login is your personal password and works with sudo, but not su, as su has more potential to harm a computer if misused. Ubuntu adds to this confusion by never setting up a root password by default. You don't really need one, but if you would like to have the ability to run "su" and keep a terminal as root (full power) for the entire session, run "sudo passwd root" in a terminal window and follow the prompts. Then, you can be overlord of your computer.

All this comes from how Linux is derived from Unix, an operating system originally designed back in the 1970's to run in huge corporate environments and do complex scientific tasks, sharing one very expensive computer among many people sitting at various monitor/keyboard combinations hooked to the computer by wires (dumb terminals). Ubuntu tries to put a pretty face on things, but  beneath the shine, GNU/Linux is largely a clone of 1970's and 1980's text-based and hacker-designed (the good type) programs designed at AT&T labs (the old phone company). A lot of the rest was designed in the 1990's to present, but these core underpinnings kept a similarly complex but robust design; it's no accident that Linux runs on about 85% of the top 500 fastest computers in the world!  With time, you will gain comfort working under the Unix philosophy, which emphasizes configurability, lots of features, and the expectation that users work through hard to solve problems using their intellect first and asking for handouts (quick help) second. In the interim, Ubuntu can and will hide as much of this old software and complexity as possible from you, unlike older types of Linux setups.

Welcome to Linux! I hope you find it to be a great (the best?) operating system, but don't expect even "your grandma can use it" Ubuntu to be as simple to use as Windows for all tasks, especially when you start spending more time in your terminal window or buying things like webcams.

----------------------------------------
ALSO, I HIGHLY recommend you do NOT install that binary driver you wanted to!  With Debian Etch, (What Ubuntu's made from, basically), it killed my xserver (that means no graphical interface)) and put my console text to Russian or something. I ended up reformating, as there may have been other damage done by it that would be hard to discover. That driver was poorly made and designed for much older/different versions of Linux (Ubuntu and Fedora get updated every six months, so drivers can get old quick). I'm not the only one who's had problems with it. Follow these suggestions instead:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-2010](http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-2010)
[http://www.linuxprinting.org/show_driver.cgi?driver=splix&fromprinter=Samsung-ML-2010](http://www.linuxprinting.org/show_driver.cgi?driver=splix&fromprinter=Samsung-ML-2010)

The instructions aren't listed on the Cups/openpirnting page anymore as I remember them, but either use the third-party Splix driver (search Ubuntu Wiki), or hand-install the Samsung driver.

I found a similar version to what I did to get mine working on the Gentoo (another Linux distribution) page:
[http://forums.gentoo.org/viewtopic-t-517014-highlight-mfp.html](http://forums.gentoo.org/viewtopic-t-517014-highlight-mfp.html)

The only issue I forsee is this... "cp ./cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsungspl /usr/libexec/cups/filter/ "

I believe Ubuntu/Debian keep printing "filters" elsewhere. Ask people in the right forum and ye shall learn, or PM me, and I can do a bit of legwork. Sorry, but unlike with Windows, Linux comes in a gazillion flavors, all with their own quirks.

Also, this printer is generally flaky in Linux and poorly supported, so if you can return it for a refund, I advise you to buy a different model. Plus, as you've probably noticed, it's much flimsier and louder than its competitors and comes with a mere 1500 page cartridge to start. At least it's very fast for the cash. Using something else will save you headaches now and in the future. HP is generally best with real-world Linux support, but always research all hardware for your Linux machines first.

---

### Post by *Sid* on 2008-01-10
i tried dragging the setup.sh file into the terminal window... but after i try to execute it... it says bad interpreter: permission denied 

i am clueless...

---

