---
title: "Kubuntu 14.04: Mysterious directory deletion after cut/paste"
date: 2014-09-18
forum: General Help
---

### Post by kevinfishburne on 2014-09-18
I'm using Kubuntu 14.04 on my file server and a workstation. There is a symlink on the desktop of my workstation pointing to a directory on an nfs share on my file server. I cut and pasted two directories on my workstation desktop (stored locally) into a directory within the nfs symlink. It began moving the files, then complained that it couldn't remove a directory. I chose "skip", which I had to do again for a second directory. After the move finished, the target symlink (to the nfs directory) was empty. Previously it had contained several directories full of files. The workstation and file server Trash directories are empty. From the file server I used testdisk to attempt to browse/copy the deleted directories to an external drive. It showed the first level of directories inside the symlink target, but none of the files or subdirectories within them and said the partition may be damaged (probably a generic error message). I'm currently using photorec to attempt to recover the files.

Does anyone know what happened? My only clue was that after the cut/paste operation I noticed the symlink on my desktop was "ghosted", as if I'd accidentally marked it to be cut/pasted. If you cut/paste a symlink it just moves the symlink, not the data it points to, so I really have no idea how a cut/paste mishap could nuke an entire directory structure across an nfs share. This is very strange and while I thought I'd been backing this data up via my normal backup script I in fact had not. I'm trying not to completely freak out...so far so good, but this is looking ugly. Any help or insight is appreciated.

---

### Post by kevinfishburne on 2014-09-18
Okay, Dropbox flat out saved my ass right as I was sharpening my katana and preparing for an honorable death. Nevertheless it would be nice to know what happened. Kinda scary that hitting Ctrl-X, Ctrl-V can nuke your **** from orbit like that though. I'd still appreciate any insight anyone has into what may have happened.

---

