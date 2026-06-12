---
title: "mount network drive via etc/init not working"
date: 2016-04-23
forum: General Help
---

### Post by abc11 on 2016-04-23
Hi,
I have just changed to a new laptop. On the previous one I had setup so that it would mount my NAS at startup through an entry in fstab. When having the same setup on the new laptop it didn't work. Running mount -a worked though. Googling a bit made me think it might be the case that the computer tried to mount before the network is up (why this would not be a problem on the previous computer I do not know...). Trying to use bits and pieces that I found in various posts online I created the file my-network-up.conf containing

```
start on net-device-up
script
/etc/init.d/mount-after-network-up
end script
```

and placed it in etc/init. I then created the file mount-after-network-up containing

```
#!/bin/bash
mount -a -t cifs
```

which I placed in etc/init.d. However, this does not work. After reboot the NAS has to be manually mounted (mount -a). As I am not at all familiar with init-files and bash code, I have no idea what is the problem here. Can you see what is wrong or can you perhaps help me debugging?

---

### Post by TheFu on 2016-04-23
I wouldn't do it this way.  I'd use autofs so the NAS storage isn't mounted until requested.  I use autofs extensively for NFS and USB storage.  It usually works for CIFS too, but sometimes the CIFS machine (if Windows), needs to be rebooted to make the mount available. That doesn't happen all the time - maybe once a month.

The other option is to make certain that the fstab line for the NFS storage delays the mount - one of the columns controls that.

---

### Post by abc11 on 2016-04-24
Is there any particular reason for not doing this as I have attempted? I had a look at using _netdev in fstab, but it seems it [is only for nfs]("https://help.ubuntu.com/community/Fstab").

---

### Post by TheFu on 2016-04-24
No. I just don't know it and have been doing it the autofs way since the mid-1990s. 
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

/etc/init is relatively new. I've never touched anything in there.  

I think autofs is the recommended solution for this sort of requirement, but maybe things have changed?

I see the _netdev,noauto options used for CIFS too in the fstab here: [https://askubuntu.com/questions/268121/how-to-mount-a-cifs-share-so-it-doesnt-warn-about-external-file-modifications](https://askubuntu.com/questions/268121/how-to-mount-a-cifs-share-so-it-doesnt-warn-about-external-file-modifications)   Maybe try those together?  I don't use fstab for non-directly connected via SATA/eSATA/Infiniband storage.  Network and USB storage get handled through autofs. Why - networks and USB connections aren't as solid. That can lock up a system when not available. I learned this the hard way over the years.  Experience.

---

### Post by bab1 on 2016-04-24
> **abc11 said:**
> Is there any particular reason for not doing this as I have attempted? I had a look at using _netdev in fstab, but it seems it [is only for nfs]("https://help.ubuntu.com/community/Fstab").
I agree with @TheFu on this one.  You do not use the init system for this kind of thing.  Init is for starting up processes not directly mounting file systems (local or remote).  If you want to run a script at the end of all the init process setup, use the script at /etc/rc.local.  Just add your code and it will be executed after everything else is running.  You will need to add a line to the fstab file that*** allows you as a non-root user*** to mount a partition to the local file system via a script.  The fstab line should look something like this ```

<remote FS> <[COLOR="#FF0000"]local mount point[/COLOR]>  cifs   user,noauto,username=XXXX,credentials=/home/XXXX/.smbcred,uid=NNNN,gid=NNNN,nobrl 0 00 	0
```... this provides a stable mount with a simple script such as this ```

# use the mount point only in the script
#  the the fstab provides the rest
mount /<[COLOR="#FF0000"]local mount point[/COLOR]>
```

In a sense, this provides the same non-root user mounting functionality as AutoFS.  The basic difference is the mount is always performed this using /etc/rc.local.  Using AutoFS it is done only if the user asks for the FS mount.

---

### Post by Morbius1 on 2016-04-24
> start on net-device-up
script
/etc/init.d/mount-after-network-up
end script
It's probably not worth getting too far into this since Upstart has been replaced with systemd but your job may be working fine but at the wrong time. 

Something like this telling it to ignore loopback: [http://serverfault.com/questions/117584/upstart-scripts-run-a-task-after-networking-goes-up](http://serverfault.com/questions/117584/upstart-scripts-run-a-task-after-networking-goes-up)

Or maybe specifically telling it which network has to be up like: start on net-device-up IFACE=wlan0

---

### Post by bab1 on 2016-04-24
> **Morbius1 said:**
> It's probably not worth getting too far into this since Upstart has been replaced with systemd but your job may be working fine but at the wrong time. 

Something like this telling it to ignore loopback: [http://serverfault.com/questions/117584/upstart-scripts-run-a-task-after-networking-goes-up](http://serverfault.com/questions/117584/upstart-scripts-run-a-task-after-networking-goes-up)

Or maybe specifically telling it which network has to be up like: start on net-device-up IFACE=wlan0
Since the whole issue can be resolved in an init agnostic way, why bother at all with Upstart vs Systemd?

---

