---
title: "Back In Time Erros: [E] Error: rsync: symlink ... -&gt; &quot;/proc/mounts&quot; failed: Permissio"
date: 2016-01-02
forum: General Help
---

### Post by DB4711 on 2016-01-02
Hello,

I have a problem with Back In Time and am not sure where to look for a solution.

Data is backed up on my Synology NAS. The networkshare is mounted in /home/username/NAS/Backup via fstab:

//NAS.local/Backup /home/username/NAS/Backup cifs credentials=/home/username/.credNAS2 0 0

User for mount has read/write on that share.

Back In Time is started with root and folder to backup are etc and home.

In Back in Time I get errors like this:

[E] Error: rsync: symlink "/home/username/NAS/Backup/Back In Time/backintime/N53SN-Ubuntu/root/1/new_snapshot/backup/etc/mtab" -> "/proc/mounts" failed: Permission denied (13)

[E] Error: rsync: symlink "/home/username/NAS/Backup/Back In Time/backintime/N53SN-Ubuntu/root/1/new_snapshot/backup/home/username/.wine/dosdevices/c:" -> "../drive_c" failed: Permission denied (13)

[E] Error: rsync: symlink "/home/username/NAS/Backup/Back In Time/backintime/N53SN-Ubuntu/root/1/new_snapshot/backup/etc/ssl/certs/a15b3b6b.0" -> "Digital_Signature_Trust_Co._Global_CA_3.pem" failed: Permission denied (13)

I can't see any problems with data in e.g. a self created folder in my home directory.

Does someone an idea where the problem could be?

Thanks a lot!

---

### Post by Germar on 2016-01-03
Your destination samba server doesn't allow to set symlinks (which would be an [security issue]("https://www.samba.org/samba/news/symlink_attack.html") otherwise). You can either activate ```
wide links = yes
``` in your smb.conf or rather don't use samba at all.

Better use BackInTime with SSH-mode. It's a lot faster than syncing to a mounted share!

Please read our [FAQ on how to enable your Synology NAS]("https://github.com/bit-team/backintime/wiki/FAQ#how-to-use-synology-dsm-5-with-bit-over-ssh") for this.

[SIZE=1]Disclaimer: I'm the current MainDev of BIT[/SIZE]

---

