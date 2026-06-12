---
title: "Mess with some .sh file"
date: 2015-06-03
forum: General Help
---

### Post by dsx2 on 2015-06-03
Well as it's said in the title i did yesterday a command to try to move all the .sh file i was working on 
I ended up with this command on my home 

find -name "*.sh" -exec mv {} ~/file \;
 
I forgot that there was hidden file in my home so i found after this command 2 files autogen.sh and ltmain.sh in the directory 
the problem is that i want to get them back where they were to make sure that everything keep everything smooth specially after i get some kubuntu desktop residue on my Ubuntu.
I though about a command that  can link you he previous position of a file any one has a clue about how to fix this 
thanks in advance :)

---

### Post by steeldriver on 2015-06-03
Hello and welcome to the forums

I'm not aware of any standard command that can unambiguously determine the previous location of a file: however, if you are lucky, the database used by the 'locate' command will not have been updated since you ran your command, in which case running

```

locate autogen.sh

```
and/or
```

locate ltmain.sh

```

should return the earlier location. Note however that many software packages that are distributed in the form of source code will have an 'autogen.sh' file, so if you have built lots of things from source it may take some additional sleuthing to figure out which one you moved: for example, by comparing the outputs of 'locate' and 'locate -e'

Don't wait too long, since the database is typically updated once per day

---

### Post by dsx2 on 2015-06-03
Greattt ideaa didnt tough about that !! Hopefully the db wasn&#8217;t updated 
tks for the welcoming and the fast answer :)))
The two files were from the htop

---

