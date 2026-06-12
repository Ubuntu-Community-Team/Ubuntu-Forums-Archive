---
title: "How to ignore object files with no extension in bzr (bazaar)?"
date: 2007-12-13
forum: General Help
---

### Post by kung fu buntu on 2007-12-13
It's easy to ignore files using a filename pattern either globaly or per project with ~/.bazaar/ignore and .bzrignore. But what about file types?

In a regular project the programmer can clean the directory with a "make clean" before submiting the source code to the version repository. But I've inherited a project where there is no Makefile and things are done with a script (long story, it has to stay that way, don't ask).
The thing is that a couple of dozen of object files (with no extension) are built everywhere. How can I ignore them? Is it possible to do this in bzr?

Other possible solution that occured me now: keeping two directories:
project-src-code
project-build
I make all my updates in project-src-code, but when building I copy (and thus overwrite) the files in project-build.
Well, cp -r also copies the .bzr directory, which I don't want. Is there a way to ignore it?

Thanks

---

