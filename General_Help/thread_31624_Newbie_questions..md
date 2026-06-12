---
title: "Newbie questions."
date: 2005-05-04
forum: General Help
---

### Post by Quad Damage on 2005-05-04
hi:

 i've just migrated to ubuntu from fedora core 2. i know a little about linux, but am completely new to ubuntu.

 is it possible to convert .rpms into .debs using alien and then use them on ubuntu?

 these are the programs that i want to install. i have their rpms.

 xmms, xmms-mp3, xmms-wma, mplayer.

 there is one more issue that i would like help on. whenever i try to mount my windows partitions on ubuntu, they get mounted all right, but the system shows directories as files.

 this is the command that i use:

 [FONT=Courier New]sudo mount -t vfat /dev/hdax /mnt/windows/x[/FONT].

 also, running [FONT=Courier New]sudo fdisk -l[/FONT] gives the following output:

 [FONT=Courier New]fdisk: cannot open /dev/hda[/FONT].

 thanks to all who help!

---

### Post by jcs296 on 2005-05-04
I don't know how well alien works, but have you tried just using synaptic to install xmms? It may not be in the default repositories, but you can install all the packages that you listed from the universe or multiverse ubuntu repositories (to enable them go to settings->repositories, then 'add' and enable universe and multiverse (non-free).  ).  To enable mp3 playback, go to ubuntuguide.org and follow the instructions as there are some other repositories you can add that will enable mp3 playback, wma, encrypted dvd playback, etc.

As for the hard drive issues, I'm not an expert (the ubuntu live cd detected by external disk's ntfs partition but now that the system is installed, it won't autodetect it).  I can only suggest using the disk mounter panel applet, which should list the drives that mounted or could be mounted (if the windows partition is FAT, it should probably show up here, and you can mount it using the applet).  If this works it may even give you the proper config line in /etc/fstab, but I'm not sure.

I hope some of this helps, sorry for the length.

---

### Post by 23meg on 2005-05-04
ubuntuguide.org has the answers to your questions.

---

### Post by Quad Damage on 2005-05-07
I'm on a dial-up connection. Using apt/Synaptic on such a connection is a real pain.

Is it possible to get .debs for the aforementioned programs somewhere? (just like you have freshrpms.net for .rpms) I do have a Debian Sarge DVD. Can I install .debs from it in Ubuntu?

Thanks once again.

---

### Post by Psquared on 2005-05-07
[QUOTE=Quad Damage]I'm on a dial-up connection. Using apt/Synaptic on such a connection is a real pain.

Is it possible to get .debs for the aforementioned programs somewhere? (just like you have freshrpms.net for .rpms) I do have a Debian Sarge DVD. Can I install .debs from it in Ubuntu?

Thanks once again.[/QUOTE]

You can, but as I understand it you will end up with a Debian Sarge system instead of Ubuntu.

Were you thinking of converting your old rpms from FC to *.deb packages to save you the download time? You probably won't have the latest and greatest that way and it may screw up your ability to update and manage packages.

As a former FC user I can tell you that Deb/Ubuntu is a lot more finicky about tracking packages and only using "official packages" than FC is. You could install about anything on FC, but you also ended up with many more dependency problems -- many of which were insoluble.

Get yourself a broadband connection. :)

---

### Post by Quad Damage on 2005-05-09
i guess you're right Psquared, i do need a broadband connection.

 thanks anyway for the help.

---

