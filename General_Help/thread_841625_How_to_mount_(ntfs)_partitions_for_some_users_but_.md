---
title: "How to mount (ntfs) partitions for some users but not others"
date: 2008-06-26
forum: General Help
---

### Post by im7766 on 2008-06-26
I have a dual-boot Ubuntu/Windows PC.

I want the windows partition mounted (or mountable) for me and another user, but not for some other users.

I've read various articles about fstab and mount, but none seem to cover what I want to do. I've tried various things without success.

Ideally I would like the windows partition to appear in the "places" list and mount when clicked, for me and another user. But not appear at all, or definitely not be mountable, for the other users.

Finally, something I might want to explore in the future: is it possible that I could mount each user's Windows "profile" folder (under Documents and Settings) for each corresponding Ubuntu user?

I'd be grateful for any ideas, any links. I'm sure other people would want to do this too?

---

### Post by niyonk on 2008-06-26
system->administration->users and groups 
-then properties of the users you want 
-then their permissions untick the mounting options u want ( i am not really sure i am stuck in WinLand lol :tongue: )

---

### Post by lswb on 2008-06-26
This may help get you on the right track though I can't test it myself. Create a group that includes only the users who are allowed access to the windows partition. Change the group of the windows partition (i,e, the /dev/sdxx device entry for that partition) to that group, and change the permissions so it is rwx for root and group only. In the /etc/fstab entry for the windows partition, include the word group in the 4th field (the options field) 

For your 2nd question, I believe you can achieve this with the right combination of permissions and symlinks. One complication will be the difference between file permissions in linux and windows, but I believe there are ways to work around this even for vfat filesystems.

Again, I can't guarantee that the outline I gave above is 100% correct, but with some experimentation (or advice from someone more knowledgeable!) I'm sure you can get this working the way you want.

---

### Post by bodhi.zazen on 2008-06-26
Permissions are set on ntfs and fat at the time of mounting ...

uid = user
gid = group
umask,dmaks,fmask = set permissions

So ...

mount /dev/sdxy /media/windows -o uid=1000,gid=100,dmask=007,fmask=117

fstab entry :

/dev/sdxy /meida/windows ntfrs-3g uid=1000,gid=100,dmask=007,fmask=117 0 0

Now every member of the "users" group has access. Remove other users from teh users group or add a new group for the ntfs partition.

---

### Post by im7766 on 2008-06-28
> **bodhi.zazen said:**
> Permissions are set on ntfs and fat at the time of mounting ...
 <snip>

Thanks, this looks like just what I was looking for. But my HDD has now gone on the blink so haven't been able to try it yet.

---

### Post by Victormd on 2008-06-28
Check the link on my signature, there's a brief explanation on the permission setting as well...

---

