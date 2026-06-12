---
title: "Virtual box"
date: 2012-11-27
forum: General Help
---

### Post by keter682 on 2012-11-27
I can't use virtual box. 
[IMG]https://ubuntuone.com/2TBiCFc8A7YHnQVW5xBXuR[/IMG]  [IMG]https://ubuntuone.com/4sZlHA9OkIYT5cluJvKP36[/IMG]

File vboxdrv don't exist.
DKMS installed/
OS Ubuntu 12.10 64-bit.

---

### Post by howefield on 2012-11-27
I think it is the headers that you need to install to match your installed kernel.

Install them then run the command in the error.

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by keter682 on 2012-11-27
> **howefield said:**
> I think it is the headers that you need to install to match your installed kernel.

Install them then run the command in the error.

```
sudo /etc/init.d/vboxdrv setup
```

 /etc/init.d/vboxdrv   don't exist

---

### Post by efflandt on 2012-11-27
How did you install virtualbox?  Did you download the deb file from [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) or follow instructions farther down the page for "**Debian-based Linux distributions**"?

I did the latter (adding the repository and using sudo apt-get), and the only thing I had to do after installing it was add myself to the **vboxusers** group (although, I am running 64-bit 12.04).  I also added the "Extension Pack" from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

**VboxGuestAdditions.iso** ends up in /usr/share/virtualbox which you can mount on the virtual CD of a guest operating system.  Although, in certain Linux distributions you might need to uninstall their older default guest additions before installing this matching version.

---

### Post by keter682 on 2012-11-29
> **efflandt said:**
> How did you install virtualbox?  Did you download the deb file from [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) or follow instructions farther down the page for "**Debian-based Linux distributions**"?

I did the latter (adding the repository and using sudo apt-get), and the only thing I had to do after installing it was add myself to the **vboxusers** group (although, I am running 64-bit 12.04).  I also added the "Extension Pack" from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

**VboxGuestAdditions.iso** ends up in /usr/share/virtualbox which you can mount on the virtual CD of a guest operating system.  Although, in certain Linux distributions you might need to uninstall their older default guest additions before installing this matching version.

Thank you. I soloved my problem.

---

