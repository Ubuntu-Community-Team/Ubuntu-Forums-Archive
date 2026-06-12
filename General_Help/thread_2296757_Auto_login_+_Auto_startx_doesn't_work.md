---
title: "Auto login + Auto startx doesn't work"
date: 2015-09-28
forum: General Help
---

### Post by leninberg on 2015-09-28
Hello all

I am trying to autologin and auto startx on my ubuntu minimal installation
(Vivid 32bits; mini.iso)
I am following several guides that I found but none of them work (the startx part works, but not the autologin)

[https://rowen121.wordpress.com/2011/09/14/enable-automatic-login-and-startx-in-ubuntu/](https://rowen121.wordpress.com/2011/09/14/enable-automatic-login-and-startx-in-ubuntu/)
[https://wiki.ubuntuusers.de/autologin](https://wiki.ubuntuusers.de/autologin)
[http://www.shellperson.net/autostart-x-without-gdm/](http://www.shellperson.net/autostart-x-without-gdm/)
[http://www.debianadmin.com/how-to-auto-login-and-startx-without-a-display-manager-in-debian.html](http://www.debianadmin.com/how-to-auto-login-and-startx-without-a-display-manager-in-debian.html)

The problem is everytime I go and look for the file they tell me to edit, it's not there.
When I do sudo nano whatever the file, it is empty (tty1.conf for example, or inittab)
In all the guides they say to uncomment a line and add another, but all those files are empty for me.
Maybe it is because they refer to Debian and things change.

I have managed to make it work installing nodm.
I would like to get it working with rungetty/mingetty/getty as they do.
Or another solution if you know the steps that have worked for you, but without the need of installing a display manager.
Thanks in advance

EDIT: nothing is encrypted

---

### Post by Bucky Ball on 2015-09-28
If you type in say,

```
sudo nano /home/biscuits
```

... and /biscuits doesn't exist, well, it does now! It opens an empty file for you to add your script to named /biscuits. That is what is happening here I suspect. The files are empty because they don't exist until you type your command. You are creating new ones. But don't worry. If you don't add anything and don't save them, they disappear.

As you have a mini install the files they are referring are probably not there, no.

Do you have a desktop environment installed on this? When you 'startx', where is that taking you? A CLI login? A dm login screen? As a minimal install is very much a custom install if you don't use a profile from tasksel during install (did you?) it is a little hard to help as what you have installed is an unknown.

As previously mentioned in another thread I think, be careful about punching a heap of commands and changes you're not sure about into files that haven't been backed up before you start editing them, for obvious reasons. :)

Let's stick with /home/biscuits. To back it up:

```
sudo cp /home/biscuits /home/biscuits.backup
```

... will copy the file /biscuits.backup to /home. 

```
sudo mv /home/biscuits.backup /home/biscuits
```

... will move it back to the correct place if you mess up the original. You could also replace 'mv' with 'cp' to copy if you want to keep a backup copy of the original on hand.

---

### Post by v3.xx on 2015-09-28
Hey Bucky :)

I use to run auto-startx with upstart by creating a ~/.xinitrc.  Seem that it has changed up somwhat since.  Not that long ago upstart was replace with systemd.

[https://wiki.archlinux.org/index.php/Systemd/User#Automatic_login_into_Xorg_without_display_manager](https://wiki.archlinux.org/index.php/Systemd/User#Automatic_login_into_Xorg_without_display_manager)

I have not researched this further, but I'm thinking that could be a problem with your older links. 

Anyhow, just a thought.

---

### Post by leninberg on 2015-09-28
> **Bucky Ball said:**
> If you type in say,
```
sudo nano /home/biscuits
```


Yes, I understand that I am creating them when I do that.
Thank you for the advice about backup, I will do that too.

After startx, it takes me to i3-wm, no desktop environment, and I didn't install a display manager (well yes, nodm, but after trying the other methods unsucessfully)
I didn't install a profile from tasksel (I don't know what that is in the first place hehe)
> **v3.xx said:**
> 
I use to run auto-startx with upstart by creating a ~/.xinitrc. Seem that it has changed up somwhat since. Not that long ago upstart was replace with systemd.
[URL="https://wiki.archlinux.org/index.php/Systemd/User#Automatic_login_into_Xorg_without_display_manager"]
https://wiki.archlinux.org/index.php/Systemd/User#Automatic_login_into_Xorg_without_display_manager[/URL]

I have not researched this further, but I'm thinking that could be a problem with your older links. 

Anyhow, just a thought.

If I understand correctly, do you want me to try those steps that refer to Arch?
Would that help with the auto login problem? (the auto startx is working right now)

Thanks

---

### Post by v3.xx on 2015-09-28
> (the auto startx is working right now)

No, not at all.  You have it working.

---

### Post by leninberg on 2015-09-28
> **v3.xx said:**
> Hey Bucky :)

I use to run auto-startx with upstart by creating a ~/.xinitrc.  Seem that it has changed up somwhat since.  Not that long ago upstart was replace with systemd.

[https://wiki.archlinux.org/index.php/Systemd/User#Automatic_login_into_Xorg_without_display_manager](https://wiki.archlinux.org/index.php/Systemd/User#Automatic_login_into_Xorg_without_display_manager)

I have not researched this further, but I'm thinking that could be a problem with your older links. 

Anyhow, just a thought.

It seems you were right, Ubuntu 15.04 now uses systemd, and apparently things have changed.
So I kept on searching now for systemd autologin and got it working.
I found this guide that served me well:
[http://memo-linux.com/debian-8-systemd-autologin-sans-display-manager/](http://memo-linux.com/debian-8-systemd-autologin-sans-display-manager/)

So I did:
```
sudo mkdir -pv /etc/systemd/system/getty@tty1.service.d/
sudo nano /etc/systemd/system/getty@tty1.service.d/autologin.conf
```
and edited the file as follows:
```
[Service]
ExecStart=
ExecStart=-/sbin/agetty --autologin username --noclear %I 38400 linux
```
Change "username" with yours.

Save and close (CTRL+O, CTRL+X)

Now:
```
systemctl enable getty@tty1.service
```
Write your password (I was asked twice)

That would be for the autologin part.
Next, to start X automatically, continue with this:
```
sudo nano ~/.bash_profile
```
and edit that file so it reads:
```
[[ -z $DISPLAY && $XDG_VTNR -eq 1 ]] && exec startx
```
Save and close (CTRL+O, CTRL+X)
(Source: [https://wiki.archlinux.org/index.php/Xinitrc#Autostart_X_at_login](https://wiki.archlinux.org/index.php/Xinitrc#Autostart_X_at_login))

At this point I found another possibility for that file here:
[http://unix.stackexchange.com/questions/42359/how-can-i-autologin-to-desktop-with-systemd](http://unix.stackexchange.com/questions/42359/how-can-i-autologin-to-desktop-with-systemd)
```
if [[ -z $DISPLAY ]] && [[ $(tty) = /dev/tty1 ]]; then
 exec startx
fi
```
But I haven't tested it and I don't really know the difference, sorry

In this last link they advised to do a last step
[I]"You will have to modify your ~/.xinitrc to start your desktop environment, how to do that depends on the DE"
[/I]So I did:
```
sudo nano ~/.xinitrc
```
and added this line
```
exec i3
```
Save and close (CTRL+O, CTRL+X)

Last thing to do:
```
sudo reboot
```

Now it auto logins and auto starts X, and no display manager was needed.
I think I read if you already have a display manager you have to remove it first.
I hope this can be useful for you. Please comment and improve it.

---

### Post by v3.xx on 2015-09-28
Nice post, I have bookmarked it.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Bucky Ball on 2015-09-28
Good news. Please see the first link in my signature. Thanks. :)

---

