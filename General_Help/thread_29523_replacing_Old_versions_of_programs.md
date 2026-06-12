---
title: "replacing Old versions of programs"
date: 2005-04-24
forum: General Help
---

### Post by dueY on 2005-04-24
This is more of an annoyance than a major problem for me.  As new versions of programs come out I like to download and use them, but the old versions are still on my computer.  

For example, Ubuntu came with gaim vers 1.4.0 and now there is 1.2.1.  So, I download the new version and put it in home/packages.  The annoyance is that I still have the 1.4.0 in /usr/bin and when I use the Gnome Applications > Run Application... it runs the 1.4.0 version.   

I tried fixing this by typing sudo -s and sudo -i (not sure the difference) to try to get to root to be able to drag the files from my /home/packages/gaim folder to the /usr/bin folder.  But i still get the Error While Moving - You do not have permissions to write to this folder  [-X  error.

So basically I'd like to get rid of the old versions of programs such as gaim and firefox and replace the new ones to make sure the newest version always runs and to clear up a little disk space as well.  Thanks for any advice

---

### Post by Xerampelinae on 2005-04-24
I think the original gaim is installed via apt-get (or synaptic), while your are installing them using autopackage.

If this is true, you can remove the apt-get installed gaim by doing:
```
sudo apt-get remove gaim
```

An alternate is to remove it from the autopackage program, and install/upgrade gaim via apt-get or synaptic.  (This is what I do)
```
(first remove gaim using autopackage)
sudo apt-get install gaim
```

---

### Post by dueY on 2005-04-24
Thanks, but is there any way to just click and drag the files without getting the permissions error? ](*,)

---

### Post by Xerampelinae on 2005-04-24
[QUOTE=dueY]Thanks, but is there any way to just click and drag the files without getting the permissions error? ](*,)[/QUOTE]

This will give you nautilus running as root, so you can do whatever.  You'll probably bork your system if you delete stuff like this though.  I still recommend using "apt-get remove gaim" instead of just deleting gaim from /usr/bin.

```
sudo nautilus
```

---

### Post by dueY on 2005-04-24
Ok one (hopefully) more question, if I do the sudo apt-get remove, will it lose my configurations for programs such as gaim/firefox?

---

### Post by Xerampelinae on 2005-04-24
They are stored in your home directory.

~/.gaim
~/.mozilla/firefox

So you will keep your configurations even if the program is removed.

---

### Post by dueY on 2005-04-25
One more  :^o 

I spawned two consoles and sudo nautilus in both of them.  Then I tried dragging a movie from my /home to my /media/usbdisk.  I get an error for not having permission on this.  Any ideas?

---

### Post by Xerampelinae on 2005-04-25
Is the filesystem on the usb drive NTFS?  If so, it could be that you are only able to read the contents from it.

```

mount

```

Otherwise, which filesystem is it using?

I have a little usb memory stick using EXT 3 and it works well.

---

