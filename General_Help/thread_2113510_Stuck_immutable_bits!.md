---
title: "Stuck immutable bits!"
date: 2013-02-07
forum: General Help
---

### Post by jimford on 2013-02-07
I set the immutable bit on a directory and all its files and subdirectories:

```
sudo chattr -R +i ./the_directory
```

I now want to move the_directory and naturally needed to unset the immutable bit:

```
sudo chattr -R -i ./the_directory
```

but some subdirectories still have the bit set!

I've tried addressing the 'stuck bit' directories directly to no effect.

Ideas anyone, please?

Jim

---

### Post by kr651129 on 2013-02-07
No idea if this will work, just an idea.  I read somewhere that the immutable bit is set after running chattr, maybe it's the same when removing?

---

### Post by linuxtechguy on 2013-02-07
Did you try lsattr to see which folders are not being changed. Of course you could always run chattr though the find command to remove the setting...

```

find ./the_directory -exec chattr -i {} \;

```

---

### Post by jimford on 2013-02-07
> **linuxtechguy said:**
> Did you try lsattr to see which folders are not being changed.

Yes.

```

find ./the_directory -exec chattr -i {} \;

```

Nope - it doesn't work. There are still the same subdirectories with the immutable bit set!

I'm baffled!

Jim

---

### Post by jimford on 2013-02-08
I've just realised that it's not the 'i' bit that's set, but the 'I' bit. This apparently shows that the file (it's actually a directory) is indexed.

I'm not sure what that means and how I can clear it so I can move the directory tree.

The directory tree is source code for a driver that I downloaded, compiled and installed. I just want to 'tuck' it away somewhere safe so I don't lose it. 

Jim

---

