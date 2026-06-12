---
title: "xubuntu minimal desktop, i386"
date: 2007-03-10
forum: General Help
---

### Post by shred_thrash on 2007-03-10
Hey all,

I recently installed xubuntu minimal onto my sisters older computer (128 SD, 1.00 ghz copper, etc...slow) and there are a few things that she would like to do but I can't seem to find, or know of, any lightweight applications that can perform the same tasks as the more "heavy" programs that I'm used to using on my computer.

She would like to be able to download music to her computer, so I thought limewire for linux would be most comfortable for her.  However, when I downloaded rpm, and installed it (tried to :P) it said that it needed "/bin/bash (weird?), and java.  I have no idea why it would tell me that I needed bash, but I understand am okay with java.

She would also like to use msn, so I installed gaim for her and she loves it.  She has an ipod and would like to be able to plug it in and transfer files back and forth with ease.  The first thing that came to mind here was amarok, but I don't want to install such a "heavy" program on her computer, not to mention her 10 gig HDD :P.  Also, I have had a lot of problems with actually transferring files between an mp3 player of any kind in linux, and I hear a lot of people have the same problem but it's fixed because there are simply bad blocks on the removable device???  Anyways, I'll try to keep this short.

Thanks so much,
Cheers!

---

### Post by kerry_s on 2007-03-10
Frostwire is better than limewire.-> [http://www.frostwire.com/](http://www.frostwire.com/)
sudo dpkg -i frostwire-4.13.1.6.i586.deb

Don't forget to install java. it's in multiverse repo, so make sure you have all the repos on. use synaptic or->
sudo apt-get install sun-java6-plugin

ipod-> gtkpod
sudo apt-get install gtkpod

mp3 player-> vlc
sudo apt-get install vlc

---

### Post by shred_thrash on 2007-03-10
Right on mate, that sounds good.  
What about the codecs, will they be installed automatically (I think they are because I use vlc all the time under suse, however that's after I install "win32-all".

Cheers mate, thanks a lot for your help.

P.S.  Do you have any other tips for running xubuntu-minimal on, well, such minimal hardware.  Any tips and tricks would be greatly appreciated but I'm impressed with canonical so far mate :P ;)

Thanks

---

### Post by kerry_s on 2007-03-11
Add this repo to your list->
sudo mousepad /etc/apt/sources.list

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main 

in terminal:
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 1F41B907
then>
gpg --armor --export 1F41B907 | sudo apt-key add -
to add the key

then run> sudo apt-get update 
or
click reload in synaptic 

and then you can install both w32codecs and libdvdcss2. 

Tip, don't be afraid to ask for help. There are alot of very knowledgeable people here that spend all day helping people. Just tell us exactly what you want or what the problem is and try to include as much info as you can. :) 

Sounds like your already on the right track, just continue to use light applications.
For instance:
mousepad= can be replaced with "leafpad" which is the original that mousepad was built on. The difference between mousepad and leafpad is that mousepad has print support and leafpad don't, plus of course size, leafpad is smaller and faster. So if you don't need to print from your text editor, that's a option. I will just copy what i want to print to abiword and print, more better printer support with abiword.

thunar= if you don't need all that flash, you can try emelfm, it's a basic file manager thats faster. Gets the job done. Attached is my settings for emelfm, just unpack it to your home, it's a hidden file, so ctrl+h to see it.

Hmm, what else you need?

---

