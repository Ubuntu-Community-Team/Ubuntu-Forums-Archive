---
title: "Can a /home Partition be Shared with Different Installs/Versions/Flavours of Ubuntu?"
date: 2008-05-05
forum: General Help
---

### Post by OzzyFrank on 2008-05-05
First off, I'm totally unfamiliar with having a /home partition, but know many do this. I've never really looked into what the possible advantages are, but have wondered about some of the possible complications, so would welcome the Pros and Cons from those of you who do this.

I've wondered if this approach is good for fresh installs of Ubuntu, where an upgrade wasn't an option, but you wanted your settings back after a fresh install. If your /home folder is on a separate partition, can you get a new system to recognise and use it? And expanding on that, could I have separate installs of, say, Ubuntu and Kubuntu, and even different versions of those, and share the one /home partition? Or even just 2 installs of the same version of Ubuntu (assuming one is the "safe" one and the other for experimenting/wrecking).

Or is putting one's /home folder on a separate partition purely for other purposes, like safety in case the system gets mangled, or the main partition gets corrupt? So I guess I am asking why do YOU have your /home folder on a separate partition, and are there even better uses of this, like being able to share a /home folder between more than 1 install?

---

### Post by eldragon on 2008-05-05
first off.
if i were to experiment with an install, i would definately consider virtualization, that set aside:

you can do this with a distro, keeping in mind that you have to keep same UID/GID for your login username/group otheriwse you will have file permission restrictions.

ive heard doing this with different distros isnt recommended since things may change between a distro and another (but i may be wrong).

advantages of a separate /home partition is that you can format / reinstall and keep your stuff separate. other than that, i wouldnt know.

---

### Post by jjk7288 on 2008-05-05
As eldragon said, one of the nice things is you keep your files. In addition, it will save all your settings - so if for some reason you need to reinstall Ubuntu, your desktop will more or less be the same when you log in after the format as pre-format.

That being said, it does restrict space on both partitions. If you install a lot of packages you might run out of room if you don't allocate enough.

The advantages, I think, heavily outweigh the disadvantages. Even if there are packages you have to reinstall, the associated programs will all still retain their settings as well.

It's fairly awesome. :)

---

### Post by OzzyFrank on 2008-05-06
OK, so I guess that means while probably all apps would have to be reinstalled after a fresh install of Ubuntu, any settings they keep in the /home folder will be used once they are reinstalled. That leaves those that keep their settings in system folders (I wonder what percentage of apps do that?). It would be great if there was a backup tool that would save installed programs and their settings and easily restore it all on a new system. Anyone know of something like that? And still interested in more pros and cons, if anyone has more wisdom to offer.

---

### Post by ladr0n on 2008-05-06
Most typical desktop applications store their configuration files in the /home folder.  This is primarily because it facilitates each user of the program having a different configuration, and also avoids any permissions issues that could be caused by writing configuration files to system directories.  There's a fairly good chance that every application you use will carry over its configuration from one install to the next if you use a separate /home partition that is re-used.  
I personally recommend doing this just because it makes upgrading so much easier.
Also, if you want to play around with using multiple distributions and sharing a /home directory, I'll tell you (cautiously) that it *should* work.  I tried this with openSuse and Ubuntu a little while ago, and it didn't work out as well as I wanted it to.  This was mostly because I didn't like openSuse enough to bother fixing it though. If you don't mind tweaking the user account settings a bit to sort out ownership issues and such, you should be able to share a /home directory between different distributions and not have any issues.

---

### Post by OzzyFrank on 2008-05-07
Thanks for all this info. I figured (based on my knowledge of Windows) that very little of my settings would work after a reinstall or what not. I am now starting to seriously consider making this step now. Just a couple of questions:

Will a distro like Ubuntu know there is a /home partition and give you the option of using it during an install?

Could you get the same results just writing over a freshly-created /home folder (on the same partition as the distro, like in a standard install) after a new install and basically restore one's settings that way?

And not seriously contemplating sharing a /home partition between distros, but thought I'd see how feasible it is.

---

### Post by forestpixie on 2008-05-07
You need to tell the partitioner that there is a /home - with ubuntu - choose manual.

Pick the home partition - edit partition, choose mount point of /home and it will do so - to use original as is - DON'T format, to use the partition and clean it format it.

Pick the / partition and edit it - pick mountpoint of / and format.

Hope that helps

---

### Post by dcstar on 2008-05-07
> **OzzyFrank said:**
> First off, I'm totally unfamiliar with having a /home partition, but know many do this. I've never really looked into what the possible advantages are, but have wondered about some of the possible complications, so would welcome the Pros and Cons from those of you who do this.
......

Different versions of Gnome can change /home system files that then make things crash when other versions are then run using it (I know this from experience......).

You technically can use a common /home for closely related releases - but it is still problematic.

The best thing about a separate /home in Ubuntu is that it is not affected by removing/installing the base Ubuntu system - so you can migrate to a new release by a brand new install (rather then an upgrade) and still keep everything in your /home tree.

It also means if your root filesystem suffers any corruption your /home is not affected.

---

### Post by eldragon on 2008-05-07
on behalf of making a system wide config backup, as far as i know, backing your /home and your /etc directories would back all systems (including users, passwords, and default config files).

thats what i do, i backup only the important stuff in my home and /etc
so i dont end up reconfiguring the system in the event of a hardware failure.

installing software is mandatory, and not that much of a problem with repositories..

---

### Post by OzzyFrank on 2008-05-07
Not sure of some things in a couple of responses:

**"DON'T format, to use the partition and clean it format it"**... means? OK, I gather that means during the install and picking the /home partition that you don't format it (which is fairly onvious, unless you enjoy data loss, hehe) but not sure about the rest. What doesn "clean it" mean, and why is it followed by "format it"?

**"installing software is mandatory,"** means I am not sure what... are you saying while settings are retained in /home, as for the software, you have to reinstall it all again? Forgive my ignorance.

**"backing your /home and your /etc directories would back all systems"** - OK, I can understand this, just making sure you are saying that if I had a one-partition system (ie /home on the same partition as the rest of Ubuntu) that I could just copy over those 2 folders and it would basically give me my old system back. Am I correct? (Just checking I have that right).

---

### Post by jjk7288 on 2008-05-09
As for the first point about formatting Ozzy, you are correct.

As for software, anything you installed via Synaptic or .deb packages will need to be reinstalled (as will anything that isn't installed in your home directory). However, some programs have installation scripts which allow you to install to your home directory if you choose.

As for backing up /home and /etc, yes, you would retain all of your settings, both on a user and system-wide basis. What it would NOT do, however, is retain installed programs. Those are usually stored in /usr/bin if I am not mistaken.

Hope that helps.

---

### Post by forestpixie on 2008-05-09
> "DON'T format, to use the partition and clean it format it" - shall rephrase it - was in a bit of a hurry.

What I meant was - if you want to use the original /home partition as such but don't want to keep data or configs, formatting it would leave you with a clean partition.

Probably a bit superfluous

---

### Post by OzzyFrank on 2008-05-09
Thanks heaps guys - I'm finding this very interesting. OK, yeah figured since most things get installed to **/usr/bin** that most programs would need to be reinstalled... and that it is one folder you wouldn't want to restore into a fresh install, of a newer version anyway (otherwise Hardy packages would conflict with Intrepid ones [thinking ahead here]).

Would there be any similar conflicts between versions of stuff by using a backed up **[COLOR="DarkRed"]/etc[/COLOR]** folder? Or is this just settings of programs etc and no real worry in that regard?

Does anyone think a central folder for programs is a good idea? GoboLinux uses its own file structure, with a /Programs folder where all installed apps go... wonder if Ubuntu is ever going to break the mould and do something like that... and if it is a good idea?

---

