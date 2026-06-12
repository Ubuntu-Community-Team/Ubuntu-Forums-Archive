---
title: "fstab help"
date: 2005-10-19
forum: General Help
---

### Post by Ocxic on 2005-10-19
i put this in my fsatb:
/dev/hdb1       /home/admin/Desktop/120GB_Storage   ext3    defaults   0      0
and now although it did mount it, I cannot use the drive at all, i "do not have permission" to do anything

---

### Post by Miguel on 2005-10-19
A quick answer. On the options, try putting :
```

defaults,uid=xxx,gid=yyy

```
Where xxx is the user ID and yyy is the group ID you want to own the mount. You can find your UID in System->Administration->Users and Groups.

If this doesn't work or if you need more help, plese ask.

Miguel

---

### Post by Ocxic on 2005-10-19
[QUOTE=Miguel]A quick answer. On the options, try putting :
```

defaults,uid=xxx,gid=yyy

```
Where xxx is the user ID and yyy is the group ID you want to own the mount. You can find your UID in System->Administration->Users and Groups.

If this doesn't work or if you need more help, plese ask.

Miguel[/QUOTE]
 k, my line looks like this now:
/dev/hdb1       /home/admin/Desktop/120GB_Storage   ext3    defaults,uid=1000,gid=1000   0      0
and it wasn't able to mount it

---

### Post by Miguel on 2005-10-19
What were your error messages? Maybe that HD is not formated in ext3 (it won't, unless you have formatted it by yourself). 

Or maybe I was plain wrong. What about "rw,user,uid=1000,gid=1000"?

---

### Post by Ocxic on 2005-10-19
[QUOTE=Miguel]What were your error messages? Maybe that HD is not formated in ext3 (it won't, unless you have formatted it by yourself). 

Or maybe I was plain wrong. What about "rw,user,uid=1000,gid=1000"?[/QUOTE]


I mounted it b4 and formated it myself i know it worls i will try your suggestion and get back to you

---

### Post by Ocxic on 2005-10-19
ok, I added the "defaults,rw,user" and removed the uid & gid cause they didn't seem do do anything but make it not work, so now it mounts but i still can't do anything, i looked at the permissions and it says the owner/group is root
/dev/hdb1       /home/admin/Desktop/120GB_Storage   ext3    defaults,rw,user   0      0

---

### Post by Miguel on 2005-10-19
Thanks for your quick answer. So everything in that line is alright (Try navigating through using sudo su, but don't forget to exit!!).

Are you the only user of your PC? Because you will need to have all permissions at /home/admin/Desktop (this will only happen if you are "admin" user or if you are in a group with permissions enabled there). Other thing: maybe your gid is 100 and not 1000 (group users instead of group admin). As you see, permissions and users are the things I would check many times in this case.

I was going to suggest the use of umask, but that is a vfat only option.

As an example, and just in case it works, my fat32 partition line in fstab looks like:
```

/dev/hda5       /fat32          vfat    defaults,user,uid=1000,gid=100,rw        0       0

```
Where /fat32  was a directory created by root and chowned to miguel:users.

Alternatively, you can create a directory in / (let's say /other-disk) with sudo, chown and mount your hdb there. You could have a link in your Desktop with a symlink:

```

cd /home/admin/Desktop
ln -s /other-disk/ .
mv other-disk 120GB_Storage

```

---

### Post by Ocxic on 2005-10-19
I tryed your other option and it worked, but i'd rather not have to do it manually every time i boot. I mad a folder /mnt/120GB_Storage and used chmod to give me permission to access it. can i just add
/dev/hdb1 /mnt/120GB_Storage ext3 defaults 0 0
to my fstab and have it work???

---

### Post by Miguel on 2005-10-19
What you did should work now. AFAIK, any partition in fstab will mount unless "noauto" has been specified as an option. You shouldn't need to change anything more. 

BTW: What did you add to your fstab file?

---

