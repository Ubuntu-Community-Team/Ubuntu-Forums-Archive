---
title: "mass remove folder keep contents"
date: 2007-08-10
forum: General Help
---

### Post by SOG420 on 2007-08-10
Hello,
     I was wondering if someone could direct me as how to move the files inside a large amount of subdirectories while deleting their container folder to leave 1 group of files with no subdirectories.Ideally terminal instructions would be helpfull

---

### Post by bodhi.zazen on 2007-08-10
cd <directory to remove>

mv * ..

cd ..

ls -la <directory to remove> # Just to make sure it is empty

rm -r <directory to remove>

Or 
> #!/bin/bash
for i in 'ls -d'; do 
cd "$i"
mv * ..
cd ..
rm -ri "$i"
done

the rm -ri is to check the directory is indeed empty. You could just rm -r "$i", but be careful

---

