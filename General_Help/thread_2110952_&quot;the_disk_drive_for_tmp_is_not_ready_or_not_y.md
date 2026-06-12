---
title: "&quot;the disk drive for /tmp is not ready or not yet present&quot;"
date: 2013-01-31
forum: General Help
---

### Post by nomike on 2013-01-31
I've boostrapped 3 machines, identical Hardware, with Netinstall and installed "ubuntu-desktop" and "xubuntu-desktop" packages afterwards.

Every time the boot, I get the message
"""the disk drive for /tmp is not ready or not yet present

Continue to wait; or press S to skip or M for manual recovery"""

Sometimes it disappears after a ~3 seconds but sometimes it takes 1min < time < 2min to continue booting.

When I press "M" I'm prompted for the root password. I could now cd to "/tmp". When I do "ls" now it spills my terminal full with aprox. thousands of entries constisting of aprox. 10 alphanumeric (or hex, dunno) characters. During the list it regularly hangs for a second or two.

After a short time, when I do "ls" again, I see an empty directory.

When I press "S" instead the system continues to boot and I'm able to login to the console and can see the same issues with files misteriously appearing and vanishing.

When the time's up and the files are gone, I could login to desktop just fine, but while files are there I get errors originating on not being able to create tempfiles in "/tmp".

My Root-FS is ext4 on LVM and I don't have anything mounted on "/tmp". "/tmp" is a plain directory residing on "/".

I have absolutely no clue what's wrong there. I couldn't find posts about that problem in google or on this forum.

If there are any additional Info's i could provide to help hunting down this problem please let me know.

Do you have any recommendations for me?

I tried to rebootstrap the boxes but this didn't make any difference.

I don't know if it's relevant but I use SSD-Disks in the machines.

Thx!

cheers
nomike

---

### Post by poisonkiller on 2013-02-06
I have the same problem and have had it since I installed Kubuntu (selected home to be encrypted) last summer. No /tmp in fstab, so maybe the problem is in the encryption mechanism?

---

### Post by Stonecold1995 on 2013-02-07
If an entry for /tmp is not present in /etc/fstab, try adding this to the bottom of the file, then rebooting:
```
tmpfs            /tmp           tmpfs   defaults,mode=1777  0       0
```

This is from *my* /etc/fstab, so it's a little different than the default entry (i.e. it places /tmp in RAM, so only do this if you have enough memory), but it should work.

Print the output of ```
cat /etc/fstab
```

---

### Post by davea88 on 2013-02-21
I get the same message when I do a Restart after installing
a kernel update. 
  
By shutting down the machine, waiting 30 seconds,
and restarting using the power button, the restart does
not show the message and all seems fine. This on two
desktop-class machines, one with 32bit kernel, 
one with 64bit kernel.  Both running xfce4.
Disks not encrypted.

---

### Post by alexsmith on 2013-05-10
+1

I have the same issue as davea88 described. Couldn't it be a result of hard disk waste (old disk, for example)?

Any news on this?

---

