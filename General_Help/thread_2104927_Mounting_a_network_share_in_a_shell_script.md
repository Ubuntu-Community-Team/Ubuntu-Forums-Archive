---
title: "Mounting a network share in a shell script"
date: 2013-01-14
forum: General Help
---

### Post by choppyfireballs on 2013-01-14
Hello, I'm currently trying to write a .sh script that will mount a network share, copy a file, and then unmount the network share.

I'm using 

mount -t cifs "*path/to/network/share/here*" "*path/to/mnt/here*"

cp "* Filename/to/copy *" "* /Filename/destination/ *"

umount "* path/to/mnt/here*"

The problem I'm running into is that it's asking for system password when the script runs, I want it to run automatically using a statement inserted into crontab -e.

---

### Post by SeijiSensei on 2013-01-14
Use a "credentials" file.  See "man mount.cifs" for details.  Basically you put two lines in a file

```

username=your_username
password=your_password

```

then reference it with "-o credentials=/path/to/file" in the mount command.  Make sure the file has 700 permissions and is owned by root so that others cannot read the password.

---

### Post by choppyfireballs on 2013-01-14
Thank you worked like a charm, will mark thread as solved.

---

