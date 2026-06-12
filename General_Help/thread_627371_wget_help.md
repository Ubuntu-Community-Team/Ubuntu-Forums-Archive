---
title: "wget help"
date: 2007-11-30
forum: General Help
---

### Post by ridetheteapot on 2007-11-30
Hey everybody

I'm using wget to get files from the live music section of archives.org, over ftp. The question i have is basically can i combined -c (continue) with -nc (don't overwrite existing files) and -r (recursive) to resume long flac file downloads (couple of gigs in all, multiple files) when i get interrupted mid-folder mid-file?

Like i have X folder with twenty 400 mb files and it times-out at the tenth file midway through.
What i have been doing in deleting the unfinished file and running ```
wget -r -nc <folder url>
``` It's not much of a problem, but if it is easy i would like to add the -c and start from where the last file left off, instead of re-downloading half the file. 
(I am just afraid that the -c will override the -nc and get all the files from scratch, which i don't what to test if i don't need to)

thanks in advance, and sorry if i explained what i am trying to do poorly.

PS 
This i can test, but just in case someone answers first: will using -P <name> or -nd get rid of all the mirror folders i don't need? Like i am usually downloading from this file structure /mirrorname/subfolder/items/the_folder_i_want .Would:
```
wget -P the_folder_i_want ftp://mirrorname/subfolder/items/the_folder_i_want
```
do the trick of getting rid of the useless part of the folder hierarchy? (mirrorname/subfolder/items/)

thanks again to anyone who replies, i realize that this might look like a bunch of gobbledygook

---

