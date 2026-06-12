---
title: "Cannot remove snap file &quot;firefox&quot;, will retry in 3 mins: unlinkat /snap/firefox/1969/"
date: 2023-02-24
forum: General Help
---

### Post by marietto2008 on 2023-02-24
Hello.

I&#8217;m trying to remove the snap &#8220;firefox&#8221; on Ubuntu 22.10. Unfortunately an error prevents the task from being completed.

```
# snap list

Nome               Versione          Rev    Tracciamento     Publisher   Note

bare               1.0               5      latest/stable    canonical?  base
core               16-2.58.2         14784  latest/stable    canonical?  core
core18             20230207          2697   latest/stable    canonical?  base
core20             20230126          1822   latest/stable    canonical?  base
firefox            106.0-1           1969   latest/stable/?  mozilla?    -
gnome-3-38-2004    0+git.6f39565     119    latest/stable    canonical?  -
gtk-common-themes  0.1-81-g442e511   1535   latest/stable    canonical?  -
hello-world        6.4               29     latest/stable    canonical?  -
snap-store         41.3-66-gfe1e325  638    latest/stable    canonical?  -
snapd              2.58.2            18357  latest/stable    canonical?  snapd
```

when I invoke Firefox,it starts correctly. At this point,I tried to remove the snap firefox like this :

```
# snap remove --purge firefox
```

but it does not want to do it :

```
errore: cannot perform the following tasks:
- Rimuovi i dati per lo snap "firefox" (1969) (unlinkat /var/snap/firefox/common/host-hunspell/en_US.aff: read-only file system)
```

I've found this helpful question :

Completely remove firefox snap package

So,this is what I did :

```
root@marietto-BHYVE:/etc/systemd/system# lsblk -fe7 -o+ro

NAME FSTYPE FSVER LABEL UUID                                                         FSAVAIL FSUSE%   MOUNTPOINTS                     RO

vda                                                                                                                                                                                                   0
--vda1
        vfat             FAT32              A17A-EEFA                                                504,9M     1%   /boot/efi                                             0
--vda2
        ext4            1.0                   2e254150-7969-4cbb-bf4c-9b9e0bf9ef64  160,8G    13%  /var/snap/firefox/common/host-hunspell
                                                                                                                                  /                                                         0

# sudo systemctl stop var-snap-firefox-common-host\\x2dhunspell.mount

Warning: The unit file, source configuration file or drop-ins of var-snap-firefox-common-host\x2dhunspell.mount changed on disk. Run 'systemctl daemon-reload' to reload units.
root@marietto-BHYVE:/etc/systemd/system# systemctl daemon-reload


root@marietto-BHYVE:/etc/systemd/system# lsblk -fe7 -o+ro

NAME FSTYPE FSVER LABEL UUID                                                         FSAVAIL FSUSE%   MOUNTPOINTS                     RO

vda                                                                                                                                                                                                   0
--vda1
        vfat             FAT32              A17A-EEFA                                                504,9M     1%   /boot/efi                                             0
--vda2
        ext4            1.0                   2e254150-7969-4cbb-bf4c-9b9e0bf9ef64  160,8G    13%  /    

root@marietto-BHYVE:/etc/systemd/system# snap remove firefox

2023-02-24T14:06:57+01:00 ERROR cannot remove snap file "firefox", will retry in 3 mins: unlinkat /snap/firefox/1969/data-dir: read-only file system.  

```

---

### Post by monkeybrain20122 on 2023-02-25
Instead of becoming root, which is a bad idea in most cases anyway.

```
sudo snap remove --purge firefox
```

---

### Post by DuckHook on 2023-02-25
Yes, you've found the solution. After FF went to snap, they had to use a workaround to get it to work with the spelling dictionary. The workaround was to mount hunspell into the snap post install.

I removed the snap version of FF almost from the beginning, so am unfamiliar with the problems that people might run into trying to uninstall it. The need to first decouple hunspell is not surprising.

---

### Post by TenPlus1 on 2023-02-27
So many workarounds just to get snap apps to work properly, why couldn't they just use the Firefox .deb from mozilla themselves.

---

### Post by DuckHook on 2023-02-27
> **TenPlus1 said:**
> So many workarounds just to get snap apps to work properly, why couldn't they just use the Firefox .deb from mozilla themselves.
It was the Mozilla devs who asked for Firefox to be made a snap. This was not a Canonical initiative.

These requests/comments might be more effective if redirected to Mozilla.

---

