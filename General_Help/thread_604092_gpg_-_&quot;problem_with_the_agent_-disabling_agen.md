---
title: "gpg - &quot;problem with the agent -disabling agent use&quot;"
date: 2007-11-05
forum: General Help
---

### Post by drs305 on 2007-11-05
I was making a gpg key and everything went fine. Then I decided to delete it and was unable to do so. Every time I got to the point of entering the passphrase, a message would appear:
```
gpg: problem with the agent -disabling agent use
```
My attempts to delete the key were unsuccessful as after this message it wouldn't accept my passphrase. I assume the two are related.

I've searched the internet and although there are many references to the phrase, I can't find any solutions.

Any ideas how to fix this. I have not altered any config files although I did see that "use-agent' is in the gpg.conf file.  Note: I'm not looking to become a gpg expert but if there is a simple solution I'd certainly like to see it.

Thanks.

---

### Post by jozef.kutej on 2008-01-09
For me it was fixed by ```
sudo apt-get install pinentry-qt
``` in Debian. Should be the same in Ubuntu.

---

### Post by drs305 on 2008-01-09
jozef.kutej, thanks.

I moved on from deleting that entry, but ever since I have been living with the 'disabling agent use' message whenever I tried encoding or decoding something with GPG. It didn't seem to affect the decryption but getting an error message was an annoyance. Installing pinentry solved it.

---

### Post by pirxx on 2008-02-07
Briliant advice, thank you so very much!

---

