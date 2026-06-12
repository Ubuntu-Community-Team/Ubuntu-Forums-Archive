---
title: "New Ubuntu User"
date: 2005-04-19
forum: General Help
---

### Post by zaxer on 2005-04-19
Hello guys!

I've just installed Ubuntu's Hoary Hedgedog and love this OS, its just awesome.

Im trying some new stuff for me (win user) and one of those is apt-get. I tried a apt-get update and got this error message.

```

GPG error: ftp://ftp.nerim.net testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
```

Can you help me?

Thanks in advance.

---

### Post by bored2k on 2005-04-19
You can still use that repository by the way ;).

---

### Post by andvaranaut on 2005-04-19
[QUOTE=zaxer]Hello guys!

I've just installed Ubuntu's Hoary Hedgedog and love this OS, its just awesome.

Im trying some new stuff for me (win user) and one of those is apt-get. I tried a apt-get update and got this error message.

```

GPG error: ftp://ftp.nerim.net testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
```

Can you help me?

Thanks in advance.[/QUOTE]
 Don't worry very much - the error you see won't affect your ability to install marillat packages.
See [http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary](http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary) to remove it.

Cheers

---

### Post by shakin on 2005-04-19
[QUOTE=zaxer]Hello guys!

I've just installed Ubuntu's Hoary Hedgedog and love this OS, its just awesome.

Im trying some new stuff for me (win user) and one of those is apt-get. I tried a apt-get update and got this error message.

```

GPG error: ftp://ftp.nerim.net testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
```

Can you help me?

Thanks in advance.[/QUOTE]

The full answer is that official repositories are authenticated with a private/public key pair. It helps ensure that you are actually connecting to the repository you think you are connecting to.

This unofficial repository doesn't have a private/public key pair. The message you got is a warning about that. In this case, it's expected so you don't have to worry about it and can continue installing software from that repository.

---

### Post by zaxer on 2005-04-19
[QUOTE=shakin]The full answer is that official repositories are authenticated with a private/public key pair. It helps ensure that you are actually connecting to the repository you think you are connecting to.

This unofficial repository doesn't have a private/public key pair. The message you got is a warning about that. In this case, it's expected so you don't have to worry about it and can continue installing software from that repository.[/QUOTE]
 Thanks for your info guys!

I have to learn so many things yet... =)

---

