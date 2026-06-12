---
title: "unable to open System/Administration/Users and Groups"
date: 2008-06-04
forum: General Help
---

### Post by Master Chief on 2008-06-04
I am using Ubuntu 8.04 and I am unable to open:
System | Administration | Users and Groups

sudo also fails, and I can no longer install software/updates.

I don't know where to start, and don't want to re-install (obviously) but I need help with this new situation for me so...any help would be great. Thanks.

---

### Post by tespio on 2008-06-04
I had the same problem try removing your domain name
in system>administration>network (under the general tab)
Also under the host tab try to remove the .something extension to your computer's name host(computer-name.domain-name[in this case only remove.domain-name])
It fixed it for me

---

### Post by drs305 on 2008-06-04
First, check to see if your /etc/hosts file has changed. It may be corrupted.

```
cat /etc/hosts | grep 127.0.1.1
```

If you dont see "127.0.1.1 yourcomputername"

```

sudo cp /etc/hosts /etc/hosts.bak
gksudo gedit /etc/hosts
```

Make the 127.0.1.1 look like this:
```
127.0.1.1 your_computers_name
```

---

### Post by iaculallad on 2008-06-04
Add your username to the /etc/sudoers file:

```
sudo gedit /etc/sudoers
```

then add your username at the bottom of the file:

**username ALL=(ALL) ALL**

That should do the trick.

OR:

%admin ALL=(ALL) ALL

---

### Post by Master Chief on 2008-06-04
Turned out to be a corrupt/damaged /etc/group file (I had a mysterious /etc/.group.edit.swp file which I :restored)

I started in server maintenance mode and used "vigr" to fix (read add username for admin group) and next "shutdown -r now" and I can open System/Administration/Users and Groups again (The unlock button works again).

Note: My brother did something to wack my Intel HD Sound card because that also vanished. Seems like I have even more work to do (:

Thanks all!

---

