---
title: "Update manager keeps trying to update a package to the exact same version"
date: 2007-08-17
forum: General Help
---

### Post by Andorien on 2007-08-17
This screen shot should explain the problem:
[img]http://img219.imageshack.us/img219/5941/synapticlm8.png[/img]

Basically, it keeps trying to update the package to the exact same version, and wont go away even if I let it.  Is there anyway to resolve it, or at least kick the icon out of the notifier space?

---

### Post by sumguy231 on 2007-08-17
I don't know how to resolve it short of removing it, but if you do a:
```
echo compiz-core hold | sudo dpkg --set-selections
```
Then it will always be unselected, though I think it will still show in the update manager.

If you do that and want to undo it, do this:
```
echo compiz-core install | sudo dpkg --set-selections
```

---

### Post by michaelzap on 2007-08-17
Same thing happened to me today right after I added Amaranth's repository as well as Treviño's to my sources.list file and tried to update Compiz. Plus when I restarted Compiz it no longer worked. So I commented out those lines and removed and reinstalled Compiz and now it's back to normal.

Basically I think that those two repositories conflict, or perhaps there's something wrong with Amaranth's.

I can wait a few more days for the Compiz updates...

---

### Post by Andorien on 2007-08-17
> **michaelzap said:**
> Same thing happened to me today right after I added Amaranth's repository as well as Treviño's to my sources.list file and tried to update Compiz. Plus when I restarted Compiz it no longer worked. So I commented out those lines and removed and reinstalled Compiz and now it's back to normal.

Basically I think that those two repositories conflict, or perhaps there's something wrong with Amaranth's.

I can wait a few more days for the Compiz updates...

I remember the problem started when I added Amaranth's (I think), so I'm gonna remove it and see what happens.

Added: That got it, thanks guys.

---

### Post by deaster2 on 2007-09-09
> **Andorien said:**
> I remember the problem started when I added Amaranth's (I think), so I'm gonna remove it and see what happens.

Added: That got it, thanks guys.

Exact same problem here...removed Amaranth 
problem solved...
Many thanks...

---

