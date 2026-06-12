---
title: "Help with server install.."
date: 2007-05-11
forum: General Help
---

### Post by GSF1200S on 2007-05-11
Im planning to do a server reinstall of kubuntu. Im going to install over my current install and install KDE core, then install apps I want from there.

My questions concern the following:

Where can I get the Add/Remove Programs and Adept Manager once KDE core is installed? Also, since I actually prefer Synaptic, could I possibly install that instead of the Adept Manager, and still have Add/Remove programs?

Is there anything I should know about the reinstall? I installed Ubuntu (GNOME variant) about 3 months ago, and I dont remember if there are any built in provisions for a reinstall. Maybe the partitioner will wipe my current linux install and install this one in its place?

How will grub be affected? Since I obviously wont have Ubuntu core anymore, will grub be automatically updated or will I need to configure/edit it?

I would like to have a seperate /home partition this time, and im curious the specifics on this, considering im already configured with a EXT3 and NTFS partition (dual-booting Kubuntu/WinXP). Do I need to do the manual partition option? Ive learned enough about partitioning where I should be fine, but do I need to be aware of anything specific?

My goal is to have a fast and light KDE. KDE has the options of setup I like/need, but its notably slower than GNOME, and definitely slower than XFCE (too bad moving hell and earth wont let Xubuntu get my wireless working, or Id use it for the speed).

Any help would be appreciated!

---

### Post by GSF1200S on 2007-05-11
Bump.. anyone?

---

### Post by jfinkels on 2007-05-11
> **GSF1200S said:**
> Im planning to do a server reinstall of kubuntu. Im going to install over my current install and install KDE core, then install apps I want from there.

My questions concern the following:

Where can I get the Add/Remove Programs and Adept Manager once KDE core is installed? Also, since I actually prefer Synaptic, could I possibly install that instead of the Adept Manager, and still have Add/Remove programs?

Just go to the website of the program you want to download, for example: [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)

> 
Is there anything I should know about the reinstall? I installed Ubuntu (GNOME variant) about 3 months ago, and I dont remember if there are any built in provisions for a reinstall. Maybe the partitioner will wipe my current linux install and install this one in its place?

You will have to download one of the Ubuntu isos (Kubuntu, Ubuntu, Xubuntu, etc.), burn it to a disc, then reinstall it that way. This way will completely clear your current hard drive and repartition it, if that's what you want it to do. You could just remove all your current programs using aptitude, then reinstall whatever you want. But that might get confusing.
> 
How will grub be affected? Since I obviously wont have Ubuntu core anymore, will grub be automatically updated or will I need to configure/edit it?

If you reinstall from an Ubuntu disc, GRUB will be recreated.
> 
I would like to have a seperate /home partition this time, and im curious the specifics on this, considering im already configured with a EXT3 and NTFS partition (dual-booting Kubuntu/WinXP). Do I need to do the manual partition option? Ive learned enough about partitioning where I should be fine, but do I need to be aware of anything specific?

You can choose to manually partition at install time, or install the default way, and then create a new partition afterwards, see here for how to do that [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
> 
My goal is to have a fast and light KDE. KDE has the options of setup I like/need, but its notably slower than GNOME, and definitely slower than XFCE (too bad moving hell and earth wont let Xubuntu get my wireless working, or Id use it for the speed).
Any help would be appreciated!
I don't know what the desktop environment has to do with your wireless networking, it shouldn't have any effect...If you want a light environment, try Openbox or Fluxbox. In general, if you want a server to be efficient, don't bother installing a GUI, it's a waste of disk space, memory, and processor power.

---

### Post by GSF1200S on 2007-05-11
> **jfinkels said:**
> Just go to the website of the program you want to download, for example: [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)


You will have to download one of the Ubuntu isos (Kubuntu, Ubuntu, Xubuntu, etc.), burn it to a disc, then reinstall it that way. This way will completely clear your current hard drive and repartition it, if that's what you want it to do. You could just remove all your current programs using aptitude, then reinstall whatever you want. But that might get confusing.

If you reinstall from an Ubuntu disc, GRUB will be recreated.

You can choose to manually partition at install time, or install the default way, and then create a new partition afterwards, see here for how to do that [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I don't know what the desktop environment has to do with your wireless networking, it shouldn't have any effect...If you want a light environment, try Openbox or Fluxbox. In general, if you want a server to be efficient, don't bother installing a GUI, it's a waste of disk space, memory, and processor power.

Thanks alot.. Yeah, I already have the disc burnt and ready to go. I did some googling and didnt seem to realize the package managers had there own websites.. thanks for that.. Ill check into.

Thats exactly what I want to do. Im just going to move all my important files to my NTFS partition and then reinstall Ubuntu. Then I can move it back once NTFS3g is installed on my new install.

The Xubuntu wireless thing has baffled me for the longest time. Ive posted 2 topics on this in the past with no response, probably because they thought I was doing something really stupid. Basically, Ive tried everything including gksudo (name of wireless manager), and it still WILL NOT connect. Interesting thing is, if I log in KDE, connect, than CTRL ALT Backspace to XFCE, wireless works fine.

This isnt a server, its a home OS. Im just somewhat of a speed whore, which is why I want to do a KDE core install and then Adept from there. Things are more simple, and I can cut down on the programs KDE opens at startup, and stuff that slows it down. Fluxbox im experimenting with.. but its small and can be added afterwards.

Ok, partitioning makes sense.. I have installed Ubuntu before, so I shouldnt have an issue here. Ill probably do the /home partition afterwards off the EXT3 partition..

Thanks for the reply.. those links helped alot :)

---

### Post by jfinkels on 2007-05-11
Yeah, what you're planning on doing shouldn't be too difficult at all, and it seems like you know what you're doing as far as partitioning etc., so have fun! Let us know if you have any other questions.

---

### Post by RedSquirrel on 2007-05-11
> **GSF1200S said:**
> Where can I get the Add/Remove Programs and Adept Manager once KDE core is installed? Also, since I actually prefer Synaptic, could I possibly install that instead of the Adept Manager, and still have Add/Remove programs?


 Both synaptic and adept are in the repositories. Once your server is installed, you can simply apt-get them, along with the other stuff you need for the GUI.

---

