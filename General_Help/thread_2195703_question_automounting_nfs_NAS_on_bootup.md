---
title: "question automounting nfs NAS on bootup"
date: 2013-12-25
forum: General Help
---

### Post by egarcia on 2013-12-25
I am able to mount a NAS shared folder using terminal command line ```
sudo mount -t nfs 192.168.0.156:/data/HardDisk1/Volume1/test /mnt -o nolock
``` i got this code in the users manual of my NAS.

How to automatically mount this everytime i bootup my ubuntu 13.10? 
i tried to search for a tutorial and all i find is how to edit your fstab to mount Synology or Netgear NAS, but the codes doesnt work with my Planet NAS 7202.

can you please convert my command line code to a fstab line? 
or is it possible to write a sh script and load it to start up applications?

---

### Post by nerdtron on 2013-12-26
Here's the fstab line that should be added:
```
 192.168.0.156:[COLOR=#000000][FONT=Ubuntu Mono]/data/HardDisk1/Volume1/test[/FONT][/COLOR]   /mnt/    nfs    [COLOR=#000000][FONT=Ubuntu Mono]nolock,[/FONT][/COLOR]rw  0   0 
```

Try to reboot and see if the works.

---

### Post by egarcia on 2013-12-28
im sorry, i cannot test your suggestion anymore. i went and used a autonfs script i found in this [tutorial]("https://help.ubuntu.com/community/AutomaticallyMountNFSSharesWithoutAutofsHowto"). but thanks!

---

