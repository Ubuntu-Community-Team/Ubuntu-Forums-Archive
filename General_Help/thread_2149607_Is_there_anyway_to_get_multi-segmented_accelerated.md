---
title: "Is there anyway to get multi-segmented accelerated FTP downloads?"
date: 2013-05-29
forum: General Help
---

### Post by FulciLives on 2013-05-29
Hello!

I'm looking for a solution as to how I can download from a FTP site but get multi-segmented accelerated downloads.

You see some of the files I'm downloading are very large, often 4GB - 8GB in size, and FileZilla just doesn't cut it on these larger files. Now I also have HTTP(S) access (as well as FTP access) so I often will download the very large files using uGet which does give me multi-segmented accelerated downloads (thanks to the aria2 plug-in). So it breaks those large files up into chunks (I set it to 10 chunks) and this speeds up the download by a vast amount.

The problem is I want to keep a certain directory style. In other words when I download a folder I want that folder and all the files in it plus any sub-folders and any files in them. That's easy with FTP but then it bogs down on the large files.

In Windows I use a program called FDM (Free Download Manager) and this is a download manager that works a bit like uGet but it also has a "Site Explorer" where I can connect via FTP and select a folder and it grabs everything under that folder (all files and all sub-folders and all files in those sub-folders etc.) and it does so in such a way that it is able to use it's built-in multi-segmented feature for accelerated downloads of large files.

Alas I can't seem to find a way to do this with uGet or any of the other Linux downloaders that I've looked at ... so I'm hoping someone knows of a Linux program and a way to do this.

By the way I've tried using FDM on Ubuntu via WINE but it only partially works (it works if you grab links from a browser or copy and paste them in) but the FTP "Site Explorer" part of it just crashes the program if you try to use it and apparently others have had the same issue (under WINE  use). So that doesn't appear to be an option.

---

### Post by FulciLives on 2013-05-31
Nobody can answer this?

---

