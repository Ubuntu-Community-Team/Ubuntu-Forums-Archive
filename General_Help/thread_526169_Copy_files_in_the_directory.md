---
title: "Copy files in the directory"
date: 2007-08-15
forum: General Help
---

### Post by don gino on 2007-08-15
Hey

What is the command to copy the content of a directory, but not the folder itself?

For example, if i have a folder called 'website', how do i copy the files in the folder 'website' to a location but not the folder itself (the folder is left empty)

Thanks

---

### Post by heimo on 2007-08-15
> **don gino said:**
> Hey

What is the command to copy the content of a directory, but not the folder itself?

For example, if i have a folder called 'website', how do i copy the files in the folder 'website' to a location but not the folder itself (the folder is left empty)

Thanks

Let's see if I understand your question.

Command:
```
cp -a source/. target/
```

Will copy everything from *source* directory to *target  *directory, it does not copy *source *directory itself to *target *directory.

---

### Post by anaconda on 2007-08-15
If you want the folder to become empty then you want to use mv (move) not cp (copy)

so just go to the directory you want to move, and then 
```
mv * /path_to_the_target_directory 
```

Just remember that mv is much more "dangerous" than cp, if you make a mistake then the orginal files are gone.

I usually use nautilus to copy files. if you copy to the same hd they are automatically moved instead of copied.

---

### Post by don gino on 2007-08-16
Thanks for the replies

I done the 'cd' to the directory i wanted to move and it moved the contents only, thanks heaps :P

Now i can continue getting my web server up and running


Thanks again

---

