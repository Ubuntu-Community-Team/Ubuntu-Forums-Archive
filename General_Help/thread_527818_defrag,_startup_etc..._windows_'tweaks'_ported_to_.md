---
title: "defrag, startup etc... windows 'tweaks' ported to ubuntu needed or not?"
date: 2007-08-17
forum: General Help
---

### Post by Guyver1 on 2007-08-17
Hi, 

I've always been very 'neat & tidy' when it comes to my PC. I like my drives regularly defrag'd (with Perfect Disk 8, we all know windows built in defrag is crap), also one of the first 'tweaks' you learn as a windows user is to remove un-needed startup apps either manually through the registry or through an app like TweakAll. 

So, now i've made that brave leap to a brave new world of Ubuntu, are there 'nix equivelants? do you need them? is there a linux defrag tool out thats as good as perfect disk? are there any other 'tweaks' that i should know about (in the same manner as you learn tweaks as you begin to learn windows)

cheers in advance for any advice/tips/apps that can help me keep my PC in tip top shape :)

---

### Post by HermanAB on 2007-08-17
Defragmenting is only needed on the file systems of yesteryear.  Windows NTFS, Linux ReiserFS, Ext3, Ext2, JFS and XFS are all immune to fragmentation.

As far as desktop tweaks are concerned, Linux has more than you can shake a stick at (especially KDE on Kubuntu) and it is all open and accessible - no need for 'XP Power Toys', just explore the configuration menus.

Cheers,

Herman

---

### Post by Steveway on 2007-08-17
NTFS does get defragment, pretty fast actually but not as fast as Fat.

---

### Post by Guyver1 on 2007-08-17
> **HermanAB said:**
> Defragmenting is only needed on the file systems of yesteryear.  Windows NTFS, Linux ReiserFS, Ext3, Ext2, JFS and XFS are all immune to fragmentation.

no file system is 'immune' to fragmentation, if files are added, moved, deleted, resized then fragmentation is inevitable, files do not just convieniently fit into cluster sizes perfectly every time.

---

### Post by Steveway on 2007-08-17
ext3 and other actual filesystems on Linux only fragment if they get filled up at about 95% of the space.
Forget everything you have learned. Little fool, how has Microsoft blinded you?
EDIT: Read this: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by K.Mandla on 2007-08-17
> **Guyver1 said:**
> Are there 'nix equivelants? do you need them? is there a linux defrag tool out thats as good as perfect disk? are there any other 'tweaks' that i should know about (in the same manner as you learn tweaks as you begin to learn windows)
I keep a collection of speed tweaks and ideas (including links to a defragmenter for Linux -- gasp!) [here]("http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/"), as a guide. Ideally it's meant for older computers, but you might want to look over it and see if there's anything that interests you. I'd give you the links to the individual posts where they're mentioned, but there are too many and half of them you wouldn't need. ;)

---

### Post by Guyver1 on 2007-08-17
> **Steveway said:**
> ext3 and other actual filesystems on Linux only fragment if they get filled up at about 95% of the space.
Forget everything you have learned. Little fool, how has Microsoft blinded you?
EDIT: Read this: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

that was a great webpage and a great explanation!! 

as yoda once said... 'unlearn what you have learned'

---

