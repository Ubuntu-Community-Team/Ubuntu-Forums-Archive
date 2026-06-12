---
title: "Drive Encryption With Ubuntu 12.04"
date: 2013-10-29
forum: General Help
---

### Post by Vannyi on 2013-10-29
I'm probably using the wrong terminology, but the older versions of Ubuntu had an alternative CD which people could use to encrypt their hard drive.

The later versions have drive encryption included as part of the base install.  When I installed Ubuntu 12.04, there was no option to encrypt the drive.  I'm just wondering, the application that is now available in 13.x to encrypt drives, is it available as an individual install through the software center so that I can go back and encrypt my drive.

Thank you

---

### Post by Vannyi on 2013-11-02
Anyone?

---

### Post by DuckHook on 2013-11-02
I'm not aware of a way to encrypt the whole drive after the fact. This is usually done during the initial install process.

I'm usually the first to preach security, but you should reconsider encrypting your whole drive. It tends to bite you hard when trouble hits, and it's like pulling teeth to solve *any* problem that requires a LiveDVD type solution.

Unless the NSA is after you, most people only need to encrypt their /home directory anyway. Even finer control is possible by encrypting only key data directories. This is what I do. It tends to avoid issues like breaking remote SSH logins due to the .ssh directory being not yet decrypted at the lightdm login stage. You have to move your e-mail, private keys, firefox password/history directories, etc into the private directory and symlink back to their original locations, but this is easy and only needs to be done once. [Here]("https://help.ubuntu.com/community/EncryptedHome") is the link to encrypting either your /home or a ~/.Private directory. It can be done after the fact.

Be forewarned--if you lose your encryption pass-phrase there is *no way* to retrieve your data. Make sure you create a good high-entropy pass-phrase, but then print it out and keep it locked away in a safe place.

---

