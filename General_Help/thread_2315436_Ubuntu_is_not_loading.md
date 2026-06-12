---
title: "Ubuntu is not loading"
date: 2016-02-28
forum: General Help
---

### Post by Ubunteo88 on 2016-02-28
Hi, i'm new to the linux distributions, so i decided long time ago to install ubuntu and try to use it. Of course, i've made something wrong, so here me asking help to avoid formatting, also because i installed a dual boot, so i'm afraid to reinstall everything and making mistake with the mbr.
Especially, as i said in the title, ubuntu isn't loading. It stops a the boot screen with the logo and doesn't start, it simply stops and force to shut down and restart the machine. Honestly, i consider myself lucky since grub is loading, so i can post on the forum with my other os. So, here what i've done:

I tried to install a program, which i guess it won't load on "ubuntu willy" but only on "trusty" infact aptitude told me to install library files, and that there was somenthing missing. I tried to solve the problem, by installing libraries, but a conflict between libraries appeared to me. (lib..1vm or something like that) 
I deleted a willy werewolf library (my idea was to replace it with a new one, but i had to remove it.. :( ), i realized from the terminal that was foundamental (a main library for the system..oops) to load python, ubuntu software center and also the nautilus and probably others programs. 
Main software of the Ubuntu system (installed by default) disappeared, the apt suggested me then to launch a "sudo apt-get install -f" (i guess, since i don't remember the right command..). I honestly don't know what happened after, since nautilus reappeared, but the ubuntu software center no, and the machine freezed by forcing me to reset.
Is there a way, to solve the situation by starting from the grub? Is there a terminal to launch , and some commands, that tells me which depedencies are missing? So, i can see what is missing and reinstall library". 

I was thinking that is a problem with kernel, and since from the grub i can load old ones, that i haven't deleted, i tried to launch them. That wasn't the solution, no kernel is loading.

Hope there's a solution.

---

### Post by kc1di on 2016-02-29
Hello Ubunte088 and Welcome to Linux,

As I read your post , I believe the best thing at this time is to reinstall Ubuntu.  Without the exact name of the library you deleted it would be very hard to reinstall it. 
Just be careful and reinstall the system.

---

### Post by Ubunteo88 on 2016-02-29
I can tell you what's happened, at least what i found... I was trying to install ace player from [here]("http://forum.torrentstream.org/index.php?topic=2969.0"). I couldn't install since, it requires the package 

[LIST]
[*]acestream-player-data - set of common libraries for the player and plug-in 
[/LIST]

llibass4 (>= 0.9.7) ma non è installabile                          Dipende: libavcodec54 (>= 4:0.7-1) ma non è installabile oppure                                   libavcodec-extra-54 (>= 4:0.7-1) ma non è installabile                          Dipende: libavformat54 (>= 4:0.7-1) ma non è installabile oppure                                   libavformat-extra-54 (>= 4:0.7-1) ma non è installabile                          Dipende: libavutil52 (>= 4:0.7-1) ma non è installabile oppure                                   libavutil-extra-52 (>= 4:0.7-1) ma non è installabile                          Dipende: libdirac-encoder0 ma non è installabile                          Dipende: libdvbpsi8 (>= 0.2.0) ma non è installabile                          Dipende: libebml3 ma non è installabile oppure                                   libebml4 ma non è installabile                          Dipende: libgcrypt11 (>= 1.5.0-0) ma non è installabile                          Dipende: libgnutls28 (>= 2.9.11-0) ma non è installabile                          Dipende: libmatroska6 ma non è installabile oppure                                   libmatroska5 ma non è installabile                          Dipende: libpostproc52 (>= 4:0.7-1) ma non è installabile oppure                                   libpostproc-extra-52 (>= 4:0.7-1) ma non è installabile                          Dipende: libproxy1 (>= 0.2.3) ma non è installabile                          Dipende: libswscale2 (>= 4:0.7-1) ma non è installabile oppure                                   libswscale-extra-2 (>= 4:0.7-1) ma non è installabile                          Dipende: libtag1c2a (>= 1.7) ma non è installabile                          Dipende: libx264-123 ma non è installabile oppure                         


As you can see there are many of them were missing, and many are just containers who needed others lib to work. So, i tried to solve them until the conflict between :

"libproxy 1.04.11"  i think was the bad guy who creates the conflict with a willy werewolf lib that was foundamental. Honestly i don't remember the right name, but, was like "lib1vs5" or something like.. I just remember that was removed from the ubuntu software center and then everything has started to not work.

EDIT


I tried to launch old kernel from recovery mode, to start the system back, and from the root terminal it returned an error: Filesystem only in read and i can't use apt.
I think, that since i was trying to install the aceplayer and meanwhile ubuntu was downloading system updates, and the pc crashed before updates take effect. The apt has some critical error.

EDIT 2

Since it removed the nautilus i tried from recovery to launch:

> apt-get install --reinstall ubuntu--desktop

and returns this error:

> "Block on file only in read /var/lib/dpkg/lock
impossible to write in var/cache/apt"

the i launched fsck and dpkg but it doesn't start the updating process. Also apt-get update it's not working.

now it returns the errror:

> failed to start unit resolvconf.service 
failed to load no such file or directory

---

### Post by kc1di on 2016-02-29
Ok you can try this go to recovery, when the terminal comes up connect to the internet 
when that's finished type the following
```
dpkg --configure -a
``` 
if that works try reinstalling the desktop

Let me know what happens and we will go from there.

---

### Post by Ubunteo88 on 2016-02-29
Launched both but:
"apt-get install --reinstall ubuntu-desktop --fixmissing " 

interrupt the installation because it can't connect to repository. Seems like resolvconf isn't installed and i can't reinstall the package

"apt-get install resolvconf --fix-missing"

that returns

"internal error, ordering was unable to handle the media swap"

---

### Post by fantab on 2016-02-29
As suggested earlier, It will be a good idea to re-install Ubuntu... you may have unwittingly removed some important deps and libs...
A simple re-install method will be to Install Ubuntu on its existing partition without the choosing the 'Format' option on the partition during re-installation. This method will save your /Home folder and will not overwrite it.
However a complete re-install is recommended.

After reinstallation... Ubuntu Software Center -> Edit -> Software Sources... enable 'Partner' and or 'Independent' resources (software provided by third parties) also known as MULTIVERSE. Then 'reload' or run "sudo apt-get update" to refresh your repos.
Now add your Ace ppa as suggested and install the package. Third party libraries and dependencies are NOT provided by Ubuntu. [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

As a better alternative to Ubuntu Software Center, you can install Synaptic Package Manager.
Also DO NOT RUN two package handlers at one time.

---

### Post by Ubunteo88 on 2016-03-01
> **fantab said:**
> As suggested earlier, It will be a good idea to re-install Ubuntu... you may have unwittingly removed some important deps and libs...
A simple re-install method will be to Install Ubuntu on its existing partition without the choosing the 'Format' option on the partition during re-installation. This method will save your /Home folder and will not overwrite it.
However a complete re-install is recommended.

After reinstallation... Ubuntu Software Center -> Edit -> Software Sources... enable 'Partner' and or 'Independent' resources (software provided by third parties) also known as MULTIVERSE. Then 'reload' or run "sudo apt-get update" to refresh your repos.
Now add your Ace ppa as suggested and install the package. Third party libraries and dependencies are NOT provided by Ubuntu. [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

As a better alternative to Ubuntu Software Center, you can install Synaptic Package Manager.
Also DO NOT RUN two package handlers at one time.

I will, i wanna also try the kde4 so it will be the occasion to install it meanwhile i will reinstall ubuntu. I was thinking at the first time to install kubuntu, but i prefer Ubuntu. 

This is mine partition table:

-sda5: swap 
-sda6: ext4 ( /home) 
-sda7: ext4 (/ (root)
-sda2: ntfs (/windows7)
-sda3:ntfs (/Data)

I hope to not make a mess and creating problems with dual-boot during the installation. I guess that where is Ubuntu right now,or otherwise called (/root)  there's also grub2 that will be formatted and reinstalled.

---

### Post by Ubunteo88 on 2016-03-01
> **Ubunteo88 said:**
> 

This is mine partition table:
-sda5: swap 
-sda6: ext4 ( /home) 
-sda7: ext4 (/ (root)
-sda2: ntfs (/windows7)
-sda3:ntfs (/Data)


Ok everything went fine, and i reinstalled Ubuntu by formatting the partition and the OS and Grub2 too, by leaving Home Folder. I still have a little problem. I tried to install Kde.


```
sudo apt-get install kde-plasma-desktop
```

 He asked to me choose between lightdm and ssdm.  Since i don't which one to choose. I preferred the old one, or first option. Is there a guide on pros and cons about them?

Now i can't finish installation, apt-get is stuck again, i can't finish updates and kde plasma of course isn't working.. 

Here's the error description:

```
kde-telepathy-minimal : Dipende: kde-config-telepathy-accounts (>= 15.04.0) ma non è installato
```

so i tried to install it:

```

dpkg: errore nell'elaborare l'archivio /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb (--unpack):
 tentata sovrascrittura di "/usr/share/accounts/services/google-im.service" presente anche nel pacchetto account-plugin-google 0.12+15.10.20150723-0ubuntu1
dpkg-deb: errore: il sottoprocesso paste è stato terminato dal segnale (Pipe interrotta)
Si sono verificati degli errori nell'elaborazione:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Again a dependency is missing, but i have problems with it too.

I discovered that's a [bug]("https://bugs.launchpad.net/ubuntu/+source/ktp-accounts-kcm/+bug/1522439") and found a way to solve the situation.. 

```
dpkg --remove --force-remove-reinstreq account-plugin-google unity-scope-gdrive
```

---

### Post by kc1di on 2016-03-01
You should install kde by the following command -- it will pull all the dependencies you will need.
```
sudo apt-get install kubuntu-desktop
```

---

### Post by fantab on 2016-03-03
Gtk and KDE are two different desktops... unlike gnome, xfce etc which use Gtk engine, gtk2 and or gtk3, so more or less they gel well... KDE however is qt based and comes with its own KDE Libs and deps and can cause issues when mixed with Gtk desktops.

I would like to suggest don't mix Ubuntu and Kubuntu... or you may end up with quite a few GUI issues among others.
It is advisable to install Kubuntu on a separate partition of its own... if you only have to "try" Kubuntu then you have an option to 'try' Kubuntu from a USB flash drive or a DVD...

My two cents....

---

