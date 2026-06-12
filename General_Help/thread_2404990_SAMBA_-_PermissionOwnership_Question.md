---
title: "SAMBA - Permission/Ownership Question"
date: 2018-10-31
forum: General Help
---

### Post by jp-tp1 on 2018-10-31
Hi all!

I am currently working in a small office environment. I am using SAMBA to create network shares for multiple users. I have two groups I am utilizing **staff** and **trainees** to distinguish permissions, so to speak. I have created a list of sub-directories which are in **/etc/skel**. Effectively every time I create a user, a folder structure appears in their home directory. The thing is, I want the trainees to be able to write into the sub-directories but not be able to delete the directories. Is there a way to do this in the smb.conf file or do I set permissions in the /etc/skel section?

Any help would be great!

Cheers.

---

