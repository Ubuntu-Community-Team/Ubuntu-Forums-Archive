---
title: "Moving /opt to another drive"
date: 2021-11-23
forum: General Help
---

### Post by makem2 on 2021-11-23
I have invested in another M2 1TB drive and would like to move /opt to the new drive from its current location /opt.

/opt currently contains 3 directories including google and teamviewer. The third program is minecraft and I know I can move that easily but I am unsure about the others. I could uninstall teamviewer and reinstall it after the move, but google which contains earth and chrome?

How do I deal with this?

---

### Post by The Cog on 2021-11-23
I would format the new drive and mount it to a temporary location, then copy all the files across to the new drive (e.g. **cp -a /opt/* /mnt/newopt**). Once happy everything is there, you can unmount the temp location and mount the new drive, rename /opt to /old-opt, create a new empty /opt and mount the new drive there. Once you're happy it all works, you can add the new drive's /opt mount point to /etc/fstab so it mounts on every boot, and reboot. Once you are happy everything is still working, all that remains is to delete the original /old-opt directory.

---

### Post by HermanAB on 2021-11-23
Simple solution: Copy it, delete the original and put a simlink to the new place.

---

