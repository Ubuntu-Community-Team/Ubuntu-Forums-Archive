---
title: "move wine &quot;c:\&quot; dir"
date: 2008-07-01
forum: General Help
---

### Post by terry f on 2008-07-01
Hi

I am trying to install steam so I can play my games.  When I go to install steam wine only prompts me to install it on "c:\"  is it possible to change where "c:\" is mounted at, right now it is at "/home/terry/.wine/drive_c".  I mean my primary disk is some what small and I don't want to fill it up with my games, I would much rather install them to a different partition.

---

### Post by sisco311 on 2008-07-01
Move the drive_c directory to the new partition and create a symbolic link
```
ln -s -T /media/new-partition/path/to/drive_c /home/terry/.wine/drive_c
```

---

### Post by ndrone1 on 2008-07-05
I'm trying to do the same thing, but it's not working the way you've set forth:

```
err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
nate@Nate-xpsm1330:~$ ln -s -T /media/sda2/path/to/drive_c /home/nate/.wine/drive_c
ln: creating symbolic link `/home/nate/.wine/drive_c': File exists

```

That's all I'm getting. Wine and Winetricks are a headache and a half!! I need major help. I can't get them to do anything. :/

---

### Post by sayakb on 2008-07-05
Try it via the GUI then. Goto Applications->Wine->Configure Wine
Click on **Drives** tab, click on [B]C:
[/B]And change the **Path** text below.
Press **Apply** and then **OK**.
Check if this works.

---

### Post by ad_267 on 2008-07-05
You need to copy the drive_c directory onto where you want it on the other drive and then **delete your current drive_c**. That's why it says "File exists."

Edit: Or just do what LinuxIsInnovation said.

---

