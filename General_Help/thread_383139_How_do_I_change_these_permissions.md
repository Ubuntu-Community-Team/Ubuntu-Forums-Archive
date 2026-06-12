---
title: "How do I change these permissions?"
date: 2007-03-12
forum: General Help
---

### Post by ardchoille42 on 2007-03-12
I have a directory which has subdirectories and files in it. Each subdirectory has subdirectories and files in them. Most of the files are 755 (-rwx-r-xr-x) and I want to make all of the files 644 (-rw-r--r--). What I did was :

```

chmod -R 644 /path/to/dir

```

but what that did was remove the execute bit (x) from all of the subdirectories too.. which means you can no longer use 'ls' to see the subdirectories, nor can you use 'cd' to go into those subdirectories. Trying to ls or cd a directory which is -rw-r--r-- will get you a "Permission Denied" error.

How do I make all the files in those subdirectories 644 without affecting the subdirectories themselves?
shouldn't the chmod command have an option that excludes directories (maybe --exclude-dirs)? Or is there an easier way to do this?

---

### Post by kokiri on 2007-03-12
to fix this just
```
chmod +x /dir
```
and just the bit on the folder will be set. You'd need to add a * to the end of it to get it to modify the files inside the directory. The -R makes chmod recursive and it smacks everything

I usually just use nautilus, select all the files in the dir, right click, choose properties, and change what I need to in the file attributes tab. It sounds like a headache but it's really easy.

---

### Post by ardchoille42 on 2007-03-13
> **kokiri said:**
> to fix this just
```
chmod +x /dir
```
and just the bit on the folder will be set. You'd need to add a * to the end of it to get it to modify the files inside the directory. The -R makes chmod recursive and it smacks everything

I usually just use nautilus, select all the files in the dir, right click, choose properties, and change what I need to in the file attributes tab. It sounds like a headache but it's really easy.

I have several hundred files in more than 60 subdirectories and the files are of several different extensions. How would I do that from the command line? I rarely use xorg on that machine.

What I need is an easy command to change all the files without changing the directories too.

---

### Post by Mr. C. on 2007-03-13
```
find startdir -type d -print | xargs chmod 755
find startdir -type f -print | xargs chmod 644

```

MrC

---

### Post by kokiri on 2007-03-13
Ugh, sorry I was fearing this you can't really do that with octal notations but you can do it by using the extended owner, group, and others bits so for your example it would be:
```

chmod -R u+xrw,g+r,g-wx,o-xw /dir

```
For reference here's what's going on
You (the owner presumably) can read write and execute, the group can only read with write and read removed, and everyone else can read but can't execute or write.
Here's a good reference page on this:
[http://www.tech-recipes.com/unix_tips691.html](http://www.tech-recipes.com/unix_tips691.html)

---

### Post by ardchoille42 on 2007-03-13
> **kokiri said:**
> Ugh, sorry I was fearing this you can't really do that with octal notations but you can do it by using the extended owner, group, and others bits so for your example it would be:
```

chmod -R u+xrw,g+r,g-wx,o-xw /dir

```
For reference here's what's going on
You (the owner presumably) can read write and execute, the group can only read with write and read removed, and everyone else can read but can't execute or write.
Here's a good reference page on this:
[http://www.tech-recipes.com/unix_tips691.html](http://www.tech-recipes.com/unix_tips691.html)

Well, what I need to do is

chmod u-x all files in the subdirectories

But if you use '[COLOR="Blue"]chmod -R u-x /dir[/COLOR]' to do that the system locks you out of all the subdirs (drw-r--r--).. you can't ls or cd a dir that is drw-r--r-- even if you own that directory. That was my whole point. It would be nice if the chmod command had an option to ignore directories when using -R (something like --exclude-dirs) so an unsuspecting user wouldn't lock himself out of a bunch of directories.

---

### Post by ardchoille42 on 2007-03-13
> **Mr. C. said:**
> ```
find startdir -type d -print | xargs chmod 755
find startdir -type f -print | xargs chmod 644

```

MrC

Ah, so I have to use find to do this? Ok, thank you.

---

### Post by Mr. C. on 2007-03-13
You don't *have* to ues it.  Like all things in *nix, there are many ways to do it.  Find is probably the easiest for this problem.

MrC

---

