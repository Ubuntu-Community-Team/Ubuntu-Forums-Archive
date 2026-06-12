---
title: "noble: FileZilla randomly crashes all the time"
date: 2024-02-26
forum: General Help
---

### Post by luckyknight on 2024-02-26
Using 24.04 and up to date as of posting (26/02/2024)
Using FileZilla 3.66.5 it randomly crashes all the time while trying to drag files across via sFTP.
There is also some random graphic corruption in the last hand side, with folder names appearing over others.
I've enabled logging as per FileZilla bug trac but it doesn't provide anything useful, the log just ends when the file starts uploading.

Anyone else experienced such issues?

Hardware is ASUS ROG Zephyrus G14 (2022)

---

### Post by lindengill1967 on 2024-04-27
Same here. Same version of FileZilla from the noble repository. When uploading the file copy starts but FileZilla just closes, leaving a 0B file on the destination. SFTP and FTP uploads only - downloads are fine. Tested with 3 destinations. No clues in the logs.

I, also, can only find older reports that are probably irrelevent to this.

*EDIT*

I think this may be permission related. I've just added the latest repo and 3.67.0 crashes out too. The portable 3.67.0 version works just fine.

---

### Post by corradoventu on 2024-05-01
[https://trac.filezilla-project.org/ticket/13056](https://trac.filezilla-project.org/ticket/13056)

---

### Post by TheFu on 2024-05-01
Almost any Linux file manager supports sftp.  Why use filezilla?  I'm curious.  Is this just left over from using *that other OS*?

Nautilus, PCManFM, Thunar, all support sftp in the URL and if you setup ssh-keys, it will be seamless access once the ssh-keys/-certs are unlocked.  The same ssh-keys/-certs work for everything ssh-related.  Just use **ssh-copy-id** to push the public key to each remote server.  Additionally, the ~/.ssh/config file is also honored, so you'll not need to remember any foreign IPs or odd usernames anymore either.

Just a suggestion. Ignore it if you like.  These capabilities aren't new. They've been around over 10, perhaps 20 yrs in the file managers.

---

### Post by Irihapeti on 2024-05-04
*Thread moved to General Help, as Noble has been released.*

---

