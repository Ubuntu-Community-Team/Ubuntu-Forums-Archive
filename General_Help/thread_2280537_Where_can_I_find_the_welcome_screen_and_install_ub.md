---
title: "Where can I find the welcome screen and install ubuntu screen?"
date: 2015-05-31
forum: General Help
---

### Post by andreadixon825 on 2015-05-31
Hi, I'm looking for the install screen when you first install Ubuntu and the welcome screen, where it says Try Ubuntu or Install Ubuntu where can I find this at, I use to know where it was but my documents are lost that I have made. :) Thank You

---

### Post by Elfy on 2015-05-31
Your request for help doesn't make a lot of sense to be honest.

Boot the install medium and you'll find it. 

If it's an example of it -  search for the image.

---

### Post by RobGoss on 2015-05-31
You will see it if you place the install DVD or USB, in your machine until then I don't think you'll see it.

---

### Post by andreadixon825 on 2015-05-31
Hi, I know how to get to I'm just saying, that I have made my own live cd but it still asked to be installed and I just wanted to change that screen and get rid of the install menu, I use to know but I just had a computer crash do to cpu fan, but got another computer and I had a lot of documents that I had but there lost now, I guess I have put this in the wrong post, sorry if I did, I'm just trying to find that part. Thanks :)

---

### Post by Elfy on 2015-05-31
> **andreadixon825 said:**
> Hi, I know how to get to I'm just saying, that I have made my own live cd but it still asked to be installed and I just wanted to change that screen and get rid of the install menu, I use to know but I just had a computer crash do to cpu fan, but got another computer and I had a lot of documents that I had but there lost now, I guess I have put this in the wrong post, sorry if I did, I'm just trying to find that part. Thanks :)

Ok - that makes a bit more sense now :)

No real idea, but something ubiquityish I would guess ... 

If you're doing this for yourself - surely it'd better to use the debian start menu that hides behind the keyboard/human icons

---

### Post by deadflowr on 2015-05-31
The boot menu is a grub boot menu.
You can looky it over in the iso by opening it in archive manager then look in the folder boot and the grub configuration file grub.cfg.
I think since this file is static it is built without the grub-updater functions, so it doesn't rely on the various scripts that grub usually does; ie the /etc/default/grub file or the scripts within /etc/grub.d.
My thought on it at least...

---

### Post by andreadixon825 on 2015-05-31
Hi, this is what I want to change.
[IMG]http://i57.tinypic.com/no6h7c.png[/IMG]

---

### Post by yancek on 2015-05-31
An explanation is at the thread below which is simply removing the ubiquity installer.  Of course, there will then be no installer and no option to install as pointed out in the thread.

[http://ubuntuforums.org/showthread.php?t=1598143](http://ubuntuforums.org/showthread.php?t=1598143)

---

