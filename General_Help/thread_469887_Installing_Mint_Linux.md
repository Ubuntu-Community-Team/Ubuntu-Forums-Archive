---
title: "Installing Mint Linux"
date: 2007-06-10
forum: General Help
---

### Post by floweringmind on 2007-06-10
You gave some instruction, but I still need some help.

First how do I create a alternative ISO. I looked at the meta link files for other alternative ISOs. There appears to be a number hashes that need to be created. Is there software that can generate this file based off a current iso of mint linux?

Second you told me to modify items in the wubi/src directory. I do not find the directories, so I presume that I need the source of wubi, modify those files and recompile. If this is the case then where can I find the source code? Second what is needed to compile the source code on linux?

Thanks!

Chris

---

### Post by ago on 2007-06-10
> **floweringmind said:**
> You gave some instruction, but I still need some help.

First how do I create a alternative ISO. I looked at the meta link files for other alternative ISOs. There appears to be a number hashes that need to be created. Is there software that can generate this file based off a current iso of mint linux?
[http://hampus.vox.nu/metalink/](http://hampus.vox.nu/metalink/)

> Second you told me to modify items in the wubi/src directory. I do not find the directories, so I presume that I need the source of wubi, modify those files and recompile. If this is the case then where can I find the source code?
[https://code.launchpad.net/~lupin-team/wubi/devel](https://code.launchpad.net/~lupin-team/wubi/devel)

to grab the code:

bzr branch [http://bazaar.launchpad.net/~lupin-team/wubi/devel](http://bazaar.launchpad.net/~lupin-team/wubi/devel)

note that when compiling you also need to have a (compiled) lupin branch. Lupin must be compiled using the same kernel that will be used in the target ISO.

bzr branch [http://bazaar.launchpad.net/~lupin-team/lupin/devel](http://bazaar.launchpad.net/~lupin-team/lupin/devel)

cd ~/src/lupin/devel
make
cd ~/src/wubi/devel
make
make test

> Second what is needed to compile the source code on linux?
wine + makensis, but if you run make from within wubi, it will install the for you.

---

### Post by antini on 2007-06-10
I might be wrong, but I don't think LM has an alternate ISO? In that case, having a metalink for the normal ISO wouldn't help.

---

