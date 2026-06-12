---
title: "Wubi - install failure modified bootloader"
date: 2007-09-24
forum: General Help
---

### Post by cliff0108 on 2007-09-24
This is VERY annoying

The spash screen for Wubi claims "Wubi is safe It does not require you to modify the partition of your PC, or to use a different bootloader".

When I tried to instal wubi 7.04 to my Win 98 computer I get an error message part way through that says " Please download manuallly the disired (sic) alternate ISO into c:\wubi\install"

- NO information is given as to where I would get this "alternate ISO" or WHICH alternate ISO - or for that matter what to do with it . Do I just place the ISO in the directory or what? Shades of the stupid microsoft "help" messages ...?

I another posting that did not solve my problem, I was directed to download "ubuntu-7.04-alternate-i386.iso" which I did and pasted into the c:\wubi\install folder . Not knowing what else to do I then re-involked  wubi 7.04 install.exe and it went through the identical process as before telling me once again " Please download manuallly the disired (sic) alternate ISO into c:\wubi\install"

I go to re-boot and I get the BLACK option screen 1 boots to windows 2 to ubuntu. Both go to Windows.

_I want to get rid of this screen._

I am told to uninstall and as wubi does appear in Add/Remove Programs I select it for uninstall and it purposted to do that but when I re-boot it goes to the SAME BLACK OPTION screen.

It would seem that Wubi has modified my bootload file and gives me NO instructions whatsoever on what to do about it and this is _certainly contrary to th information provided on the initial splash screen_.

I would like to either 1. Get Wubi up and running on this machine or 2. Get rid of it, including putting the machine mack to where it was before I attempted the install.

Thanks for reading this harangue - but I am mildy annoyed.
Cliff

---

### Post by ago on 2007-09-24
> **cliff0108 said:**
> When I tried to instal wubi 7.04 to my Win 98 computer I get an error message part way through that says " Please download manuallly the disired (sic) alternate ISO into c:\wubi\install"
That has been corrected in 7.10, please be patient, that will be released "soon".

> 
- NO information is given as to where I would get this "alternate ISO" or WHICH alternate ISO - or for that matter what to do with it . Do I just place the ISO in the directory or what? Shades of the stupid microsoft "help" messages ...?

In fact there is a bug in the old code so that you would still see the same error even if you download separately. Again, 7.10 does not have this issue.

> 
_I want to get rid of this screen._

Edit config.sys, there should be a wubi section in there, you can safely remove it.

---

### Post by cliff0108 on 2007-09-24
Thanks !

---

