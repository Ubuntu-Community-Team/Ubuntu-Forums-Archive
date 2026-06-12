---
title: "Ubuntu Boot Screen Hanging"
date: 2007-02-25
forum: General Help
---

### Post by naz37 on 2007-02-25
I just installed ubuntu 6.10 for the first time today, i created it as a virtual machine using vmware on fedora core 6. Ubuntu originally worked fine until i tried installed vmware tools. i restarted after i installed vmware tools and now the startup screen hangs when the progress bar get near the end. 

Screenshot;
[http://i166.photobucket.com/albums/u98/naz37/Screenshot-Ubuntu-VMwareServerConso.png]("http://i166.photobucket.com/albums/u98/naz37/Screenshot-Ubuntu-VMwareServerConso.png")

It appearers everything else is still running in the background, i get control of the mouse and i can hear the drum sound it make at the login screen. if i try to restart the x server (ctrl+alt+backspace) i can hear the login drum sound again but the screen stay hung.

Also i hadn't yet run a update of the system so all the software is the original version.

**Update**
i managed to login in rescue mode and run apt-upgrade but doesn't seem to have helped

---

### Post by naz37 on 2007-02-25
in booting into rescue mode i can start the Xserver manually with "startx" and gnome seems to work fine. still cant see what is stopping it from booting properly.

---

### Post by nandotron on 2007-03-06
Hi,

my installation of Ubuntu hangs at pretty much exactly the same point as that screen, except i cannot hear any of the login sounds.

my installation is as part of a dual boot system with xp on a dell inspiron 9400.  From what i can tell, I had no problems booting ubuntu until the first time i had implemented the drivers to get my mobility radeon x1400 to display the correct resolution of 1920x1200.

I was successful with changing the resolution to 1920x1200 but the next time i rebooted, ubuntu froze at that point on startup.  

I'm a total noob to all of this, so i don't even know what i need to to to gain any info about the point at which the problem starts during startup.  Anyone out there had a similar experience to mine?  any help whatsoever would be greatly appreciated!

Thanks,
nando

---

### Post by nandotron on 2007-03-06
forgot to mention that my installation is 6.10, my x1400 is 256mb ram and its a full install on the dual boot system, not vmware, not sure if any of that is important...

---

### Post by AaronD on 2007-03-19
Hello I had the same problem and I think it is a problem with the version of VMWare Tools you are running.  I was using the 5.5.3 Workstation tools with XP as the host and I was getting the exact same thing.  After a bunch of fiddling I was able to get it going by loading the updated VMWare Tools from Workstation Beta 6.  I know I am being vague but it was a pain to get going.  If you are still stuck, let me know and I will see what I can do.

Thanks!

---

### Post by btetampa on 2007-03-22
I found no solution except uninstalling vmware tools:

1.  Start in rescue mode.

2.  Execute /bin/vmware-uninstall-tools.pl in tarball unarchive directory.

---

### Post by nandotron on 2007-03-22
i eventually got ubuntu installed and loading properly after i tried a fresh install.  i think i may have originally been trying to use the intel 915resolution graphics drivers instead of the fglrx drivers for ati.  sorry i cant be more exact, i'm a noob to all this and it was very much trial and error....

---

