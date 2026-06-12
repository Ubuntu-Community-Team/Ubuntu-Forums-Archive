---
title: "Thunar takes 30 seconds to launch first time, then quickly after that"
date: 2024-03-01
forum: General Help
---

### Post by fishwebby on 2024-03-01
When I launch the Thunar file explorer on Xubuntu, the first time I launch it after a reboot it takes about 30 seconds to launch. Subsequent launches are almost instantaneous.

How can I debug this? Is there a log I can look in that will tell me what's going on?

Any help is greatly appreciated!

---

### Post by ajgreeny on 2024-03-01
I haven't heard of this for a very long time but about 10-12 years ago I had the same problem.  After searching I found that it was related to samba mounts slowing things down.
I never used or needed samba but nevertheless when I made the changes shown below opening speed of thunar was back to normal.

Give it a try. If it makes no difference you can either leave the edits or restore the original.

Edit /usr/share/gvfs/mounts/network.mount and change it from:
```

[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=true

```
to

```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=false

```
it will make opening up thunar very quick again even for the first time.  If you want the smb browsing you just click on the network:/// link in thunar and it will then do the browsing search which takes a bit of time.

---

### Post by fishwebby on 2024-03-02
Alas the file /usr/share/gvfs/mounts/network.mount doesn't exist... the only files in that folder are

burn.mount
computer.mount
localtest.mount
trash.mount

I'm wondering if it is something to do with network shares - I used to have a network-connected drive, but no longer, perhaps the configuration for that is still around somewhere.

---

### Post by Morbius1 on 2024-03-02
>  I'm wondering if it is something to do with network shares - I used to have a network-connected drive, but no longer, perhaps the configuration for that is still around somewhere. 

Um....

It could be Gigolo if you are using it.

It could be a gio mount that you added to your autostart folder:
```
ls -al $HOME/.config/autostart
```

Or it's in fstab:
```
cat /etc/fstab
```

---

### Post by fishwebby on 2024-03-02
I just looked at all those as  you suggested, and alas it's none of those... is there a log that Thunar or the system writes to when starting the app that might contain some timeout errors or something?

---

