---
title: "BusyBox (initramfs)"
date: 2008-01-08
forum: General Help
---

### Post by MakuseruSukotto on 2008-01-08
hi. im not coming off a new install or upgrade or anything, i dont remember what i did. but the last time i restarted my computer it wouldnt boot up properly. it goes past the grub then instead of getting my login screen i get a terminal-like screen and it says "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) built-in shell (ash)" then it drops down and instead of my username it says "(initramfs)" in a terminal style prompt. i have limited commands while in this, but i can tell that i am on my main partition because im able to cd through folders. i looked around the internet and the most common responce was to remove "quiet splash" and add "all_generic_ide" to the thing in the grub (pressing escape then e for edit and b to boot it up) but that didnt work for me. a few sites i looked at also suggested just messing with "noacpi, nodma, noapic, and nolapic" i tried each one of those, with and without the "quiet splash" there and none of it worked. What is this problem, and how can i fix it? Thanks in advance for the help.

---

### Post by MakuseruSukotto on 2008-01-08
anyone?

---

