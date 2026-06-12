---
title: "Adding new packages to TeTeX makes me hoge problem"
date: 2007-01-19
forum: General Help
---

### Post by neocortex on 2007-01-19
Hello,
I am really wrestling with the way to put latex packages where they can be seen by the program. Mainly they are various sty-, bst- and cls-files. I have tried so many places, in my local directory, and in /usr/share/texmf, /usr/share/texmf/tetex etc., but without any luck. I have installed tetex via Synaptic manager on my Dapper, and everything works fine, except that I cannot add anything new. The only way the things are working is to have those files in every directory where I have my tex-file, which is consuming and stupid. Can anyone help me, and explain me the way to add new packages (files, that is) into my tetex? Please!

Sincerely,
Petar

---

### Post by venik212 on 2007-02-01
Since I have the very same problem, I add my plea to his request.

---

### Post by llamakc on 2007-02-01
I put my cls and sty files in ~/texmf/tex/latex/ and bst files in ~/texmf/tex/latex/bst/ which were directories I made.

Of course, one should run `texhash` after adding any files.

You have already ran texhash, correct? That's SOP with LaTeX.

---

### Post by WW on 2007-02-01
Here is one way:
In your home directory, create the directory texmf/tex
```
$ cd
$ mkdir texmf
$ mkdir texmf/tex
```
Put your latex package files in the directory texmf/tex.
You can create subdirectories in this directory if you like.

I found this tip, and a few other methods, here: [http://support.math.arizona.edu/tex/accountpackages.php](http://support.math.arizona.edu/tex/accountpackages.php)

Edit: llamakc beat me by seconds!

You don't need to run texhash for files in ~/texmf/tex.

---

