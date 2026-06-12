---
title: "Can't read files on Samba share..."
date: 2008-04-03
forum: General Help
---

### Post by eriqjaffe on 2008-04-03
I have a PC in my living room running GeexBox patched to provide an anonymous read-only Samba share, which works flawlessly when I connect from XP, but I'm running into some odd behavior on Hardy...

I can mount the share fine (either using mount -t smbfs or mount.cifs) and I can list the contents of the share without issue:

```
eriq@eriq-desktop:~/Music/rock/Voxtrot/Voxtrot$ ls -l
total 64448
-rwxr-xr-x 1 eriq eriq 4927488 2007-12-15 10:50 01. Introduction.mp3
-rwxr-xr-x 1 eriq eriq 6817792 2007-12-15 10:50 02. Kid Gloves.mp3
-rwxr-xr-x 1 eriq eriq 7319552 2007-12-15 10:50 03. Ghost.mp3
-rwxr-xr-x 1 eriq eriq 4847616 2007-12-15 10:50 04. Stephen.mp3
-rwxr-xr-x 1 eriq eriq 5914624 2007-12-15 10:50 05. Firecracker.mp3
-rwxr-xr-x 1 eriq eriq 6119424 2007-12-15 10:50 06. Brother In Conflict.mp3
-rwxr-xr-x 1 eriq eriq 5623808 2007-12-15 10:50 07. Easy.mp3
-rwxr-xr-x 1 eriq eriq 5498880 2007-12-15 10:50 08. Future Pt. 1.mp3
-rwxr-xr-x 1 eriq eriq 6864896 2007-12-15 10:50 09. Every Day.mp3
-rwxr-xr-x 1 eriq eriq 5146624 2007-12-15 10:50 10. Real Life Version.mp3
-rwxr-xr-x 1 eriq eriq 6606848 2007-12-15 10:50 11. Blood Red Blood.mp3
-rwxr-xr-x 1 eriq eriq  115065 2007-12-15 10:50 Voxtrot.jpg
```

...but any attempts at reading the files leads to errors:

```
eriq@eriq-desktop:~/Music/rock/Voxtrot/Voxtrot$ feh Voxtrot.jpg
Bus error (core dumped)
```

```
audacious "01. Introduction.mp3"
Unable to read from file:////home/eriq/rock/Voxtrot/Voxtrot/01. Introduction.mp3, giving up.
Unable to read from file:////home/eriq/rock/Voxtrot/Voxtrot/01. Introduction.mp3, giving up.
Unable to read from file:////home/eriq/rock/Voxtrot/Voxtrot/01. Introduction.mp3, giving up.
Unable to read from file:////home/eriq/rock/Voxtrot/Voxtrot/01. Introduction.mp3, giving up.
Unable to read from file:////home/eriq/rock/Voxtrot/Voxtrot/01. Introduction.mp3, giving up.
Unable to read from file:////home/eriq/rock/Voxtrot/Voxtrot/01. Introduction.mp3, giving up
```

...any ideas what might be going on?  FWIW, I'm using Hardy on this system, I'll have to test the behavior on my Gutsy laptop later on.

---

### Post by eriqjaffe on 2008-04-05
Hmm.  Following up on this, I can successfully use the share from my Gutsy laptop, so I'm wondering if it's a problem with either Hardy or smbfs 3.0.28a.  I suppose I could roll back to the 3.0.26 and see if that fixes things...

---

