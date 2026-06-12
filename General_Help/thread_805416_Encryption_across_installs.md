---
title: "Encryption across installs"
date: 2008-05-23
forum: General Help
---

### Post by armitage1337 on 2008-05-23
Hi,

I'm thinking about implementing OS-wide encryption (i.e. except for /boot), but I was wondering what would happen when I reinstalled, with the same, separate /home partition - how would the new install be able to access the /home partition encrypted by the old install? Would I just have to use the same OS password?

Thanks in advance for the help!!!

---

### Post by Steve413z on 2008-05-23
the easiest way to do that, (the way I do it) is to back up your home directory to an external hard drive, do a fresh ubuntu install with the text installer, and then restore the home directory

---

### Post by armitage1337 on 2008-05-24
You mean back it up unencrypted? If this is the only way to do it, I might as well keep /home in the same partition as / .

---

### Post by Steve413z on 2008-05-24
> **armitage1337 said:**
> You mean back it up unencrypted? If this is the only way to do it, I might as well keep /home in the same partition as / .

thats the way I do it, and I do it like that every time there is a new version of Ubuntu out, I do a fresh install

---

### Post by armitage1337 on 2008-05-25
Yeah, I always do a fresh install, which is why I'd rather keep the /home partition separate. But since this is a laptop (hence the encryption) I'm going to be regularly backing up my /home directory to a desktop/server anyway, so I guess it wouldn't be too much trouble to just move the /home directory back after reinstall.

---

