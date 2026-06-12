---
title: "grub error 16: inconsistent filesystem"
date: 2006-12-03
forum: General Help
---

### Post by blindmist on 2006-12-03
so my computer locked up for some unknown reason and so i had to hold the power button for 5 seconds to shut it off. when i turned it back on, grub prodeced this message

Error 16: Inconsistent filesystem


do i need to check the disk? ive already reinstalled grub to no avail and everytime i run fsck or fsck -f it just says fsck (version) and goes no further. i really would like to be able to get my computer running without having to reinstall ubuntu because then i am going to have to reinstall TONS of packages. any help?

---

### Post by wilso027 on 2006-12-03
A quick google came up with this:

This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.

If you boot from the live cd can you mount the working partition. Have you tried a fsck on that? Try working with a large file and see if you hear any clicking. That is a sure sign your drive is going out.

Allan

---

### Post by blindmist on 2006-12-03
yeah, i finally got fsck to work and i checked both of my drives and they both came up clean.

the drives are brand new and there is no clicking. i ran the western digital check on them and they checked out perfect. im starting to think that the only way i am going to fix this is to reinstall ubuntu again. :(

both of the drives mount fine and i can read my video files that i am working on perfectly fine, no clicking on either drive. i dont think the drives are going out but now that i do think about it, it locked up while i was installing wine.

---

### Post by blindmist on 2006-12-04
i just formated and reinstalled and its working just fine. i knew it wasnt from a failing hard drive.

---

