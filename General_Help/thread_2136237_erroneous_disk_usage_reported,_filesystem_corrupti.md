---
title: "erroneous disk usage reported, filesystem corruption?"
date: 2013-04-16
forum: General Help
---

### Post by jayekub on 2013-04-16
i have a pretty plain vanilla 12.04.2 LTS machine, although i believe i've upgraded it through a couple releases. my root partition (ext4) will routinely show almost 100% disk usage, like so:

$ mount | grep /dev/sda5
/dev/sda5 on / type ext4 (rw,errors=remount-ro,user_xattr)
$ df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       117G  111G     0 100% /

however, using the disk usage analyzer (or just du) i can never account for more than a fraction of this. if i 'sudo touch /forcefsck' and reboot, i can sometimes reclaim the space for a couple of days, but eventually the usage always shoots back up.

the phantom space used appears to live under my homedir (attached a screenshot of disk analyzer showing this). not sure if this means anything.

so it looks like i've got some sort of fs corruption here. anyone ever dealt with this before? any ideas on how to fix it permanently? do i just have to move everything over to a freshly formatted partition (ugh)?

thanks for any help!

---

### Post by jayekub on 2013-04-17
oops...looks like i have a 96G .xsession-errors file. i inadvertently enabled upnp port-mapping for remote desktop and some leet haxors have apparently been trying to brute-force my vnc server. closing that one down...

nevermind!

---

