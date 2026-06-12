---
title: "/etc/group and sudoers problem"
date: 2006-11-22
forum: General Help
---

### Post by eXistenZ.online on 2006-11-22
Hi,

I know it is stupid, but the problem is simple. I wanted to add a new user to the sudo group in /etc/group, but I forgot to add a : to the end of my name. 

Addition to this, I opened the sudoers file with vi, not /usr/sbin/visudo. The problem is, the system says I'm or somebody not in the sudoers group, so I could not sudo anything (fix /etc/group, sudoers, etc.) How can I fix that problem without installing the entire system?

Thanks for the help. :(

---

### Post by krismatth3 on 2006-11-22
Hehe, visudo has saved me a couple of times. You'll have to boot with the livecd, mount your root partition and manually editor /etc/sudoers. :/

---

### Post by taurus on 2006-11-22
Or boot into recovery mode from GRUB menu and either correct your /etc/group or edit your /etc/sudoers with visudo, NOT vi...

---

### Post by DaveBorealis on 2006-11-22
> **taurus said:**
> Or boot into recovery mode from GRUB menu and either correct your /etc/group or edit your /etc/sudoers with visudo, NOT vi...
Hello taurus,

Would the backup copy in '/var/backups' have been updated with the misconfigured one, or is that a possibility to replace the dodgy one in '/etc'?  (I notice that my 'group.bak' is three days old, and as far as I know I haven't installed anything for several days that would have added anything to '/etc/group'.)

Best regards,
Dave

---

### Post by taurus on 2006-11-22
If you are not sure you created it, better check.  You can compare the backup file with the current file by using the diff command.  They should be almost the same...

```
diff <first file> <second file>
```

---

### Post by DaveBorealis on 2006-11-22
> **taurus said:**
> If you are not sure you created it, better check.  You can compare the backup file with the current file by using the diff command.  They should be almost the same...

```
diff <first file> <second file>
```

Thanks for the reply.  And yep, the files were identical.  And instead of being three days old (2006-11-19) it was actually a month and three days.  I misread the date of '2006-10-19'.

So, could the OP use his '/var/backups/group.bak' to replace '/etc/group' and get back to square one?  Or would the backup copy be overwritten right away when the '/etc/group' was changed?

---

