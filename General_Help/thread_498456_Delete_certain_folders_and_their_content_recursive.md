---
title: "Delete certain folders and their content recursively."
date: 2007-07-11
forum: General Help
---

### Post by sebast on 2007-07-11
Hi,

I'm still not an expert with Linux nor with scripting languages and I
need to delete all the "_notes" and "_vti_cnf" folders inside the main
folder of a website I'm maintaining.

I know it should be easy to do with a little bash script, but I don't
know how.

I need a script to look for each _notes and _vti_cnf folder and delete
it with it's content.

I would appreciate any king of help.

---

### Post by gepatino on 2007-07-11
something like this?

```
for folder in *_notes
do
  echo rm -rf $folder
done

```

remove the <b>echo</b> if it returns what you want, I don't want to destroy your data via RC :)

---

### Post by Copter on 2007-07-11
Or run this
```

find -path _notes -exec '/bin/rm -r ' {} \;
find -path _vti_cnf -exec '/bin/rm -r ' {} \;

```It will delete all _notes and _vti_cnf directories' content inside **current** directory. Tip: better try this on some test directory structure first.

copter :]

---

### Post by sebast on 2007-07-11
Thank a lot guys.

I can see there is more than one way to do it.

I finally did something like this:

```
find . -depth -type d -name _notes -o -name _vti_cnf | xargs rm -rf
```

Which was an answer from someone on Usenet.

Didn't try your answers, but I'm sure they would have worked fine as well.

I'm starting to see how powerful the command line is when I see that I can do things like that with one simple line and two programs (find and rm)

Thanks again.

---

