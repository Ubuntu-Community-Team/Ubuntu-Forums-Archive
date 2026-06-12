---
title: "I want to back up my home directory, but what's the best way to do it?"
date: 2007-04-22
forum: General Help
---

### Post by rainwalker on 2007-04-22
I did it before by tarballing it but I can't remember the command, and some of the stuff in my home directory I don't really need to bother backing up (like all my music).

Any suggestions?

---

### Post by dyous87 on 2007-04-22
well if i was you i would just back it all up on and external hard drive. You don't really need to tarball it but you can if you like.

---

### Post by rainwalker on 2007-04-22
You mean just copy the entire folder over?

---

### Post by leg on 2007-04-22
cpio is a fantastic command for this kind of thing. Try something like
 ```

cd <directory to back up>
find . -depth -print0 | cpio -0dmvo <target>

```

use man first for both the find and cpio commands so you can get a better understanding of what you will be doing. Basically the find command will list all files from this directory down and list them with null terminated strings. That output is then passed to the cpio command. the -0 is for compatibility with the null terminated strings generated. the o at the end makes an archive. you could change it to a p to just copy them instead of archiving. Look into it it is a great tool.

---

### Post by rainwalker on 2007-04-22
I'll see about that, thanks!

---

### Post by DoktorSeven on 2007-04-22
cd ~
tar cfvp home.tar * 
gzip home.tar

---

### Post by rainwalker on 2007-04-22
DoktorSeven, you're my hero. That's EXACTLY what I was looking for, thanks!

---

### Post by rainwalker on 2007-04-22
One more question:
Is there a way to only tar certain files/folders? I have a LOT of music, some photos, and random screenshots saved on my computer; is there a way to exclude certain things (files and folders) so that I don't have to tar up un-needed stuff?

---

### Post by DoktorSeven on 2007-04-22
**man tar** from a commandline.

You'll find the **--exclude** switch that does that.

**tar cfv home.tar --exclude=Music --exclude=Pictures ***

---

### Post by rainwalker on 2007-04-22
Ahhh, that makes sense!

But why do you have the asterik after "Pictures"? And does it classify any type of audio file as "Music"?

---

### Post by hikaricore on 2007-04-22
Music and Pictures are the names of the folders (or individual files) to exclude :P

---

### Post by rainwalker on 2007-04-22
Ohh, so I would exclude folder names! Gotcha.

Would it be the same for file names?

---

### Post by rainwalker on 2007-04-22
Is it important to have the "p" in that command? Like "cfvp" versus "cfv"? I know it preserves the permissions, but is that important when tarring?

---

### Post by rainwalker on 2007-04-22
I doubt anyone is still listening, but I'll ask anyway.
```
 tar cfvp home.tar --exclude=beryl-plugin-screensaver --exclude=downloads --exclude=Incomplete --exclude=Shared --exclude=stuff --exclude=vmware --exclude=frostwire-4.13.1.i586.deb *
```
and then opened the archive to make sure it had saved everything I wanted it to, and it didn't save any of the "dot-whatever" folders that you have to go "View -> Show Hidden Files" too see (like .mozilla, .nautilus, etc.).
Aren't those important, like configuration files or something?

---

### Post by GuitarRocker2562 on 2007-04-22
Seeing as you aren't root, but have permissions, keep the p.

---

