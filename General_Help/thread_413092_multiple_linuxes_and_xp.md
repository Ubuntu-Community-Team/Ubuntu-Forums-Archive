---
title: "multiple linuxes and xp"
date: 2007-04-18
forum: General Help
---

### Post by nonewmsgs on 2007-04-18
what i would like

i want to have Oz, ubuntu, openSuSe, and xp on one computer.  how is the best way to handle this?  i remember reading somewhere that multiple grubs will install and i really dont want that.  i want a single fancy little select OS menu defaulting with ubuntu.  now i can install multiple linuxes togther in the same drive/partition right? and ill have the same linux home folder and desktop?

please type slowly.  i catch on fast but i'm still relatively new.

---

### Post by Compyx on 2007-04-18
For each distribution you'll need a separate partition, you can't stick 'em in the same one. (You can however use the same swap partition for all Linuxes, just be careful when also using Solaris, if I remember correctlu Solaris partitions show up as swap in fdisk) As far as grub goes, many (if not all) Linux distributions allow you to install grub in the partition of the distribution, instead of the MBR. However, you'll need one grub to be installed into the MBR to be able to boot anything.

And as for using the same /home partition for multiple distributions: I wouldn't do that, many applications store their settings in your home directory, usually with files/directories starting with a dot. This will lead to conflicts between distributions.
What you can do however is using another partition to mount into you home directory as a subdirectory. For example: you want a downloads dir in all your home's: you'll need a separate partition for downloads which you then mount at /home/$USER/downloads in each distribution.

For all this, you'll need a basic understanding of the structure of /etc/fstab, configuring grub and managing user-rights and groups. I've done all this with Solaris, FreeBSD and several Linuxes on the same box, it's not hard but takes some time to properly set up.

---

### Post by nonewmsgs on 2007-04-18
first thank you for the fast reply.  i say it a lot, but i always appriciate that.

i am already setting up one drive for shared data.  all ext3 file systems arent automatically mounted?  

i don't have knowledge of the etc/fstab...yet, but i just bought unix: the complete reference (which of all my recent linux books i have purchased, this is my favorite).  and more importantly i have a strongly knit group of my brothers and sisters on this forum to help me out.

---

### Post by nonewmsgs on 2007-04-18
one other question why would i want grub on each partition? maybe i have the wrong idea but i thought it was like  OS shell ZZZZZ starts here--->_____
and then it starts that OS.

---

### Post by FatherDale on 2007-05-05
Why not run them as virtual machines? Currently, I'm running Feisty as my main OS, with XP and FC6 as VMs. If you have the horsepower, you can run all of them at once.

---

### Post by DJiNN on 2007-05-05
> **FatherDale said:**
> Why not run them as virtual machines? Currently, I'm running Feisty as my main OS, with XP and FC6 as VMs. If you have the horsepower, you can run all of them at once.

I think it's down to what you've just said..... "HorsePower!" :) 

I still haven't tried the VM route properly (Although i do have a couple of machines with enough HP now which is cool). I'd be interested to know what machine you're running them on (Specs etc, how much RAM in particular) and how they work in the VM environment, if you wouldn't mind? 

Glad to hear that you have them running though.... VM certainly saves the hassle of having to reboot all the time and also having only One OS running at any time. :)

DJiNN

---

### Post by DJiNN on 2007-05-05
Oooops, nearly forgot to ask, what size are your VM images, and did you create them yourself? :)

DJiNN

---

### Post by nonewmsgs on 2007-05-06
i'm not real familiar with virtual machines, but im a quick learner.  do you have a link for a good how-to?  i do hate having to reboot everytime i want to play a fricken game that only works with winblows.  i have never realized how much i hate windows until i started dual booting.  windows is gaming and a couple dvd ripping programs and linux is what i love.

this machine's specs.
duo core 2 - 2.18 ghzoverclocked to 2.34ghz, 2gb ram, about 600gb disk space free

i actually have lots of computer but this is my baby...ive already decided that none of my other desktops is going to have windows.  it's bad enough it on one desktop and one laptop.

---

