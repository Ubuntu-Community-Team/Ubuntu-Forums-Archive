---
title: "How become a Superuser?"
date: 2007-06-16
forum: General Help
---

### Post by J.One on 2007-06-16
Hi to all, i've just set up my new Ubuntu with compiz 3d effect sound (except not playing login and out sounds) and everythings cool...
I tried to copy a file from my desktop and paste it to my second hard drive wich is ide and ntfs with files i had managed older with windows platform. I noticed that is read on;y because i can see all of my videos but not move them copy or paste.I also notice that on my Fliesystem drive.
I tried to install Borealis theme but when i put on terminal su -p to install Borealis i get this:

john@pc:~/Desktop/Borealis$ su -p
Password: 
su: Authentication failure
Sorry.

Installation notes says that:

2) Install the theme:

cd Borealis/

su -p

(IMPORTANT! You must do 'su' with the '-p' flag in order to preserve your home dir variable while running as [COLOR="Red"]superuser[/COLOR])

sh install.sh

What does all that mean? Why i don't have full control of my files even on Filesystem?
Help will be appreciated!

---

### Post by J.One on 2007-06-16
I forgot to say i run a AMD64 3500 1024 RAM 256 gf gt and ubuntu 7,04

---

### Post by ForzaItalia250 on 2007-06-16
Although I'm new, from what I've read and my own issues with the same thing, I believe the command to use is "sudo"

After typing it in, it prompts for your password, and I believe it gives you temporary superuser powers. It's worked for me.

---

### Post by J.One on 2007-06-16
Yes but what about the rest of my files on the other hard drive? Why i cant even create a folder there?

---

### Post by J.One on 2007-06-16
As i now understood when i type su on terminal i gain superuser right.Despite that why i get a


su: Authentication failure
Sorry.

???

---

### Post by J.One on 2007-06-16
and when i do 

john@pc:~/Desktop/Borealis$ su -p sh install.sh

i get a

Unknown id: sh

---

### Post by gjtoth on 2007-06-16
> **J.One said:**
> Hi to all, i've just set up my new Ubuntu with compiz 3d effect sound (except not playing login and out sounds) and everythings cool...
I tried to copy a file from my desktop and paste it to my second hard drive wich is ide and ntfs with files i had managed older with windows platform. I noticed that is read on;y because i can see all of my videos but not move them copy or paste.I also notice that on my Fliesystem drive.
I tried to install Borealis theme but when i put on terminal su -p to install Borealis i get this:

john@pc:~/Desktop/Borealis$ su -p
Password: 
su: Authentication failure
Sorry.

Installation notes says that:

2) Install the theme:

cd Borealis/

su -p

(IMPORTANT! You must do 'su' with the '-p' flag in order to preserve your home dir variable while running as [COLOR="Red"]superuser[/COLOR])

sh install.sh

What does all that mean? Why i don't have full control of my files even on Filesystem?
Help will be appreciated!

First things first -- which version of Ubuntu are you running?  Different versions offer different options.  If you are running Feisty, you'll need to install ntfs-config and set up your drive from there.  You can install it using Synaptic.  Just open Synaptic, do a search for ntfs-config, mark it for installation, and click "apply".

---

### Post by J.One on 2007-06-16
thank you very much! that was it!

---

