---
title: "System hangups--How can I pinpoint them?"
date: 2008-03-05
forum: General Help
---

### Post by Front187 on 2008-03-05
All day today I have been have ~30 second system hangups.  My screen becomes completely locked, but my mouse can still move.  

Being new to linux, I'm not exactly sure if there is a good place to start looking for answers.

Any tips?

EDIT:

I should really search more before posting.

Found the logs dir at /var/logs

Check kern.log and found
```
Random freezes with "exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2" error
```

googled the above, returned this solution:

```


I've solved the problem editing /etc/initramfs-tools/modules, and adding this lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

after editing:

sudo update-initramfs -u

after reboot I have my hard disks with the old fashioned /dev/hd*, without bugs!!!:)

```

---

### Post by pr0grammer1 on 2008-03-05
Was this by chance for an IDE drive? Because my SATA-based system gives me a kernel panic on boot after doing this...

---

