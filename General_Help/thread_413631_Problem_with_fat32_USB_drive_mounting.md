---
title: "Problem with fat32 USB drive mounting"
date: 2007-04-19
forum: General Help
---

### Post by jessegillies on 2007-04-19
I am using Feisty and I have two drives that are formatted to fat32. When I plug them in, they mount, but the permissions on both are set to 700. After seeing [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131), I realized that umask=077 sets permissions to 700 on vfat filesystems. I checked hal-mtab and that is exactly what umask is set to for both drives. Is there any way to change this so I can have the proper permissions set?

---

### Post by kidders on 2007-04-20
Hi there,

There isn't really any such thing as "proper" permissions, since FAT filesystems don't support them. If you would like to override the default "sensible" umask, the easiest place to do it is in /etc/fstab. You might like to take a look at **mount**'s man page for details on mount options like "dmask" and "fmask".

The default behaviour for filesystems with no access control support is usually to deny access to all users except the one that mounted the device in question. You can do whatever you want though. :-)

---

### Post by jessegillies on 2007-04-21
ok, thanks for that info. what i'm trying to do is to run a script that takes a file from my portable mp3 player, which is formatted as fat32, and insert the contents of the file into the mysql server that is running on my machine. when i run the script after the drive is mounted automatically, the file can't be accessed by the script. however, when i mount it manually, everything works fine. any suggestions on how i might be able to get this to work?

---

### Post by kidders on 2007-04-22
Hey again,

> **jessegillies said:**
> what i'm trying to do is to run a script that takes a file from my portable mp3 player, which is formatted as fat32, and insert the contents of the file into the mysql serverYikes! Are you sure that's wise?

> **jessegillies said:**
> when i run the script after the drive is mounted automatically, the file can't be accessed by the script.This may be because automatic mounts are being performed by root, but it's impossible to know without a little more information. How do the mount options *you* use to mount the device manually compare to those used automatically by Ubuntu?

---

### Post by jessegillies on 2007-04-22
Well, I guess I'm not sure that it's wise. The port for the MySQL server is blocked on my firewall, and the data is used by a web server that is only locally-accessible. What might be dangerous about this?

If I were to add the drive to fstab, I would set umask to 022, with the owner being me, and the group being *users*.

Thanks again for your help.

---

### Post by kidders on 2007-04-22
Hiya,

> **jessegillies said:**
> Well, I guess I'm not sure that it's wise. The port for the MySQL server is blocked on my firewall, and the data is used by a web server that is only locally-accessible. What might be dangerous about this?Sorry... I really should've been clearer about what I meant. I was just wondering whether putting entire files into a database is an efficient way of organising data. I had no business mentioning that really ... it's miles off topic hehe.

> **jessegillies said:**
>  If I were to add the drive to fstab, I would set umask to 022, with the owner being me, and the group being *users*.Oh I see ... you you *know* you can add entries to your /etc/fstab to prevent the problem from arising in the first place ... you just don't want to do that? (I have to say, I like to do things that way too, in general :-) )

The file you're looking for is probably **/etc/hal/fdi/policy/preferences.fdi** ... there should be examples in there that demonstrate how to fiddle with mount options, depending on some criteria. That would let you impose "chmod 755" permissions on hotplugged devices in a more general way than /etc/fstab can.

To be honest however, I would probably use neither approach in this case ... but only because I'm making the assumption that you are only interested in overriding the default mount options for this specific device, for the purposes of one specific script. (That's just me though!) From a design perspective, you could argue that a script that doesn't require special system modifications is a better script hehe.

---

### Post by jessegillies on 2007-04-22
OK, thanks again. I'll look into that configuration file.

---

