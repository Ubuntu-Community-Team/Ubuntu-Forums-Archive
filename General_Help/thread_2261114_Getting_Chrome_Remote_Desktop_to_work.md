---
title: "Getting Chrome Remote Desktop to work?"
date: 2015-01-16
forum: General Help
---

### Post by ncage on 2015-01-16
I'm having a heck of a time getting chrome remote desktop to work and hoping somewhere here can help me out. First of all when chrome remote desktop (CRD) is initially installed it doesn't work correctly when you log in all you will see is the wallpaper on your desktop. You can right click and see the menu bar and thats about it. Here is the fix i had to apply to get it working:
 [https://productforums.google.com/forum/#!topic/chrome/LJgIh-IJ9Lk](https://productforums.google.com/forum/#!topic/chrome/LJgIh-IJ9Lk)

look to the best answer. This does work but while editing the file in the post the CRD service will always (randomly i might add) not come up with you reboot your computer. Once it starts not starting automatically it wont' start from that time on. At first i thought maybe i had screwed up something while editing the file but fortunately i made a backup of the original file and tried to copy it back to see if it would fix it and it didn't. I've been through multiple iterations of purging the app and reinstalling it. I've also tried removing the service and adding it back:

sudo update-rc.d -f chrome-remote-desktop remove
sudo update-rc.d chrome-remote-desktop defaults

that didn't fix it either. If i run the service manually it works fine:

/etc/init.d/chrome-remote-desktop --start

when i check the service status after rebooting: 

service --status-all
i get a  '?'

be aware i'm very computer literate but not very linux competent at this point (which i'm working on). Any help would be appreciated.

I'm running 14.04

---

### Post by Penguin360 on 2015-01-16
I would like to know how you fix the issue too.

In the mean time, I am just curious, why do you want to connect to your Ubuntu via CRD, instead of other programs?

---

### Post by ncage on 2015-01-16
> **Penguin360 said:**
> I would like to know how you fix the issue too.

In the mean time, I am just curious, why do you want to connect to your Ubuntu via CRD, instead of other programs?

Are you having the issue too? Why do i want to use CRD:

1. Free
2. No ports to open in firewall
3. Client connectivity just requires google chrome (which is my preferred browser anyways)
4. Works on all clients (i have Windows, MAC, & Linux clients). I don't really have a need but "i think" it works on mobile too.
5. Connecting to multiple clients behind a single ip (behind firewall) is trivial.

If i can't get it working then i will probably go with teamviewer. While team viewer is supposed to be free for personal use i think i've had issues in the past when trying to install it on windows server (thinking i'm an enterprise) and i don't like the nags it gives you. I'm pretty sure i had CDR working on ubuntu in the past (its been awhile) but this time has been a nightmare.

---

### Post by Penguin360 on 2015-01-18
I tried CRD to connect to my Windows PC without any problems, I can even connect via my tablet. But I never tried to use it to connect to my Ubuntu.

According to the reasons you have, you can try X2Go ([http://wiki.x2go.org/doku.php](http://wiki.x2go.org/doku.php)) if you don't mind opening the SSH port 22.

1. Free
2. Clients need to install X2Go client, your Ubuntu box install X2Go server
3. Works on all clients (Windows, MAC, and any Linux distros)

I am using X2Go to connect to my Ubuntu box from Windows 8 pc, and everything works well.

---

