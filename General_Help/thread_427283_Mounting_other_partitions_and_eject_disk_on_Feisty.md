---
title: "Mounting other partitions and eject disk on Feisty"
date: 2007-04-29
forum: General Help
---

### Post by dxdemetriou on 2007-04-29
Hi,
when I made an upgrade to Feisty I have seen these changes:
1) When I try to eject an external usb disk it didn't and remount it. I fixed this with changing the file:
 /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi
with:
       <match key="storage.bus" string="usb">
        <merge key="storage.requires_eject" type="bool">false</merge>
      </match>
or moving the file to: storage-policy.fdi.bak
I saw discussions about this, and about how the disk is umounts, but don't eject (don't turn off)
From the other side, if the eject worked well, like on Edgy and before, when one disk have many partitions, when trying to eject one partition, all others ejects too and I don't know if umount them first.
I think is a good idea when eject fixed on Feisty, to there are both options, to umount or eject the disk
2) This is something I can't understand. Before the Feisty I had the hda1 as /, and the hda6 as secondary partition. Because the right click didn't work before I made shortcuts to mount and umount it (I didn't prefer the fstab). Now that the right click works, it mounts ok, but if there +x programs can't execute. The same thing is on external usb disks too.
When I mount them with the old way I used, everything is ok.
Why is this difference between the pmount and the manual mounting?
I like Feisty, and is the only release that I haven't many troubles to fix things except these up to now.
I hope somebody founds the solution
Sorry if the title doesn't fit all of them, I didn't know what to write :)
Thanks

---

### Post by dxdemetriou on 2007-04-30
I found the solution for not exec on partitions
[http://ubuntuforums.org/showthread.php?t=358136](http://ubuntuforums.org/showthread.php?t=358136)

---

