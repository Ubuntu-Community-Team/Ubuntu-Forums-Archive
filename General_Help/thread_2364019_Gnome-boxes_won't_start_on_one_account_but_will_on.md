---
title: "Gnome-boxes won't start on one account but will on another"
date: 2017-06-17
forum: General Help
---

### Post by Fuji_in_Japan on 2017-06-17
Hello,

Gnome-boxes begins to start then crashes on my account.  However, I created another account and boxes loaded fine.  I tried to deleting the files in ~/.config and ~/.share but no luch.

When I launch from the CL I get the following error:

```
(gnome-boxes:13410): Libvirt.GObject-CRITICAL **: gvir_storage_vol_get_info: assertion 'GVIR_IS_STORAGE_VOL(vol)' failed
Segmentation fault (core dumped)
```


Thanks in advance for any advice how to correct this problem.

---

### Post by Fuji_in_Japan on 2017-07-05
No hits for two weeks so I moved to general help.

Dave

---

### Post by Fuji_in_Japan on 2017-07-05
Hello,

Gnome-boxes begins to start then crashes on my account.  However, I  created another account and boxes loaded fine.  I tried to deleting the  files in ~/.config and ~/.share but no luch.

When I launch from the CL I get the following error:

```
(gnome-boxes:13410): Libvirt.GObject-CRITICAL **: gvir_storage_vol_get_info: assertion 'GVIR_IS_STORAGE_VOL(vol)' failed
Segmentation fault (core dumped)
```

```
 gnome-boxes --checks

(gnome-boxes:7452): Boxes-WARNING **: util-app.vala:270: Failed to execute child process ?virsh? (No such file or directory)

(gnome-boxes:7452): Boxes-WARNING **: util-app.vala:250: Failed to execute child process ?restorecon? (No such file or directory)
• The CPU is capable of virtualization: yes
• The KVM module is loaded: yes
• Libvirt KVM guest available: no
• Boxes storage pool available: no
    Could not get “gnome-boxes” storage pool information from libvirt. Make sure “virsh -c qemu:///session pool-dumpxml gnome-boxes” is working.
• The SELinux context is default: no

Report bugs to <https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-boxes>.
Boxes home page: <https://wiki.gnome.org/Apps/Boxes>.
 
```


Thanks in advance for any advice how to correct this problem.

---

### Post by coffeecat on 2017-07-05
Threads merged, and merged thread moved to General Help.

@Fuji_in_Japan, if you don't get a reply please simply bump your thread to bring it up to the top, and to bring it to the attention of people in different time zones. Not less than 12 hours, but certainly after a day if you get no responses.

Also, if you want a thread moved to another sub-forum, simply use the report post button to send a request to the staff area.

---

### Post by Fuji_in_Japan on 2017-07-08
bump

---

