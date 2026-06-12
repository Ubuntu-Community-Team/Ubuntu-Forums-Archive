---
title: "clamav: any point?"
date: 2005-07-21
forum: General Help
---

### Post by gammyhand on 2005-07-21
I installed clamav...is there any need for it? And does it have a control panel? Or is it just a terminal application that lets me scan via a crontab set automation or by a manual scan?

---

### Post by Lunde on 2005-07-21
There are a lot of different opinions about the subject of antivirus in Ubuntu being needed. My opinion is:
Very litle point for your own safety, but i still think you may temporary store infected / host files that may harm others. Unless you share files in a network or pass on a lot of unsafe files by other methods, you may just as well run without.

No interface that I know of for ClamAV, but it's easy to write a shellscript to manage the needed commands, so there may be some out there.

---

### Post by jasplund on 2005-07-21
Clamtk ([http://clamtk.sourceforge.net](http://clamtk.sourceforge.net)) is gtk2 interface for clamav  but it depends on clamav 0.86 or higher which is not in the repositories.

---

### Post by Lunde on 2005-07-21
Nice to know..

---

### Post by jasplund on 2005-07-21
Gnome-Anti-Virus ([http://gnomeantivirus.berlios.de/](http://gnomeantivirus.berlios.de/)) is another frontend for clamav

---

### Post by gammyhand on 2005-07-21
Thanks.  I will try the front ends out :)

---

### Post by jasplund on 2005-07-21
[QUOTE=gammyhand]Thanks.  I will try the front ends out :)[/QUOTE]
I don't know about Gnome-Anti-Virus. But you can't use clamtk with the clamav version that's in hoary take a look at [http://ubuntuguide.org/#antivirusserver](http://ubuntuguide.org/#antivirusserver)

---

### Post by gammyhand on 2005-07-21
[QUOTE=jasplund]I don't know about Gnome-Anti-Virus. But you can't use clamtk with the clamav version that's in hoary take a look at [http://ubuntuguide.org/#antivirusserver](http://ubuntuguide.org/#antivirusserver)[/QUOTE]
 OK...how do I install the gnome-anti-virus package? It is a .gz file.

---

### Post by lotusleaf on 2005-07-21
[ClamAV Homepage]("http://www.clamav.net/")
[ClamAV Project Page]("http://sourceforge.net/projects/clamav/")
[KlamAV Front-End]("http://klamav.sourceforge.net/")
[KlamAV Front-End Project Page]("http://sourceforge.net/projects/klamav/")
[KlamAV Front-End Screenshot]("http://klamav.sourceforge.net/images/klamav_scan1.png")

KlamAV (a front end for ClamAV) requires ClamAV installed prior to use.

** While I use ClamAV I also use F-Prot Anti-Virus for Linux which is free:

[F-Prot for Linux]("http://www.f-prot.com/products/home_use/linux/")
[F-Prot Downloads]("http://www.f-prot.com/download/home_user/download_fplinux.html")
F-Prot direct downloads FTP directory: [ftp://ftp.f-prot.com/pub/linux/]("ftp://ftp.f-prot.com/pub/linux/")
[QtFprot Front End]("http://freshmeat.net/projects/qtfprot/")
[Xfprot Front End]("http://web.tiscali.it/sharp/xfprot/")
[Xfprot Front End Project Page]("http://freshmeat.net/projects/xfprot/")

QtFprot and Xfprot are front-ends for F-Prot antivirus and require F-Prot to be installed prior to use.

** All the above links and more are in my freely down loadable bookmarks file listed below in my sig.

---

### Post by dataw0lf on 2005-07-21
ClamAV main usage is for Linux mail servers that cater to Windows clients to clean out any suspicious emails. Linux in and of itself isn't very susceptible to viruses.

---

### Post by gammyhand on 2005-07-22
[QUOTE=dataw0lf]ClamAV main usage is for Linux mail servers that cater to Windows clients to clean out any suspicious emails. Linux in and of itself isn't very susceptible to viruses.[/QUOTE]
 I tried to install fprot and qtfprot and while I can run qtfprot it says no library found. This is my terminal output:

ralph@ralph:~$ sudo dpkg --force-overwrite -i $HOME/fp-linux-ws.deb Password: dpkg: error processing /home/ralph/fp-linux-ws.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/ralph/fp-linux-ws.deb
ralph@ralph:~$ sudo dpkg --force-overwrite -i $HOME/Desktop/fp-linux-ws.deb
Selecting previously deselected package fp-linux-ws.
(Reading database ... 99751 files and directories currently installed.)
Unpacking fp-linux-ws (from .../ralph/Desktop/fp-linux-ws.deb) ...
Setting up fp-linux-ws (4.5.4) ...
ralph@ralph:~$ sudo dpkg $HOME/Desktop/qtfprot_0.2.1c_i386.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use dselect for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
ralph@ralph:~$ sudo dpkg -i $HOME/Desktop/qtfprot_0.2.1c_i386.deb
Selecting previously deselected package qtfprot.
(Reading database ... 99796 files and directories currently installed.)
Unpacking qtfprot (from .../qtfprot_0.2.1c_i386.deb) ...
Setting up qtfprot (0.2.1c) ...

ralph@ralph:~$

---

### Post by lotusleaf on 2005-07-22
[QUOTE=gammyhand]I tried to install fprot and qtfprot and while I can run qtfprot it says no library found.[/QUOTE]

Have you tried Xfprot with fprot? See this thread it may help:

["**HOWTO: Install F-Prot with GTK frontend (anti-virus)"](http://www.ubuntuforums.org/showthread.php?t=25421)**

---

### Post by Hairy_Palms on 2005-07-22
does anyone know if theyre is an antivirus that can be used to scan windows for viruses? im customising a livecd and want to put an antivirus on there to scan any fubared windows disks

---

### Post by alb1954 on 2005-07-23
I use clamav  with Insert live cd to disinfect Windows machines.

---

### Post by caratcus on 2005-07-23
> I use clamav with Insert live cd to disinfect Windows machines.

Why not use [clamwin](http://www.clamwin.com) and prevent the infection?

While clamav isn't (yet) needed for a linux machine, it does have it's uses.  It can scan samba shares, both on the linux server and the windows server.  Clamav also regards phishing e-mails as quarantine material, so you can keep users free of this moderately dangerous garbage.  Additionally, it's nice to know that you won't inadvertently pass on an e-mail or file containing a virus.  I've not used any of the GUIs with clamav (unless you count clamwin), but I definently have it installed on two e-mail servers and all of the samba servers.

-caratcus

---

### Post by Tyche on 2005-07-24
[QUOTE=lotusleaf][ClamAV Homepage]("http://www.clamav.net/")
[ClamAV Project Page]("http://sourceforge.net/projects/clamav/")
[KlamAV Front-End]("http://klamav.sourceforge.net/")
[KlamAV Front-End Project Page]("http://sourceforge.net/projects/klamav/")
[KlamAV Front-End Screenshot]("http://klamav.sourceforge.net/images/klamav_scan1.png")

KlamAV (a front end for ClamAV) requires ClamAV installed prior to use.
[/QUOTE]

Thanks.  You just made an old W*****s user very happy, and MUCH more comfortable.

---

### Post by Hairy_Palms on 2005-07-24
thx, i would use clamwin it to prevent but i want to use it on other peoples comps not mine.

---

### Post by jasplund on 2005-07-27
ClamAv 0.86 has been added to the official backports. So ClamTk now installs fine

---

### Post by gammyhand on 2005-07-30
[QUOTE=jasplund]ClamAv 0.86 has been added to the official backports. So ClamTk now installs fine[/QUOTE]
I have reloaded my repositories and I still only see 0.85 (I have backports enabled).

---

### Post by jasplund on 2005-07-30
[QUOTE=gammyhand]I have reloaded my repositories and I still only see 0.85 (I have backports enabled).[/QUOTE]

Do you have that official backports in sources.list? 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

---

### Post by gammyhand on 2005-07-30
[QUOTE=jasplund]Do you have that official backports in sources.list? 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted[/QUOTE]
 I tried adding that in and get this error in synaptic:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Anyway, I downloaded the gz file from the website, alien'd it and installed it so I now have 0.86 and clamtk installed. However, if I run clamtk nothing happens...What is the command to run it?

---

