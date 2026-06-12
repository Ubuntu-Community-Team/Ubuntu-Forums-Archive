---
title: "special device hostname:/home/share does not exist"
date: 2007-11-30
forum: General Help
---

### Post by dancro on 2007-11-30
On a gutsy machine I try to mount a folder located on a dapper machine.  I have no trouble mounting this same folder on a second dapper machine on the same network.

root@gutsymachine:~# mount dappermachine:/home/share /mnt/gallery 
and receive this message:
mount: wrong fs type, bad option, bad superblock on dappermachine:/home/share,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@gutsymachine:/mnt/gallery# dmesg | tail  
[85710.289627] eth0: link up.

root@gutsymachine:~# mount -t ext3 dappermachine:/home/share /mnt/gallery 
and receive this error
mount: special device dappermachine:/home/share does not exist

Thanks in advance for any suggestions or ideas.
Dan

---

