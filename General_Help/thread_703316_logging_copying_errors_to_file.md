---
title: "logging copying errors to file?"
date: 2008-02-21
forum: General Help
---

### Post by Ashrael on 2008-02-21
I am trying to copy some files to my freenas server and i get some errors. some files won't copy because of an error 22. I know it has some to do with the coding of the files, some have german characters in the name.
Since it's a lot of data that needs copying, i have skipped the files that generate errors. But now i have to find out which files have not been copied... Anyone have an idea how tolog the errors or an other way to correct this problem.

TIA....

---

### Post by mojoman on 2008-02-29
Maybe you've already found a solution but I believe that you can solve this by redirecting standard error to a specific file simply by adding output, e.g.
```

cp /stuff/stuff/* /stuff1/stuff1/* > output.file 2> error.file
```

This, I think, will copy all contents from the selected directory to the specified directory while writing all stdout in the output.file and writing all stderror (i.e. error messages) to error.file. The log files will be placed in the current directory.

/mojoman

---

### Post by Ashrael on 2008-03-13
thanks mate, i'll give that a try....solved the problem in the mean time by copying all the files to a w*nd*ws pc of all things!! But in the future i would like to be able to do it without... ;)

thanx!

---

