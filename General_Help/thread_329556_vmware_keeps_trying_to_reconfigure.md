---
title: "vmware keeps trying to reconfigure"
date: 2007-01-01
forum: General Help
---

### Post by gwpritch on 2007-01-01
I have installed vmware-player via automatix in order to run a very few XP apps. Everything works fine, networking is operating etc. but now every time I run synaptic or apt-get from the CL the player attempts to reconfigure itself...searching for free subnets etc. It terminates as follows:

```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
```

The player still works fine :???: 
How can I get this to stop?

---

### Post by arnieboy on 2007-01-02
This is a known bug in the vmware player package in Ubuntu multiverse which Automatix installs. The discussion of the bug can be found here:
[https://launchpad.net/distros/ubuntu/+source/vmware-player/+bug/57957](https://launchpad.net/distros/ubuntu/+source/vmware-player/+bug/57957)

---

### Post by gwpritch on 2007-01-02
Having read through the discussion I'm not sure if this is the same bug or not since my copy of vmplayer is actually up and working. Its just that the network configuration script seems to want to keep running (and failing) every time I run apt-get. If I say no to overwriting the files I seem to be all right. I will however try modifying the script as suggested and see if that helps.
Thanks.

---

### Post by speedwell68 on 2007-01-14
> **arnieboy said:**
> This is a known bug in the vmware player package in Ubuntu multiverse which Automatix installs. The discussion of the bug can be found here:
[https://launchpad.net/distros/ubuntu/+source/vmware-player/+bug/57957](https://launchpad.net/distros/ubuntu/+source/vmware-player/+bug/57957)

I had this exact same problem and using the script changes in the above thread and it worked a treat.  Thanks a lot Arnieboy, this bug was really beginning to bug me.

---

### Post by arnieboy on 2007-01-14
This is a case of a broken post installation file. Try the following:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.postinst
sudo apt-get remove vmware-player
```
and check to see if the error appears again.
If its **not fixed**, try the following:```

sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo apt-get remove vmware-player
```

---

