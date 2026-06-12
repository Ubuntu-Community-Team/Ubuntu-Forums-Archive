---
title: "what is the best way to wipe/overwrite a file with Gutsy GIbbon"
date: 2007-11-06
forum: General Help
---

### Post by mamadu bwana on 2007-11-06
Hi,

Could you please recommend and safe, simple and effective wiping/file overwriting application which would (almost) totally wipe a file off the hard drive?

I did see 'secure-delete' but there was no man, info or doc with it so I don't want to use that.

And a GUI working with GNOME would be nice too.

Many thanks,

Mamadu

---

### Post by honeydew on 2007-11-06
shred is a really good option..  so 'shred -z'  looks nice.. I suggest maybe doing 'man shred' in the terminal.

nguts:~$ shred --help
Usage: shred [OPTIONS] FILE [...]
Overwrite the specified FILE(s) repeatedly, in order to make it harder
for even very expensive hardware probing to recover the data.

Mandatory arguments to long options are mandatory for short options too.
  -f, --force    change permissions to allow writing if necessary
  -n, --iterations=N  Overwrite N times instead of the default (25)
  -s, --size=N   shred this many bytes (suffixes like K, M, G accepted)
  -u, --remove   truncate and remove file after overwriting
  -v, --verbose  show progress
  -x, --exact    do not round file sizes up to the next full block;
                   this is the default for non-regular files
  -z, --zero     add a final overwrite with zeros to hide shredding
      --help     display this help and exit
      --version  output version information and exit

---

### Post by mamadu bwana on 2007-11-06
thanks, that is exactly what I needed.  appreciate it! cheers

---

