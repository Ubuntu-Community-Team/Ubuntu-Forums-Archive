---
title: "mkisofs changes filenames"
date: 2008-02-11
forum: General Help
---

### Post by deavik on 2008-02-11
Hello there,

I have a strange problem where I am trying to make a CD image of a directory on my harddrive, but mkisofs strangely changes the filenames, from MixedCase to lowercase, and even truncates filenames to shorter names.

I am running it on a ntfs-3g partition, I don't know if that has anything to do with it.

I really need the filenames to be the same in the iso created, does anyone have any tips?

Thanks!

---

### Post by DoctorMO on 2008-02-11
The CD ISO data format doesn't allow long filenames or mixed case filenames. You can add on what are known as extentions which allow long file names and mixed case. these do come with their own set of problems but none that should worry you.

Your looking for the jollet and other extensions. you may need to research both the mkisofs man page and the internet to learn more about iso. You can also use a CD creation program such a k3b which will take care of these problems for you.

---

