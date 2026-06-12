---
title: "Software center question"
date: 2013-06-07
forum: General Help
---

### Post by vadimkolchev on 2013-06-07
Got a question about software center. Just today noticed that some applications that are present there cannot be found from terminal and can only be installed via Software center. How can it be so? Is this software not in repos? Where does it come from, then?

---

### Post by slickymaster on 2013-06-07
See [this]("http://askubuntu.com/questions/110059/why-wont-ubuntu-software-center-install-deb-files").

---

### Post by vadimkolchev on 2013-06-07
Ok, I read this, but I still do not understand half of the things I asked about. I'm interested in the process the apps go through getting to software center and avoiding repos.

---

### Post by slickymaster on 2013-06-07
> **vadimkolchev said:**
> ... I'm interested in the process the apps go through getting to software center and avoiding repos.

Well, that I can't answer, just because I'm not completely aware of the process in depth. But you could start trying to find an answer in [Ubuntu Manual]("http://ubuntu-manual.org/downloads")'s Software Management chapter.

---

### Post by vadimkolchev on 2013-06-07
Ok, I'll try to research it deeper on my own. The only thing I can say is that I will hate it if Ubuntu will go into two separate deb packaging standards, lol:

---

### Post by slickymaster on 2013-06-07
> **vadimkolchev said:**
> ..I will hate it if Ubuntu will go into two separate deb packaging standards, lol:

On that subject, [here]("https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037074.html") is some more food for thought.
Also this:[ Ubuntu might get a new, simplified packaging format and app installer]("http://www.webupd8.org/2013/05/ubuntu-might-get-new-simplified.html") and this [thread I started here in the forums]("http://ubuntuforums.org/showthread.php?t=2143216").

---

### Post by vadimkolchev on 2013-06-07
thanks a lot, interesting

---

### Post by vadimkolchev on 2013-06-07
Another step too simplify user experience and to hide internals deeper. Don't think it will do too much good. And the system will probably become heavier because of developers packaging all needed libs into their apps, so we will end up with a lot of instances of the same libs on one installation. It's windows way. Is it really necessary? What do you think?

---

### Post by oldos2er on 2013-06-08
Moved to General Help.

---

### Post by deadflowr on 2013-06-08
> **vadimkolchev said:**
> Another step too simplify user experience and to hide internals deeper. Don't think it will do too much good. And the system will probably become heavier because of developers packaging all needed libs into their apps, so we will end up with a lot of instances of the same libs on one installation. It's windows way. Is it really necessary? What do you think?

If two packages contain the same libs, then the newer packages libs will override the older ones upon installation.
So you'll only have one lib, not two or fifty.

Edit: Looking at the way the new package system thought about looks, it could be possible to have multiple instances of libs, and dependencies.
But this won't affect the existing packaging scheme, as it is right now.
Only newly built packages.

And besides, the way programs are built for windows isn't what causes problems on windows.
It's the way the files are thrown onto the disk that cause problems.
Fragmentation.

---

