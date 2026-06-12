---
title: "Memory Editor"
date: 2008-07-03
forum: General Help
---

### Post by Deo Favente on 2008-07-03
Anyone know where to get a memory editor for Linux? Particularly one that searches the memory too cause i cant edit the memory if i dont know where im editing...

EDIT: lolxor, i seriously had searched thru many pages of google and other resources before i posted here but then i just clicked the next page button on google and i found one. I'm trying to compile it right now so i don't know if it works yet. Its called game cheater, homepage: [http://sourceforge.net/projects/gamecheater/](http://sourceforge.net/projects/gamecheater/) help compiling it or other suggestions would be appreciated. 
When i follow the compile instructions it seems to work fine as it produces an executable, but when i execute it it poops out with: "gamecheater: error while loading shared libraries: libgcheater.so.0: cannot open shared object file: No such file or directory"
after that i took a bunch of random files, renamed them to libgcheater.so.0 and then ploped them in the same directory but none of them worked.

EDIT: ok so my next step was to sudo apt-get install and then a bunch of random words pooped out by the make thing. after i dled 10 things i tried compiling it again and it worked!!! i think it was the g77 that did the trick tho. So, i answered my own question, and for all those othe people looking for a memory editor i would like to say that this does work! 
You select a process, then type in a value and search for it. Searchign for any value after that will filter your results, until there are no matching results and your search will start over again. double click on an adess to edit it, and your done! Could be better but ive noticed the version number is .4

---

### Post by kiovanx on 2011-09-12
i get the same error.

so i try to install g77 but in ubutuntu 11.04, so i get another error, that g77 was not available, so i went to synaptic and search for g77, and installed a package named ratfor.

that worked for me.

---

### Post by oldos2er on 2011-09-12
Closed, necromancy.

---

