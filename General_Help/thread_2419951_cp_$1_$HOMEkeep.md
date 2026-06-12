---
title: "cp $1 $HOME/keep"
date: 2019-05-27
forum: General Help
---

### Post by jmbrown2 on 2019-05-27
I am taking a linux class and could use a little help.  I have searched and searched for the answer to this and haven't had much luck. 

I'm doing an assignment where I take a program and add comments explaining it.  

There is a line that says:

cp $1 $HOME/keep

I know cp is copy and I assume HOME/keep is trying to refer to the file named keep.  Except I don't have a file named keep and there is no mention of needing that file in the homework instructions.  

Sorry this is such a newb question!  I would appreciate any guidance.  

Thank you!

---

### Post by oldos2er on 2019-05-27
Is "keep" a file or a folder? I suggest you speak with your instructor regarding this.

---

### Post by SeijiSensei on 2019-05-27
Is there a line
```
mkdir -p $HOME/keep
```
before it? mkdir "makes a directory;" the -p tells it to ignore the command if the directory already exists.

Otherwise, if $1 is a file, it will copy it within the home directory and name it "keep".  If $1 is a directory, you'll get an error.

---

