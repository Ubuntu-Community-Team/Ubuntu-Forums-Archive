---
title: "find breaks on .gvfs directory"
date: 2008-05-04
forum: General Help
---

### Post by spudtheimpaler on 2008-05-04
Hi all.

I've searched the forums for a while and found plenty of problems with gvfs, but none seem to address the issue I'm facing.

when running find in a particular way there is an error reading the ~/.gvfs directory and find bombs.

For example:
```
sudo find / -name '.*something.*'
find: /home/myboxoftricks/.gvfs: Permission denied
```

A couple of points:
[LIST][*]doesn't happen without the sudo
[*]doesn't happen without the -name
[*]shockingly, doesn't happen when ~/.gvfs isn't on the search path...[/LIST]

so basically when .gvfs in on the search path, and you use sudo and the name switch, find bombs.

I was wondering if anyone else had this, or if it was local to my machine (which apart from a few package installs is a clean Hardy install), and if there is any way around it.

Thanks!

Mitch.

---

### Post by spudtheimpaler on 2008-05-07
Can someone else please test this for me? It will only take 2 seconds! :)

---

### Post by pmorton on 2008-05-11
> **spudtheimpaler said:**
> Can someone else please test this for me? It will only take 2 seconds! :)

I've come across the same problem, and I've seen it reported with Fedora. It seems to be a Gnome glitch. It's an irritation when your attempts to  find something as root get curtailed for no apparent reason; never mind the inconsistency that root should have access to everything.

If /home is on a separate partition, the way round it is not to sudo for the home directory, but for searching the root directory to do:

sudo find / -xdev -name "*foobar"

(the '-xdev' avoiding  descending into other partitions mounted somewhere in /).

---

### Post by rubicon on 2008-05-11
> **pmorton said:**
> never mind the inconsistency that root should have access to everything.Not true. Whereas root have rights to manipulate every part of the system, a directory with *(dr-x------)* permissions may be accessed by **nobody but the owner**. Root is just a *user* after all and kernel treats him likewise.

Of course, root can just change permissions for that folder, and get access to it in a mo :)

---

### Post by pmorton on 2008-05-11
> **rubicon said:**
> Not true. Whereas root have rights to manipulate every part of the system, a directory with *(dr-x------)* permissions may be accessed by **nobody but the owner**. Root is just a *user* 

Sorry, Rubicon, but indeed it's true. Root is, of necessity, far from just another user. If Root can't go anywhere and do anything, (compatible with not breaking the system), who can? Root giving himself permission to carry out an action is of as much practical use as me giving myself permission to comb my hair. What's the point?

---

### Post by rubicon on 2008-05-11
> **pmorton said:**
> Sorry, Rubicon, but indeed it's true. Root is, of necessity, far from just another user. If Root can't go anywhere and do anything, (compatible with not breaking the system), who can? Root giving himself permission to carry out an action is of as much practical use as me giving myself permission to comb my hair. What's the point?
I would like to disagree with you, but I see you not quite fully understood my words. I guess this is my fault.

Root have *administrative* access and is therefore administrator (not just a regular user), but what differs him from regular users is **just uid 0**. And he can't get instant access to everything &#8212; this would be a security flaw!

---

### Post by gwi on 2008-05-16
I have a directory entry in a home directory that looks like this when listed with ls -la:
```
d?????????  ? ?      ?          ?                ? .gvfs
```

In another user's home directory it looks normal, and has the user as owner and primary group.

The directory entry shown above is inaccessible, even by root. Why is that directory entry there, why does it look so strange, and how can I fix it?

---

### Post by spudtheimpaler on 2008-05-17
> **pmorton said:**
> I've come across the same problem, and I've seen it reported with Fedora. It seems to be a Gnome glitch. It's an irritation when your attempts to  find something as root get curtailed for no apparent reason; never mind the inconsistency that root should have access to everything.

If /home is on a separate partition, the way round it is not to sudo for the home directory, but for searching the root directory to do:

sudo find / -xdev -name "*foobar"

(the '-xdev' avoiding  descending into other partitions mounted somewhere in /).

The xdev switch is a useful find - thanks! (Of course home is on a separate partition ;-)) 

And I'm quite interested to see how this 'root' discussion pans out...

---

### Post by meonkeys on 2008-06-07
Related (and currently open) bugs:
[LIST]
[*][Superuser cannot access ~/.gvfs folder when mounted]("https://launchpad.net/bugs/225361")
[*][Root user can not access .gvfs]("http://bugzilla.gnome.org/show_bug.cgi?id=534284")
[/LIST]

---

### Post by alex_o on 2010-01-01
i think this is because ONLY the user of the home directory of the .gvfs can actually acces this, i have the same problem:
```
alex@alex-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             582G   26G  528G   5% /
udev                  2.0G  360K  2.0G   1% /dev
none                  2.0G  396K  2.0G   1% /dev/shm
none                  2.0G  312K  2.0G   1% /var/run
none                  2.0G  4.0K  2.0G   1% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
none                  582G   26G  528G   5% /var/lib/ureadahead/debugfs
/dev/md0              917G  622G  295G  68% /mnt/raid
/dev/sdi1             112G   55G   58G  49% /mnt/120GB
/dev/sda2             183M   53M  121M  31% /boot
df: `/root/.gvfs': Permission denied

```

but when ran as sudo the last line doesnt appear

---

