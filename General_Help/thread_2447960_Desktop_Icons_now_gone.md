---
title: "Desktop Icons now gone"
date: 2020-07-29
forum: General Help
---

### Post by claven123 on 2020-07-29
I have Ubuntu 20.04LTS installed on my laptop.  I upgraded quite a while ago when it came out.  Has been running fine since.  Then I installed rclone to sync my onedrive with my laptop.  Set up to mount onedrive on start up and restarted my computer. 
When it restarted I do not have desktop icons.  I've restarted a couple of times and did apt install dist-upgrade  which did fix a few things.  No change in icons.  I did right click on the desktop as I saw some people lose this ability, I had it so I added a new folder, which worked and after that the icons were back, until I restarted then they are now gone.   (I deleted the startup mount for onedrive).

I've searched and come up with alot of references to bugs AFTER upgrading to 20.04, which is not my situation. 

Dennis

---

### Post by ajgreeny on 2020-07-29
This is a subject that has been discussed a great deal over the past few months, or maybe years, though I don't use Ubuntu so I'm not sure when this problem first appeared.
It is, however, a symptom of the way in which the gnome developers are moving the whole system and their views on the way the system should be used and how it should look.

See [https://ubuntuforums.org/showthread.php?t=2446948&highlight=desktop+icons](https://ubuntuforums.org/showthread.php?t=2446948&highlight=desktop+icons) for one of the most recent discussions with a few solutions and ways to get back icons on the desktop, along with some other desktop items.

Alternatively you could simply use another flavour of the Ubuntu family, eg Kubuntu, Xubuntu, Ubuntu-Mate, all of which are a great deal more easily configured to look exactly how you want.  As you can see from my signature below, I am using Xubuntu with the Xfce4 DE, a more traditional desktop layout, and also less resource hungry than Ubuntu.

---

### Post by claven123 on 2020-07-30
So, technically nothing is amis with my current system.  I was thinking something was 'broken' and needed repair.  I did see the chatter about ubuntu not having icons in 20.04 on install/upgrades, but since I had then after the upgrade I thought I was in a different situation.  I read that post you cited already.  

I've often thought about changing flavors of linux, just never get around to it.  Maybe its time.

Thanks,

Dennis

---

### Post by claven123 on 2020-07-31
Actually, why do I get icons back AFTER I add a folder to the desktop.  If there was a change in ubuntu, that is a planned change in programming,   Would I not lose them for good, all the time?  Even when I add a folder to the desktop?

Just wondering.

D

---

### Post by deadflowr on 2020-07-31
Desktop icons are now a function of a gnome shell extension.
Installed and always on by default.

It's significantly crippled in comparison to the older method,
which used a function the nautilus file manager to handle the desktop.
(the older function has been removed from nautilus,
so the developers felt the best option was a shell extension)
> Actually, why do I get icons back AFTER I add a folder to the desktop. 
You mean that previously placed icons start showing again when a new folder is placed on the desktop?
I have no idea why it does that.
> I've often thought about changing flavors of linux, just never get around to it. Maybe its time.


I think almost every other flavor does what you want, normally and perfectly fine.
And since most use a more traditional desktop layout the learning curve is actually small.
Of the flavors I'd probably recommend I'd suggest either Ubuntu Mate or Kubuntu.
Mate is basically the old desktop (before unity and gnome shell) reborn.
And Kubuntu is it's own world mostly unfettered by gnome's insanity.

---

### Post by kurt18947 on 2020-08-01
enter this line in a terminal
```
gsettings set org.gnome.shell disable-user-extensions false
```

I've had extensions 'turn off' for no apparent reason. The reason behind the change to desktop icons as i recall is that the ability of Nautilus to handle desktop icons was due to a programming oops. The poobahs at Gnome felt that Desktops should be pristine not cluttered with icons. Someone or something changed their minds so an extension was developed to accommodate desktop icons without requiring a potentially exploitable programming oops. At least that's how I understand it.

There is one downside for me to using an alternative 'flavor' of Ubuntu. 'Mainline' Ubuntu is supported for 5 years. 'Flavors' (Xubuntu, Mate etc.) are supported for 3 years. 5 years support covers 2 LTS releases - LTS release every 2 years, 3 years support does not.

---

### Post by ActionParsnip on 2020-08-01
Could install the xfce4 package then log in to the new XFCE session. It'll still be Ubuntu but with XFCE instead.

---

### Post by claven123 on 2020-08-01
Yes, when I add a new folder all the icons that were there before show back up (until I restart).  Ie trash and all the others.   

I have Mate installed on another laptop, but only use it for backups.  So, don't fiddle with it much. 


D

---

### Post by claven123 on 2020-08-01
I ran that command "gsettings....." it did not change the behavior.  

D

---

### Post by claven123 on 2020-08-01
How do I install Mate over my ubuntu install?  I have dual boot with Win 10.  Or, point me in the direction on where to find this.  Tweaks does not work for enabling extension (the add icon to desktop).

Thanks,

d

---

### Post by deadflowr on 2020-08-01
> How do I install Mate over my ubuntu install? 
Well you can go dirty and install the desktop on to the existing install:
```
sudo apt install ubuntu-mate-desktop
```
This will give the mate desktop as an option to log into from the login screen.
It's dirty because it means you will still have the normal Ubuntu installed so various programs may show more than one,
like having multiple text editors or file managers. So having different desktops installed can cause confusion sometimes.

or you could go clean and reinstall it over the existing install 
see: [https://askubuntu.com/questions/1042746/reinstalling-ubuntu-with-a-dual-boot]("https://askubuntu.com/questions/1042746/reinstalling-ubuntu-with-a-dual-boot")

---

### Post by monkeybrain20122 on 2020-08-02
> **claven123 said:**
> How do I install Mate over my ubuntu install?  I have dual boot with Win 10.  Or, point me in the direction on where to find this.  Tweaks does not work for enabling extension (the add icon to desktop).

Thanks,

d

A less drastic way would be to simply use a different file manager to run the desktop, for example nemo, see this [post]("https://ubuntuforums.org/showthread.php?t=2446948&p=13971682#post13971682").

---

