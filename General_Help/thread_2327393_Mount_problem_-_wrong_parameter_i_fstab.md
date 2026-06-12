---
title: "Mount problem - wrong parameter i fstab"
date: 2016-06-10
forum: General Help
---

### Post by dagring on 2016-06-10
Hi,

I can mount my network share, but get an error message that says: mount: /etc/fstab: parse error: ignore entry at line 14.

Line 14 is the line about the network share, and I have written:

192.168.1.6:/home/dag/Public /home/dag/public@opensuse  nfs4 rsize=8192,wsize=8192, timeou=14, intr

Can anybody give me som directions to fix this entry?

Dag R

---

### Post by yancek on 2016-06-10
It's the '@' character in fstab.  Search the forums or do an online search for using special characters in fstab.

---

### Post by dagring on 2016-06-11
I removed this caracter and changed the name of the folder, and now the fstab line reads:

192.168.1.6:/home/dag/Public /home/dag/Public   nfs4 rsize=8192,wsize=8192, timeou=14, intr

I still get the same error message

---

### Post by steeldriver on 2016-06-11
It would have been easier to spot if you'd used code tags:

```

192.168.1.6:/home/dag/Public /home/dag/Public   nfs4 rsize=8192,wsize=8192, timeou=14, intr

```

You mustn't use spaces between fstab options. Also it probably needs to be 'timeo' rather than 'timeou'

```

192.168.1.6:/home/dag/Public /home/dag/Public   nfs4 rsize=8192,wsize=8192,timeo=14,intr

```

---

