---
title: "Lost icons on desktop!"
date: 2008-05-22
forum: General Help
---

### Post by LasseNC on 2008-05-22
Hello there! 

I lost all my icons on my desktop, can't right click on it either, otherwise it seems okay.

Anyone?

Kind regards, Lasse

---

### Post by drs305 on 2008-05-22
I often completely clear off my desktop using the following with the switch set to 'false'. Running this command with 'true' may restore your icons:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
```

You could also try to refresh your desktop with:
```
killall gnome-panel
```

---

### Post by LasseNC on 2008-05-22
No change :(

---

### Post by Goklagie on 2008-05-23
Same here. This happened after installing the last updates.

---

### Post by Goklagie on 2008-05-23
Solved.:D
Try in terminal:

sudo killall nautilus
sudo nautilus &

---

### Post by vanadium on 2008-05-23
sudo nautilus ???????? Don't do that! Remove the "sudo" in front.

---

### Post by Goklagie on 2008-05-23
Why not?
Works fine with sudo.

---

### Post by chrisccoulson on 2008-05-23
No no no **NO**! It does **NOT** work fine with sudo. I have to point this out to any other users who read this who might believe that running Nautilus with sudo is a good idea. Any changes it makes to your profile may cause it to be owned by root, preventing you from running it as normal user in the future (or causing problems). It could also cause your .Xauthority file to be chowned to root, preventing you from logging in at all.

You shouldn't run **any** graphical tool with sudo!!! If you need to run a particular tool with root privileges, use *gksudo*

Nevertheless, you shouldn't run Nautilus with gksudo unless you're doing a particular file operation that absolutely needs root privileges.

---

### Post by RealMabu on 2008-06-24
> **Goklagie said:**
> Solved.:D
Try in terminal:

sudo killall nautilus
sudo nautilus &

I'm not trying that but I tried rebooting.
Rebooting should be as effective as "kill it & fire it again", shouldn't it?
Well, it didn't work for me.
For those willing to help, this is my case:
*Cross post from [http://ubuntuforums.org/showthread.php?t=814079]("http://ubuntuforums.org/showthread.php?t=814079")*
> 
Same for me too.
That was after an update that required a reboot.
I believe (but am not sure) that it was right after the release of 2.6.24-19-generic kernel.
So, symptoms:
-/home/myname/Desktop folder still exists and is in good health
-menu bar is fine too
-nautilus displays only the background and nothing can be done there (no new folder, no drag&drop)
-rebooting won't work for me
-under gconf-editor->apps->nautilus->preferences the "show desktop" checkbox IS checked. Tried to run gconf-editor as root also, same result: checked.

Oh, BTW, the OS is working fine, all apps run seamlessly and everything seems to be ok... just NO DESKTOP.

Any help?

Thanks

---

### Post by RealMabu on 2008-06-30
Finally, I found a workaround:
1)ctrl+alt+f1 and text-mode login
2)sudo /etc/init.d/gdm restart
3)ctrl+alt+f7 if graphics-mode login doesn't appear.

It works for me.
Someone can explain why rebooting doesn't work, while restarting only gdm works?

---

