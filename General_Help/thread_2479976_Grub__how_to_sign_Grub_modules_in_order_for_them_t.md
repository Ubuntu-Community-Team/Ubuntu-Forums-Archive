---
title: "Grub : how to sign Grub modules in order for them to run when secure boot is enabled"
date: 2022-10-14
forum: General Help
---

### Post by georgesgiralt on 2022-10-14
Hello !
As a French Linux user, I wanted to have a French keyboard under Grub. This is relatively easy to do and it works when secure boot is not enabled. 
Essentially it use a Grub module "keylayouts.mod" to load a French keyboard definition file I created myself. 
Alas, when using secure boot, the Grub shell complain that keylayouts.mod can't be loaded because it is not signed. 
I thought that re-installing the Grub on the proper disk would solve the problem by, first, loading the modules and embedding them in the Grub EFI binary but it is not. 
The module is actually added, but it is in the same condition as the others. No modules are signed except the shim executable.... 
So how could I get it signed with the proper signature ? 
Many thanks in advance for your answer ! 
Have a nice and bright day !

---

### Post by MAFoElffen on 2022-10-14
Not sure, but have you tried this:
[https://superuser.com/questions/1560481/how-to-secure-boot-efi-images-signed-with-an-installed-custom-key](https://superuser.com/questions/1560481/how-to-secure-boot-efi-images-signed-with-an-installed-custom-key)
[https://ubuntu.com/blog/how-to-sign-things-for-secure-boot](https://ubuntu.com/blog/how-to-sign-things-for-secure-boot)

---

### Post by georgesgiralt on 2022-10-15
Thank you for your answer. 
Alas, even if I have the "proper" key in place (the one in /var/lib/shim-signed/mok/MOK.priv which is Ubuntu's signing key for the shim), I can't figure how to sign a grub module (one in /boot/grub/x86_64-efi, and keylayouts.mod in particular) in order to be able to use this module under Grub to load a keymap... 
And I can't figure how Grub can use modules such as ext4.mod, lvm.mod and so on.... and how they are/where signed... 
So I'm as dumb as I was a couple of days ago. 
Have a nice and bright day !

---

### Post by dragonfly41 on 2022-10-15
I am thinking intuitively that rEFInd might bypass such issues.

[https://teejeetech.com/2020/09/05/linux-multi-boot-with-refind/](https://teejeetech.com/2020/09/05/linux-multi-boot-with-refind/)

Moreover you can write your own theme in French to view in rEFInd GUI.

Other than that idea perhaps use Cubic to customise boot process.

Or possibly both.

These are just seeds of ideas.

---

### Post by georgesgiralt on 2022-10-15
Hi !
A quick look at ReFind shows that it's use with Secure Boot enabled is somewhat difficult. 
So maybe not the easiest path to a solution...But who says the easiest past is the better.....
If I find something useful, I'll report back.

---

### Post by #&amp;thj^% on 2022-10-15
I find no mention of how your trying this process....are you trying with "grub-mkstandalone"**_ that's just a question and not a suggestion._**
EDIT: Never Mind, I picked up on:
> I thought that re-installing the Grub on the proper disk would solve the problem by, first, loading the modules and embedding them in the Grub EFI binary but it is not. 

---

### Post by dragonfly41 on 2022-10-15
> **georgesgiralt said:**
> Hi !
A quick look at ReFind shows that it's use with Secure Boot enabled is somewhat difficult. 
So maybe not the easiest path to a solution...But who says the easiest past is the better.....
If I find something useful, I'll report back.

I agree that it looks complicated.
But here is the tutorial .. I have not tried it ..
[https://www.rodsbooks.com/refind/secureboot.html](https://www.rodsbooks.com/refind/secureboot.html)


**Footnote:**

Regarding complexity of above process, read the last paragraph in above tutorial.

[COLOR=#000000][FONT=Ubuntu]"Some of the awkwardness of using rEFInd with Secure Boot is due to the need to manage MOKs (either keys with Shim or hashes with PreLoader). Such problems would evaporate if you could get a copy of rEFInd signed with your distribution's Secure Boot key. Thus, if you're annoyed by such problems, try filing a feature request with your distribution maintainer to have them include rEFInd (and sign it!) with their official package set."[/FONT][/COLOR]

---

