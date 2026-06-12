---
title: "stuck at root@ubuntu~# after install"
date: 2008-02-02
forum: General Help
---

### Post by sumsa on 2008-02-02
I am trying to install Xubuntu on an old machine with no internal cdrom drive which previously ran windows XP. 
I created a partition, moved the contents from the Xubuntu 7.10 alternative cd using a USB cd drive onto it and got it going.

Along the way the installer said something about going into low mem mode, but it completed the installation anyways reformatting the entire Hd drive.
 Then it rebooted, came up to grub.. Chose kernel mode.. and got stuck after:
* Running local boot scripts (/ect/rc.local)  [OK]


If I press enter i'll get prompted for a log in.. I log in using the username and passwd i chose. And am now in some kind of terminal.

I can also choose the debug option in grub and end up in the  root@ubuntu~#  terminal. 

I am able to get into the Cd rom drive from the terminal with cd /cdrom

My limbo is this.. Since this installation has clearly failed I want to try to reinstall.. but since I only have an USB Cdrom drive I can't simply boot with another distro's cd.. I somehow need to use the root@ubuntu~#  terminal to run a reinstallation since it is the only way to access the USB cd drive
Or maybe I could try to reconfigure grub to boot from the USB cdrom drive. 
Is this even possible or am i stuck in a catch 22 where the only sulution is to throw the darn desktop out the window=)

---

### Post by pointone on 2008-02-02
I'm guessing you simply didn't select the GUI for installation. Simple fix, run:

```
sudo apt-get install xubuntu-desktop
```

... from the terminal.

---

### Post by sumsa on 2008-02-02
Ok thanks.. I&#8217;m trying it.. Ok lots of chatter coming up on the screen&#8230; looks good&#8230;&#8230;

---

### Post by sumsa on 2008-02-02
I&#8217;m guessing you were right! 
Now everything works.. Thanks a million!
Now I can finally get to bed!

---

