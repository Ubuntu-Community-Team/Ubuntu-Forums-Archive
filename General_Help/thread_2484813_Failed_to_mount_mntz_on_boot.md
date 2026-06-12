---
title: "Failed to mount /mnt/z on boot"
date: 2023-03-10
forum: General Help
---

### Post by stevermann on 2023-03-10
I have a drive on an Intel NUC (running Ubuntu 20.04) that is acting as a file server for the household. (Drive Z)
Here are the lines in smb.conf:
```
[z]
   comment = Z Public folder
   path = /home/steve/z
   create mask=0777
   directory mask=0777
   read only = no
   browsable = yes
   guest ok = yes
   force group = steve
   force user = steve

```

In another computer also running Ubuntu 20.04, I mount the share in fstab:
```
#Share on Zeus, (Mapped as drive Z on the PC)
//192.168.1.70/z /mnt/z cifs nofail,iocharset=utf8,_netdev,  0  0

```

Here's my problem.  The share does not mount on start or reboot, but ```
sudo mount -a
``` does mount it without error.

Here is the startup error:
```
 sudo journalctl -b -p err
Mar 10 19:13:52 BMAX-mini kernel: x86/cpu: SGX disabled by BIOS.
Mar 10 19:13:56 BMAX-mini kernel: sof-audio-pci-intel-apl 0000:00:0e.0: error: tplg request firmware intel/sof-tplg/sof>
Mar 10 19:13:56 BMAX-mini kernel: sof-audio-pci-intel-apl 0000:00:0e.0: you may need to download the firmware from http>
Mar 10 19:13:56 BMAX-mini kernel: sof-audio-pci-intel-apl 0000:00:0e.0: error: failed to load DSP topology -2
Mar 10 19:13:56 BMAX-mini kernel: sof-audio-pci-intel-apl 0000:00:0e.0: ASoC: error at snd_soc_component_probe on 0000:>
Mar 10 19:13:56 BMAX-mini kernel: sof-essx8336 sof-essx8336: ASoC: failed to instantiate card -2
Mar 10 19:13:56 BMAX-mini kernel: sof-essx8336 sof-essx8336: snd_soc_register_card failed: -2
Mar 10 19:14:02 BMAX-mini kernel: CIFS: VFS: Error connecting to socket. Aborting operation.
Mar 10 19:14:02 BMAX-mini kernel: CIFS: VFS: cifs_mount failed w/return code = -101
Mar 10 19:14:02 BMAX-mini systemd[1]: Failed to mount /mnt/z.

```

Any tips of what I am doing wrong would be appreciated.

---

### Post by MAFoElffen on 2023-03-11
Try this:
```

#Share on Zeus, (Mapped as drive Z on the PC)
//192.168.1.70/z /mnt/z cifs nofail,iocharset=utf8,x-systemd.device-timeout=9,_netdev  0  0

```
Or this
```

//192.168.1.70/z /mnt/z cifs nofail,iocharset=utf8,x-systemd.after=network-online.target,_netdev 0 0

```

---

### Post by stevermann on 2023-03-12
> **MAFoElffen said:**
> Try this:
```

#Share on Zeus, (Mapped as drive Z on the PC)
//192.168.1.70/z /mnt/z cifs nofail,iocharset=utf8,x-systemd.device-timeout=9,_netdev  0  0

```
Or this
```

//192.168.1.70/z /mnt/z cifs nofail,iocharset=utf8,x-systemd.after=network-online.target,_netdev 0 0

```


Thanks, but neither helped.  Same error in journal.
I can't find anything about error -101, but I am wondering if the fact that there is no user/password (anyone on the net can read/write to the share) might be contributing to the error?

---

### Post by MAFoElffen on 2023-03-12
I was wondering about that... On mine, (years ago,) instead of using the username and pasword in the fstab... I used a credential file that i pointed to and read.

---

### Post by Morbius1 on 2023-03-12
> //192.168.1.70/z /mnt/z cifs nofail,iocharset=utf8,_netdev**[COLOR="#FF0000"],[/COLOR]**  0  0
Is that a typo - the comma after _netdev? Shouldn't be there.

I think you would be better off replacing **_netdev** with **noauto,x-systemd.automount**:

> //192.168.1.70/z /mnt/z cifs nofail,iocharset=utf8[COLOR="#FF0000"],noauto,x-systemd.automount[/COLOR]  0  0

And technically, if you want to access a share that allows guest access you should pass the **guest** option as well:

> //192.168.1.70/z /mnt/z cifs [COLOR="#FF0000"]guest[/COLOR],nofail,iocharset=utf8[COLOR="#FF0000"],noauto,x-systemd.automount[/COLOR]  0  0

And lastly(?) unless you want a read only mount you need to at least take posession of the mount so you need to add something like **uid=stevermann** to the list:
> //192.168.1.70/z /mnt/z cifs [COLOR="#FF0000"]guest,uid=stevermann[/COLOR],nofail,iocharset=utf8[COLOR="#FF0000"],noauto,x-systemd.automount[/COLOR]  0  0

---

### Post by MAFoElffen on 2023-03-12
Thank you **Morbius1**. You are "who" helped me over a decade ago on a NAS smb mount I was pulling my hair out on. LOL

---

