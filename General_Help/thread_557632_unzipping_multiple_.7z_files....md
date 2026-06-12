---
title: "unzipping multiple *.7z files..."
date: 2007-09-22
forum: General Help
---

### Post by prion on 2007-09-22
I have a directory with about 1100 7zip compressed files.  I'd like a way (using bash) to unzip all of them, one at a time.  Ideally, I'd like each to be unzipped into a new directory named after the name of the 7z file.  Is this possible?  Any help is greatly appreciated, I don't want to have to do this by hand...

_prion

---

### Post by dlanor78 on 2007-09-22
Here's an example of how to unzip multiple zip files in linux (but I don't know if it makes new folders) :

```

for z in *.zip; do unzip $z; done

```

Just replace *.zip with *.7z and unzip with whatever the command is for extracting 7-zip files in linux (p7zip -d maybe).

Sorry I couldn't be more exact.  I don't have any 7-zip files to try this on.

And here's another zip example that's supposed to make new directories with each zip (but again, untested) :

```

for file in `ls 123_*.zip'; do unzip $file -d `echo $file | cut -d "." -f 1`; done

```

Again, just try replacing the parts that apply to you like 123_*.zip might be replaced with just *.7z.  All speculation here ;-P

---

