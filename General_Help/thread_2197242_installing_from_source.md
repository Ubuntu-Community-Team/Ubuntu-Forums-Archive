---
title: "installing from source"
date: 2014-01-02
forum: General Help
---

### Post by chasehead2 on 2014-01-02
I'm just wondering how installing a program from source differs from using apt or the software center. Specifically where the files get placed and whether or not dependencies are automatically downloaded and installed. Most programs installed via apt are placed in the bin folder and have configs hidden within the home folder. Is this a standard that all Linux programs try to adhere to including when installing from source? And what is the primary benefit of compiling from source vs a binary install as a none programmer who doesn't desire to alter the code in any way?

---

### Post by monkeybrain20122 on 2014-01-02
You have to install the dependencies separately if you want to install from source. Usually those are -dev files (developmental files) and chances are they are in the repo. The default location for installing from source is usually /usr/local so instead of having the binary in /usr/bin you will find it in /usr/local/bin etc. But you can change it (say if it has a configure script, you would run it with the prefix option) The .config files will still be created in /home/

Running the configure script (./configure) or something equivalent will also tell you what dependencies are missing. If you install something that is in the repo (maybe you want a newer version) then the command

```
sudo apt-get build-dep foo
```

would install all the dependencies required to build package foo.

You also need to install some build tools, usually build-essentials, automake, git-core, libtools  etc  They are all in the repo

---

### Post by chasehead2 on 2014-01-02
Is there a more manual method or is this the way it's always been done on Linux?

---

### Post by monkeybrain20122 on 2014-01-03
What do you mean by "more manual method"? No, this is not the way it is always done, but probably the most common way. When you download a source tarball, usually there are some instructions to build the package(Readme, INSTALL, or something like that)

---

### Post by tgalati4 on 2014-01-03
The advantage of compiling from source is the appreciation you get from building your own code.  It sometimes even works.

---

### Post by Mark Phelps on 2014-01-04
> as a none programmer who doesn't desire to alter the code in any way? 

Then, I strongly advise that you do NOT install from source.  It really is the most difficult way to install an app, requires the most work, and encounters the most problems.

There are other ways to get more recent app versions than using the repositories and one of them is using PPAs.

Really, you should only resort to installing from source if there is no other way to get the version of the app you want.

---

