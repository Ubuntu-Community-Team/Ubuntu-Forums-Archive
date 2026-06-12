---
title: "Which distro for lightweight file sharing/storage?"
date: 2013-09-25
forum: General Help
---

### Post by Skillet98 on 2013-09-25
Okay, this requires a little bit of a story. I have a laptop that I'm currently using as a desktop (it's the most powerful PC in the house...). I also have two old Dell desktops (Pent 4, 512MB of RAM, on-board graphics... nothing too powerful). I've combined the two desktops (meaning, placed the hard drive from one into the other), and would like to use the storage space from the two hard drives with as little hassle as possible.

Basically, I'm asking how to turn them into some kind of media server so that I can store my music library on those twin hard drives in the desktop, and access it from my laptop. I saw a tutorial on using Samba in Ubuntu 12.04 to allow file sharing between Windows 7 and Ubuntu on my network. This would be great, except for the fact that my desktop hardware doesn't seem to be powerful enough for the latest versions of Ubuntu. I have 13.04 successfully installed, but the app launcher and top bar don't appear, and neither do window buttons or borders. I'm guessing this is because the later versions of Ubuntu aren't compatible with the 10 year old motherboard-integrated graphics.

So my question is... which distribution besides Ubuntu would allow me to (easily) turn that desktop into one giant shared folder, and is lightweight enough to run well on such an old system?

And before anyone suggests upgrades or "just buy an external HDD"... I'm obviously trying to avoid spending any cash on this particular project. And I'd rather put our old desktops to use, rather than having them sat in the closet collecting dust for another 10 years. ;)

Thanks in advance for any help.

---

### Post by nerdtron on 2013-09-25
NAS4Free is my vote here.
1. Get a flash drive and install the NAS4Free OS to the flash drive. 
2. Plug it in the computer and boot the Nas4Free
3. Configure your media share/storage using the NAS4Free web GUI.
Done.
This is very easy to setup. Plus, you can use whole 2 drives for storage, no reserve space/partitions for OS or system files. And you don't have to edit a single config file.

Anyway, that is just the easy route. Samba is still easy to setup with a bit of effort.

---

### Post by Doug S on 2013-09-25
I run ubuntu server edition (no gui) on a very very old 200Mhz computer with only 128 Megabytes of RAM. It runs samba surprisingly well.

---

### Post by whatthefunk on 2013-09-25
Ubuntu Server would be ideal, but you wouldnt have a GUI so if you arent familiar with the command line that might not be for you.
Another good option would be Crunchbang.  I run it on an old laptop with only 256 MB of ram and it works great.

---

### Post by mörgæs on 2013-09-25
> **Skillet98 said:**
> I'm guessing this is because the later versions of Ubuntu aren't compatible with the 10 year old motherboard-integrated graphics.

It does happen that support for old hardware is dropped, but it's a rare event. Which graphics card do you have?

---

### Post by BBQdave on 2013-09-25
> **Skillet98 said:**
> ...Pent 4, 512MB of RAM, on-board graphics... Basically, I'm asking how to turn them into some kind of media server...

Not sure about media server, but I have an old desktop with AMD Athlon XP processor at 1.53GHz with 256MB of RAM - running Ubuntu Server 12.04.

I have [**vsftpd**]("https://security.appspot.com/vsftpd.html") installed on the server, and access it with [**FileZilla**]("https://filezilla-project.org/") from my notebook. Easy to use, easy to backup and access data. This operates on a secure home network.

---

### Post by walterorlin on 2013-09-25
Would an old dell with a pentium 4 and 512 mb ram have usb boot? I know one I have lubuntu did not. You can get aroudn this with the plop bootloader on a livecd.

---

### Post by mastablasta on 2013-09-26
there are a couple of GUI options. the way they work is they install server software on it and then access the computer via webbrowser (you don't need whole desktop just to store files).
there are a couple of distributions that are already pre-configured with a webgui. for example have a look at:
Openmediavault (debian stable based server): [http://en.wikipedia.org/wiki/OpenMediaVault](http://en.wikipedia.org/wiki/OpenMediaVault)
Zentyal (ubuntu, gui based server for home and smaller companies): [http://en.wikipedia.org/wiki/Zentyal](http://en.wikipedia.org/wiki/Zentyal)
NAS4free is also another good option, however this one is BSD based.: [http://en.wikipedia.org/wiki/NAS4Free](http://en.wikipedia.org/wiki/NAS4Free)
edit: clearOS is another server version with a GUI (this one is based on CentOS/red hat)

you can just install server to it and then add/install **webmin** if you want a gui to administer it. server doesnt' need any GUI for administraiton but then you need to know the commands.

since you plan to put media on it you should also look at XBMC project.

---

