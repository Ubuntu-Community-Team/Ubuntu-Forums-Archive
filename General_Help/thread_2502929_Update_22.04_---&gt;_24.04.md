---
title: "Update 22.04 ---&gt; 24.04"
date: 2024-12-05
forum: General Help
---

### Post by mikegreen8 on 2024-12-05
Hi.

I want to update my Ubuntu 22.04 LTS Desktop to 24.04.01 LTS, AND retain all my apps. This is what I am planning to do:

A. Create a 100GB EXT4 GPT partition on an empty 1 TB SATA.

B. Download the 24.04 ISO, and using balenaEtcher, make a bootable USB.

C. Boot the USB and install ubuntu 24.04 on the newly created 100gb partition.

D. Boot the newly created 24.04 SATA, and mount my 22.04 Desktop partition.

E. rsync ALL my apps from my Desktop to the newly created ubuntu 24.04.

Questions:

1. What directories should I rsync FROM in order to retain all my apps ?

2. My desktop is running Unity and Nemo. Do I have to do anything special for these ?

3. I'm using alacarte. Do I have to do anything special to retain all my Menu Items ?

4. Note that my Desktop is MBR not GPT. Is this a problem ?

5. Any other suggestions ?

Thanks,
M....

---

### Post by grahammechanical on 2024-12-05
If you download and install Ubuntu 24.04 LTS you will get Ubuntu with the Gnome desktop environment. Why not download and install Ubuntu Unity. It is an official flavour of Ubuntu. 

[https://ubuntuunity.org/](https://ubuntuunity.org/)

Others on this forum might have more accurate information but my guess is that if you do what you are planning to do you will end up with a mess and a broken mess at that. Linux applications are spread over a range of folders. You will in effect be cloning the 22.04 system folders and then overwriting the 24.04 system folders. How is that an upgrade?

Better to do an online upgrade from 22.04 to 24.04 and hope for the best. You do not mention backing up your data. The home folder has the application configuration files. Backup the home folder might be a good idea.

How many applications that were not part of the default set of applications have you personally installed? If it is just alacarte and nemo, then why not install Ubuntu Unity and then install alacarte and nemo and copy over their configurations files.

Regards

---

### Post by Bashing-om on 2024-12-05
mikegreen8 - Yuk 2

2nd what grahammechanical says - you are looking at a real good way to break your system.

> 
5. Any other suggestions ?

debfoster :D
consider:
```

apt show debfoster

```

[LIST]
[/LIST]
[INDENT]a pointer in a better direction
[/INDENT]

---

### Post by oldfred on 2024-12-05
All your iser data is in /home including your apps.
Only if you modified system settings may you need files in /etc. I modify grub, but save a copy in /home so backed up with my backup of /home.
I export list of installed apps and use that to reinstall them. I now use a script to reinstall many, but still export list as part of backup.
Then new install & restore from backups.

If using gpt, you need either a bios_grub partition for old BIOS boot or an ESP - efi system partition for UEFI boot. Best to have as first partition(s). If old BIOS install, you may still want ESP, for future use. Easier to add when drive is new.

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)

If reinstalling same system, same apps are ok, but if an upgrade, you may not get all the same apps. Defaults to change.
And you need to manually remove obsolete apps that you do not want and remove old kernels, so they are not installed.
```
/usr/bin/apt-mark showauto > pkgs_auto_$(date '+%Y-%m-%d_%H:%M:%S')_$(hostname).list

/usr/bin/apt-mark showmanual > pkgs_manual_$(date '+%Y-%m-%d_%H:%M:%S')_$(hostname).list

```
For more info see:
man apt-mark


I do not use snaps, so not sure if easy way to reinstall them.
You can list snaps.
snap list
 ls -lh /var/lib/snapd/snaps/

---

### Post by dragonfly41 on 2024-12-06
> [COLOR=#000000]4. Note that my Desktop is MBR not GPT. Is this a problem ?[/COLOR][COLOR=#000000]
Your current sailing ship is holed below the waterline. Abandon ship and save any cargo (files) to move to a new ship (24.04 / GPT / EFI). Do it quickly since this flagship (UbuntuForums) is under a new Admiral Discourse.
You do not write what desktop you are using. You will need a new desktop which supports GPT / EFI.  Or try it out first in a Azure VM.  All my Ubuntu "cargo" is held in external SSD's in caddies. So all you need to install from LiveUSB to run Ubuntu attached to your desktop is (a) a powered USB 3.0 port (not USB 2.0 which is slow) and a powered external SSD container. At LiveUSB stage you need to use GParted to create a first EFI partition (about 500 MB, FAT, boot flags) and your second partition (Ext4) is where Ubuntu is installed. Other partitions are optional such as Share partition with Windows if you have that bed partner (as I do).  Dual boot or even poly boot. But 100 GB is too small for that plan. Multiple by at least 10.  1000 GB.  I have two 1000 GB caddies in a StarTech dual docking bay (powered).


[/COLOR]

---

### Post by mikegreen8 on 2024-12-06
Hi again.

Yikes and thanks for all the info.

Does this sound like a better plan:

A. on an empty 1TB SATA., use GParted to create a GPT partition structure, with a first 500MB EFI partition, and a second EXT4 100GB partition. 

B. Download the 24.04.01 LTS ISO, and using balenaEtcher, make a bootable USB.
(I am pondering using Ubuntu Unity, but it does not support QT. I use  filezilla, audacious, librecad, freecad, master pdf editor, and possibly some future mobile devices, all of which require qt. Is there any way around this ? AND, this post about Ubuntu Unity scares me:
                        [FONT=Verdana][SIZE=2][https://www.reddit.com/r/linux/comments/1c4zrb5/unity_desktop_in_2024_whats_youre_opinion/](https://www.reddit.com/r/linux/comments/1c4zrb5/unity_desktop_in_2024_whats_youre_opinion/)[/SIZE][/FONT]

   )

C. Boot the USB and install ubuntu 24.04 on the newly created 100gb partition.

D. Boot the newly created 24.04 SATA

E. Now for the real work - reinstall my key apps: 
audacity, bleachbit, bluefish, bless hex editor, calc, cairo dock, cherrytree, dlume, dosbox, filezilla, flameshot, freecad, geany, chrome, jedit, libreoffice (already installed), librecad, masterpdfeditor, menulibre, Nemo, proton bridge & mail, pulseaudio, qualculate, sqlite, thunderbird, and any others that I have forgotten about. A daunting task!

F. Mount my 22.04 Desktop partition. rsync my Desktop 'home' and 'etc' directories to the  newly created ubuntu 24.04.

G. Boot the newly created 24.04 SATA, Log in and select Unity on the gear icon.

H. Try to figure out how to get alacarte working.

Does this sound any better ?

Thanks again for all your help,
M....

---

### Post by oldfred on 2024-12-06
Better.
I like Kubuntu, but still install some gnome based apps. That ends up installing a lot of dependencies. But back when running fallback/gnome based, I added kde apps and got those dependences.

I would not just sync /etc. Newer versions may have different defaults, or not all settings from old install may be best. But good to have backup of /etc for any customizations you did. But even then some customizations may not be needed or are obsolete.

Sometimes I totally reinstall all apps that I have exported.
I do have a bash script that just reinstall the main apps I want. example of a couple of my lines. I just have multiple lines rather than only long line as over the years some app is obsolete and then entire line is not installed. Narrows down chance of issue.

```
apt-get install galculator gparted geany gimp  gramps
apt-get install procinfo lshw nmap gdisk

```

Note that now both Firefox & Thunderbird are snaps. 
I do not prefer snaps, so install the .debs from the ppa.

---

### Post by guiverc on 2024-12-07
I'm late to the party here, but I noted *Ubuntu Unity* mentioned.

Ubuntu Unity uses the `calamares` installer as do Kubuntu & Lubuntu, which makes a *non-destructive* re-install an option too don't forget.

Non-destructive installs aren't possible when using `ubuntu-desktop-installer` for 24.04 or 24.10 due to a problem with `ubuntu-desktop-provision`, which for now is being fixed by forcing format of `/` partition, meaning you can't non-destructively re-install.

I wrote about the install type [here on another support site]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533") but you'll also find links to Lubuntu's discourse/forum where its mentioned in a doc for *Quality Assurance* testing (*though that only applied up to 24.04; those testcases are no longer used*).

MBR or GPT doesn't impact this; it'll work equally well on both.

If you want to learn how it goes, COPY your existing system [partition] to the drive/partition where you were going to *fresh* install, then when *non-destructively* re-install over that & see if it keeps what you're wanting.

Do note:  QA testing only includes Ubuntu repository software, and it can work, and can also not-work with some third party software (*depending how they package & provide packages*), so you'll find some third party packages may require re-install; but it can make the process easier.  I've had success & failure with *snap* packages auto-reinstalling, but I've never worried as I always have a list of what was installed (*deb*, *snap*) anyway, and the install method was only ever intended to be used with official repository *deb* software anyway. I have not tested it with *flatpak* or *appimage*.

If you understand what I'm suggesting, you'll still have your old system (*which as I understand it you were going to have anyway*) if you have problems, so you can try again (ie. reformat; then recopy/sync data & re-install to copy)

---

### Post by dragonfly41 on 2024-12-07
> [COLOR=#000000]E. Now for the real work - reinstall my key apps:[/COLOR]
[COLOR=#000000]audacity, bleachbit, bluefish, bless hex editor, calc, cairo dock, cherrytree, dlume, dosbox, filezilla, flameshot, freecad, geany, chrome, jedit, libreoffice (already installed), librecad, masterpdfeditor, menulibre, Nemo, proton bridge & mail, pulseaudio, qualculate, sqlite, thunderbird, and any others that I have forgotten about. A daunting task![/COLOR][COLOR=#000000]

You have some that I also favour.
CherryTree, MasterPDFEditor, FlameShot. Proton Bridge, Thunderbird et al. Add Sublime Text, Inkscape etc. if you are in CAD work.

Tip: CherryTree in particular can be used as your base camp 1. Build your installation workflow in there.  Use CherryTree CodeBoxes as your repository for installing each application. One app per node. Commands can be in CodeBoxes (any language you choose - Bash, Python .. whatever).

In Proton add Proton VPN and Proton Pass.

Install Recoll for indexing files in your new desktop (and old desktop).

Add Krusader for file management. Dual panel.

Grsync. GUI for rsync.  And a host of others for backup. Study TheFu posts on backup.

[/COLOR]

---

### Post by mikegreen8 on 2024-12-09
Hi once again.

A few days ago I started this thread on upgrading from 22.04 to 24.04 by doing a clean install from a 24.04 ISO and re-installing all my apps.

Due to time constraints at this time, I decided do a 24.04 upgrade via the Software Updater, and just clicking on 'Upgrade'. With some minor issues, I got it churning away. 

When it finally requested a Reboot, I did so. Now it comes up with a screen in Terminal that says 'Ubuntu 24.01 LTS tty1' and asks me to login. Very different than the way it was.

What happened to my usual front end, and what do I do from here ?

Thank goodness for backups.


Thanks,
M...

---

### Post by oldfred on 2024-12-10
No gui?
What video card/chip?
If nVidia and you can boot to a terminal, you can install the nVidia driver and update kernels to use it.

---

### Post by grahammechanical on 2024-12-10
> When it finally requested a Reboot, I did so. Now it comes up with a  screen in Terminal that says 'Ubuntu 24.01 LTS tty1' and asks me to  login

What happens when you log in?

>  My desktop is running Unity and Nemo. Do I have to do anything special for these ?

You have lost the Unity desktop user interface because it is not part of the standard Ubuntu LTS upgrade path. The upgrade scripts are designed to upgrade a default LTS version to the next default LTS version. Had you been asking about doing an online upgrade I would have suggested taking the installation back to its default configuration as much as possible.

Did you remove Gnome Display Manager (GDM) and Gnome 3 shell? This might help you to install Unity Desktop and Light Display Manager (LightDM) which controls the login screen in Unity Desktop.

Regards

---

### Post by mikegreen8 on 2024-12-10
Hey [**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878")

A little off topic but:

How does Krusader compare with Nemo ? I like Nemo because of toggle (F3) dual pane option, option to open folder as root, and option to open a folder in terminal.

I will look into sublime. I use pycharm for coding in python,  and geany for coding in freebasic.

Luvin ubuntu,
M...

---

### Post by mikegreen8 on 2024-12-10
Hi.

After I log in, it stays in what appears to be terminal.

I did not remove Gnome Display Manager (GDM) and Gnome 3 shell.

I will restore, and change my 22.04 desktop to gnome and try again. When 24.04 is up and running, I will try to re-instate Unity. 

My big question - is it worth upgrading my perfectly running 22.04 for 24.04 ? Other then 2 extra years of support, what does 24.04 buy me ? And, down the road, I can always try installing the next ubuntu lts.

Interesting to note - I upgraded from 20.04 running unity to 22.04 seamlessly. No issues with unity at all. The best upgrade ever! Are they going downhill, or is it just me liking unity over gnome ?

Not sure how discourse is going to work out. Maybe we will meet there in the future.

Merry Christmas,
M...

---

### Post by yancek on 2024-12-10
>  My big question - is it worth upgrading my perfectly running 22.04 for 24.04 ?

If you don't have a reason to upgrade then don't.  Usual reasona are software a user wanta is available in a newer release and not the current, some software on your current system does not work and you believe it will on the newer release or you simply always want the newest software.  If the last is what a user want, Fedora is best for that with Linux.   You might look into Ubuntu pro which extends support.

---

