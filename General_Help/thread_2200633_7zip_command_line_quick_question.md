---
title: "7zip command line quick question"
date: 2014-01-20
forum: General Help
---

### Post by NertSkull on 2014-01-20
According to just about any documentation you find online in forums for 7zip they say that for the compression switch you use something like -mx9.  For example:

```
7z a -mx9 Out.7z Input/
```

BUT, according to the actual 7zip sourceforge documentation.  It says it should be -mx=9.  For example

```
7z a -mx=9 Out.7z Input/
```

So, does it matter? I can't really see a difference when I do it.  But I thought I'd ask here to see if anyone has any thoughts on a reason for this.

Secondariliy, is this just the way most switches work? If you have a switch that has a '=' part.  can you just leave out the equals for any program?  Or is this specific to 7zip?

---

### Post by Dave_L on 2014-01-20
7zip uses its own conventions that don't conform exactly to the usual GNU/Linux utilities. My guess is that it was written originally for Windows and then ported to Linux.

I would use the man page as the reference: [http://manpages.ubuntu.com/manpages/precise/en/man1/7z.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/7z.1.html)

For backing up Linux files, it's better to use tar (and gz or another compression algorithm), since the file attributes are preserved.

---

### Post by NertSkull on 2014-01-20
That makes sense. It does seem to be kind of not integrated great yet with linux.

The man page and docs definitely suggest you use mx=9.  But as far as I can tell either (mx9 or mx=9) work just the same. I've tried a bunch of files and they all come out the same.

Yeah for regular backups I'd use gzip/tar (I actually am using duplicity) but for some archiving discs I'm making 7zip gives me the best compression. And pretty fast decompression. I actually kind of hope it becomes more fully integrated into the linux environment. I quite like it.  But yeah, I wouldn't recommend it for system backup/daily use type stuff yet in linux.

---

