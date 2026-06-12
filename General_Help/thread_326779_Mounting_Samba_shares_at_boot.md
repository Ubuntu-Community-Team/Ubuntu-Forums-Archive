---
title: "Mounting Samba shares at boot?"
date: 2006-12-28
forum: General Help
---

### Post by sharperguy on 2006-12-28
I have two samba shares in my /etc/fstab file.

Every time I boot my computer I have to remount them with:
```

sudo mount -a

```

Is there any way I can get them to load automatically at boot.

Also this problem has only occurred in Edgy, and was fine in dapper.

---

### Post by kidders on 2006-12-28
Hi there,

Could you post the relevant lines from your /etc/fstab? It's possible that you're missing an "auto" or need to remove a "noauto".

There are other possibilities, but they're harder to pin down ... so let's start with the easy one. :-)

---

### Post by sharperguy on 2006-12-28
```

//path/to/share /path/to/folder smbfs credentials=/etc/samba/.smbpasswd,user,rw,auto,fmask=0777,dmask=0777,uid=1000,gid=100 0 0

```

---

### Post by kidders on 2006-12-29
Hmmm... anything in your system messages to indicate a problem?

---

### Post by sharperguy on 2006-12-29
not sure where you mean

but when i do "sudo mount -a" i just works with no errors.

---

### Post by kidders on 2006-12-30
I was wondering whether your system logs might show that Ubuntu tries and fails to mount your shares at boot time. It's possible that it doesn't even try, but if it does, I imagine you'd see an error message mixed in with all the other messages generated during boot.

---

### Post by Buck2348 on 2007-01-01
I have exactly the same problem.  Worked around with a small script:
```
#!/bin/bash
      sudo mount /mnt/share/myshare
```
with a line for each share.  You probably know this:  give the file a name with extension .sh, chmod +x file.sh to make it executable and put it in /etc/init.d.

I wish I could find out why it doesn't mount during boot.

Buck

---

### Post by kidders on 2007-01-01
Rather than adding an individual line for each share (which you would then have to tweak every time you made a change), you could try **mount -a -t smbfs,cifs**.

Does this problem apply only to samba shares, or are other non-local /etc/fstab entries affected also?

---

### Post by automatthias on 2007-02-05
I have this problem when the mounted shares are local. Perhaps at the time of attempt to mount the network shares samba isn't started yet?

---

### Post by featherking on 2007-02-05
Yeah i think i read about this being a bug, see a fix post by dmizer [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2002495&postcount=2")

---

### Post by Buck2348 on 2007-02-05
This worked well for me--see the fifth post.

[http://www.ubuntuforums.org/showthread.php?t=103274](http://www.ubuntuforums.org/showthread.php?t=103274)

Buck

---

