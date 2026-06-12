---
title: "[SOLVED] from xubuntu to ubuntu"
date: 2007-02-14
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2007-02-14
I have a friend who is running xubuntu-edgy and he wants to have ubuntu.  I told him to install ubuntu-desktop. He said it wanted to download about 200 packages. I told him go ahead. When that is done, remove xubuntu-desktop. Did I give the correct info for him to do the switch? Any thing else that should be done? Thanks, Sally

---

### Post by llamakc on 2007-02-14
> **MustangSallydd said:**
> I have a friend who is running xubuntu-edgy and he wants to have ubuntu.  I told him to install ubuntu-desktop. He said it wanted to download about 200 packages. I told him go ahead. When that is done, remove xubuntu-desktop. Did I give the correct info for him to do the switch? Any thing else that should be done? Thanks, Sally

That'll do it.

---

### Post by IusedTObeSOMEONEelse on 2007-02-14
> **llamakc said:**
> That'll do it.

Thank you!!  Sally :)

---

### Post by taurus on 2007-02-14
And here is how you would remove Xubuntu.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by IusedTObeSOMEONEelse on 2007-02-14
ok, synaptic is done. I wanted to restart computer but when I click Applications>Quit the window with restart/shutdown options does not come up. How can I shut down from terminal (sudo magic?) silly me :confused:

---

### Post by llamakc on 2007-02-14
sudo shutdown -h now

---

### Post by IusedTObeSOMEONEelse on 2007-02-14
oOPs, it's borked. blue screen of death. Able to get ubuntu login screen and when I login I get colored lines all over screen. So I restarted again and when login screen came I selected Options>Failsafe Terminal, and that is where I am at. I'm using another machine to communicate the forum. Is there some kind of sudo magic for the failsafe terminal I can use? I suspect the X is broken:(  Thanks for any help given

---

### Post by drivel on 2007-02-14
sudo apt-get install ubuntu-desktop
sudo apt-get remove xubuntu-desktop

---

### Post by taurus on 2007-02-14
```
sudo dpkg-reconfigure xserver-xorg
```

---

