---
title: "New to Ubuntu Neverwinter Nights Original Version"
date: 2007-07-21
forum: General Help
---

### Post by Project_2501 on 2007-07-21
Hi,

 I just recently came over to Ubuntu from Windows and I am having a little problem. I have an original version of Neverwinter Nights that I am trying to install. I followed the instructions on Bioware's website, but when I try to run the game nothing happens. 

I am using Ubuntu Feisty Fawn 7.0.4 the AMD64 version. 

Here is a screen shot  of the directory that I have it installed in.  

[IMG]http://i204.photobucket.com/albums/bb61/burnedtubes/Screenshot.png[/IMG]

---

### Post by mpeters on 2007-07-21
I notice you are missing at least one file. You should have a file called "nwn" in the directory you've shown. This is just a shell script which sets some environment variables and runs the main executable "nwmain", however, the fact that you are missing it at all probably means you are missing other stuff. 

Are you sure you removed everything from the override directory and unpacked the .tar.gz file  in the right place? Open a Terminal and type:

```

cd "/home/john/My Games/Neverwinter Nights/nwn"
rm -rf override/*
tar -xzf English_linuxclient168_orig.tar.gz

```

This should, among other things, create the nwn file mentioned above. You should then be able to run NWN:

```

cd "/home/john/My Games/Neverwinter Nights/nwn"
chmod 750 nwn
./nwn

```

If this still doesn't work, any errors should be printed to the Terminal, post them here if that is the case.

---

### Post by Project_2501 on 2007-07-21
Well I wound up using that Rage Installer and my Disks. It installed it. I then used the codes you gave me. 

```
cd "/home/john/My Games/Neverwinter Nights/nwn"
~/My Games/Neverwinter Nights/nwn$ rm -rf override/*
~/My Games/Neverwinter Nights/nwn$ tar -xzf English_linuxclient168_orig.tar.gz
~/My Games/Neverwinter Nights/nwn$ chmod 750 nwn
~/My Games/Neverwinter Nights/nwn$ ./nwn
Failed to initialize graphics.

```
And as you can see it said my Graphics did not initialize.

---

### Post by Project_2501 on 2007-07-21
Ok I figured it out. My motherboard has an ATI Graphics chip so I had to download and install their proprietary drivers. The only reason I thought to do this was remembering hearing that ATI had/has problems in Linux.

Anyways thanx [mpeters]("http://ubuntuforums.org/member.php?u=333009")!!

---

