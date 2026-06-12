---
title: "File overwritten using &quot;mv&quot;"
date: 2017-07-10
forum: General Help
---

### Post by andrewgerm on 2017-07-10
Good day all

I'm trying to help someone who attempted to move two files into a directory.
However, the file wasn't moved into a sub-directory, but into the file system root, and was named to the sub-directory name. Then, they moved a second file, using the same command (altering only the file to be moved name).

This has resulted in the first file vanishing, and the second now in the root directory, named the same as the initial sub-folder name.

Is there anyway to retrieve the first file? My assumption would be that the second could be retrieved merely by moving it back, correctly, and renaming. But hesitant to do this, before knowing how to retrieve the first file.

Thank you in advance :)

---

### Post by Impavidus on 2017-07-10
I assume this person tried to move the files to a non-existent directory, or a directory with a typo in the command.

For the second file, just move it back. For the first however, it's indeed deleted. The best option is to use a backup or, if it was something simple, to recreate it, or you're in for some file recovery. In that case, don't use the drive until the file has been recovered. If this happened just now, there's a reasonable chance you can get it back. I've never done file recovery myself, but this page may be helpful: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by andrewgerm on 2017-07-10
All your assumptions are correct. I've done recovery for people on a Windows drive before, so also followed your suggested "cautions".
I was a bit hesitant to touch an ext filesystem before checking.

I did find PhotoRec, and after a good many hours, it is still running, so will see what that leads to.
Great resource at that link! Thank you!!

---

### Post by TheFu on 2017-07-10
I doubt you will like what PhotoRec does.  Might be better off using this as a teaching opportunity. You'll see why when it finishes.  Restoring from a backup is 10,000x easier than dealing with photorec.

---

### Post by andrewgerm on 2017-07-11
@TheFu: indeed, I totally agree, and have found a few things to implement for myself (alias for cp and mv, to prevent possible issues).
I am aware of a backup, but do not think it is current. So another thing I shall be implementing.

An initial run of PhotoRec looked scary. Many directories, with countless files.

From this alone, and the links / info provided, I've found a host of resources I never knew existed.

---

