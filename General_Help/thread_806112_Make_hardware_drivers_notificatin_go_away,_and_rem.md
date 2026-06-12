---
title: "Make hardware drivers notificatin go away, and remove drive icon from desktop"
date: 2008-05-24
forum: General Help
---

### Post by keeler1 on 2008-05-24
I have two problems.

1.) The notification that I am using the nvidia driver always shows up in the panel.  I click on it to see the notification and click close but it still remains.

2.)  I have mounted a fat32 partition under /home/user/Music (did this in my fstab)  However a desktop icon is also created.  How can I not have this desktop icon.  It is really annoying.

If anyone knows solutions to either of these problems please post.

---

### Post by TeoBigusGeekus on 2008-05-24
2.) Applications->System Tools-> Configuration Editor
Apps->Nautilus->Desktop
Uncheck volumes visible.

---

### Post by Steve413z on 2008-05-24
does the icon on the desktop actually link to that partiton, because I have had broken mount points stay on the desktop before,

if that device showing on the desktop stays there even though it doesn't link to anything, here is the solution:

let's just say that it shows up on the desktop as "musicpartition"

```
sudo umount -f /media/musicparition/
```should do the trick


and you can remove that nvidia notification from the panel somehow, i forget how exactly, i think you just gotta right click it.

---

