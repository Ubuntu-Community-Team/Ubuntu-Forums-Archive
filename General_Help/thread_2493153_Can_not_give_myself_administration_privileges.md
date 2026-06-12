---
title: "Can not give myself administration privileges"
date: 2023-12-05
forum: General Help
---

### Post by garyed on 2023-12-05
I'm having problems being able to make some simple changes like changing the date format in settings. 
So I checked my user permissions both standard & administrator under account type are grayed out & I can't select either one even after I unlock with the password.
The only thing it will let me change is the automatic login. Any ideas on what I'm missing?
I can however give other users administrator privileges but I just can't do anything with mine.

---

### Post by #&amp;thj^% on 2023-12-05
Try backing up your ".config" and moving it out of way ie:
```
mv .config .config.bk 
```
Reboot to see if that helps
Also check:
```
stat .Xauthority 
  File: .Xauthority
  Size: 224       	Blocks: 10         IO Block: 512    regular file
Device: 0,40	Inode: 160596      Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2023-12-05 10:36:02.456136670 -0700
Modify: 2023-12-05 10:36:02.420136494 -0700
Change: 2023-12-05 10:36:02.420136494 -0700
 Birth: 2023-12-02 18:23:46.177464776 -0700

```

---

### Post by garyed on 2023-12-05
> **1fallen said:**
> Try backing up your ".config" and moving it out of way ie:
```
mv .config .config.bk 
```
Reboot to see if that helps
Also check:
```
stat .Xauthority 
  File: .Xauthority
  Size: 224       	Blocks: 10         IO Block: 512    regular file
Device: 0,40	Inode: 160596      Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2023-12-05 10:36:02.456136670 -0700
Modify: 2023-12-05 10:36:02.420136494 -0700
Change: 2023-12-05 10:36:02.420136494 -0700
 Birth: 2023-12-02 18:23:46.177464776 -0700

```
I tried the first thing,rebooted & it didn't work.
The second thing just came up with "no such file"

---

### Post by #&amp;thj^% on 2023-12-05
> **garyed said:**
> 
The second thing just came up with "no such file"
Must be a Gnome thing then, but what is this output:
```
groups
me adm cdrom sudo dip plugdev users lpadmin sambashare libvirt

```

---

### Post by garyed on 2023-12-05
> **1fallen said:**
> Must be a Gnome thing then, but what is this output:
```
groups
me adm cdrom sudo dip plugdev users lpadmin sambashare libvirt

```

output of groups is::    gary adm cdrom sudo dip plugdev lpadmin sambashare kvm

I'm gary so it looks like I'm admin from the terminal but in gnome as a user it doesn't show  me that way.
What I'm really trying to do is just change my clock from 24 hr to 12 hr. format & nothing will allow me to change it. 
That's why I assume it's a permission thing. Is there a way to change the clock format from the command line?

---

### Post by garyed on 2023-12-05
I actually found a way to change the clock format to 12 hr in terminal:
code: > gsettings set org.gnome.desktop.interface clock-format 12h
Maybe my user settings being grayed out is normal since I'm already admin in terminal but that doesn't tell me why I couldn't change my clock settings in gnome.

---

### Post by yancek on 2023-12-06
You have not indicated which release of Ubuntu you are using.  I still have 20.04 installed and going to Settings/ Date & Time as a user allows me to make the change after entering the password used for sudo privileges.  Is that how you tried to make the change?  If not, what release of Ubuntu are you using?

---

### Post by garyed on 2023-12-06
I'm using 18.04  on the laptop that I was having the problem with being able to change the date format.
I just checked my desktop where I'm using 22.4 & I found that the main user is also grayed out just like the laptop, so it looks like that is normal to not be able to change permissions on the main default user.

---

### Post by #&amp;thj^% on 2023-12-06
> **garyed said:**
> I actually found a way to change the clock format to 12 hr in terminal:
code: 
Maybe my user settings being grayed out is normal since I'm already admin in terminal but that doesn't tell me why I couldn't change my clock settings in gnome.

Along with:
```
timedatectl --help
```
or as something like:
```
timedatectl set-time 10:30:00
```

---

