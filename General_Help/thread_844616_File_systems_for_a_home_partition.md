---
title: "File systems for a /home partition?"
date: 2008-06-29
forum: General Help
---

### Post by Goombie on 2008-06-29
I have a ~25GB partition formatted for fat32, on which I keep all my personal data. I've seen a couple guides on the internet on how to make your own partition for the /home folder in Ubuntu, and I would like to do that. Before I do, though, I have one question: Does the home partition need to be formatted for the ext3 filesystem, or can I use the partition I currently have, which is fat32 formatted? Thanks!
:popcorn:

---

### Post by geirha on 2008-06-29
I recommend you use ext3. You are likely to encounter odd problems if you use fat32 for /home. 

To mention a few things that may give you problems, 

fat32 only allows a limited set of characters in filenames. '?' and '+' for example are not allowed. On ext3, you can have every character you can think of, except '/' which is used as path delimiter, and '\0', the string terminator. Programs tend to store configuration in your home-folder, and if it fails to create a file because it contains an illegal character, you might see odd behavior.

Fat32 does not have permissions and ownership, so you can't keep your files protected from other users. I.e. all users will have read and write access to all files in /home. Which happens to also be a major security risk.

---

