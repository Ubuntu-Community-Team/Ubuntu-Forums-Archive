---
title: "GDM and Unity"
date: 2013-05-12
forum: General Help
---

### Post by OmgItsPixelated on 2013-05-12
Hey there so a while ago I decided to change to gnome and ditch unity but now I've gotten rid of gnome and gone back to unity, I can't seem to switch from gdm to lightdm. it wouldn't boot to the login screen and I had to press ctrl-alt-f1 to get into the command line to change the default dm back to gdm so that I can login to the desktop.
So my question is, Is it ok to use gdm with unity or should I find another way to switch to lightdm? Currently I'm having no trouble with it though it does look a bit ugly.

---

### Post by grahammechanical on 2013-05-12
They both manage the login. If it works, then it works. But there is a way to switch over that must be followed. Do you have Lighdm installed? Or did you remove it? We need to stop one display manager and then start the other display manager but both have to be installed, that is on the system if not in use. This may still work.

```
sudo service gdm stop
```
```
sudo service lightdm start
```

Regards.

---

### Post by mcduck on 2013-05-12
How did you try to change to lightdm? This command should do the job:
```
sudo update-alternatives --config x-session-manager
```

---

### Post by sgage on 2013-05-12
Another thing to try is 

```
sudo dpkg-reconfigure gdm
```

and you will get a dialog asking which one you want to be the operational DM.

---

### Post by OmgItsPixelated on 2013-05-13
> **sgage said:**
> Another thing to try is 

```
sudo dpkg-reconfigure gdm
```

and you will get a dialog asking which one you want to be the operational DM.

This was command I used to switch from gdm to lightdm but it didn't work.
Now that I'm sure that gdm won't cause any conflicts with unity I won't have any need to change back to lightdm. thanks for the answers guys.

---

