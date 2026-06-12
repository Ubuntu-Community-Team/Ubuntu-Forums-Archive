---
title: "debuild: &quot;cannot find readable debian/changelog anywhere!&quot;"
date: 2006-11-13
forum: General Help
---

### Post by Old Pink on 2006-11-13
Hi there,

Trying to create a Scribes package using debuild for the Ubuntu repositories, as I've been made a REVU. All is well, except debuild complains there is no changelog and refuses to build.

Here's the terminal history:
> matt@matt-desktop:~/scribes-0.3$ debuild -S -sa
debuild: fatal error at line 600:
cannot find readable debian/changelog anywhere!
Are you in the source code tree?
There is a changelog, but I have no idea whether it's readable, I can read it fine. :-k

I've tried renaming and moving the changelog everywhere, even tried copying it into every folder, absolutely no luck.

Following the instructions from: [https://wiki.ubuntu.com/MOTU/Packages/REVU](https://wiki.ubuntu.com/MOTU/Packages/REVU) > 
Uploads to REVU should only be signed source files, with the original tarball. Please do not upload unsigned source or binary packages. 
 Inside your package directory, issue  
     debuild -S -sa
-S builds a source package, and -sa includes the original source. If your GPG key is not configured correctly, add -kGPGKEYID to the command line.

Nothing seems to work, any ideas?

- Matt

---

