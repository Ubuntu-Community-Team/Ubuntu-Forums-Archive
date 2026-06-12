---
title: "Nautilis network share mount location"
date: 2019-11-19
forum: General Help
---

### Post by yaminb on 2019-11-19
Hi all,

I've found the best way for me to mount network shares is to use Nautilis.
Yet, sometimes, I'd like to writes scripts or whatever that uses the share location.

Does anyone know how consistent the share location will be?

For example, I can see my current share location shows as:
```

run/user/1000/gvfs/smb-share:server=diskstation.local,share=media
/run/user/1000/gvfs$ ls
'smb-share:server=diskstation.local,share=media'
'smb-share:server=diskstation.local,share=video'

```

Will this location stay the same across reboots, password changes...?

I know that if the password changes or I choose not to save the pw, I will have to login initially using nautilis.
But once that initial login is done, the location should be the same?

The main part that concerns me ir the 1000. I don't know where that comes from. The rest looks like it should be the same.

---

### Post by jetsam on 2019-11-19
If you don't need dynamic behavior, consider using fstab for permanently mounting your shares.  Here's a general introduction page:
[Introduction to fstab]("https://help.ubuntu.com/community/Fstab")

I'm rusty on this, but can answer further questions if you have them.  Samba was one of my bags on the Ubuntu forums for about year a long time ago, before everything had a gui and did things for you.

---

### Post by Morbius1 on 2019-11-19
The gvfs mount point is consistent but it depends on who is mounting the share. This goes with your other question about 1000.

The 1000 is you. It's your user id ( uid ) number. Run this command:
```
id
```
In the output you should see something like:
> uid=1000(your user name)

And the permissions by design of /run/user/1000 is 700 so only that user can traverse the directory to get to the actual mount point.

---

### Post by yaminb on 2019-11-19
> **Morbius1 said:**
> The gvfs mount point is consistent but it depends on who is mounting the share. This goes with your other question about 1000.

The 1000 is you. It's your user id ( uid ) number. Run this command:
```
id
```
In the output you should see something like:


And the permissions by design of /run/user/1000 is 700 so only that user can traverse the directory to get to the actual mount point.

Thanks!

---

