---
title: "Bad kernel update caused password problem"
date: 2018-12-23
forum: General Help
---

### Post by Spae on 2018-12-23
In the previous week I allowed an update which caused an error message, which I didn't think much of. However, when I restarted my password (system encryption) was being rejected, and I thought I must be confused and entering it wrong. 

However, I decided to boot from 4.18.0-13-generic to an earlier kernel version and my password was accepted. It still automatically goes for 4.18.0-13 though, so my first question would be how to delete or rather have my system choose a functional kernel on boot.
 
How could this happen? I mean it's the most obscene kind of bug imaginable. Giving someone the exact same message that they would receive on a wrong password.

Now I have trouble on a main file drive (separate from system) rejecting my password, although this is more likely to be my memory than my system pass. I don't know. This drive isn't used to boot so i assume it's not the same bug..? But I swear i'm entering the right password. It's a coincidence for both of these to happen in the same week, but totally possible.

---

### Post by ubname on 2018-12-23
Probably you are using some experimental/development system (?), so I think it is not strange but to be expected instead.

---

### Post by vidtek on 2018-12-23
> **Spae said:**
> In the previous week I allowed an update which caused an error message, which I didn't think much of. However, when I restarted my password (system encryption) was being rejected, and I thought I must be confused and entering it wrong. 

However, I decided to boot from 4.18.0-13-generic to an earlier kernel version and my password was accepted. It still automatically goes for 4.18.0-13 though, so my first question would be how to delete or rather have my system choose a functional kernel on boot.
 
How could this happen? I mean it's the most obscene kind of bug imaginable. Giving someone the exact same message that they would receive on a wrong password.

Now I have trouble on a main file drive (separate from system) rejecting my password, although this is more likely to be my memory than my system pass. I don't know. This drive isn't used to boot so i assume it's not the same bug..? But I swear i'm entering the right password. It's a coincidence for both of these to happen in the same week, but totally possible.

Spae-
This is a way you can remove the new kernel and revert to an older one:

```
uname -r
```
This gives you your present running kernel, do not delete this one!
then: ```
dpkg --list | grep linux-image
```

This gives you a list of all installed kernels.  Make a note of the latest one you want to remove.

Then run this command making sure you put the correct kernel version numbers in place of the x's

```
sudo apt-get purge linux-image-x.x.x.x-generic
```

Then run this command to update your grub:

```
sudo update-grub
```

Reboot and you should be back where you started before the new kernel was installed.

Cheers, Tony.

---

### Post by Impavidus on 2018-12-23
> **ubname said:**
> Probably you are using some experimental/development system (?), so I think it is not strange but to be expected instead.
According to  [https://packages.ubuntu.com/cosmic-updates/linux-image-generic](https://packages.ubuntu.com/cosmic-updates/linux-image-generic), the  latest kernel for Ubuntu 18.10 is 4.18.0-12, so that definitely looks  like an experimental/development system. Problems are to be expected. Have you by any chance enabled the proposed repository?
> **vidtek said:**
> Spae-
This is a way you can remove the new kernel and revert to an older one:


It's not that easy. If you remove the latest kernel, you will automatically remove the metapackage that drew in that kernel. That means you'll no longer get kernel upgrades as they come available. Also, it's not necessary to run update-grub, as that's done automatically by the post-removal script.

---

### Post by vidtek on 2018-12-23
Imp-
I've been doing this method for years and have never had any issues with updates.  Perhaps you are not using the correct command?  Check your syntax.  You are correct with regard to update-grub, but I use a belt and braces approach and like to double check my grub install on a regular basis with this command.
Tony.

---

