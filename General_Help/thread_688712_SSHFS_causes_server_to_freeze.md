---
title: "SSHFS causes server to freeze"
date: 2008-02-05
forum: General Help
---

### Post by snafle on 2008-02-05
I'm trying to use sshfs to xfer files from my desktop to my laptop, but it's not working as well as I'd hope. It goes very well up until [x] (where x is a random integer) files are copied, at which point the desktop freezes totally- no gui response, no consoles (ctrl alt) or remote logins. Only option is a reboot. 

Any ideas?

---

### Post by kuja on 2008-02-05
Perhaps you can mount it with the "-o sshfs_debug"  option, and see if it yields any useful debugging output?

---

### Post by snafle on 2008-02-05
Certainly, will do it tomorrow.

---

### Post by snafle on 2008-02-08
Ran it with -o sshfs_debug. It output "Server version 3" in the console, so I started copying files over. After 100 mp3s had gone the server froze, and there was nothing new on the debug console.

---

### Post by snafle on 2008-02-09
I tried changing the network cards, to no avail. I'm seriously considering going back to windows 2003- I had to reboot it every week, but at least I could copy a few files and have it actually work.

Does anyone at least have any ideas where to look, I've googled it and just found people with the same problem but no solution.

---

### Post by snafle on 2008-02-09
I'm going to get samba working on the machine, then I'll be able to see whether it's a big file transfer that mucks it up or actually ssh/sshfs. I had a look in syslog, but there's nothing of interest there so I have a suspiscion it might not be the right place- I'm going to work out what tcpdump and have a look in that.

[EDIT] Just realised I should have been editing my posts to make it all neater, oh well. 

I got Samba working, tried to transfer a file and it died around ~ 100 meg into the copy. It definitely seems like a network issue, but I have no problems getting +100meg files of the intertubes using apt and, thinking it was a NIC problem, I've swapped those round. If anyone can help it'll be cool.

---

### Post by snafle on 2008-02-13
Reinstalled, no luck. I've just compiled the latest kernel on a fresh install- no luck. I'm kinda at a loss here- it's not drivers, since I've used several network cards with different chipsets, it's not the kernel (well, it could be, but on a bugzilla bug I found the same problem was fixed by a kernel update) since I've got the latest one going, it's not ssh since samba locks up as well.

Could it be that I'm trying to copy off an NTFS disc? I'll test it later today of the ext3 partition.

---

### Post by snafle on 2008-02-13
Welp, decided to quite with ubuntu on the server. DLing Desktop BSD to give that a shot, and I've got my trusty 2003 server disc lying about. Might give it another go when 8 comes out.

---

