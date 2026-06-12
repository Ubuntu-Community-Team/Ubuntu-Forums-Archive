---
title: "Hardy behaving like Windows?? Not good."
date: 2008-06-05
forum: General Help
---

### Post by jemjulio on 2008-06-05
Hi everyone. My name is Julio and I used to me a Windoze user :)

Not any more though. Decided to move to Ubuntu Hardy a few weeks ago and I'm happy about it.
This is my first post, as Ive been able to find the solutions to my questions in these forums. Great stuff. 

I'll explain where I am.
When I installed Ubuntu, the idea was a dual-boot, but I lost the Windows system partition. No big deal, I was sick of it anyway. And I have XP on my laptop ( they get on great on the network).
Anyway my Data partition was NTFS, so I moved all the files to some external drives , formatted in ext3 and put files back. I also moved my home folder to the Data partition.
Now the thing is, after all these alterations, the system runs like Windows... VERY BADLY.
App will freeze. Firefox will start, crash and disappear. Amarok will hang etc etc.

So these are my questions
- Whats my best bet to resolve this?  some kind of repair? a fresh installation? If so, Am I in danger of losing the data thats in the home folder? Should I disable the Data drive when I do? I'm concerned , because I didnt intend to delete my windows partition, but it happened ( that part wasnt very dumb proof, )
- If I re-install, should I try an older Ubuntu version, as I've read thet this release is not the best?
- Isnt there a "system restore" feature?

Thanks guys. Keep in mind that I am still lost with all this code ( thank god for copy and paste) so I need serious hand holding here :)

Julio

---

### Post by TWO on 2008-06-05
> **jemjulio said:**
> 

App will freeze. Firefox will start, crash and disappear. Amarok will hang etc etc.




First and foremost, I think it'd help if you said what your system specifications are. Those in the know will then be able to advise you accordingly.

Secondly, if you could state which versions of applications you are using, that would help. You can try reinstalling them via the Synaptic Package Manager and see if that solves anything. 

With regards to Amarok, I love Amarok a lot, but don't forget that it is a KDE program and whilst KDE programs can work under GNOME, it would run much better under say, Kubuntu. Consider trying Rhythmbox for size which is designed for GNOME. Also, I'd recommend downloading and trying Songbird. It is still in development, but I think it has the makings of a superb music player for Linux. In addition to that, I'm sure there is something to do with Amarok's database which might make it sluggish. You might have to set up MySQL database. Instructions can be found here: [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

> - If I re-install, should I try an older Ubuntu version, as I've read thet this release is not the best?

If you feel you need to re-install, don't go for an older version. This was only released in April so expect changes to it to be ongoing. As always, and just like with Windows, it'll take time for things to settle down. Opinion with regards to distributions is rarely objective. If anything, the developers of Ubuntu have been raving about Hardy Heron. It is improving all the time, you just have to be patient.  

> - Isnt there a "system restore" feature?
Not that I'm aware of. Someone else may know better though.

Just to finish, I don't think it's fair to say that Windows runs badly by default. If you're careful about what you download and install, there is no reason why Windows should become so sluggish. I dual boot with XP and whilst I admit that when you install things over time, XP does slow down, when you take care of it, it runs fine.

---

### Post by ibuclaw on 2008-06-05
Your problem seems very curious indeed.

In continuation to what TWO suggested.
These would show sufficient enough information about your system.
Can you post the output of these commands for us?

Release Version:
```
lsb_release -rd
```
CPU Model:
```
cat /proc/cpuinfo | grep "model name"
```
Kernel Version:
```
uname -r
```

Can you post your sources file too? (This will produce a sizeable output).
```
cat /etc/apt/sources.list
```

And the version numbers of FireFox and Amarok
```
apt-cache policy amarok firefox
```

I am also curious how you setup your partitions too.
```
df -Th
```

With that, should be able to help find a problem, if it exists.

Regards
Iain

---

### Post by TWO on 2008-06-05
> Can you post the output of these commands for us?

I like tinivole's suggestions! Much more to the point!

:)

---

### Post by jemjulio on 2008-06-05
Wow...:)

Thanks to you both. Thank god you gave me the commands......

Release Version:
Description:	Ubuntu 8.04
Release:	8.04


CPU Model:
model name	: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
model name	: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz


Kernel Version:
2.6.24-18-generic

sources file:
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) hardy/
 

Amarok and Firefox

amarok:
  Installed: 2:1.4.9.1-0ubuntu3+medibuntu1
  Candidate: 2:1.4.9.1-0ubuntu3+medibuntu1
  Version table:
 *** 2:1.4.9.1-0ubuntu3+medibuntu1 0
        500 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
        100 /var/lib/dpkg/status
     2:1.4.9.1-0ubuntu3 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/main Packages
firefox:
  Installed: 3.0~b5+nobinonly-0ubuntu3
  Candidate: 3.0~b5+nobinonly-0ubuntu3
  Version table:
 *** 3.0~b5+nobinonly-0ubuntu3 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy/main Packages
        100 /var/lib/dpkg/status

partitions

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3     71G   13G   55G  19% /
varrun       tmpfs   1014M  216K 1014M   1% /var/run
varlock      tmpfs   1014M     0 1014M   0% /var/lock
udev         tmpfs   1014M   60K 1014M   1% /dev
devshm       tmpfs   1014M   88K 1014M   1% /dev/shm
lrm          tmpfs   1014M   38M  977M   4% /lib/modules/2.6.24-18-generic/volatile
/dev/sdb1     ext3    463G  403G   37G  92% /home
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon     71G   13G   55G  19% /home/julio/.gvfs



Amarok has become unusable. The collections are full of files that link to the old ntfs partition, and although I have uninstalled and reinstalled its the same and I cant even delete these files.
Firefox, starts loading and while its loading the 4 tabs, it dissapears!! Completely. I launch again and its ok....

I really appreciate the help, I'm determined to stay with Linux, and maybe even understand how it works even :-)

You guys are awesome

Julio

---

### Post by bingoUV on 2008-06-05
1. Did you update Ubuntu after installation? Lot of problems that you are facing might have been solved by now. You can update using Add/Remove Programs.

2. If updates do not solve your problem, biggest suspect is bad graphics card drivers. Post the output of the following command to let us know your hardware details
```

sudo /sbin/lspci

```

---

### Post by jemjulio on 2008-06-05
Hey.
No joy:


julio@ubuntu:~$ sudo /sbin/lspci
sudo: /sbin/lspci: command not found

It updates itself regulary. 
I probably havent been very clear. At first it was great....running beautifully, even with the NTFS Data drive. Its been updating and tampering to get stuff to work that have caused all this I think  :(


Julio

---

### Post by ibuclaw on 2008-06-05
Hi, sorry for the wait. I'm back from work now :)

From what I can see your partitions look very sound! Well Done on that! :popcorn:

Your sources list is fine. Medibuntu is a great repository, so no problems there. (I see you also have the latest version of miro).

Kernel package and CPU should should work together very well together.
And the firefox and amarok package numbers are fine too.

So, I'm left with thinking that you should remove your config folders and start both firefox and amarok fresh.

Close firefox and amarok.

Then open up nautilus in your home directory ("Places>Home Folder" in your Gnome menu), press "**Ctrl+H**" to show the hidden folders, then find and remove the folder named **.mozilla**

Then enter the directories **.kde/share/apps** and remove the folder named **amarok**.

Then restart the apps, and hopefully all should be restored.

Regards
Iain

---

### Post by Lord Xeb on 2008-06-05
This is one of the main reason I love Ubuntu *nix. Its fast, percise, and always to the point.

---

### Post by jemjulio on 2008-06-07
Hey!

First of all, I'm happy I havent done too bad with the migration :)

Mono was installed to get Thundercat to work. The idea was to sync the desktop (Ubuntu) and the laptop (XP). I have failed miserably though.....Cant get it to work.

Ok, I have deleted the amarok and firefox folders. Re-scanning now correct music folders on Amarok. 
Seems to be running ok ....:guitar:

Apart from the email sync issue, the only thing that I havent been able to get to work are the rear speakers. I have tried all sorts of solutions 
found in these forums, no joy.

As for the laptop ( Sony Vaio VGN-S5HP), when I find something to replace AnyDVD, I wouldnt mind getting rid of XP and installing Ubuntu as well.Using DVDshrink and K3B on the Ubuntu machine, which copies ok, but I assume that some protections will not be removed. For these I can use XP.

Thanks guys. Any assistance with the rear speakers will be appreciated.

Seeing how my partitions are set up, and if I do decide at some point to re-install, will my Data be safe, as its in the home folder? Upon installation, will it recognise this, or will I have to re-direct Home to the second drive again?

Thanks again "amigos"

Julio

---

### Post by snobby500 on 2008-06-07
You could try the duplicate sound option when you double click on speaker in top right.
You go to edit>preferences then tick duplicate front or something like that.
then yuou go to switches and enable it if it isnt already.

This isnt true surround sound but if you dont find anything else it may be better than nothing :)

Hopefully it works :)

---

### Post by jemjulio on 2008-06-07
Mmmmm....

I dont have the duplicate option....
Also unsure what device should I use.:
HDA Intel
Realtek ALC662
Alsa mixer
:(
I have Alsa, Pulse Audio.....

Duplicating is what I want. I have 2.1 in front and 2 decent studio monitors on rear, 

Help!!!!

Julio

---

