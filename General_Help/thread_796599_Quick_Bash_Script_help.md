---
title: "Quick Bash Script help"
date: 2008-05-16
forum: General Help
---

### Post by shironeko on 2008-05-16
Hello to everyone,

there's some quick bash script help I would need.

What I want to do is that if a file exists in a directory, the scripts changes the directory to where that file was found.


if [ -f */file.x ]            #checks that file exists
then

cd .........             #here it should change to the directory of the file
rm [^file.x]             #Delete everything but the file
cd ..                    # go back to the parent directory.

fi


As you can see what I'm missing is a way to move to the directory of a given file.

Thank you.

---

### Post by |{urse on 2008-05-16
> As you can see what I'm missing is a way to move to the directory of a given file.
A little confused, cd /where/you/want/to/be is the way to move to the directory.

---

### Post by |{urse on 2008-05-16
or do you mean you want it to change to the directory of the given file as it finds it?

---

### Post by shironeko on 2008-05-16
> **|{urse said:**
> or do you mean you want it to change to the directory of the given file as it finds it?

Exactly.
It should change to the directoy where the file is.

Imagine we've got these directories

1
2
3
4
5

And the file is hidden somewhere under those 5 directories.

If it is, it should change into the one where it is.

---

### Post by |{urse on 2008-05-16
cd ~

find . -name "filename.extension"

will search recursively starting from you home folder for the file filename.extension and return back the path

if you want the full path of the files the start searching from the root folder /

you could make the output of that a variable $whatever and cd $whatever

---

### Post by shironeko on 2008-05-16
The point is that I want to create a script, so that the script automatically operates inside the directory where it found the file.

---

### Post by |{urse on 2008-05-16
if you use find . -name you cand send its results to a variable with a > $whateveryouwanttocallit then cd $whateveryoucalledit,

---

### Post by Monicker on 2008-05-16
find also has a -execdir option, for doing operations in the directory where a file is found.

---

### Post by shironeko on 2008-05-16
Thank you!
That is what i needed

---

### Post by |{urse on 2008-05-16
.

---

