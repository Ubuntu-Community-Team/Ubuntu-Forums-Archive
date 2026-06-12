---
title: "Running Wubi from CD on Vista with latest patches will make the installer jam"
date: 2008-04-24
forum: General Help
---

### Post by ago on 2008-04-24
If you run Wubi from CD (or via the Ubuntu CD Menu), and have Vista with the latest patches, Wubi will jam at the end of the installation, once the CD is ejected.

Screenshot of hang: [http://launchpadlibrarian.net/13364302/wubi-stall.jpg](http://launchpadlibrarian.net/13364302/wubi-stall.jpg)

There is no point in waiting, that has **no consequences on the actual installation**, since the Windows-side installation is already completed at that stage. If that happens you can close the tray, close Wubi (or kill it if necessary) and reboot (without the CD in the tray) to comple the installation.

Again this **only affects Vista, and only when the latest Vista updates are installed**, and it **only affects the Wubi version on CD**. To avoid that simply copy Wubi (or Wubi.exe) from the CD to your Desktop and run it from there. If you download and run wubi from Ubuntu.com or wubi-installer.org it will also work well!

Unfortunately that issue was discovered late in the process and it was not practical to delay the release to fix that. The point release CD (8.04.1) in July will address it properly.

If you have other issues please see the troubleshooting section of the [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by startgame412 on 2008-04-30
I am having a similar problem execpt that I am running on Windows XP Home SP2. Once Wubi installs ubuntu and the cd ejects, I am given the option to restart now or manually restart later. Choosing to restart now does nothing and when I try to manually restart, the system hangs execpt that I am still able ot move the mouse but I cannot do ctrl alt del to bring up task manager. The app does not freeze but it makes the pc freeze when choosing to reboot to proceed with the installation of ubuntu. This forces me to do a hard reboot by holding down the power button on my pc and when I try proceed with the installation of ubuntu, I get dumped into a busybox so seems that not being able to reboot normally currupts the installation.

---

### Post by ago on 2008-04-30
Always run chkdsk /r after you hardreboot
Also try to uninstall and install and use wubi.exe from wubi-installer.org. Please let me know if the same thing happens again.

---

### Post by jmemm37 on 2008-05-01
I am running Windows Vista Business and I had no problems with Wubi install. I even have the latest patches and all. It could possibly be select systems but mine is not included.:KS

---

### Post by jmemm37 on 2008-05-02
I just wanted to add one thing. If you are including SP1 as ALL updates, I must say that I downloaded and installed Vista SP1 on the day it was first released on two different computer systems. I experienced Blue Screen problems on both so I went ahead and uninstalled SP1 from both computers and am now not running SP1 at all. That may be a conflict with Wubi and SP1 though, and not  Vista without SP1.

---

### Post by the_anomaly on 2008-05-11
Would also like to add:  I am running Vista x64 Ultimate and the Wubi installer gets to 99.9% and stops, then says it cant read from the disk.  I too have all my updates installed.

I know that the ISO is ok and I was running it as administrator.  So as an alternative I loaded up Daemon tools, mounted the ubuntu ISO and installed it from there.  It installed quicker and gave no trouble what-so-ever.

:)

---

### Post by Brain_of_J on 2008-06-11
edit: deleted wrong thread

---

### Post by radar.duse on 2008-06-12
..it seems the same problem (wubi performs "...an illegal bla, bla, bla...") comes up on a recently patched XP-pro SP3 updated machine...

Is MS already feeling threatened by Ubuntu?..

---

### Post by godshah on 2008-06-14
oh that problem i also had that but fixed it, i found out that it my laptop was on Power saver and other one was Norton 360 which was conflicting but doing it Virus checking and other scans in background and Vista cannot handle the multitasking 

so i uninstalled Norton 360 using a Norton Tool Remover and then tried using WUBI it worked but didnt installed Ubuntu sadly cause of Raid :(

---

### Post by nukemelamers on 2008-06-15
i didnt have that problem on Vista Home SP1, 
it was running smoothly,
i insert the cd, open the wubi.exe >> follow the instruction >>> done >>> reboot >>> open ubuntu (completing installation)...done
but i got wireless problem

it was 32bit,
i am running on Acer Aspire 5520G, Turion64X2 1.9,2GB ram, 160GB HDD

---

