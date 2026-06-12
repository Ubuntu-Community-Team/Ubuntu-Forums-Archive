---
title: "Linking /dev/dvd on boot"
date: 2013-01-10
forum: General Help
---

### Post by searchfgold6789 on 2013-01-10
Hi,
I am trying to play DVDs on my Kubuntu 12.10 system. I can only play them with Dragon if /dev/dvd links to /dev/sr0. I need to make this link every time I need to play a DVD, however. Is there any way that I can have Ubuntu make this link when the system boots, maybe even when /dev is being populated by the kernel? I would like to know what the best way to do this is.
Thanks,
 - searchfgold6789

---

### Post by dino99 on 2013-01-10
is your system has been tweaked ?
because "mountall" usually deals itself with such case, mounting "on demand" when needed.

look at /etc/fstab , to see if the dvd entry is set, and if it match with the output of "sudo blkid"

---

### Post by searchfgold6789 on 2013-01-10
Thank you for your reply, but my system, like many linux systems, does not have any optical device in my fstab. I would need to tweak my system in order to do that, and I chose not to. Mountall does not automatically mount optical devices unless I tell it to with fstab, and that is not what I am doing.

Even if the DVD is mounted, its device name is /dev/sr0, and it needs to be /dev/dvd because that is what Dragon (my DVD player software) tries to read. (I might add that this feature in Dragon is very elementary and needs to be more like VLC, so we can choose a device and play from it rather than only having one option. But that's just how Dragon is.) 

When I want to play a DVD, I can go to the trouble of opening a terminal and doing a `sudo ln -s /dev/sr0 /dev/dvd` and thus create the link myself, but I would much rather this be done automatically on boot.

---

### Post by LewisTM on 2013-01-10
What about inserting 'ln -s /dev/sr0 /dev/dvd' in your /etc/rc.local?

---

### Post by searchfgold6789 on 2013-01-10
> **LewisTM said:**
> What about inserting 'ln -s /dev/sr0 /dev/dvd' in your /etc/rc.local?
Thank you. This will work perfectly (:
Was not aware of this Linux feature.

---

