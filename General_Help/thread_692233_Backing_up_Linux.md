---
title: "Backing up Linux"
date: 2008-02-09
forum: General Help
---

### Post by The-Russ on 2008-02-09
Hello everyone,

I am currently dual-booting with Windows XP and Ubuntu on a single 60GB hard drive. I just received a 500GB hard drive that I wish to use as a secondary drive, and I wish to transfer my Linux partition to the new hard drive, delete it from the old one, and still have the ability to dual-boot as I currently do with a mostly seemless transition, if possible. My goal is to have my 60GB dedicated to Windows XP, and my 500GB dedicated to Linux.

I have already formatted the 500GB HDA to ext3 and it is set up as the slave drive on my computer. If anybody has any advice on how I can do this in a relatively easy manner, I would appreciate your help. Thank you.

---

### Post by bwhite82 on 2008-02-09
I would recommend creating a harddisk image and simply transferring it to your new drive, check out:

[http://www.osalt.com/ghost](http://www.osalt.com/ghost)

As far as dual-booting it still, you will need to change your '/boot/grub/menu.lst' to reflect your new drive. After all of that, you still may have some issues, as some of your apps may have configuration files for your old drive. A better option would be to backup your FF bookmarks, the contents of your home folder, and compile a list of your installed apps and simply do a clean install on the new drive.

---

### Post by The-Russ on 2008-02-11
Thank you. I'll go ahead with the transfer tomorrow and let you know how it works out.

---

### Post by The-Russ on 2008-02-13
Well I have completed my reinstallation and it's working great. However, I'm having some sort of a graphic problem, which I'm not sure of the cause. I took a screenshot, which is located at:

[http://geocities.com/yonhmen/pics/lines.png](http://geocities.com/yonhmen/pics/lines.png)

It just seems to be a that every now and then, some random lines appear all over the place (there were more before I took the screenshot). It also sometimes appears that parts of the screen are highlighted as if I had selected a file, only the color inversion will just take up a small block of the scene. This started to happen shortly before I decided to move Linux over to my new HDA, and was after I switched my resolution to 1400 x 1050 (the native resolution of my monitor).

So it seems to me like it's a driver problem, although I'm not positive, since with the new installation, I haven't had to mess anything up in order for it to present the option of using 1400 x 1050, that was selected automatically.

I did a clean installation, by the way, so none of the settings were carried over from my previous installation. Thanks again for all your help.

---

### Post by The-Russ on 2008-02-13
Nevermind that last questions. I seemed to have fixed it, at least for now. I just used the

sudo dpkg-reconfigure xserver-xorg

command in the terminal and went through that whole process and everything seems to be great now.

---

