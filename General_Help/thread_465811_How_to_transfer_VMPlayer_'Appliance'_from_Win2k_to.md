---
title: "How to transfer VMPlayer 'Appliance' from Win2k to Feisty"
date: 2007-06-06
forum: General Help
---

### Post by longlegs on 2007-06-06
Hi !
I have DOS 7.1 with USB, CD, long file name and NTFS supported, installed on a 1g virtual drive running in VMPlayer 2.0 under Win2k.

I have a second comp running Feisty, to which I have downloaded VMPlayer linux version.

Is it possible to transfer files from Win2k to Feisty such that the VMPlayer can use them, so that I do not have to re-install all the DOS stuff?

The files in my VMPlayer DOS dir are
1GB.vmdk
Dos5VM.vmdk
Dos5VM.vmsd
Dos5VM.vmx
Dos5VM-s001.vmdk
nvram
vmx86.sys

and sometimes I see a .lck file, usually 0bytes.

all help appreciated
Thanks
Longlegs

---

### Post by longlegs on 2007-06-09
Hi !
I finally got VMPlayer 2.0 on my Ubuntu computer. Then made a "projects" dir and copied the files from my win2000 comp to that dir. Then started VMPlayer. It let me browse for those files (looking for a .vmx ) and my VM from win2k worked just fine.
There were 8 files :
xxxx.vmdk
xxxx.vmem
xxxx.vmsd
xxxx.vmss
xxxx.vmx
xxxx-s001vmdk this is the result of a suspend operation and won't exist sometimes
nvram
vmx86.sys
As is usual, it's easy once you find out HOW!
Have a good day!
longlegs

---

