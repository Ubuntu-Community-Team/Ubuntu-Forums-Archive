---
title: "WHat The &amp;@%!"
date: 2007-04-22
forum: General Help
---

### Post by electroconvulsive on 2007-04-22
OK I am really at a loss to explainthis one but considering that I spent 2 days of my life playing with Feisty I think I owe it to myself to tell this community about this. 

Anyone who knows anything should read this post through and try to think what  caused this to happen. 

Anyway I have a P4 1.6 ghz P4 system with 512 mb RAM, 80 GB hdd, originally had a ATI Radeon 9200 se but replaced it on my second attempted install of Feisty with a nVidia Geforce mx4000 because I wasnt able to get desktop effects or Beryl to run with it. The machine has XP on the first partition and a storage partition for the second partition and Feisty was installed in the free space thereafter and grub went over boot.ini on  the first Windows partition.

The first install  was going well until after a touch of installing lots of things through synaptic rendered my desktop effect and 3d acccelaration useless. So I went out and bought a mx4000 nVidia card for nice and cheap and put it in. 

When I  put it in today I thought I would go for a full reinstall. Fair enough because I just wanted things to go smoothly this time around. Well anyway I got through the install installed heaps of apps I wanted running on the machine and again lamented the fact that there was no way I could get  the mplayer plugin for Firefox happening under Feisty. I installed Firestarter but forgot to enable it. Well anyway about  6hrs into installing stuff I went back to synaptic again and I had got to the stage of applying changes. The apps all downloaded and installed and then right at the end of the process I got an error message asking me if I was really root and then at the same time I was being told that  folder on my desktop didnt exist.. Thinking that this was strange and a reboot would be in order to fix things I rebooted and was given the error message from grub ```
ERROR 15
``` Well this left me with an inoperable computer. Grub was missing and I then put my CD back in the drive and tried to recover grub using grub in terminal but this seemed to say that grub didnt exist. I even tried to follow a thread from a guy that had a similar problem but it came to no avail because not only did grub no longer exist nor did /mnt/root. 

Finally I go the $%*&s and decided to stick my XP disk back in the machine and recover boot.ini. This was done succesfully and because I had already had the ext3 driver installed in Windows I decided to have a look at my Linux partition to see if I could check what the problem was. Now this is where things get really spaced out. 

When I looked at my Linux Prtition I was surprised to find that only these diectories still remained.

```
/dev
/proc
/sys
/usr
```

Where did the rest of my install go? I dont recall deleting them. Hey I was just installing some stuff and then half of my OS had dissapeared without a trace and after spending about 15hrs of this weekend being a nerd playing around with Feisty I was pretty much ready to snap the disk in half and yell profanities at my neighbours.

So anyway I will probably try to install again in the near future but before I actually do I want to hear from anyone who might even have a slight idea why this happened. My guess is I got hacked while I wasnt looking or something crazy like that which is highly possible that I had not yet enabled the firewall . I dont think it was the disks fault as it is less than a year old and the XP install didnt suffer at all. :confused:

---

### Post by rich.bradshaw on 2007-04-23
Unlikely that you "got hacked", there are no open ports by default, so you don't need a firewall unless you have specifically opened insecure ports to run services such as apache, ssh etc. Even then you will have been pretty unlucky...

That is very very weird....

---

### Post by electroconvulsive on 2007-04-23
Well anyway Ive reinstalled the hat is again and everything seem to be going fine. I will have say this time has been no worries everything has worked first go.

Im going to have to withdraw my comment about the mplayer plugin as I have found it in the add/remove programs panel when you select the all available packages option.

The only thing that has gone wrong since is some of the compiz features aren't working but there is going to be another thread on that. Im even going to try beryl out.:)

---

