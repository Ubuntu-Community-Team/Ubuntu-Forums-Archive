---
title: "Ubuntu Software Center Stuck in the Middle of Installation"
date: 2017-06-12
forum: General Help
---

### Post by decapo on 2017-06-12
I tried to install team viewer today and the Ubuntu software center seems to be stuck in the middle of the installation. It's been like this for a few hours. Is there a safe way to cancel the installation or kill the installation process?

---

### Post by howefield on 2017-06-13
If it has been several hours I'd suggest it is ok to kill the installation process and see if it has been installed, if not purge anything that has been installed and install fresh with the terminal.

```
wget https://download.teamviewer.com/download/teamviewer_i386.deb -P ~/Downloads
```

to download the package and place it into your ~/Downloads folder. Then to install it use..

```
sudo apt install ~/Downloads/teamviewer_i386.deb
```

---

### Post by Autodave on 2017-06-13
I have Teamviewer installed on quite a few machines. I use *GDebi *to install. I have never had a problem with that.

---

### Post by howefield on 2017-06-13
> **Autodave said:**
> I have Teamviewer installed on quite a few machines. I use *GDebi *to install. I have never had a problem with that.

Yes, rereading the post again I should clarify that apt install will only with 16.04 and later, earlier versions gdebi would be a good choice.

---

### Post by decapo on 2017-06-13
@howefield ok something weird happened.  

I did not kill the process, I rebooted the computer hoping this would be a safer way to stop it.  When my machine came back up, I checked if teamviewer was installed using the dash search and it did not show up in the search.  I then retried the installation through the software center and it got stuck again.  I killed the process which was named "gnome-software" and then attempted the installation using apt.  When I tried apt I got a message back saying that teamviewer was installed and up to date.   I checked dash again and there it was.  I did not check if team viewer was installed after I killed the process; it must have installed on that attempt.  I'm probably just going to use apt from now on.  Thanks for your help.

---

### Post by howefield on 2017-06-14
Cool, the main thing is that you have your software installed, feel free to mark your thread as solved :)

---

