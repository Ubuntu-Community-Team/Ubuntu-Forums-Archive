---
title: "Permission Denied on Lubuntu 17.10.1"
date: 2018-03-04
forum: General Help
---

### Post by ghostbacon on 2018-03-04
Sorry, I am a noob to Linux as a whole.

I was following the instructions of this post ([http://wiki.serviio.org/doku.php?id=how ... all:ubuntu]("http://wiki.serviio.org/doku.php?id=howto:linux:install:ubuntu"))  when i got to step 3, i followed what it said and created a script. It  says "Permission Denied" when i copy it over or save the text document into that folder. I am an administrator on the account, Do i have  to be a higher rank, if so, how do i do it? I have the latest version  of Serviio and lubuntu 17.10.1.

I understand that posting on this forum should be questions about Ubuntu but the serviio forums are dead.

---

### Post by oldos2er on 2018-03-04
You'll need to use "sudo" to copy a file to /etc/init/, so ```
sudo cp serviio.conf /etc/init/
```

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more info.

---

