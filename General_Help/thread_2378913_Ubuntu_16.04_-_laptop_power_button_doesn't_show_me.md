---
title: "Ubuntu 16.04 - laptop power button doesn't show menu"
date: 2017-11-29
forum: General Help
---

### Post by LifeEnemy on 2017-11-29
Hi all,

I just bought a new laptop (Acer Nitro 5) and installed Ubuntu 16.04 alongside the default Windows 10. I've been setting it up, but I notice that the settings for the power button don't seem to do anything anymore. On my last computer (running 14.04) hitting the power button brought up a convenient menu that had options to restart/shut down/etc. But now, nothing happens.

I don't have any relevant options in Power Settings, and I've tried setting it to "Interactive" using dconf-editor, but the setting doesn't seem to have any effect - the power button still does nothing.

Does anyone know how to make the shutdown menu show up when pressing the power button?

Thanks!

---

### Post by LifeEnemy on 2017-11-29
Bump

---

### Post by LifeEnemy on 2017-12-02
Shoot. I found that it worked on Windows 10 after holding the power button for a few seconds, but it doesn't seem to work on Ubuntu. Thought it might have been hardcoded.

---

### Post by LifeEnemy on 2017-12-07
Any suggestions? Pleeeeease. :)

---

### Post by DuckHook on 2017-12-07
I don't use the functionality you are asking for, so haven't the foggiest notion if this will work, but Googling turns up this: [https://www.hiroom2.com/2016/10/19/ubuntu-16-04-shutdown-with-pressing-power-button/](https://www.hiroom2.com/2016/10/19/ubuntu-16-04-shutdown-with-pressing-power-button/)

The instructions are unnecessarily convoluted. In particular, *sudo su* followed by *cat* is just silly. Just do *sudo nano* to get into a simple editor and you can create the needed file and populate it with the needed instructions.

You are on your own with these instructions. I have not tested them nor gone through them with anything more than a cursory glance. Proceed at your own risk, and make sure you have your data backed up.

---

