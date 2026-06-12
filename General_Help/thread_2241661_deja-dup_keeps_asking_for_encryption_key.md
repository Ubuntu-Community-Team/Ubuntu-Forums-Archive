---
title: "deja-dup keeps asking for encryption key"
date: 2014-08-27
forum: General Help
---

### Post by eduardosilva on 2014-08-27
Greetings,

I'm setting up my deja-dup backup to mount a remote smb share on my Time Capsule. Deja-dup was able to mount the share and start the first backup ok. As soon as it starts the backup, it asks me if I want to use an encryption key, after typing my encryption key (also checked the option to remember key) it starts backing up but every 30 to 60 seconds the backup pause and ask my encryption key again

Any ideas of how to make deja-dup really remember my encryption key?

Using ubuntu 14.04 amd64 / gnome-session-flashback / mbair

thank you

---

### Post by eduardosilva on 2014-08-28
Seens that I found the solution here: [http://askubuntu.com/questions/462085/deja-dup-repeatedly-asks-encryption-password](http://askubuntu.com/questions/462085/deja-dup-repeatedly-asks-encryption-password)

the folder .gnupg was owned by root, after changing ownership to my user, dejadup looks to be running as it should.

---

