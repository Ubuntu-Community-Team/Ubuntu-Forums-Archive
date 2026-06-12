---
title: "The best way to merge Config files."
date: 2015-05-25
forum: General Help
---

### Post by fernando29 on 2015-05-25
Hi.

I was given a .config file containing several settings to support a single board computer (MinnowBoardMax) that uses Bay Trail Intel processor. It is supposed I must merge this file with Ubuntu standard file and compile the kernel, but I have some problems.

In the past, when I needed to build (Ubuntu) kernel, first I used editconfig ([COLOR=#0000FF]$fakeroot debian/rules editconfigs[/COLOR]) and then I built by using scripts ([COLOR=#0000FF]$fakeroot debian/rules binary-headers binary-generic[/COLOR]). . However, the MinnowBoard wiki indicate to merge the .config they provide like this:
[COLOR=#0000ff]$ make defconfig
$ scripts/kconfig/merge_config.sh .config FileToMerge.txt[/COLOR]However when I run [COLOR=#0000FF]$fakeroot debian/rules binary-headers binary-generic[/COLOR], the build process fail after some minutes. Actually, if I have any .config in the kernel root, despite it is the standard Ubuntu one, the process always fails.

So my question is. How can I merge both .config files (the standard and the given by the board) and generate a kernel installer (.deb) that I can use in other machines. 

Thanks.

---

### Post by fernando29 on 2015-05-27
I have posted this question on the MinnowBoard mailing list, but nobody seems to have tested building the kernel if not with:

$ make -j4 && make -j4 modules

However, as far as I know this way does not produce an installer that could be used to other Ubuntu installations.

---

