---
title: "Folder Integrity"
date: 2007-06-24
forum: General Help
---

### Post by Hygelac on 2007-06-24
I've been transferring thousands of files between computers on my home network, and I want to be able to check that the files have not been corrupted during transfer.  I know how to check the md5sum's and whatnot, but only for individual files.  Is there a similar way to check the integrity of entire folders?  Any help on this would be much appreciated!

---

### Post by 5-HT on 2007-06-24
md5deep (in the repos) can recursively generate/check various message digests.
You can make a list of hashes with something like```
md5deep -rl top_level_directory >> path_to_output_file
```And check them with```
md5deep -x path_to_file_containing_hashes -r top_level_directory
``` The output will only spit out files that do not match. The man page is very nicely documented.
Another way to go would be to make an archive of all the files, generate a hash for the archive, and transfer that. 

cheers,

---

### Post by Hygelac on 2007-06-26
That first way seems good; thanks!

---

