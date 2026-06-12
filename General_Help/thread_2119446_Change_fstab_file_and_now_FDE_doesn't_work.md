---
title: "Change fstab file and now FDE doesn't work"
date: 2013-02-23
forum: General Help
---

### Post by iamnoahc on 2013-02-23
I recently changed my fstab file by taking the part of the line that read like this:

```
errors=remount-ro 0
```

and changed it to:

```
errors=remount-ro, ,barrier=0 0
```

Now I can't get logged in to the full disk encryption. 

I had just got done doing some tax work and I'd hate to have to redo it, however, I should have a fairly recent backup.

How screwed am I ? Is there anyway to get back in there and recover at least the tax documents?

---

### Post by papibe on 2013-02-23
Hi iamnoahc.

If you boot into recovery mode, you'll boot into a minimalistic environment, and only using the root (/) partition.

You may need to remount the / partition by doing:
```
mount -o rw,remount /
```
Then you'll be able to edit the fstab:
```
nano /etc/fstab
```
Here's a [tutorial]("http://www.psychocats.net/ubuntu/resetpassword") that explains the details. Although it is for a different concern, all the important points are there.

Let us know how it goes.
Regards.

---

### Post by iamnoahc on 2013-02-23
The problem is that with full disk encryption I can't even get that far. I keep trying to type in my password and it says "no key available with this passphrase" even when I boot into recovery mode.

I have access to the much of unencrypted filesystem (not just /home). So if I could somehow copy the file via liveCD or something like that would that be a possibility?

---

### Post by papibe on 2013-02-23
I've never had to deal with this kind of problem, but yes, if I were you, I'd try to mount the root partition using the live CD.

It should ask you the passphrase in order to mount it. [This]("http://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line") may be useful in case you are not able to mount it using the GUI.

Let us know how it goes.
Regards.

---

### Post by iamnoahc on 2013-02-24
I've made some progress:

```
xubuntu@xubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 encrypt
Enter passphrase for /dev/sda5: 
Cannot use device /dev/sda5 which is in use (already mapped or mounted).
```

Above I type in my password and I get the error. Below I type in gibberish and I get the no key available error. This confirms that I have not in fact forgotten my password.

```
xubuntu@xubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 encrypt
Enter passphrase for /dev/sda5: 
No key available with this passphrase.
```

Any thoughts on where to go from here to recover my files? Why I try to open it via the GUI in a live cd it says "Failed to Mount. The Given volume was not found" but as you can see above it's already mapped or mounted.  Any thoughts?

---

### Post by iamnoahc on 2013-02-24
I am a moron. I setup a new machine today and somehow set the password on that to use shift when I didn't use shift on this machine and that must have reset my muscle memory.

Once I confirmed what the password is supposed to be, I was able to type it in.

---

