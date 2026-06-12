---
title: "How to change the icon of virt-manager of KVM on favorites"
date: 2022-01-10
forum: General Help
---

### Post by satimis on 2022-01-10
Hi all,

I have KVM/QEMU installed with the icon of virt-manager pinned on menu bar.

I have a new icon download on Internet and expect to replace it.  Please advise how to change the icon of virt-manager on menu bar?

Thanks

Regards

---

### Post by Dennis N on 2022-01-10
I would put my new icon in ~/.local/share/icons. Then, I would copy the virt-manager.desktop file in /usr/share/applications to ~/.local/share/applications, and in the copy, replace "virt-manager" in the Icon= line with the full path to the replacement icon. 

You copy the .desktop file first so that your change doesn't affect other users.

---

### Post by satimis on 2022-01-10
> **Dennis N said:**
> I would put my new icon in ~/.local/share/icons. Then, I would copy the virt-manager.desktop file in /usr/share/applications to ~/.local/share/applications, and in the copy, replace "virt-manager" in the Icon= line with the full path to the replacement icon. 

You copy the .desktop file first so that your change doesn't affect other users.
It is very strange to me.  I couldn't find virt-manager.desktop file, only those software running AppImage having  .desktop file

---

### Post by Dennis N on 2022-01-10
> **satimis said:**
> It is very strange to me.  I couldn't find virt-manager.desktop file, only those software running AppImage having  .desktop file

Its definitely there. Check again. 

```
dmn@Sydney:~$ ls /usr/share/applications/virt-manager.desktop
/usr/share/applications/virt-manager.desktop

```

---

### Post by satimis on 2022-01-10
> **Dennis N said:**
> Its definitely there. Check again. 

```
dmn@Sydney:~$ ls /usr/share/applications/virt-manager.desktop
/usr/share/applications/virt-manager.desktop

```
$ ls /home/satimis/.local/share/applications/```

avidemux_2.8.0.appImage  mimeapps.list    shotcut-linux-x86_64-211224.AppImage
avidemux.desktop         shotcut.desktop

```

Sorry, I mistakenly read your advice that virt-manager.desktop is there.

$ ls /usr/share/applications/ | grep virt-manager```

virt-manager.desktop

```

$ cat /usr/share/applications/virt-manager.desktop ```

......
......
Icon=virt-manager
Exec=virt-manager
Type=Application
Terminal=false
Categories=System;

```

The new icon is located on /home/satitims/Pictures/Icons/kvm.png

So I replace the line as Icon=/home/satitims/Pictures/Icons/kvm.png
save -> exit

Do I need to copy the edited virt-manager.desktop back to /usr/share/applications/ to replace the old file ?

Regards

---

### Post by Dennis N on 2022-01-10
> Do I need to copy the edited virt-manager.desktop back to /usr/share/applications/ to replace the old file ?

No, you leave the edited virt-manager.desktop file it in ~/.local/share/applications

---

### Post by TheFu on 2022-01-10
To find files on any Unix/Linux system, install locate (or whatever package that tool is inside I've seen it named mlocate or updatedb too), then run **sudo updatedb** to create the initial DB of all files on the system (it won't look in /mnt or /media by default).  Every day, there is an anacron job that updates the DB automatically going forward.

Then we can use 
```
$ locate -i virt
```
or 
```
$ locate -i manage
```
or
```
$ locate -i desktop
```
to instantaneously get a list of files with those parts somewhere in the filename.
The only gotcha with locate is that it has delayed knowledge. If the file we want to look for was just installed, then using a tool like find would be a better choice, though it has to traverse the entire directory system looking for partial matches.  'find' accepts other inputs which can make searches a little faster, but it will never be as quick as 'locate'.

It should go without saying that searching for the wrong name of a file doesn't work.
```
$ locate -i virtmanager
```
won't find "virt-manager" files.  I would probably use
```
$ locate -i desktop |egrep -i virt
```

Which returned a bunch of junk, but also 
/usr/share/applications/virt-manager.desktop

---

### Post by satimis on 2022-01-10
> **Dennis N said:**
> No, you leave the edited virt-manager.desktop file it in ~/.local/share/applications

Performed following steps;

$ sudo cp /usr/share/applications/virt-manager.desktop /home/satimis/.local/share/applications/
$ sudo nano /home/satimis/.local/share/applications/virt-manager.desktop 

replace the line
Icon=virt-manager
with;
Icon=/home/satitims/Pictures/Icons/kvm.png

Save modified buffer? -> Yes
File Name to Write:<op  [enter]

Done

Pls refer to attached screenshot_virt-manager.png

Thanks

Regards

---

### Post by satimis on 2022-01-10
> **TheFu said:**
> To find files on any Unix/Linux system, install locate (or whatever package that tool is inside I've seen it named mlocate or updatedb too), then run **sudo updatedb** to create the initial DB of all files on the system (it won't look in /mnt or /media by default).  Every day, there is an anacron job that updates the DB automatically going forward.

Then we can use 
```
$ locate -i virt
```
or 
```
$ locate -i manage
```
or
```
$ locate -i desktop
```
to instantaneously get a list of files with those parts somewhere in the filename.
The only gotcha with locate is that it has delayed knowledge. If the file we want to look for was just installed, then using a tool like find would be a better choice, though it has to traverse the entire directory system looking for partial matches.  'find' accepts other inputs which can make searches a little faster, but it will never be as quick as 'locate'.

It should go without saying that searching for the wrong name of a file doesn't work.
```
$ locate -i virtmanager
```
won't find "virt-manager" files.  I would probably use
```
$ locate -i desktop |egrep -i virt
```

Which returned a bunch of junk, but also 
/usr/share/applications/virt-manager.desktop

$ sudo apt install locate

$ sudo updatedb```

/usr/bin/find: '/run/user/1000/gvfs': Permission denied

```

$ locate -i virt-manager.desktop```

/home/satimis/.local/share/applications/virt-manager.desktop
/usr/share/applications/virt-manager.desktop

```

$ locate -i .desktop | grep virt```

/home/satimis/.local/share/applications/virt-manager.desktop
/usr/share/applications/virt-manager.desktop

```

Thanks

Regards

---

