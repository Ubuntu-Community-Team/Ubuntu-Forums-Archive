---
title: "Revert to original 24.04 login screen"
date: 2024-08-22
forum: General Help
---

### Post by von Stalhein on 2024-08-22
I loaded KDE to see if I liked it on Ubuntu 24.04 

I wasn't too fussed so have tried to revert.

I think I've largely done that, but I can't change this login screen (below). I've deleted and purged any KDE or XFCE files I can find via cli but this one has eluded me.

It did start up with a virtual keyboard but I fluked getting rid of that.

Any tips? Thanks!
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294110&stc=1[/IMG]

---

### Post by tea for one on 2024-08-22
KDE may well have included another Display Manager
Gnome > gdm3
KDE > sddm

Let's check by opening a terminal:-
```
apt policy sddm
```

---

### Post by von Stalhein on 2024-08-22
Thanks for the reply - result from that query is:

```
sddm:
  Installed: 0.20.0-2ubuntu4.2
  Candidate: 0.20.0-2ubuntu4.2
  Version table:
 *** 0.20.0-2ubuntu4.2 500
        500 http://au.archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.20.0-2ubuntu4 500
        500 http://au.archive.ubuntu.com/ubuntu noble/universe amd64 Packages


```

So I should?
```
sudo apt remove sddm
```

---

### Post by tea for one on 2024-08-22
It's been ages since I mucked around with Display Managers but I'm pretty sure that it would be better to reconfigure gdm3 first.
```
sudo dpkg-reconfigure gdm3
```
Then, reboot to see if gdm3 has priority

---

### Post by von Stalhein on 2024-08-22
Rightyho, I'll give that a bash (!) and report back....

---

### Post by tea for one on 2024-08-22
> **von Stalhein said:**
> I'll give that a bash (!) 
Arf arf - very good
Better than json bourne again shell?

---

### Post by von Stalhein on 2024-08-22
> **tea for one said:**
> Arf arf - very good
Better than json bourne again shell?

Touche!

Well that was exciting. I had to drop to root prompt in recovery mode to get in the system. 

I have a relatively traditional login screen back. At least it has the requisite login boxes available.

I used to have a lovely pic of  F/A-18 A21-39 similar to my GRUB screen, but it was so zoomed in there were no boxes for user/pword.

I tried to resize it using info from [here]("https://www.themtparty.com/fix-ubuntu-gnome-login-screen-scaling/") but if I tried a value lower than 0 it spat the dummy.

I still have some gremlins - "Settings" has no dialogue to change icon sizes in the dock for instance. I'm using GDM Settings to handle that. It seems stable so maybe I'll cut the "learning experiences" out for a while.

Thanks for your help!!

---

### Post by tea for one on 2024-08-22
To add a picture to the gdm3 log-in screen, I used the Test Case instructions/terminal commands to install systemd-container
[https://github.com/PRATAP-KUMAR/ubuntu-gdm-set-background?tab=readme-ov-file](https://github.com/PRATAP-KUMAR/ubuntu-gdm-set-background?tab=readme-ov-file)

---

### Post by von Stalhein on 2024-08-22
> **tea for one said:**
> To add a picture to the gdm3 log-in screen, I used the Test Case instructions/terminal commands to install systemd-container
[https://github.com/PRATAP-KUMAR/ubuntu-gdm-set-background?tab=readme-ov-file](https://github.com/PRATAP-KUMAR/ubuntu-gdm-set-background?tab=readme-ov-file)

Thanks, I had used that but not with the systemd procedure so will give it a try.

---

