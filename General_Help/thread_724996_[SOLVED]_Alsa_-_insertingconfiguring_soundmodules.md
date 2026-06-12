---
title: "[SOLVED] Alsa - inserting/configuring soundmodules"
date: 2008-03-15
forum: General Help
---

### Post by jon.mithe on 2008-03-15
Hi,

I am trying to install my "Echo layla 3G" soundcard for music recording purposes and have run into a little trouble.

My setup:

I running an up to date version of Ubuntu 7.10 x64 (uname -a  Linux main-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64) on an fairly modern system (core duo 2.4 etc).

I have a Creative Audigy ZS2 which is my system soundcard and the Echo layla 3G is hopefully going to by a secondary soundcard that I only use for recording / producing music.

Where I am at:

My soundcard is supported by the alsa-project.  I looked at the instructions to install - [http://www.alsa-project.org/main/index.php/Matrix:Module-echo3g](http://www.alsa-project.org/main/index.php/Matrix:Module-echo3g) - (and various forums via google), and they talked about compiling + installing the alsa from the source, but including some configurations options for the echo3g.

I can not work out if this is necessary, I already have the default alsa + alsa tools installed. I did a "modinfo snd-echo3g", which exists on my system.  My spidey senses are telling me that a compile + installing alsa is unnecessary and I have to just configure my card / patch it into the kernel somehow. (modinfo soundcore - module exists)

Inline with the documentation I tried "modprobe snd-echo3g", got no feedback from the console so I assume it did whatever it did with no errors (this is on the limit of my linix knowledge) and cant see the card but there seem to be some more configuration that I really dont know about:

The documentation says to insert this into a file in the /etc/&#8203;modutils/&#8203; directory

```

# ALSA portion
       alias char-major-116 snd
       alias snd-card-0 snd-echo3g
       # module options should go here
       
       # OSS/Free portion
       alias char-major-14 soundcore
       alias sound-slot-0 snd-card-0
       
       # card #1
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss

```

However, my shiver at the look at doing that given that there is no alsa files in that directory and it talks of setting up card #1 and soundservice0-x and my spidey senses are telling me this might conflict with my current soundcards.

Poking around my system (find /etc -name "alsa*" + locate alsa )  there seem to be a few alsa files but I have no idea what to configure to get my card working.

Can anyone offer any help, or point me in the right direction? 

I heard about of ubuntustudio and sounds like it may solve my problem but do not really want to swap with it, I am happy with my standard ubunutu (seems ubuntostudio is just that with a fancy theme and a apps automatically installed - i.e. what I am trying to do should work on my setup). Also I am a developer by trade so I have local development setup that I do not want to mess around.

I really want to try Ardour 2 with my setup to see how we all get along and if I can migrate from cakewalk, from what I can see it looks good (I did not get along with Audacity). 

Thats it, any help will greatly be appreciated. Cheers, 
Jon

---

### Post by efflux on 2008-03-15
I've got the Echo Layla3g working. I just wrote some about it here then edited the message and lost what I'd written by accident. I have no time now but will get back here for further explanations.

---

### Post by efflux on 2008-03-16
OK. Before doing anything else. This is something to try. Down this file. It's from the alsa site where the drivers etc are and it's the same version as the rest of alsa on Ubuntu 7.10. Not sure that it makes any difference but I've chosen that version:

[ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14.tar.bz2)

Extract it into /usr/src

You may need to install configure-debian for the next steps. Look in synaptic package manager to see if that is installed.

Then from a terminal move to the directory with this command:

cd /usr/src/alsa-firmware-1.0.14

Then run this command:

sudo ./configure ; make ; make install

Now you should have a folder with sound card firmware drivers installed.

Now copy the ea folder at /lib/firmware/ea into /lib/firmware/<your kernel version>

Reboot your system and see what happens. See if audio plays back. I'm interested to know the result. The trouble is I've tweaked my system a bit so it might be a different process to get the card working. However I might be reinstalling Ubuntu soon.

---

### Post by jon.mithe on 2008-03-16
Hello! Thank you very much for taking the time to help me with this, and the good news is with following your instructions I have it all working now (touch wood) - thanks.   The audio all seems to be working and I will test the midi tonight (I wrote a small java program and there were layla 3g midi devices avaliable so should wourk hopefully)

I had a little trouble with some missing libraries with GCC and had to sudo su to get it make / make install working and the layla went to my default soundcard on the restart (just had to set the default mixer in the gui sound preferences + reboot) but your instructions were spot on. The echomixer works great as well.  

Now to try Jack and Ardour 2 when I find the time.

Thanks :)


edit: Setting default soundcard did not work, it was randomly assigning the default soundcard.  To fix this I used a command "asoundconf set-default-card=XXXXX".   - where the X's were the ID of the normal / creative soundcard.  To find the id's of the soundcards on a system, do a "asoundconf list", and it will print them in the console.

---

