---
title: "Ubuntu 7.04 -&gt; 7.10 -&gt; Ubustu... +WinXP"
date: 2008-02-29
forum: General Help
---

### Post by Th3Professor on 2008-02-29
Okay, soon I will be making the move to Ubuntu Studio.

I currently have Ubuntu Live CD, 7.04 "Feisty Fawn".

I believe Ubustu works better with Ubuntu 7.10 "Gutsy Gibbon" (now using the main repo).

Once I get Ubuntu 7.04 installed, what steps would I take to get up to 7.10 and then get 7.10 up to the present release of Studio?

Most of my "*nix" experience is on Slackware Linux (about a year on that) and OpenBSD Unix (almost two years on that). I have yet to dive deep into the world of Debian-based systems, though from testing them out: I definitely prefer Debian-based over Red Hat-based, when comparing just those two.

Also, I'm going to have a partition (just a small bit) set aside for WinXP for no reason other than playing the game MapleStory. (I've tried various emulators and similar apps but they've generally disagreed with that particular game.) That game has a minimum HD requirement of 1.5g and recommended 3g.

I've read that the WinXP OS requires a "bare minimum" of 1.5g, a "recommended" of 2g, and a "'real world'" of 8g. Another source said that both "minimum" and "recommended" is 1.5g (for both Home and Pro).

What would you recommend as the minimum gigs to set aside for WinXP (Home or Pro)? (Excluding the game.)

I only have a 40g harddrive and would like to put as much of it into Ubuntu Studio as possible. Could I get away with 7g on WinXP, or 8g, or should I go as high as 10g? Any remaining HD space on the WinXP partition will otherwise just be wasted space... space I'd rather put into Ubuntu.

Should I install WinXP first, since I'll be splitting the computer between that and Ubuntu Studio?

Thanks! :)

p.s.- quick side question - is it true that Ubuntu doesn't have a "root" account but, rather, uses the 1st created account (regardless of name) as a type of root or type of superuser?

p.p.s.- Ubuntu Studio looks like a pretty cool set-up... do you use it? (I'd like to know peoples thoughts on it, like pros, cons, etc.)

p.p.p.s.- Is there such thing as a Fluxbox Ubuntu Studio? Or any non-Gnome and non-KDE version of the studio? Or even something like an WM2 version. (I'm a fan of simplicity when it's possible.) Thanks! :)

---

### Post by Iandefor on 2008-03-01
> **Th3Professor said:**
> Okay, soon I will be making the move to Ubuntu Studio.

I currently have Ubuntu Live CD, 7.04 "Feisty Fawn".

I believe Ubustu works better with Ubuntu 7.10 "Gutsy Gibbon" (now using the main repo).

Once I get Ubuntu 7.04 installed, what steps would I take to get up to 7.10 and then get 7.10 up to the present release of Studio?I'd just download an Ubuntu Studio 7.10 ISO, but if that's not an option or less desirable, you can just replace every instance of the term 'feisty' with 'gutsy' in /etc/apt/sources.list, run ```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop
```And, if it didn't upgrade you to Gutsy by then, do a dist-upgrade.

If bandwidth is a concern, it may actually be less bandwidth-intensive to download the Ubuntu Studio ISO, or you can request a Gutsy disc from [ShipIt]("https://shipit.ubuntu.com/") or buy a DVD from Amazon.> What would you recommend as the minimum gigs to set aside for WinXP (Home or Pro)? (Excluding the game.)8 gigs is usually around what I need.> Should I install WinXP first, since I'll be splitting the computer between that and Ubuntu Studio?XP should go first, if only to ease headaches around bootloaders. Ubuntu and XP each install their own bootloader, but Ubuntu's is generally less of a pain to manage. Installing Ubuntu last ensures that Ubuntu will install its bootloader over XP's.
> p.s.- quick side question - is it true that Ubuntu doesn't have a "root" account but, rather, uses the 1st created account (regardless of name) as a type of root or type of superuser? Sort of. Ubuntu has a root account, but it's left unconfigured by default. The idea is that the first created user is given root-like powers in /etc/sudoers, and any administration is done through sudo. You can read more about the rationale for doing this [here]("https://help.ubuntu.com/community/RootSudo").
> p.p.p.s.- Is there such thing as a Fluxbox Ubuntu Studio? Or any non-Gnome and non-KDE version of the studio? Or even something like an WM2 version. (I'm a fan of simplicity when it's possible.) Thanks! :)Not to my knowledge, but making [metapackages]("https://help.ubuntu.com/community/MetaPackages") for dpkg is [easy-peasy]("http://iandefor.wordpress.com/2006/12/16/howto-make-a-metapackage-and-repository-for-your-metapackage-and-surprise-im-quit-of-bumps/"). You could probably just modify the Ubuntustudio metapackage to pull in what you want. Or you could append studio-specific packages to the Xubuntu metapackage or something.

---

### Post by Th3Professor on 2008-03-01
Thank you! :)

> **Iandefor said:**
> I'd just download an Ubuntu Studio 7.10 ISO, but if that's not an option or less desirable, you can just replace every instance of the term 'feisty' with 'gutsy' in /etc/apt/sources.list, run ```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop
```And, if it didn't upgrade you to Gutsy by then, do a dist-upgrade. If bandwidth is a concern, it may actually be less bandwidth-intensive to download the Ubuntu Studio ISO, or you can request a Gutsy disc from [ShipIt]("https://shipit.ubuntu.com/") or buy a DVD from Amazon.

Good point... I'll go ahead and burn a fresh 7.10 cd.

Would it still be a good idea to run "sudo apt-get update" with 7.10?

That is very cool that to get Studio all I have to do is "sudo apt-get install ubuntustudio-desktop"! Is that the big change from 7.04 to 7.10? (Part of Studio going to the main Ubuntu repository?)

> **Iandefor said:**
> 8 gigs is usually around what I need.XP should go first, if only to ease headaches around bootloaders. Ubuntu and XP each install their own bootloader, but Ubuntu's is generally less of a pain to manage. Installing Ubuntu last ensures that Ubuntu will install its bootloader over XP's.

I've used 8gigs in the past, was hoping I could get away with reducing that. Although an attempt to save 1 or 2 gigs so I can put it back into Ubuntu could do well (even in this day and age, just 1 or 2 gigs can really come in handy), perhaps it'd be too much trouble to do that only to find out later that WinXP needed that extra space for more unnecessary space-wastage (as that OS tends to do).

I've considered the perspective - of which to install 1st and which to install 2nd - along lines of less headaches in dealing with partitioning the hard drive when putting XP 1st. However, I've never thought of the advantage of actually putting a non-Windows on 2nd, as with your mention of Ubuntu's bootloader going on top of XPs. You've gotta very good point in that.

Does Ubuntu use GRUB or LILO or something else?

My early experience was with LILO and I liked it, though when I discovered GRUB - and all the features built in to it - I was much more impressed with that.

> **Iandefor said:**
> Sort of. Ubuntu has a root account, but it's left unconfigured by default. The idea is that the first created user is given root-like powers in /etc/sudoers, and any administration is done through sudo. You can read more about the rationale for doing this [here]("https://help.ubuntu.com/community/RootSudo").

Good reference. It explains a lot.

When I require superuser-type access, the vast majority of the time I do use "sudo". However, I would like to enable root (without having to use sudo). How do I do that? (That page basically said to ask someone how to do it.)

My number 1 concern in switching from Unix to Linux is security. I understand that enabling root always opens the window of brute-force attacks, though with implementing strong security (including insane passphrases) that should help a lot.

Does OpenBSD's "pf" work in Linux? (Or how would I otherwise maximize the security of my Ubuntu set-up?)

> **Iandefor said:**
> 
Not to my knowledge, but making [metapackages]("https://help.ubuntu.com/community/MetaPackages") for dpkg is [easy-peasy]("http://iandefor.wordpress.com/2006/12/16/howto-make-a-metapackage-and-repository-for-your-metapackage-and-surprise-im-quit-of-bumps/"). You could probably just modify the Ubuntustudio metapackage to pull in what you want. Or you could append studio-specific packages to the Xubuntu metapackage or something.

Wow! That is very cool! I have never heard of the metapackages (except, I suppose, xubuntu, kubuntu, edubuntu).

The ubuntu.com link mentions "Desktop metapackages", "Ubuntu system metapackages", "kernel metapackages", and "language metapackages". My hunch is someone can just pick one and go with it? (The exception being the kernel and language metapackages might require adding GNU-type stuff, like window manager or desktop environment, on top?)

I'm confused between desktop metapackage and Ubuntu system metapackage. The Ubuntu system metapackage also has desktop environments. It looks like that section should just be merged into the desktop metapackage section?

I'm really curious about the "Ubuntu-minimal" metapackage, it automatically fits within my fondness of "simplicity when possible". Does the "minimal" include a gui (possibly x.org or xfree86) or is it strictly console-based?

If I was going to put Ubuntu - but *not* Ubuntu Studio - on the computer, I'd probably go with that minimal metapackage and build up from there with a personalized set-up. However, I have a hunch Ubuntu Studio might require use of some of features that come with GNOME, or at least a similar DE. (Though, if Studio would work with just a "window manager", not requiring an actual "desktop environment", then I might actually go with that.)

I've briefly used KDE, don't really have an opinion on it. I've used GNOME a lot more, it's nice. I've used the Fluxbox wm quite a bit - really like it a lot. I've toyed around with XFCE and it seems to be quite an effective "light-weight" version of a desktop environment. (In that case, I suppose I could just try the xubuntu or xfce metapackage.) And yet, upon further consideration, the edubuntu might come in handy - as I'll be using the Studio features for instructional purposes. There are so many options! :)

Perhaps it would be better to select only certain features from edubuntu and studio. Then pick either xubuntu, gnome, kde, or a window manager-only option (I'm not sure which to pick for a DE or for a WM)... and then piece it all together.

It seems like any one of those would include applications that I really don't want on the computer, which would allow for improving efficiency of how I'd be using it.

> **Iandefor said:**
> 
Not to my knowledge, but making [metapackages]("https://help.ubuntu.com/community/MetaPackages") for dpkg is [easy-peasy]("http://iandefor.wordpress.com/2006/12/16/howto-make-a-metapackage-and-repository-for-your-metapackage-and-surprise-im-quit-of-bumps/"). You could probably just modify the Ubuntustudio metapackage to pull in what you want. Or you could append studio-specific packages to the Xubuntu metapackage or something.

The wordpress.com link you mentioned will definitely come in handy. I like that it provides an approach without being 100% "generic howto" or 100% "do-it-yourself". The compromise keeps it simple.

Side-note regarding that link:
There is an interesting step on that page - where it mentions making the directory "[dir]/pool/[dir]/[dir]/". The concept of "pool" is introduced in the recent release of Solaris Unix. Solaris 10 now implements a completely new file system. Older versions of Solaris used UFS, which was derived from BSD's FFS. (Interesting how SysV and BSD borrow from each other.) Anyway, the new - and *vastly* improved file system that Solaris uses is ZFS. It is a godsend. From spending some time in the realm of Solaris I grew quite fond of the new file system... it'd be nice if it complete ports were available for Linux and multiple flavors of BSD Unix. Maybe it is and I just don't know about it. Sun's NFS (and VFS, too, for that matter) was of course another great contribution to the world of computing in general. Anyway, ZFS is "Zettabyte File System", though I personally like to just think of it in more of a slang-sense, as "zone file system" for the use of zones and pools.

Here's a paraphrased wiki's explanation...
Their use of "storage pools" breaks away from the function of traditional file systems. ZFS doesn't require a volume manager (like other file systems), it consists of "virtual" storage pools, aka "zpools", that are built on top of "virtual" devices, aka "vdevs", which are built on top of the actual block devices (files, partitions, and most significantly: *entire drives*). Crazy stuff! And awesome. The vdevs can be set up non-redundantly, or as a RAID or RAID-Z. To top it off, the entire capacity of all vdevs is available to all within the pool ("zpool"). Unlike the common 32-bit or more popular 64-bit file systems, ZFS is a *128-bit* file system! Again, awesome. "...it can store 18 billion billion (18.4 × 10^18 ) times more data than current 64-bit systems." (Regarding it as the "zettabyte file system" - zettabyte comes after exabyte, which comes after petabyte, which comes after terabyte, which comes after gigabyte. Is a 128-bit file system practical right now? In most cases, probably not, but it's available; and regardless of how massive the data storage capacity can be, the actual function - pools and zones (sharing load and space) - is immediately a much more practical feature.) On the subject of data compression: "If data compression is enabled, variable block sizes are used. If a block can be compressed to fit into a smaller block size, the smaller size is used on the disk to use less storage and improve IO throughput".

It looks like ZFS is potentially available for non-Sun/Solaris systems... Porting it to Linux might work but would be tricky; one suggestion is porting it to Linux's FUSE system to run in userspace; there's mention of an impact on performance due to the kernel; mention of NTFS-3G doing well with it; optimization required to allow for an "excellent performance"; and Sun has also been incorporating more of Linux (or at least Linux compatibility) into their base system, including "investigating" an actual Linux port for ZFS. It looks like there's a BSD port, though I only see mention of a completed port for FreeBSD (not OpenBSD and others).

So anyway, back to the link - mention of the ".../pool/..." directory reminded me of ZFS. :)

In an ideal world, one could take pieces of several different systems and put them together into a completely separate one. The capability of playing the Windows-only game, "Maple Story", without headaches of emulators, the advantages of Sun's ZFS, security of OpenBSD, and gobs of goodies that come with Linux.

---

### Post by Th3Professor on 2008-03-01
Looks like edubuntu is mostly a general education system... maybe it won't do well for music instruction purposes.

The languages metapackages lists Japanese... but not Chinese... I'm curious - are there any Chinese Ubuntus? Or ways of incorporating it into the system. (Perhaps stick with a normal English system but use apps that allow for typing Chinese characters?)

---

### Post by Iandefor on 2008-03-01
> **Th3Professor said:**
> Thank you! :)No problem!

> Good point... I'll go ahead and burn a fresh 7.10 cd.

Would it still be a good idea to run "sudo apt-get update" with 7.10?

That is very cool that to get Studio all I have to do is "sudo apt-get install ubuntustudio-desktop"! Is that the big change from 7.04 to 7.10? (Part of Studio going to the main Ubuntu repository?)I'd still recommend running sudo apt-get update with 7.10, just to pull in security updates.

 Regarding Studio, it is pretty convenient how they keep all those useful metapackages in the main repository.> I've used 8gigs in the past, was hoping I could get away with reducing that. Although an attempt to save 1 or 2 gigs so I can put it back into Ubuntu could do well (even in this day and age, just 1 or 2 gigs can really come in handy), perhaps it'd be too much trouble to do that only to find out later that WinXP needed that extra space for more unnecessary space-wastage (as that OS tends to do).I'm betting you could get away with as little as five, but I'd try it out on a VM first.
> I've considered the perspective - of which to install 1st and which to install 2nd - along lines of less headaches in dealing with partitioning the hard drive when putting XP 1st. However, I've never thought of the advantage of actually putting a non-Windows on 2nd, as with your mention of Ubuntu's bootloader going on top of XPs. You've gotta very good point in that. Yeah, the XP bootloader can be a bit of a pain to make work with other operating systems. From what I've heard, it's not *hard*, but you do have to update entries on kernel upgrades for the other operating system, and if you're just going to use XP for playing games, you may as well use GRUB.

> Does Ubuntu use GRUB or LILO or something else?

My early experience was with LILO and I liked it, though when I discovered GRUB - and all the features built in to it - I was much more impressed with that.You're in luck, because Ubuntu uses GRUB.

> Good reference. It explains a lot.

When I require superuser-type access, the vast majority of the time I do use "sudo". However, I would like to enable root (without having to use sudo). How do I do that? (That page basically said to ask someone how to do it.)It's pretty easy. just do "sudo passwd root" and set root's password. That enables the account, and if you should ever need to login as root using GDM for whatever heavens-forsaken-reason, remember to enable that option in the GDM configuration dialog (It's under System->Administration->Login Window in the menus), under the "Security" tab.> My number 1 concern in switching from Unix to Linux is security. I understand that enabling root always opens the window of brute-force attacks, though with implementing strong security (including insane passphrases) that should help a lot.True, and if you know what you're doing, it should be pretty easy to minimize the risk.
> Does OpenBSD's "pf" work in Linux? (Or how would I otherwise maximize the security of my Ubuntu set-up?) I don't know about pf, but you can use iptables in Linux. The manpage documentation is fairly extensive. I also know that in the next release of Ubuntu under development (Hardy Heron, set for release in late April), they're working on a command-line tool to make managing firewalls simpler. It's called ufw or something like that.
> 
Wow! That is very cool! I have never heard of the metapackages (except, I suppose, xubuntu, kubuntu, edubuntu).

The ubuntu.com link mentions "Desktop metapackages", "Ubuntu system metapackages", "kernel metapackages", and "language metapackages". My hunch is someone can just pick one and go with it? (The exception being the kernel and language metapackages might require adding GNU-type stuff, like window manager or desktop environment, on top?)

I'm confused between desktop metapackage and Ubuntu system metapackage. The Ubuntu system metapackage also has desktop environments. It looks like that section should just be merged into the desktop metapackage section?Looking at that page, it looks like the "desktop" metapackages are for people who want to use the vanilla desktop distribution. The *-desktop metapackages under "Ubuntu System Packages" are metapackages that provide a particular Ubuntu distribution- for instance, while the xfce metapackage pulls in xfce, xubuntu-desktop pulls in xfce, artwork, xubuntu's default settings, and the Xubuntu application set.> I'm really curious about the "Ubuntu-minimal" metapackage, it automatically fits within my fondness of "simplicity when possible". Does the "minimal" include a gui (possibly x.org or xfree86) or is it strictly console-based?It's console-based. I won't list all of the packages it pulls in (because there are like, 80), but you can inspect the dependencies of any package by using the command "apt-cache depends [package]", and, if you want a more general summary, "apt-cache show [package]"> 
If I was going to put Ubuntu - but *not* Ubuntu Studio - on the computer, I'd probably go with that minimal metapackage and build up from there with a personalized set-up. However, I have a hunch Ubuntu Studio might require use of some of features that come with GNOME, or at least a similar DE. (Though, if Studio would work with just a "window manager", not requiring an actual "desktop environment", then I might actually go with that.)From what I can tell by looking at the dependencies, Ubuntu Studio really is just Ubuntu with Studio additions. The ubuntustudio-desktop package pulls in most of the same packages that ubuntu-desktop does, with some more added on.
> I've briefly used KDE, don't really have an opinion on it. I've used GNOME a lot more, it's nice. I've used the Fluxbox wm quite a bit - really like it a lot. I've toyed around with XFCE and it seems to be quite an effective "light-weight" version of a desktop environment. (In that case, I suppose I could just try the xubuntu or xfce metapackage.) And yet, upon further consideration, the edubuntu might come in handy - as I'll be using the Studio features for instructional purposes. There are so many options! :)

Perhaps it would be better to select only certain features from edubuntu and studio. Then pick either xubuntu, gnome, kde, or a window manager-only option (I'm not sure which to pick for a DE or for a WM)... and then piece it all together.

It seems like any one of those would include applications that I really don't want on the computer, which would allow for improving efficiency of how I'd be using it.You should be able to freely trim packages you don't want from the installation to get it as you like it.

One thing to remember: if you remove a package which a metapackage depends on, it'll uninstall that metapackage, too. That's fine, since the metapackage itself is only useful for depending on a bunch of other stuff and provides nothing on its own.
> 
The wordpress.com link you mentioned will definitely come in handy. I like that it provides an approach without being 100% "generic howto" or 100% "do-it-yourself". The compromise keeps it simple.

Side-note regarding that link:
There is an interesting step on that page - where it mentions making the directory "[dir]/pool/[dir]/[dir]/". The concept of "pool" is introduced in the recent release of Solaris Unix. Solaris 10 now implements a completely new file system. Older versions of Solaris used UFS, which was derived from BSD's FFS. (Interesting how SysV and BSD borrow from each other.) Anyway, the new - and *vastly* improved file system that Solaris uses is ZFS. It is a godsend. From spending some time in the realm of Solaris I grew quite fond of the new file system... it'd be nice if it complete ports were available for Linux and multiple flavors of BSD Unix. Maybe it is and I just don't know about it. Sun's NFS (and VFS, too, for that matter) was of course another great contribution to the world of computing in general. Anyway, ZFS is "Zettabyte File System", though I personally like to just think of it in more of a slang-sense, as "zone file system" for the use of zones and pools.I seem to recall seeing in the FreeBSD 7.0-STABLE release notes that they implemented ZFS support, though don't quote me on that. Neat filesystem concept, though it's a little hard for me to wrap my head around.
> It looks like ZFS is potentially available for non-Sun/Solaris systems... Porting it to Linux might work but would be tricky; one suggestion is porting it to Linux's FUSE system to run in userspace; there's mention of an impact on performance due to the kernel; mention of NTFS-3G doing well with it; optimization required to allow for an "excellent performance"; and Sun has also been incorporating more of Linux (or at least Linux compatibility) into their base system, including "investigating" an actual Linux port for ZFS. It looks like there's a BSD port, though I only see mention of a completed port for FreeBSD (not OpenBSD and others).Well, porting it to an in-kernel module would be a bit of a problem because of licensing nonsense, but there was a Google SoC project to make a FUSE module, and [this blog]("http://zfs-on-fuse.blogspot.com/") seems to indicate it's still being maintained.

---

### Post by Iandefor on 2008-03-01
Another thought just occurred to me regarding dual-boot.

If you don't want to worry too much about juggling partitions between Windows and Ubuntu, you could try giving Windows your entire disk and then installing [Wubi]("http://wubi-installer.org/").

Wubi installs Ubuntu to a virtual filesystem, and enables booting from that filesystem from the Windows bootloader. It'll make apportioning space between Ubuntu and Windows easier to manage and more dynamic (NTFS and FAT resizing is kind of hazardous, but virtual disk resizing is pretty safe). There's a more complete guide to Wubi on the [Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide").

---

### Post by Th3Professor on 2008-03-01
> **Iandefor said:**
> It's pretty easy. just do "sudo passwd root" and set root's password. That enables the account, and if you should ever need to login as root using GDM for whatever heavens-forsaken-reason, remember to enable that option in the GDM configuration dialog (It's under System->Administration->Login Window in the menus), under the "Security" tab.

Cool, thanks!

> **Iandefor said:**
> I don't know about pf, but you can use iptables in Linux. The manpage documentation is fairly extensive. I also know that in the next release of Ubuntu under development (Hardy Heron, set for release in late April), they're working on a command-line tool to make managing firewalls simpler. It's called ufw or something like that.

Good to know. That'll definitely help.

> **Iandefor said:**
> It's console-based. I won't list all of the packages it pulls in (because there are like, 80), but you can inspect the dependencies of any package by using the command "apt-cache depends [package]", and, if you want a more general summary, "apt-cache show [package]"

Regardless of if I build up from the minimal package, that "apt-cache" will come in handy.

> **Iandefor said:**
> From what I can tell by looking at the dependencies, Ubuntu Studio really is just Ubuntu with Studio additions. The ubuntustudio-desktop package pulls in most of the same packages that ubuntu-desktop does, with some more added on. You should be able to freely trim packages you don't want from the installation to get it as you like it.

The default Ubuntu install - any idea how much hard drive space that alone takes?

I'll probably just be using the audio features in Studio, not the video or graphics. I might go ahead and remove the unnecessary Studio apps, as well as any unnecessary default Ubuntu apps, to help save space. Chances are audio recordings will eat up a lot of space.

> **Iandefor said:**
> ...[this blog]("http://zfs-on-fuse.blogspot.com/") seems to indicate it's still being maintained.

I'll probably stick with one of the default Linux file systems for the time being. If they ever manage to implement the zfs on fuse into the mainstream - more updates, larger community, etc. - I'll likely give that a try.

...in the mean time, lots of backing-up of current files to do before I can finally redo the computer and put "Ubustu" on it.

---

### Post by Th3Professor on 2008-03-01
> **Iandefor said:**
> Another thought just occurred to me regarding dual-boot.

If you don't want to worry too much about juggling partitions between Windows and Ubuntu, you could try giving Windows your entire disk and then installing [Wubi]("http://wubi-installer.org/").

Wubi installs Ubuntu to a virtual filesystem, and enables booting from that filesystem from the Windows bootloader. It'll make apportioning space between Ubuntu and Windows easier to manage and more dynamic (NTFS and FAT resizing is kind of hazardous, but virtual disk resizing is pretty safe). There's a more complete guide to Wubi on the [Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide").

Have you (or anyone else here) ever used Wubi?

---

### Post by Iandefor on 2008-03-01
> **Th3Professor said:**
> Regardless of if I build up from the minimal package, that "apt-cache" will come in handy.I use it all the time. If you haven't already you should read the manpage.> The default Ubuntu install - any idea how much hard drive space that alone takes?Around 2 or 3 gigs.> **Th3Professor said:**
> Have you (or anyone else here) ever used Wubi?I haven't. I haven't had a Windows install in ages.

---

### Post by Islington on 2008-03-01
Jjust chiming in to say, that although I have no interest in changing my current setup, this is a damn good thread.

---

### Post by Th3Professor on 2008-03-02
> **Islington said:**
> Jjust chiming in to say, that although I have no interest in changing my current setup, this is a damn good thread.

I make changes in my own set-ups quite a bit, trying out new things.

What's your current set-up?

---

