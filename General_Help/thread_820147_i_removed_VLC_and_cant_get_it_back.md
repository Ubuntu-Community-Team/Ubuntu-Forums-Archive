---
title: "i removed VLC and cant get it back?"
date: 2008-06-06
forum: General Help
---

### Post by leah1984 on 2008-06-06
so i removed VlC media player to try some other media players, and now i cant get it back.when i try to add it via the add/remove it gives me a message saying this:
VLC media player cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
 what does this mean?
and when i try to add it via synaptics i get this :
vlc:

Package vlc has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

the following packages have unresolvable dependancies .make sure that all required repositories are added and  enabled in the preferances.

how can i get VLC back?:KS

---

### Post by PmDematagoda on 2008-06-06
Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by heatblazer on 2008-06-06
I may sounds bad, but what can VLC do that TOTEM can`t???

---

### Post by leah1984 on 2008-06-07
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe



## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse

#AUTOMATIX REPOS START

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports restricted main universe
owner@ubuntu1:~$ 

this is what i got

---

### Post by leah1984 on 2008-06-07
well i like to have 2 and im used to using VLC also half the time one of them will not go to full screen when the other one will and i havent figured that problem out yet?

---

### Post by doorknob60 on 2008-06-07
Change this line: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted multiverse
to this: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse

Then run this:
```
sudo apt-get update && sudo apt-get install vlc
```

Don't forget [img]http://ubuntuforums.org/images/buttons/post_thanks.gif[/img]

---

### Post by leah1984 on 2008-06-09
how do i change that line? i try to type on the terminal and it wont let me?

---

### Post by Bubba64 on 2008-06-09
> **leah1984 said:**
> how do i change that line? i try to type on the terminal and it wont let me?

Copy and paste it.

---

### Post by ryanhaigh on 2008-06-09
Press alt-f2 to bring up the run dialog and then enter 

```
gksudo gedit /etc/apt/sources.list
```

Enter your password when promted, edit and save the file.

Open synaptic and refresh your package list then try reinstalling vlc.

---

### Post by leah1984 on 2008-06-09
thanks i managed to get it all changed:) and ive got VLC back

---

### Post by leah1984 on 2008-06-09
funny thing though whenever i try to put it into full screen ,vlc closes up on me?

---

