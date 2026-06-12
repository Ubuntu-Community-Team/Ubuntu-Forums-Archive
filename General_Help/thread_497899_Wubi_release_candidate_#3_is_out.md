---
title: "Wubi release candidate #3 is out"
date: 2007-07-10
forum: General Help
---

### Post by ago on 2007-07-10
Get it from the [http://wubi-installer.org](http://wubi-installer.org)

* Fix for invalid username problem
* Added edubuntu
* Disabled hibernation/suspend in gnome
* Minor fixes

---

### Post by ago on 2007-07-10
If all goes well this will be the final version, so please give it a good go.

---

### Post by Brandonson112 on 2007-07-10
Is there anyway to upgrade without reinstalling wubi?

---

### Post by ago on 2007-07-10
If the installation was ok, the only difference from rc1 would be to disable suspend/hibernate, you can use gconf-editor for that.

---

### Post by tinybit on 2007-07-10
FYI, Bean has released grub4dos-0.4.3-2007-07-10, This release fixed a **serious** bug in bootlace **** AND in grldr.mbr **** compared to the 2007-07-09 release. The final should be coming soon(around 2007-7-31, according to the optimistic estimates).

---

### Post by ago on 2007-07-11
> **tinybit said:**
> FYI, Bean has released grub4dos-0.4.3-2007-07-10, This release fixed a **serious** bug in bootlace **** AND in grldr.mbr **** compared to the 2007-07-09 release. The final should be coming soon(around 2007-7-31, according to the optimistic estimates).

Thanks tinybit, I will upgrade it soon with rc3 then. Do I need to use a new version of grubutils as well to generate wubildr?
By the weay I do not see the new release on gna.org yet.

---

### Post by ago on 2007-07-11
I have uploaded rc3, only change is basically grub4dos 2007-07-10, from [http://grub4dos.jot.com/WikiHome](http://grub4dos.jot.com/WikiHome)

---

### Post by tinybit on 2007-07-12
grubutils also updated:

[http://grub4dos.sourceforge.net/grubutil-1.1-bin-w32-2007-07-11.zip](http://grub4dos.sourceforge.net/grubutil-1.1-bin-w32-2007-07-11.zip)

This version works with the grub4dos release of 2007-07-10.

I think the adoption of the new grubinst is a Must.

The sources will be uploaded to gna later(by Bean). But I think they are already stable enough.

----------------

According to Bean ( Translated from Chinese to English by me ):

This version added a  -e  option. It can be used to modify fields in grldr and grldr.mbr

For instance:

grubinst -e -b=mygrldr C:\mygrldr
grubinst -e -b=grldr1 C:\grldr.mbr

grldr is required to be of 2007-07-10 or later.

If any questions, ask Bean please.

---

### Post by ago on 2007-07-12
Tinybit I do not use windows, can you also upload the sources pls?

---

### Post by ago on 2007-07-12
PS Tonight I'll do an rc4 then using the new grubutils + gurb4dos-07-10. 
We will push the final before the 30th, we will have an extra release once grub4dis 4.3 final is out. In the meantime we will use the above. Any objection on your side?

---

### Post by tinybit on 2007-07-12
I will ask Bean to upload the sources to a place, if it is not gna.org, for you.

I think the grubutils and grub4dos are quite ok now, so you may release wubi this w/e.

On the other hand, the grub4dos final could be delayed until next month.

---

### Post by bean123 on 2007-07-12
This is the patch file for the latest 07-10 build, you should update to 07-09(r47) before applying this patch.

---

### Post by tinybit on 2007-07-12
Bean maybe you have not noticed that also grubutil source was wanted.

---

### Post by bean123 on 2007-07-12
grubutil source code:

[http://grub4dos.sourceforge.net/grubutil-1.1-src-2007-07-12.zip](http://grub4dos.sourceforge.net/grubutil-1.1-src-2007-07-12.zip)

---

### Post by ago on 2007-07-12
Thanks bean I used, I am now using grub4dow-2007-07-10 as downloaded from [http://grub4dos.jot.com/WikiHome](http://grub4dos.jot.com/WikiHome)

does that require the patch?

---

### Post by tinybit on 2007-07-12
grub4dos-2007-07-10 is only a binary build. No patch is needed.

If you want to see the source, you need to download 07-09(r47) in gna.org and apply the above patch by Bean.

---

### Post by ago on 2007-07-13
Of course, what I meant was whether the 7-10 binary already included the patch.

---

### Post by ago on 2007-07-13
New minefield includes the grub4dos 07-10

---

### Post by tinybit on 2007-07-13
> **ago said:**
> Of course, what I meant was whether the 7-10 binary already included the patch.

Yes.

---

