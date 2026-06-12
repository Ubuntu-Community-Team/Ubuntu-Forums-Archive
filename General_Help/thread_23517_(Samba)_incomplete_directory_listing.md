---
title: "(Samba) incomplete directory listing"
date: 2005-04-02
forum: General Help
---

### Post by fa2k on 2005-04-02
Hi, I have a weird problem with Samba (probably). In a specific directory, on a SMB mount, Nautilus shows up no files. The directory really contains 393 files, mostly directories and 140 mp3 files. When I press Refresh, it lists 127 files, both mp3 and directories. ls and the Xmms file browser shows no files. Alle files are accessible by their full path. The directory is at ~/mnt/shr2/Musikk/. Other directories on the same share, even those containing more than 127 files, are fully listed. The server is running windows 2000 advanced server, and the user har all permissions. ](*,)

---

### Post by fa2k on 2005-04-02
sorry. bad clue removed

---

### Post by fa2k on 2005-05-04
Strange command output, the first obtained by pressing TAB:

```
fa2k@fa:~$ cd mnt/shr2/Musikk/
Display all 127 possibilities? (y or n)
003 Lynyrd Skynyrd - Freebird.mp3
01 Abandonned, Pleased, Brainwashed, Exploited.mp3
01-[Carlos]-The Silmarillia.mp3
01 - Metallica - Frantic.mp3
-snip-
(1994) Oasis - Definitely Maybe/
fa2k@fa:~$ cd mnt/shr2/Musikk/
fa2k@fa:~/mnt/shr2/Musikk$ ls
fa2k@fa:~/mnt/shr2/Musikk$ ls -l q.mp3
-rwxr-xr-x  1 fa2k root 6861930 2004-07-14 22:25 q.mp3
fa2k@fa:~/mnt/shr2/Musikk$ ls -l q*
ls: q*: No such file or directory
fa2k@fa:~/mnt/shr2/Musikk$ ls ..
Appz  Games  Musikk  OS  Series
fa2k@fa:~/mnt/shr2/Musikk$ ls -l Offspring
total 12
drwxr-xr-x  1 fa2k root 4096 2004-09-27 13:29 Offspring - americana
drwxr-xr-x  1 fa2k root 4096 2004-09-27 13:29 Offspring - Conspiracy of one (2000)
drwxr-xr-x  1 fa2k root 4096 2004-09-27 13:29 Offspring - Smash
fa2k@fa:~/mnt/shr2/Musikk$ smbclient //fa2k/Share2 *** -D Musikk -c ls | wc
Domain=[FA2K] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
    404    4583   32315
fa2k@fa:~/mnt/shr2/Musikk$

```

the smb password is hidden. the smbclient gets the correct listing, I ran it through wc so this post wouldn't get too long

---

