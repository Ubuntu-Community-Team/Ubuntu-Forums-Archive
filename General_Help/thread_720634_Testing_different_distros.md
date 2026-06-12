---
title: "Testing different distros"
date: 2008-03-10
forum: General Help
---

### Post by intense.ego on 2008-03-10
I want to try out different distros such as fedora and mandriva and was wondering what the easiest way of doing this? is it possible to try these out (not a live cd, but an actual install - i want to see how it would actually work) without doing anything to my ubuntu install (i.e. not having to reinstall all applications, etc)? If it helps, I already have a /home partition, so that shouldn't be a problem.

---

### Post by Oldsoldier2003 on 2008-03-10
> **intense.ego said:**
> I want to try out different distros such as fedora and mandriva and was wondering what the easiest way of doing this? is it possible to try these out (not a live cd, but an actual install - i want to see how it would actually work) without doing anything to my ubuntu install (i.e. not having to reinstall all applications, etc)? If it helps, I already have a /home partition, so that shouldn't be a problem.

either install them in thier own partition, or you might consider running them in a vritual machine such as virtualbox or VMWare

---

### Post by Therion on 2008-03-10
I don't know how practical a solution this will be for you, but having dual-hard drives helps a lot -- it's the ONLY way to fly, in my opinion.  I just unplug my "system drive" (the one I keep my 'real' install on), adjust my BIOS, install the distro I want to test drive (full install, aye!) and I'm off and running.

---

### Post by bodhi.zazen on 2008-03-10
Easiest way to get a feel is to run a live CD (iso) in Virtual Box / VMWare / QEMU.

This does NOT test your hardware though, best way to do that is by booting a live CD.

---

### Post by Shazaam on 2008-03-10
Adding to Oldsoldier2003's post remember that virtualization programs use their own hard-coded virtual drivers. An os might work perfectly well in a virtual setup but could fail in an actual physical install. Using a livecd will give you a better indication of how said distro's will work with your hardware.

---

### Post by intense.ego on 2008-03-10
I was considering live cd, but i thought that perhaps performance in a live cd could not be interpreted to represent actual performance on an installation. Am i wrong in thinking this? I will download some live cds and check them out, regardless, however.

i am looking for something more stable (gutsy is not very stable for me) linux distro that allows for large amount of configuration graphically. So far I am considering mandriva and fedora. Anything wrong with these ideas, and are there any more you would add to the list?

---

### Post by Shazaam on 2008-03-10
To get a sample of what's out there you could go here and poke around.....

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Whiffle on 2008-03-10
> **intense.ego said:**
> I was considering live cd, but i thought that perhaps performance in a live cd could not be interpreted to represent actual performance on an installation. Am i wrong in thinking this? I will download some live cds and check them out, regardless, however.

i am looking for something more stable (gutsy is not very stable for me) linux distro that allows for large amount of configuration graphically. So far I am considering mandriva and fedora. Anything wrong with these ideas, and are there any more you would add to the list?

Thats correct, a LiveCD generally does not run as fast as a hard drive install.  

I'd add SUSE to your list as well.  

I usually keep an extra partition on my hard drive just for installing distros to play with.  They don't take much room really, and I've got oodles of space.

---

### Post by intense.ego on 2008-03-10
> **Whiffle said:**
> Thats correct, a LiveCD generally does not run as fast as a hard drive install.  

I'd add SUSE to your list as well.  

I usually keep an extra partition on my hard drive just for installing distros to play with.  They don't take much room really, and I've got oodles of space.

My problem is that my HDD is only 60 gb (laptop). 6gb is for windows (i keep it sort of as a backup), 10gb is for root and the rest is for home. I really do not want to reduce my home, and I don't think any more than 2 distros could fit on that root directory.

---

### Post by AndyCooll on 2008-03-10
> **intense.ego said:**
> My problem is that my HDD is only 60 gb (laptop). 6gb is for windows (i keep it sort of as a backup), 10gb is for root and the rest is for home. I really do not want to reduce my home, and I don't think any more than 2 distros could fit on that root directory.
Unfortunately you're stuck between a rock and a hard-place unless you add an additional hard-drive. 

Apart from that, essentially your options are:
1. Create additional partitions by resizing the partitions you've got and then installing the distros on the new partitions.
2. Run a Live CD, which will obviously run slower.
3. Use VirtualBox (or an equivalent), which will run at a comparable speed but won't use your native hardware directly.

:cool:

---

### Post by intense.ego on 2008-03-10
> **AndyCooll said:**
> Unfortunately you're stuck between a rock and a hard-place unless you add an additional hard-drive. 

Apart from that, essentially your options are:
1. Create additional partitions by resizing the partitions you've got and then installing the distros on the new partitions.
2. Run a Live CD, which will obviously run slower.
3. Use VirtualBox (or an equivalent), which will run at a comparable speed but won't use your native hardware directly.

:cool:

I suppose i will use the live cd as this will give me a good all-round impression. As for the performance, I will just read what's online and maybe run it in VirtualBox as well.

---

### Post by intense.ego on 2008-03-10
I'm going to download the fedora 8 xfce spin ([http://spins.fedoraproject.org/](http://spins.fedoraproject.org/)) and was wondering what category (i686 or x86_64) my processor would fall under. It is a core duo t2400 1.83 ghz ([http://en.wikipedia.org/wiki/List_of_Intel_Core_microprocessors#Dual-Core_Mobile_Processors](http://en.wikipedia.org/wiki/List_of_Intel_Core_microprocessors#Dual-Core_Mobile_Processors)) . I'm pretty sure I should go for the i686 option because it is not 64-bit, but I don't really know.

---

### Post by AndyCooll on 2008-03-10
> **intense.ego said:**
> I'm going to download the fedora 8 xfce spin ([http://spins.fedoraproject.org/](http://spins.fedoraproject.org/)) and was wondering what category (i686 or x86_64) my processor would fall under. It is a core duo t2400 1.83 ghz ([http://en.wikipedia.org/wiki/List_of_Intel_Core_microprocessors#Dual-Core_Mobile_Processors](http://en.wikipedia.org/wiki/List_of_Intel_Core_microprocessors#Dual-Core_Mobile_Processors)) . I'm pretty sure I should go for the i686 option because it is not 64-bit, but I don't really know.
Yes, if in doubt i686 (or i386) will usually be fine.

:cool:

---

### Post by intense.ego on 2008-03-11
I have done some research and found that Gentoo seems to be the fastest OS. My concern, however, is that on this site ([http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Gentoo](http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Gentoo)) it mentions that Gentoo has **no** graphical system tools. I am not very linux experienced and a GUI for controlling my system is pretty essential. Can I live without it?

---

### Post by Therion on 2008-03-11
Ummm... You mention you're "not very linux experienced" so you might want to look at this [Quick Install Guide](http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml) for Gentoo and decide for yourself if this is "your type of distro" or not.

---

### Post by intense.ego on 2008-03-11
> **Therion said:**
> Ummm... You mention you're "not very linux experienced" so you might want to look at this [Quick Install Guide](http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml) for Gentoo and decide for yourself if this is "your type of distro" or not.

Thank you. i have now ruled gentoo out.

I am really quite keen on XFCE, not because I have a slow computer but because I like to get the best performance i can. Mandriva seems to have a simple XFCE configurator, whereas Fedora has an XFCE spin that is really only maintained by one guyl and has bugs (from what I have heard). Are there are any other linux OSes you would recommend for someone looking to get the best performance? Preferably, it would be able to run the same applications as ubuntu. 

I have an XFCE install that I made straight from ubuntu, and am also considering installing directly from a disc instead as this would make it more stable and less buggy.

What do you think?

---

### Post by notwen on 2008-03-11
You may also want to consider Arch.  It is similar to Gentoo in the sense that you build your distro from the ground up, except in Arch you do not need to compile everything.  I've been running Arch in VirtualBox for a month-ish now and am somewhat surprised at it's ease of use, but not to mention it's blazing fast(in VirtualBox at that).  =]

---EDIT---

Lots of people like to say Arch is a good distro to figure out how and what makes Linux work.  After using it I could agree w/ them to a degree.  I've been a Debian stable user for years and other than Ubuntu no distro has really caught my eye until I test drove Arch.  Read up on it and give it a try if you feel up to it.  =]

---

### Post by bodhi.zazen on 2008-03-11
There are several distros that work on older hardware. I suggest :

Wolvix (Wolvix is an under rated distro IMO).

Zenwalk

PCLinuxOS, fluxbox edition

Puppy

Or you can try something like this :

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

[http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/](http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/)

---

### Post by intense.ego on 2008-03-11
I'm trying to check the md5sum of the mandriva iso i downloaded. Which file do i download to do that and how? Link: [http://www.mirrorservice.org/sites/carroll.cac.psu.edu/MandrivaLinux/official/iso/2008.0/](http://www.mirrorservice.org/sites/carroll.cac.psu.edu/MandrivaLinux/official/iso/2008.0/)

I downloaded the GNOME version (i.e. the first one on the list)

---

### Post by bodhi.zazen on 2008-03-11
```
md5sum /path/to/mandriva.iso
```

If you download the md5sum file (mandrivaxxx.iso.md5)

cd in to the directory with the iso and *.md5

```
md5sum -c mandrivaxxx.iso.md5
```

---

### Post by intense.ego on 2008-03-11
How do I know which md5sum it is supposed to be like? The site I downloaded from (mandriva.com) only gives a KDE checksum

---

### Post by bodhi.zazen on 2008-03-11
It should be posted on the download page or on the server where you got the iso.

---

### Post by intense.ego on 2008-03-11
The md5 file itself (mandriva-linux-2008-one-GNOME-cdrom-i586.iso.md5),when opened, displays the same number and letter I got from running 

```
 md5sum mandriva-linux-2008-one-GNOME-cdrom-i586.iso

```

in the terminal

Other than that, I cannot find anything else.

EDIT:

I also have another question. Will my home folder work completely fine with another distro, such as mandriva, or will there be conflicts? Will I have to start with new settings on all programs?

---

### Post by bodhi.zazen on 2008-03-11
Sounds like you are good to go \o/

---

### Post by intense.ego on 2008-03-11
I like the sound of the enlightenment WM. What distros use this by default and on which ones can i install it without too much difficulty? I have heard of elive, but that requires a "donation", and i am not so sure about opengeu.

---

### Post by bodhi.zazen on 2008-03-11
You can download the "development" versions of ELive

[http://elive.cmhacks.com/development/elive_1.6_development.iso](http://elive.cmhacks.com/development/elive_1.6_development.iso)

If you like it, please consider a donation.

There is also opengeu: 

And gos : [http://www.thinkgos.com/](http://www.thinkgos.com/)

Of the three Elive has been my favorite, but opengeu is nice too ...

[http://opengeu.intilinux.com/Home.html](http://opengeu.intilinux.com/Home.html)

In my experience all three distros are nice :)

There is also OzOs : [http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents](http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents)

---

### Post by intense.ego on 2008-03-11
The development version seems very unstable (at least that is what the elive website says - but then again they would want you to give a donation). 

I don't like gOS because its focus is only on Web 2.0 really. OpenGEU sounds good, but not as good as elive. OzOs, I heard of before because RAV TUX uses it.

from what I've read elive seems to be the favorite, so I will try that.

One more thing, is installing enlightenment thru a distro like xubuntu going to give worse performance then a pre-installed one such as elive?

---

### Post by bodhi.zazen on 2008-03-11
No, I doubt you will see any performance difference.

The repos have E16. E17 had been in development for what seems forever, so you will need to install from SVN and that may be more unstable then any release.

[http://www.ubuntuforums.org/showthread.php?t=319336](http://www.ubuntuforums.org/showthread.php?t=319336)

You will then need to find themes ...

I have not found the ELive development releases to be unstable. I do not user Elive enough to contribute.

All of these distros can be customized post install and really, IMO, it comes down to Debian (Elive) vs Ubuntu and what themes you want. Everything else can be installed / customized post install.

---

### Post by intense.ego on 2008-03-12
> **intense.ego said:**
> 
I also have another question. Will my home folder work completely fine with another distro, such as mandriva, or will there be conflicts? Will I have to start with new settings on all programs?

Will it? I assume with something like elive (which is based on debian) the home folder should work for both distros together, but with something like mandriva, I am not sure.

---

### Post by bodhi.zazen on 2008-03-12
Missed that one.

Well I advise against that one. The problem is your /home has config or . files that may well confilct across distros. Also, you are not identified by the system by user name , rather by a number uid. Some distros (Ubuntu) the first user is uid=1000, others (fedora) default to first user uid=500.

Best, IMO, to use a /data partition (I mount mine in /mnt/data). You then keep your data on that partition and make links

ln -s /mnt/data/music /home/<user>/music

and on ...

---

### Post by intense.ego on 2008-03-12
so you're suggesting I keep my /home partition, but shrink it, and use that extra space to create a /data partition for torrent downloads, videos, music, etc.

---

### Post by intense.ego on 2008-03-12
Also, would I have to create another /home partition for whichever other distro I install? What size would I need?

---

### Post by bodhi.zazen on 2008-03-12
Partitioning is an art and there aer multiple ways to skin the cat. I allow each distro to put /home on the same partition as / and use a /data partition of all user data.

How big to make each partition ? / 5-10 Gb. /home /data ? how much data do you have ? How big is your hard drive ?

It is not such a critical decision as you can resize your partitions almost at will with gparted, so up to you.

---

### Post by intense.ego on 2008-03-12
At the moment, my hard drive (60gb) is divided like thus:
6 GB for windows (just in case/backup solution)
10GB for root (ubuntu)
39GB for /home
1 GB for swap (i currently have 512mb of ram)

how would you recommend I partition it?

PS: my root is only 3.2 gb full, and my /home is 30 gb (though it can a lot large if I am downloading large torrents, etc.)

---

### Post by intense.ego on 2008-03-13
anyone?

---

### Post by intense.ego on 2008-03-14
bump bump

---

### Post by intense.ego on 2008-03-14
can anyone give me some partition advice?

---

### Post by AndyCooll on 2008-03-14
> **intense.ego said:**
> can anyone give me some partition advice?
The reason folk are not replying is because it's like saying what's the best make of car, or what's the best distro, or the best music player. There is no absolute right or wrong answer, it's simply what best suits your needs. What you've got is fine. As bodhi.zazen says there are multiple ways to skin a cat, how I set up my partitions, may be different to bodhi.zazen, which may be different to yours, which may be different to someone elses.

Ubuntu by default creates one big partition. You've set it up as you have. I usually have 10gb /, 10gb /home, 1gb swap, and the rest is spare. My data (e.g. music, pictures etc) is on my server, so I simply mount this. As you can see my layout is different from yours, but that's simply because my setup is different. So, I repeat it's what best suits your needs.

:cool:

---

### Post by intense.ego on 2008-03-15
> **AndyCooll said:**
> The reason folk are not replying is because it's like saying what's the best make of car, or what's the best distro, or the best music player. There is no absolute right or wrong answer, it's simply what best suits your needs. What you've got is fine. As bodhi.zazen says there are multiple ways to skin a cat, how I set up my partitions, may be different to bodhi.zazen, which may be different to yours, which may be different to someone elses.

Ubuntu by default creates one big partition. You've set it up as you have. I usually have 10gb /, 10gb /home, 1gb swap, and the rest is spare. My data (e.g. music, pictures etc) is on my server, so I simply mount this. As you can see my layout is different from yours, but that's simply because my setup is different. So, I repeat it's what best suits your needs.

:cool:

Oh okay. Sorry for bumping this thread so many times. I suppose I will just experiment. there is no harm in doing that since I can just resize. Thank you

---

