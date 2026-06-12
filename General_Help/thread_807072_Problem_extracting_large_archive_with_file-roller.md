---
title: "Problem extracting large archive with file-roller"
date: 2008-05-25
forum: General Help
---

### Post by johnrxxv on 2008-05-25
I have been trying to extract a 3.5gb bz2 file using file-roller. The file is stored on a separate partition with plenty of free space (I am extracting to the same partition).

It appears that file-roller copies the file to a hidden directory in my home partition while it is extracting. The problem is my home partition does not have enough free space.  Is there a way to extract a large file without file-roller using my home partition?  Is there something else I should be using for extracting this file?

The error message I get when I right-click on the file and select "Extract Here" is the following:
```
bzip2: I/O or other error, bailing out.  Possible reason follows.
bzip2: No space left on device
	Input file = /home/johnrxxv/.fr-vJRn7U/file.xml.bz2, output file = /home/johnrxxv/.fr-vJRn7U/file.xml
bzip2: Deleting output file /home/johnrxxv/.fr-vJRn7U/file.xml, if it exists.

```

I'm using Ubuntu 8.04.

Thanks.

---

### Post by Monicker on 2008-05-25
You could try extracting it from the console

Applications -> Accessories -> Terminal

```

cd /dir/of/file
bunzip2 humongous.bz2
```

---

