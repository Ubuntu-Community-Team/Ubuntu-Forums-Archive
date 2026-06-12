---
title: "how can I bulk rename files with console's wildcards?"
date: 2006-08-28
forum: General Help
---

### Post by pmark on 2006-08-28
I have a big list of directories in the following form:

```
2006-07-22
2006-07-20
...
2005-03-08
...
```

I want to convert the dashes ("-") to dots ("."). I am trying this:

```
mv 200?-??-?? 200?.??.??
```

and this:

```
mv 200*-*-* 200*.*.*
```

But it doesn't work. When I tried in only one directory, it just renamed the directory to "200?.??.??" (question makes included in the file's name).

How can I rename these directories using the console?

---

### Post by gborzi on 2006-08-28
Try this> for i in 200[0-9]-[0-9][0-9]-[0-9][0-9]; do newname=`echo $i|sed 's/-/./g'`; mv $i $newname; done
note the (`) are backquotes.

---

### Post by pmark on 2006-08-30
Thank you. It worked.

---

### Post by Haegin on 2008-01-12
```

for i in *; do mv $i `echo $i|tr . -`; done

```
also works

---

### Post by erginemr on 2008-04-07
Although this problem has been solved long ago, for future reference:

The above methods used bash to do the trick. Yet, one can also use **thunar** or **krename** for desktop bulk renaming, or simply the command **rename** for text-mode renaming. 

The terminal command **rename** uses regular expressions (as does sed) to evaluate the text string to be replaced. For this specific example:
> replacing dashes with dots in a list of folders with names:
2006-07-22
2006-07-20
...
2005-03-08
one can use
```
rename "s/\-/\./g" *
```
to replace all dashes(-) with dots(.) or use:
```
rename **-n** "s/\-/\./g" *
```
first to do a test run before the actual replacement. And the command:
```
rename **-v** "s/\-/\./g" *
```
will act in verbose mode, so will list the files that are renamed.

The following link will show how to use rename on a bunch of examples:
[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

---

### Post by erginemr on 2008-04-07
And **Metamorphose **([http://file-folder-ren.sourceforge.net/index.php?page=Main](http://file-folder-ren.sourceforge.net/index.php?page=Main)) might be an answer for those looking for a native Gnome bulk-rename application, as **thunar **is made for Xfce and **krename **is made for KDE.

---

