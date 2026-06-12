---
title: "Can't upgrade Ubuntu 18.04 to 20.04"
date: 2023-08-04
forum: General Help
---

### Post by kubasienczyk on 2023-08-04
I'm having trouble upgrading my Ubuntu 18.04. Everytime I try, the process is interrupted with the following message:

[IMG]https://i.stack.imgur.com/toQRZ.png[/IMG]

What do I do?

---

### Post by yancek on 2023-08-04
Support for 18.04 ended in April of this year so you will have to find the correct mirrors for the archived 18.04.  Check the site below.

[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

---

### Post by ActionParsnip on 2023-08-04
You may need to install it
[https://ubuntu.pkgs.org/18.04/ubuntu-updates-main-amd64/ubuntu-minimal_1.417.5_amd64.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-updates-main-amd64/ubuntu-minimal_1.417.5_amd64.deb.html)
Its such an old release

---

### Post by kubasienczyk on 2023-08-04
@ActionParsnip The problem is, when I attempt to install the file, the terminal says:
ubuntu-minimal is already the newest version (1.417.5)

and aborts the process. So, according to my CPU, I both have and don't have the this file. I'm confused.

---

### Post by kubasienczyk on 2023-08-04
@yancek Thanks. I've taken a look, but I have zero idea how to utilize this and what to do next.

---

### Post by readableauthor on 2023-08-04
What's the output for this:
```

sudo apt-get update

```

---

### Post by kubasienczyk on 2023-08-04
@readableauthor

sudo apt-get update
[sudo] password for dell: 
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease
Hit:2 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) bionic InRelease         
Hit:3 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) bionic InRelease 
Hit:4 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease                
Get:5 [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable InRelease [5,931 B] 
Hit:6 [ftp://ftp.fu-berlin.de/linux/ubuntu](ftp://ftp.fu-berlin.de/linux/ubuntu) bionic InRelease                     
Hit:7 [http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu](http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu) bionic InRelease
Hit:8 [ftp://ftp.fu-berlin.de/linux/ubuntu](ftp://ftp.fu-berlin.de/linux/ubuntu) bionic-updates InRelease
Hit:9 [ftp://ftp.fu-berlin.de/linux/ubuntu](ftp://ftp.fu-berlin.de/linux/ubuntu) bionic-security InRelease            
Ign:10 [http://ppa.launchpad.net/smoser/bluetooth/ubuntu](http://ppa.launchpad.net/smoser/bluetooth/ubuntu) bionic InRelease       
Hit:11 [http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu) bionic InRelease
Err:12 [http://ppa.launchpad.net/smoser/bluetooth/ubuntu](http://ppa.launchpad.net/smoser/bluetooth/ubuntu) bionic Release         
  404  Not Found [IP: 185.125.190.52 80]
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/smoser/bluetooth/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by oldfred on 2023-08-04
You typically have to comment out or uninstall all ppas and hardware drivers.
Then with new install, reinstall those ppas you may need or want.
But new releases do not always have the same ppa available, either not required or not updated.

---

### Post by readableauthor on 2023-08-04
The updater seems to want to have an official mirror in the sources list which you do not have.
You could do the following:
Add the following lines to the /etc/apt/sources.list:
```

deb http://archive.ubuntu.com/ubuntu/ bionic main universe multiverse
deb http://archive.ubuntu.com/ubuntu/ bionic-security main universe multiverse

```
You can use gedit to edit the file:
```

sudo gedit /etc/apt/sources.list

```
Then update local caches:
```

sudo apt-get update

```
Then try updating the system via a GUI utility from the first post.

---

### Post by kubasienczyk on 2023-08-05
@readableauthor That got me a tad further. But:

[IMG]https://tinypic.host/image/GRzTm[/IMG]

---

### Post by readableauthor on 2023-08-05
You should remove all PPAs. You can use Software & Updates app for that.

---

### Post by yancek on 2023-08-05
Did you comment out the ppa entries in the /etc/apt/sources.list file?  You can do this by putting a # at the beginning of each line with ppa in it as shown below.

>  # [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) bionic InRelease         

---

### Post by kubasienczyk on 2023-08-08
"An unresolvable error occured while calculating the upgrade".

Not very informative.

---

### Post by kubasienczyk on 2023-08-08
I haven't! Trying that now.

---

### Post by kubasienczyk on 2023-08-08
Same thing again:
[I]
After updating your package information, the essential package 'ubuntu-minimal' could not be located. This may be because you have no official mirrors listed in your software sources, or because of excessive load on the mirror you are using. See /etc/apt/sources.list for the current list of configured software sources.
In the case of an overloaded mirror, you may want to try the upgrade again later.

[/I]This is my sudo gedit /etc/apt/sources.list[I]:

# deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
# deb [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) bionic main restricted
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) bionic-updates main restricted
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) bionic universe
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic universe
# deb [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) bionic-updates universe
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) bionic multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic multiverse
# deb [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) bionic-updates multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

# deb [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
# deb [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) bionic-security multiverse
# deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) focal main # disabled on upgrade to focal
# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse[/I]

---

### Post by Holger_Gehrke on 2023-08-08
Most PPAs these days are installed in files of their own in '/etc/apt/sources.list.d/'. The sources you commented out in /etc/apt/sources.list where not PPAs but official sources which might by now have gone offline. There's a [page in the Ubuntu Community Wiki]("https://help.ubuntu.com/community/EOLUpgrades") which describes the procedure for upgrading an EOL release.

Holger

---

### Post by atrab101 on 2023-08-09
I recently posted this thread, to thank the developers and community for a remarkably smooth upgrade from 18.04 to 20.04.  [https://ubuntuforums.org/images/ubuntu-VB4/bg_dotted.gif](https://ubuntuforums.org/images/ubuntu-VB4/bg_dotted.gif).  I am an unusual case, in that I built my system over 7 years ago with the last generation of ASUS motherboard that was XP compatible.  My research also showed Linux compatibility.  So I have a frozen configuration with spare parts I purchased to insure that I can support my system when obsolete parts are no longer available.  The government does something similar when purchasing spare parts for remotely located systems that have no external connectivity, this they can support as a self contained configuration for decades.  

So few people (if any!) will do what I am doing, but it is still remarkable to me that Ubuntu is so stable and upgrades have always worked without any problems.  My dual boot system gives me great performance on the Ubuntu side, and it preserves 30 years of Windows history on the XP side.  I regularly do disk images with Norton Ghost 14 and Acronis True Image on the XP side.  I do Disk Images with Clonezilla on the Ubuntu side.  All image methodology has been proven with tests, so I know I am protested in the event of system failures.

I caution that upgrades should be done with great care, to follow exact instructions.  If in doubt, pause and research.  Read about problems on this forum that others have experienced and avoid the same.  For example, I believe that if I had removed obsolete packages, my upgrade would have been burdened with searching for the same to address and update them first, but they could not be found because obsolete.  Maybe there is a way to overcome this, but it seemed best to me to avoid.  I have found no negative consequence to retaining obsolete packages, which of course are just inactive.

Best wishes for your upgrading.  Perhaps another attempt would be more successful.  Follow the advice of the great people that support these forums.

---

### Post by atrab101 on 2023-08-09
Sorry for the bad link.  Hopefully this will work:

[https://ubuntuforums.org/showthread.php?t=2489725](https://ubuntuforums.org/showthread.php?t=2489725)

---

### Post by kubasienczyk on 2023-08-11
So I'm trying to follow the instructions at this link: 
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

The crucial part is apparently getting my sources.list in order. As dumb as that question might come across, how do I get from **this**:

[I]# deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ubuntu.task.gda.pl/ubuntu/](http://ubuntu.task.gda.pl/ubuntu/) bionic main restricted
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.task.gda.pl/ubuntu/](http://ubuntu.task.gda.pl/ubuntu/) bionic-updates main restricted
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.task.gda.pl/ubuntu/](http://ubuntu.task.gda.pl/ubuntu/) bionic universe
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://ubuntu.task.gda.pl/ubuntu/](http://ubuntu.task.gda.pl/ubuntu/) bionic-updates universe
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.task.gda.pl/ubuntu/](http://ubuntu.task.gda.pl/ubuntu/) bionic multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://ubuntu.task.gda.pl/ubuntu/](http://ubuntu.task.gda.pl/ubuntu/) bionic-updates multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

deb [http://ubuntu.task.gda.pl/ubuntu/](http://ubuntu.task.gda.pl/ubuntu/) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://ubuntu.task.gda.pl/ubuntu/](http://ubuntu.task.gda.pl/ubuntu/) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://ubuntu.task.gda.pl/ubuntu/](http://ubuntu.task.gda.pl/ubuntu/) bionic-security multiverse
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main
# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse[/I]

To **this**:

[I]## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-backports main restricted universe multiverse[/I]

I'm having a hard time figuring out what to comment out, comment in - and how. Also, what's the codename? *Bionic*? *Bionic Beaver*? *bionic-beaver*?

Help the brother out. I'm in the dark here.

---

### Post by readableauthor on 2023-08-11
Have you tried Software & Updates app I suggested to remove the PPAs? You shouldn't be using old-releases, it's in general archive under bionic codename

---

### Post by oldfred on 2023-08-11
This shows a very basic sources list for bionic, back up first as shown.
reset /etc/apt/sources.list to bionic
[https://ubuntuforums.org/showthread.php?t=2414194&p=13843080#post13843080](https://ubuntuforums.org/showthread.php?t=2414194&p=13843080#post13843080)

Then change from bionic to focal
Change distribution. using find to replace in sources
#sudo sed -i 's/find/replace/g' /etc/apt/sources.list
sudo sed -i 's/bionic/focal/g' /etc/apt/sources.list

---

### Post by readableauthor on 2023-08-11
It's not a proper way to update your system oldfred

---

### Post by oldfred on 2023-08-11
While not the recommended way, we have an issue where sources are all mixed up & need to be fixed.
My suggestion for correct way is almost always, new clean install & restore from backups. But too many users do not even have any backup.

---

### Post by kubasienczyk on 2023-08-14
@oldfred Thanks. Let me clear the procedure up:

1: back up the sources.list doc
2: move it elsewhere (can it be done with GUI?)
3: create a new sources.list file with the linked terminal command
4: inside the sources.list file, replace each "bionic" entry with "focal"
5: sudo apt-get update > sudo apt-get upgrade > Software Updater > Upgrade

Is the above correct?

---

### Post by readableauthor on 2023-08-14
> **kubasienczyk said:**
> 

Is the above correct?

No, this will mess your system up.

Do the following:
1. Restore default /etc/apt/sources.list from here:
[https://gist.github.com/rhuancarlos/c4d3c0cf4550db5326dca8edf1e76800](https://gist.github.com/rhuancarlos/c4d3c0cf4550db5326dca8edf1e76800)
2. Update the APT caches:
```

sudo apt update

```
3. Delete all your PPAs using this answer:
[https://askubuntu.com/a/646918/1592865](https://askubuntu.com/a/646918/1592865)
4. Run the GUI updater tool.

---

### Post by oldfred on 2023-08-14
The link above I think is really the same, just with all the normal comments whcih are not processed as they have # as first char.

---

### Post by kubasienczyk on 2023-09-04
I would like to sincerely thank everyone who provided their insights on the matter. I was eventually able to upgrade 18.04 to 20.04 on both machines. @readableauthor's instructions were spot on and solved my problem.

Thank you!

---

