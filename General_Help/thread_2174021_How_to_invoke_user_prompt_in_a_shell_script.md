---
title: "How to invoke user prompt in a shell script?"
date: 2013-09-12
forum: General Help
---

### Post by vperaino on 2013-09-12
I tried searching for this and I didn't get the exact answer I wanted. 

Basically, what I'm trying to do is have a file copied and renamed as something else in the middle of a shell script, and the file has to be renamed according to a convention that can't be referenced against any information that's already on the computer. So I need the user to enter the information. 

What would I enter in the shell script to get the user to rename the copied file?

---

### Post by SeijiSensei on 2013-09-12
How about using a command-line parameter:

```
$ script 'name_of_the_renamed_file'
```

Then in the script use the positional parameter $1 to get the user's input.  Have the user get in the habit of encasing the name in single quotes in case the name has embedded spaces.

There are ways to [make scripts interactive]("http://www.tldp.org/LDP/abs/html/intandnonint.html"), but I've never used those.

---

### Post by steeldriver on 2013-09-12
Do you need anything more than a simple prompt/read?

```
$ read -p "please enter a filename: " newname
```

This will assign whatever the user types at the prompt to variable "$newname", which you can use as the new filename

---

### Post by vperaino on 2013-09-12
How would I position the "read" prompt in relation to the cp command in the script?

---

### Post by steeldriver on 2013-09-12
```

read -p "please enter a filename: " newname
cp "oldfile" "$newname"

```

The quotes are to allow whitespace in the names. You may want to add some checking e.g. does a file called "$newname" already exist, if so what do do etc.

---

### Post by vperaino on 2013-09-12
Thanks guys! :)

---

