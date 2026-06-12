---
title: "Some general questions from a Gentooer"
date: 2004-11-13
forum: General Help
---

### Post by celloandy on 2004-11-13
I've been using Gentoo for the past year and a half or so, and in general, I like it, but I've inadvertently rendered my system unbootable a few times, and I'm feeling like I'd be more productive with something that was a little more friendly and "just worked" a little more.  I've been thinking about switching to Ubuntu, but I'm curious about a couple of things:

First, Gentoo doesn't really have much of a concept of discrete versions.  Basically, running "emerge -u world" upgrades all of your packages to the latest versions, so you can pretty much always be running the latest versions of everything.  I really liked this in Gentoo, and it's one of the reasons I switched from Red Hat (I'd had some unpleasant consequences when upgrading from one version of Red Hat to the next).  How does this work in Ubuntu?  Can you just use Synaptic to always have the latest and greatest, or do you need to download new versions of Ubuntu as they are released and upgrade?

Second, at present, I have my whole filesystem (except /boot) on one big ext3 partition.  My home directory is about 30 gigs in size, and I'd rather not have to copy it all to DVD.  If I manually delete everything else on the HD, but just leave /home, can Ubuntu install around that, so that I can keep my home directory in place?  That would really save a lot of trouble.

Andrew

---

### Post by allen on 2004-11-13
apt-get dist-upgrade 

is the equivalent of ...

emerge -u world

i'm not to sure about the /home directory bit. but you shouldn't need to reinstall anyway. just add the new depository to synaptic and dist-upgrade.

---

### Post by fng on 2004-11-13
emerge sync -> apt-get update
emerge -u world -> apt-get upgrade

UNLESS there is a new ubuntu release -> apt-get dist-upgrade

---

### Post by celloandy on 2004-11-13
[QUOTE=allen]i'm not to sure about the /home directory bit. but you shouldn't need to reinstall anyway. just add the new depository to synaptic and dist-upgrade.[/QUOTE]
I'm running Gentoo right now, and it's not apt-based.  In any case, right now, I'm running Gentoo compiled for amd64, but I think if I reinstall, I'll install the 32-bit version (so I can use flash, w32codecs, etc.), so I'll need to reinstall no matter what.
[QUOTE=fng]UNLESS there is a new ubuntu release -> apt-get dist-upgrade[/QUOTE]
And that pretty much answers my question... so it's not exactly equivalent.  With Gentoo, there arent' releases.  You just upgrade, and get the newest everything... you don't have to worry about what versions of what packages are in what releases.  Still, this looks a lot better than Red Hat.  Thanks.

Andrew

---

### Post by celloandy on 2004-11-15
Does anyone know about installing around an already-existing home directory, though?

Andrew

---

### Post by TravisNewman on 2004-11-15
[QUOTE=celloandy]Does anyone know about installing around an already-existing home directory, though?

Andrew[/QUOTE]
 you should be able to make another partition, copy your home directory over to it, and then either set that partition as /home or copy it back over after you install. You may have to repartition and copy in increments depending on how much free space you have.

---

### Post by duff on 2004-11-15
[QUOTE=celloandy]Does anyone know about installing around an already-existing home directory, though?

Andrew[/QUOTE]

I haven't tried this, but maybe you could:

1) boot off a gentoo live cd
2) mount your harddrive
3) manually delete everything from `/` except for `/home`
4) reboot with the Ubuntu installer
5) during the Ubunu install you can manullay set up the paritions
6) select your 30 gigger, choose "use, but do not format" and "mount point: /".. I can't remember the exact labels for those options, but it should be obvious.

That should do the trick, although I've never done that.  When I moved from gentoo to ubuntu I copied my home dir to another computer over the network.

---

### Post by HungSquirrel on 2004-11-15
> Can you just use Synaptic to always have the latest and greatest, or do you need to download new versions of Ubuntu as they are released and upgrade?
Ubuntu has new releases every six months.  You can apt-get each new release to easily upgrade to new releases.  If you think every six months is too long for a package to be considered "latest and greatest", you can upgrade to the development release if you want.  Personally, I don't mind waiting six months for new packages, so I probably won't upgrade to the development release until it nears final.

---

### Post by daniels on 2004-11-15
The /home thing is easy, just set that partition to be mounted as / in the installer, but make ABSOLUTELY SURE you only specify this partition be mounted, NOT formatted.

You'd be better off having a separate partition though, honestly ...

---

### Post by celloandy on 2004-11-15
Alright, thanks for everybody's help.

Andrew

---

### Post by jdong on 2004-11-15
I don't agree with the **apt-get *upgrade** analogies.

apt-get upgrade tells the system to only bump packages <b>up to a newer version</b>. It also tells APT not to go resolving too many dependencies (i.e. back in firebird->firefox rename days, apt would upgrade firebird to the latest firebird, but fail to see firefox as a newer version of firebird). In this manner, it's most similar to **emerge -Ua world**

apt-get dist-upgrade tells APT to "try harder" to upgrade, like removing packages in favor of replacing them by others, etc. This command is much like **emerge -uDa world**.


Either way, APT is just as good, or even better, at doing updating and dependency resolving compared to Portage.


Note that the stable branch of Ubuntu (Warty at the moment) **does NOT receive version updates**. It only receives security updates, and critical bugfixes backported to the released versions of packages.

stable branches will get version updates in every 6 months -- in this case, April 05 when Hoary Hedgehog comes out. It'll be a case of changing 5 Warty's to Hoary's and running your typical **apt-get update ; apt-get dist-upgrade**.

If you want a faster-evolving system, switch to Hoary now. I've yet to see any breakage, and it runs just as well as Warty.

---

### Post by wallijonn on 2004-11-16
[QUOTE=jdong]If you want a faster-evolving system, switch to Hoary now. I've yet to see any breakage, and it runs just as well as Warty.[/QUOTE]

Unless you have an ATI video card and want to use 3D acceleration. You'd probably be better off sticking with Warty. I created a dual boot with Hoardy and decided it just wasn't worth it to me.

I also tried Gentoo's VidaLinux and couldn't put up with their compile times and Portage (I'm sorry, but, I much more prefer SPM). It did look nicer in many respects (fonts, GRUB menu, splash screen) but it didn't come packaged with OpenOffice, FireFox, and I believe, The GIMP. But it did boot floppies well. After playing around with it for a week, I deleted it.

---

### Post by celloandy on 2004-11-17
Another question: I'm curious what packages are available for Ubuntu, and which ones are in which trees.  Is there something equivalent to [http://packages.gentoo.org](http://packages.gentoo.org) or [http://www.gentoo-portage.com](http://www.gentoo-portage.com), where one can browse the apt trees?

Andrew

---

### Post by jwb on 2004-11-17
I haven't reformatted my /home directory in 2 years. I set up / and /home (and the swap and boot) so that the bulk of the drive was /home.

Every time I upgrade or even change distros, I reformat all partitoins except /home. I just tell the partioning tool to mount the largest part of the drive as /home, and not format it.

Once you log in, after install, your settings are all still intact. Datas there, configuration settings are there. The only issues I've had are occasional icon issues or launchers not working for a program I have to install later. The data is always perfect, though.

I've done this over 2 years, going from Mandrake 8 -> RH 8&9-> Mandrake 9 -> Fedora 1 & 2 -> Ubuntu. I've even thrown SUSE, Lycoris and Linspire on a time or two just to see what they are about.

If you have a second machine, just rsync your home directory each night to that, and you'll always have a backup. Throw in stuff like /etc/fstab and any samba settings, etc, you need and you can be back up and running in no time.

---

### Post by jdong on 2004-11-17
[QUOTE=celloandy]Another question: I'm curious what packages are available for Ubuntu, and which ones are in which trees.  Is there something equivalent to [http://packages.gentoo.org](http://packages.gentoo.org) or [http://www.gentoo-portage.com](http://www.gentoo-portage.com), where one can browse the apt trees?

Andrew[/QUOTE]

I wish so, but not yet. That is a great idea though.


You could use packages.debian.org and search testing/unstable, which should contain roughly the same packages, or browse **archive.ubuntu.com**, which  is what I do.

---

