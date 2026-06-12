---
title: "migrating from windows problem"
date: 2007-06-12
forum: General Help
---

### Post by Josey on 2007-06-12
I'm trying to get my friend to convert to linux but the problem is she has saved thousands of .url files over the years.  Here is what they look like.
```
[DEFAULT]
BASEURL=http://autoinsuranceweb.com/
[InternetShortcut]
URL=http://autoinsuranceweb.com/

```

Does anyone know how I could mass convert these .url files into something she can click on and the file will open the default browser to that url?

---

### Post by PgR on 2007-06-12
Try this (it seems to work for me!)

```
perl -pi -e "s/InternetShortcut/Desktop\ Entry/g;" *
```
Replaces [InternetShortcut] with [Desktop Entry] for all files in the current directory
```
for f in *.url; do echo Type=Link >> $f; done;
```
Adds the line "Type=Link" to each .url file in the current directory
```
for f in *.url; do mv $f `basename $f .url`.desktop; done;
```
Renames *.url to *.desktop

Try it with some test data first, of course, but as I say it seems to work for me!

---

### Post by Josey on 2007-06-12
thanks!

---

### Post by Josey on 2007-06-12
It didn't work for me though :(
the first command does what you say it will but when I run
```
for f in *.url; do echo Type=Link >> $f; done;
```
I get
```
bash: $f: ambiguous redirect
```
and it doesn't make the changes in the file.
also this
```
for f in *.url; do mv $f `basename $f .url`.desktop; done;
```
gives me this.
```
Try `basename --help' for more information.
mv: target `.desktop' is not a directory

```

any suggestions?

---

### Post by Josey on 2007-06-13
anyone?

anyone?

bueller?

bueller?

---

### Post by PgR on 2007-06-13
Hmmm... 

does this cat the contents of the files? ```
for f in *.url; do cat $f; done;
```

---

### Post by PgR on 2007-06-15
> **Josey said:**
> anyone?

anyone?

bueller?

bueller?

?

---

### Post by Josey on 2007-06-15
Oh... thanks for the help but I opened them with different browsers and epiphany opens them to the webpage specified.
  
Thanks for trying to help me with these silly files. :)

---

