---
title: "[SOLVED] How to check filesystem at boot? Or other."
date: 2008-07-09
forum: General Help
---

### Post by L337_K3y5 on 2008-07-09
What I need to do is this: ```
e2fsck -f /dev/sda6
``` I need to do this check on this partition 'cause Gparted (using LiveCD) won't let me move any more file systems without doing it...It whined about needing to be root, so I logged into my normal user on the same partition, tried it, and it told me not to do it while on the partition...well I had a brainfart](*,)...How do I check this while not on the partition, like at startup when it checks it sometimes.  I don't CURRENTLY have a triple-boot, and I can't surely have Vi$ta to run this command, 'cause it can't see EXT3...Blind-@$$ piece of....well lets not go there.  Back to the point how do I? :-k

---

### Post by iaculallad on 2008-07-10
Had you tried:

```
sudo touch /forcefsck
```

---

### Post by L337_K3y5 on 2008-07-10
> **iaculallad said:**
> Had you tried:

```
sudo touch /forcefsck
```

Uhhh...what did that do, I'm guessing it happens when I restart?

---

### Post by bodhi.zazen on 2008-07-10
You can also :

```
shutdown -Fr now
```

-r = reboot
-F = force check

---

### Post by iaculallad on 2008-07-10
> **L337_K3y5 said:**
> Uhhh...what did that do, I'm guessing it happens when I restart?

If the file named /forcefsck exists, your file system will be checked at the
next boot. It will also reset the 30-mount count for your file system check.

---

### Post by L337_K3y5 on 2008-07-10
Ok...I did the system check at boot...wasn't good enough for Gparted, then I did the system check while in Live CD by putting sudo in front of the command.  It checked it, no errors right?  Well, then I tried to shrink partition 6 by 1.02GB then let the partition 5 absorb it...It would always go through with it until I get to the part when it ACTUALLY shrinks it, not the error checking.  Then looking through the details afterwards, I see that it wants me to do a ```
e2fsck -f /dev/sda6
``` before I can go through with it.  I've done a diskcheck twice......[Here's]("http://pastebin.com/m1e43f704") the link to Pastebin.

---

### Post by L337_K3y5 on 2008-07-10
I don't know what to do now to make sure Gparted knows I've done a disk check.  How do I make it notice that?:confused:

---

### Post by bodhi.zazen on 2008-07-10
what problem are you having exactly ?

---

### Post by L337_K3y5 on 2008-07-10
Ummm...To put it bluntly, whenever I do a disk check, then go into Gparted and try to move/resize a partition, it fails, and in the details it tells me to run a ```
e2fsck -f /dev/sda6
```Which is wierd 'casue it makes me think Gparted isn't seeing the disk check...?  Let me try it one more time....I'll post back later, if this time doesn't work, literally writing this going out the door.  [Here]("http://pastebin.com/m1168497a"), look at this...try figuring this out, I highlighted some areas.

---

### Post by bodhi.zazen on 2008-07-10
What happens when you :

```
sudo umount /dev/sda6

sudo e2fsck -f /dev/sda6
```

You can not check or resize a mounted partition, so if sda6 is / you need to run from a live CD.

---

### Post by L337_K3y5 on 2008-07-10
Well, I tried the above, and turns out it was never mounted whenver I did the transfer/resize/whatever.  It ALWAYS gives me the same output, did you read my report all the way through on my last post on Pastebin?

---

### Post by bodhi.zazen on 2008-07-10
Sorry, no I missed the paste bin.

/me reads ...

LOL, that is normal behavior, I do not know why, but you must run e2fsck before resize2fs. I am not sure why, but my guess would be as a "sanity check" to make sure the file system is in good health before you resize it.

:popcorn:

---

### Post by L337_K3y5 on 2008-07-10
Ummm...thanks, it finally worked after going through the check like six times (literally).  Well, guess Gparted is picky as crap, lol.

---

