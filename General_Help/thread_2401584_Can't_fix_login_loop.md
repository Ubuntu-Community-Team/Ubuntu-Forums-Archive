---
title: "Can't fix login loop"
date: 2018-09-19
forum: General Help
---

### Post by michael1026 on 2018-09-19
I have the infamous login loop after my computer froze and I had to do REISUB to restart it. I have tried many things....

Checked the owner of .Xauthority and .ICEauthority. (chown just in case)
Renamed .Xauthority so a new one would be created.
Checked permissions for /tmp
Renamed .config so the config file is created again with defaults.
Tried uninstalling unneeded programs.
Tried doing dpkg reconfigure gdm3
Tried using lightdm instead.
Opened .xsession-errors, but no errors are shown, just information like `dbus-update-activation-environment: setting XAUTHORITY=/home/michael/.Xauthority`

I am able to create a second account and use that just fine. I'm also able to run startx to access the desktop (it's different though. I have to use activities in the top right to access the side bar and applications. No desktop icons).

---

### Post by Claus7 on 2018-09-20
Hello,

I have faced a login loop, yet it was not the same issue as yours. A simple suggestion would be to reinstall your desktop environment, since gnome purges desktop icons or try an alternative one. 

Just to verify: when issuing startx you do not do that as root, since this would be a reason for a login loop.

Also: when using lightdm, have you purged completely gdm3? If so, try using lightdm with its proposed greeter.

And finally: are you using cairo-dock? I have checked that it might conflict with your configuration, so it would be advised to remove it and check again.

Ah! And welcome to the forums,
Regards!

---

### Post by michael1026 on 2018-09-20
> **Claus7 said:**
> 
[COLOR=#000000] A simple suggestion would be to reinstall your desktop environment, since gnome purges desktop icons or try an alternative one. [/COLOR]

I wanted to try this, but I wasn't sure how to. If it's just apt-get install --reinstall ubuntu-desktop, that did not help.
> **Claus7 said:**
> 
Just to verify: when issuing startx you do not do that as root, since this would be a reason for a login loop.

I'm aware. I don't using startx as root as I know it'll change the owner of .Xsession.
> **Claus7 said:**
> 
Also: when using lightdm, have you purged completely gdm3? If so, try using lightdm with its proposed greeter.

I don't think I purged gdm3, but I'll have to try that.
> **Claus7 said:**
> 
And finally: are you using cairo-dock? I have checked that it might conflict with your configuration, so it would be advised to remove it and check again.

I am not.

Thank you for the help.

---

### Post by Claus7 on 2018-09-20
Hello,

> **michael1026 said:**
> I wanted to try this, but I wasn't sure how to.



this depends on the actual environment that you are using. In order to check that issue the command:
echo $DESKTOP_SESSION

then from the output you will get you can go to synaptic package manager and reinstall it.

Some easy additional thoughts. What is the output of the commands:
sudo apt update
sudo apt upgrade

Do you have any errors there? Maybe updating your system you might avoid the problems you are getting.

Regards!

---

### Post by michael1026 on 2018-09-20
> **Claus7 said:**
> 
this depends on the actual environment that you are using. In order to check that issue the command:
echo $DESKTOP_SESSION

Ubuntu-Wayland. So I reinstalled xwayland using Synaptic (hopefully that's the correct package).
> **Claus7 said:**
> 
Some easy additional thoughts. What is the output of the commands:
sudo apt update
sudo apt upgrade

Applied needed updates. No errors.

Restarted computer, still same issue unfortunately.

---

### Post by Claus7 on 2018-09-20
Hello,

try and purge wayland. 18.04 is supposed to come with Xorg as default. I suppose in your system, under the login screen, you have the option of ubuntu xorg instead of just ubuntu wayland. Choose that instead.

Question: when you connect with another user, do you choose wayland as well?

If affirmative, another option would be to reset your user configurations completely, yet this means that you will lose all your configurations. 
You can try to backup first your current configuration and then re-load it. 

You could try this:
[https://ubuntuforums.org/showthread.php?t=2400810&page=2&p=13801066#post13801066](https://ubuntuforums.org/showthread.php?t=2400810&page=2&p=13801066#post13801066)

Regards!

---

### Post by michael1026 on 2018-09-20
> **Claus7 said:**
> 
try and purge wayland. 18.04 is supposed to come with Xorg as default. I suppose in your system, under the login screen, you have the option of ubuntu xorg instead of just ubuntu wayland. Choose that instead.

I've tried both Xorg and Wayland, which is how I ended up using Wayland. Neither work.
> **Claus7 said:**
> 
Question: when you connect with another user, do you choose wayland as well?

I'm able to login with another user using both options.
> **Claus7 said:**
> 
If affirmative, another option would be to reset your user configurations completely, yet this means that you will lose all your configurations. 
You can try to backup first your current configuration and then re-load it. 

You could try this:
[https://ubuntuforums.org/showthread.php?t=2400810&page=2&p=13801066#post13801066](https://ubuntuforums.org/showthread.php?t=2400810&page=2&p=13801066#post13801066)

I tried renaming the .config folder yesterday to see if that helped, but it didn't. I also tried your solution from that post without restoring the configuration, then again, after restoring it, but nothing.

---

### Post by Claus7 on 2018-09-21
Hello,

could you follow this link as well, in combination to the above? 
[https://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults](https://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults)

From what you mention, system wide, things are working. So the problem lies to your user configurations. Mind to backup first your files and folders and remove files both for gnome2 and gnome3.

Regards!

---

### Post by HermanAB on 2018-09-21
Hmm, not what you would want hear but, I would do 'apt install xfce4' and abandon Gnome.  It will feel like you just bought a brand new, much faster machine.

---

### Post by michael1026 on 2018-09-21
> **Claus7 said:**
> Hello,

could you follow this link as well, in combination to the above? 
[https://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults](https://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults)

From what you mention, system wide, things are working. So the problem lies to your user configurations. Mind to backup first your files and folders and remove files both for gnome2 and gnome3.

Regards!
I'll try this out. Two questions.

Do I only need to backup the files listed in that answer?

What is saved inside Gnome's configuration files? I don't think I customized Ubuntu too much. If it's just my preferences, sidebar, and things like that, I probably don't need to worry about backing those up.

---

### Post by Claus7 on 2018-09-21
Hello,

> **michael1026 said:**
> 
Do I only need to backup the files listed in that answer?
yes

> **michael1026 said:**
> 
What is saved inside Gnome's configuration files? I don't think I customized Ubuntu too much. If it's just my preferences, sidebar, and things like that, I probably don't need to worry about backing those up.
then you won't have much trouble missing them. 

Regards!

---

### Post by michael1026 on 2018-09-21
> **Claus7 said:**
> Hello,


yes


then you won't have much trouble missing them. 

Regards!
Sigh, still have the same problem after deleting all config files for Gnome2 and Gnome3. I have no idea what could be the problem at this point.

---

### Post by Claus7 on 2018-09-21
Hello,

another thing you could try is to remove completely your home directory under safe mode, yet I have not tested this one and I do not know how your system will behave afterwards:
[https://askubuntu.com/questions/92521/deleted-home-directory-please-help](https://askubuntu.com/questions/92521/deleted-home-directory-please-help)

You could back up your home directory first, yet if sth goes wrong, I do not know what will happen moving it back the way it was. 

Before this: have you checked to change your theme and/or shell? 

An easy thing for you to try would be: enter your session by using startx as you mention in your first post. Then, by having installed gnome-tweaks, change the theme or shell and reboot. Can you see your configurations as normal? 

Regards!

---

