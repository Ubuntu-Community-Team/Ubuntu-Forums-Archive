---
title: "encrypting home directory (or, mounting truecrypt volumes at boot)"
date: 2006-10-30
forum: General Help
---

### Post by zeus77 on 2006-10-30
I'd like to encrypt my home directory (/home/zeus77) by using a Truecrypt volume which gets mounted at boot.  Obviously, I would need to be prompted for the Truecrypt password during the boot process.  I thought that the most obvious way to do this would be to write a quick script which mounts the volume, and put the script in /etc/init.d.  This approach doesn't seem to work, however, as interactive scripts (i.e. those asking for a password) don't seem to be supported by the init.d mechanism.  Another user reported similar difficulties [here]("http://ubuntuforums.org/showthread.php?p=1103275").  

Has anyone successfully automated the mounting of truecrypt volumes at boot?

Alternatively, I would be willing to accept a solution that mounted my truecrypt volume at login.  However, placing the truecrypt command in ~/.bash_profile did not seem to work, either.  I would much prefer a solution that mounted the volume at boot, though, if it's possible.  

It seems this question has been asked on these forums several times ([here](http://ubuntuforums.org/showthread.php?p=1103275) and [here](http://ubuntuforums.org/showthread.php?t=251840)), and also on the truecrypt forums ([here](http://forums.truecrypt.org/viewtopic.php?t=3800), [here](http://forums.truecrypt.org/viewtopic.php?t=3811), and [here](http://forums.truecrypt.org/viewtopic.php?t=1830) -- may require logon).  It's not clear that anyone has gotten it to work (with Ubuntu, anyway). 

Thanks.

[NB: I realize there are other encryption tools which may work, but I want to use Truecrypt.  Also, for more complete security, I realize that I should encrypt more than just the home directory -- probably also the swap and tmp, at the very least -- but this suffices for my needs.]

---

### Post by TheGurke on 2008-02-08
I had the same problem and didn't find an answer online, so I tried to solve it myself. The solution I came up with is as follows:

edit the script  /etc/gdm/Init/Default which is run every time the x server gets started / restarted, for example if you log in. Just insert a few lines at the beginning of the script.

```
sudo gedit /etc/gdm/Init/Default
```

The beginning of the script looks something like this on gusty:
```
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George
```

insert on the second line your truecrypt mount command / script:

```
#!/bin/sh
zenity --entry --text "Enter password" --hide-text | truecrypt /path/to/volume /path/to/mountpoint
```

The zenity command is necessary since the x server has already started so you need a graphical interface.

Since this is pre-login, it can be used for an encrypted /home directory, however I don't know if you can do this with /root. Also I have no idea how to start an interactive script before the xserver.

I hope this is helpful although late

---

### Post by update_manager on 2008-03-21
You could use ccrypt:


[LIST]
Insert create a passphase and save it as a plain text file on the USB key.
[/LIST]

[LIST]
Put this line in /etc/rc.local or /etc/gdm/Init/Default
ccrypt -rR -e -k /media/disk/keyfile /home/<user>
[/LIST]

Without the keyfile (on a USB key, external hard drive, CD-ROM), the directory can not be decrypted.

uur

---

