---
title: "Unpacking libc6:amd64 stuck forever!"
date: 2018-03-25
forum: General Help
---

### Post by jsfrost on 2018-03-25
Hi guys, anyone could help me with this issue? its been taking forever!

[IMG]https://ibb.co/iLDGjn[/IMG][IMG]https://ibb.co/iLDGjn[/IMG][IMG]https://ibb.co/iLDGjn[/IMG]I've attached an image.

Please help!

---

### Post by cruzer001 on 2018-03-25
Are you doing a version upgrade?  What command or update method did you use?  And whats your current status?

---

### Post by jsfrost on 2018-03-26
I wanted to install Bash on my Win10, so this is my first time installing Ubuntu. 
I am trying to use GCC compile but it told me I don't have GCC so it advice me to use apt-get install gcc, and so I did that and got to that stage of version upgrade.
My current status is still stuck at the upgrade.

---

### Post by cruzer001 on 2018-03-26
Did you do a update/upgrade after you installed Ubuntu?

Its been stuck a long time, go ahead and shut it down however you can.  Then bring it back up and:

```
sudo dpkg --configure -a && sudo apt -f install
```

If it complains about missing packages:

```
sudo apt update && sudo apt full-upgrade
```

Reboot and try the install again.

```
sudo apt install gcc
```

---

### Post by Yellow Pasque on 2018-03-26
Is this inside a WSL session?

---

