---
title: "how to copy all files from ubuntu A to ubuntu B,preserving everything,permissions and"
date: 2020-06-06
forum: General Help
---

### Post by marietto2008 on 2020-06-06
Hello to everyone.

I would like to copy all files of this kind : *vmware* with the same permissions and simlinks whatever they are on the ubuntu distribution that I have installed on the PC A to a usb stick and from the usb stick to the ubuntu distribution that I have installed on the PC B. Can someone give me some help ? I tried to do something like this,but it didn't work :

> root@ziomario-I9:/media/ziomario/ACRONIS_MED/vmware/etc/rc2.d# rsync -avz /etc/rc2.d/*vmware* /media/ziomario/ACRONIS_MED/vmware/etc/rc2.d/

sending incremental file list

rsync: symlink "/media/ziomario/ACRONIS_MED/vmware/etc/rc2.d/.K08vmware-USBArbitrator.7003" -> "/etc/init.d/vmware-USBArbitrator" failed: Operation not permitted (1)
rsync: symlink "/media/ziomario/ACRONIS_MED/vmware/etc/rc2.d/.S01vmware.7003" -> "../init.d/vmware" failed: Operation not permitted (1)
rsync: symlink "/media/ziomario/ACRONIS_MED/vmware/etc/rc2.d/.S01vmware-workstation-server.7003" -> "../init.d/vmware-workstation-server" failed: Operation not permitted (1)
rsync: symlink "/media/ziomario/ACRONIS_MED/vmware/etc/rc2.d/.S50vmware-USBArbitrator.7003" -> "/etc/init.d/vmware-USBArbitrator" failed: Operation not permitted (1)

sent 276 bytes received 670 bytes 1,892.00 bytes/sec
total size is 115 speedup is 0.12
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1207) [sender=3.1.3]

thanks.

---

### Post by bobnn on 2020-06-07
Have you reformatted the USB stick to a Linux type of file system, such as ext4?  They normally are formatted in some DOS/Windows format that may not like the symlinks it's complaining about.  It's got to be safer to use a Linux file system on the USB.

---

### Post by marietto2008 on 2020-06-07
thanks. formatting the usb stick with ext4 fixed the problem. again thanks.

---

