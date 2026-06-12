---
title: "Enabling Multimedia In Kubuntu"
date: 2007-11-21
forum: General Help
---

### Post by highboy on 2007-11-21
The command line > $gksudo gedit /etc/apt/sources.list will not work for me in my terminal for Kubuntu. Is the command line different?

---

### Post by taurus on 2007-11-21
```
kdesu kwrite /etc/apt/sources.list
```

---

### Post by highboy on 2007-11-21
Thanks, but the response I got was > X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


---

### Post by taurus on 2007-11-21
Then just try a text editor.

```
sudo nano -Bw /etc/apt/sources.list
```
Save it with <Ctrl>o and exit with <Ctrl>x.

---

### Post by highboy on 2007-11-21
I got this and it won't let me do anything it just sits there: > # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

                               [ Read 43 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell 

---

### Post by highboy on 2007-11-21
I'm not understanding why nothing is working. I can't enable any multimedia whatsoever.

---

### Post by taurus on 2007-11-21
What do you mean it just sits there?  Use the arrow keys to navigate around!

---

### Post by highboy on 2007-11-21
I added these repositories to the list > ## Medibuntu - Ubuntu 7.04 "feisty fawn"
 ## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
 deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
 deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free and like I said, it just sits there. Also, I'm now encountering a problem where I can't even install anything from my Adept Installer. I keep getting this error T> here was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.  when trying to install anything. The Macromedia Flashplugin is checked as installed but isn't working, and the gstreamer programs are all greyed out.

---

### Post by taurus on 2007-11-21
After you add those lines, you need to save and edit nano.  Save it by <Ctrl>o and exit with <Ctrl>x.  Then, you need to install the key for that new repo.

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by highboy on 2007-11-21
Nothing is happening. I typed <Ctrl>o<Ctrl>x after those lines and its sitting there. Perhaps I'm misunderstanding you.

---

### Post by taurus on 2007-11-21
Did you actually type in <Ctrl>o or did you hold down the <Ctrl> key while pressing letter o?

---

### Post by highboy on 2007-11-21
I'm holding down CTRL while pressing o and it says>  File Name To Write [Backup]: etc/apt/sources.list When I try to CTRL x to exit it just beeps at me.

---

