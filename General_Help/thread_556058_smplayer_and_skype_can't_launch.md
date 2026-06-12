---
title: "smplayer and skype can't launch"
date: 2007-09-20
forum: General Help
---

### Post by championeer on 2007-09-20
I updated a file, it is likely something about [COLOR="Red"]QT[/COLOR], then my smplayer and skype can't start , when I run them in terminal, the error was below:

```
smplayer: symbol lookup error: /usr/lib/libQtNetwork.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv
```

I checked this file ( libQtNetwork.so.4) , it seems to be good, at least I can't find any problems:confused:, who guys can help me ??

my machine: Dell D620, Ubuntu 7.04

---

### Post by rvm4000 on 2007-09-21
Probably a symbol have been changed in the new Qt version (this shouldn't happen, all Qt 4.x releases should be binary compatible with previous onces, but probably it has been patched by kubuntu or debian).

You can probably fix the problem by recompiling those two programs.

---

### Post by mrf76 on 2007-11-09
Same problem for me solved by removing duplicate libQT4 librares. In my case it was lib path /opt/nessus/lib in /etc/ld.so.conf file. After removing run ldconfig. Hope it helps.

Gutsy, Skype 2.0 beta.

---

### Post by freed0m on 2007-11-11
> **mrf76 said:**
> Same problem for me solved by removing duplicate libQT4 librares. In my case it was lib path /opt/nessus/lib in /etc/ld.so.conf file. After removing run ldconfig. Hope it helps.

Gutsy, Skype 2.0 beta.

Thanks.

---

### Post by e_double on 2008-01-09
> **mrf76 said:**
> Same problem for me solved by removing duplicate libQT4 librares. In my case it was lib path /opt/nessus/lib in /etc/ld.so.conf file. After removing run ldconfig. Hope it helps.

Gutsy, Skype 2.0 beta.

Great! Removing /opt/nessus/lib from /etc/ld.so.conf worked for me too.

Thanks.

---

### Post by wormser on 2008-03-12
> **mrf76 said:**
> Same problem for me solved by removing duplicate libQT4 librares. In my case it was lib path /opt/nessus/lib in /etc/ld.so.conf file. After removing run ldconfig. Hope it helps.

Gutsy, Skype 2.0 beta.

Thanks.  It is now working!

---

### Post by ofirp on 2008-03-18
It's not working for me, I don't even have nessus libraries on my system and I'm still getting the same error message.

---

### Post by LoXieL on 2008-03-26
> **mrf76 said:**
> Same problem for me solved by removing duplicate libQT4 librares. In my case it was lib path /opt/nessus/lib in /etc/ld.so.conf file. After removing run ldconfig. Hope it helps.

Gutsy, Skype 2.0 beta.

thanks man, work for me too

:)

---

### Post by baeda on 2008-05-26
ofirp, may be this helps you:

In my case, I also got the error:

symbol lookup error: /usr/lib/libQtNetwork.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

The ld.so.conf file was ok, the following solution worked for me:
I added medibuntu to the repository, see: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu),

then you will find skype in synaptic. Remove the old package and install skype-common and skype-static.

After this, skype was running...

---

