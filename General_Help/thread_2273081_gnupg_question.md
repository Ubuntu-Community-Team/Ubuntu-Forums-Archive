---
title: "gnupg question"
date: 2015-04-10
forum: General Help
---

### Post by GrouchyGaijin on 2015-04-10
I am running 14.04 64 bit with Thunderbird as the primary email program.
I have Enigmail installed.  Recently Thunderbird was updated automatically to version 31.6.0.

I noticed after the update that I could no longer send or decode encrypted mail.  I was a bit irritated and wasn't sure how to revoke a key when I no longer had access to the key.  In the end, I looked in ```
~/.gnupg
``` and saw that for some reason my pubring.gpg file was set to root and Thunderbird could not access it.

I solved the issue with a work around of changing the permissions on the file.  Once I did that, Thunderbird could read the pubring file again and I was able to send and receive encrypted messages.

This seems pretty strange to me and I don't think my solution is recommended.  My question is why would this happen and what can I do to prevent it from happening the next time Thunderbird is updated?

---

### Post by matt_symes on 2015-04-10
Hi

> I solved the issue with a work around of changing the permissions on the  file.  Once I did that, Thunderbird could read the pubring file again  and I was able to send and receive encrypted messages.

This seems pretty strange to me and I don't think my solution is recommended

I think the way you solved the issue was not a "workaround" but the actual fix. 

Sounds like something went wrong with the update as it should have not changed the permissions of any files in ~/.gnupg.

Wait to see if it happens again when you next update Thunderbird and Enigmail.

Out of interest, what version of enigmail are you using ? I am currently getting a warning about an impending incompatibility between Enigmail and gpg.

Kind regards

---

### Post by GrouchyGaijin on 2015-04-11
Thanks Matt,

Now that you mention it, I wonder if that had something to do with the problem.
I got that warning message too and updated.  If I remember correctly I updated gpg to version 2.0.22

When I just checked, however, I have _two_ versions of gpg installed.  I wonder if that caused the problem?  I bet it has something to do with it.

```
gpg2 --version
gpg (GnuPG) 2.0.22


```

 and 
```
gpg --version
gpg (GnuPG) 1.4.16


```

To asnwer your actual question ;) I am using Enigmail version 1.8.1 (20150323-1740)

---

### Post by matt_symes on 2015-04-11
Hi

What version of pgp is Enigmail using on your PC ?

On my machine, i'm using.....

> **Running Enigmail version 1.8.1 (20150323-1740)**     
               
           
Using gpg executable /usr/bin/gpg to encrypt and decrypt

.. but still using...

```
matthew-laptop:/home/matthew:2 % /usr/bin/gpg --version
gpg (GnuPG) 1.4.16
```

I'm wondering if it happened when you installed gpg at version 2.x.x.

Kind regards

---

### Post by GrouchyGaijin on 2015-04-11
> **matt_symes said:**
> Hi



I'm wondering if it happened when you installed gpg at version 2.x.x.



That is my guess.

Because Enigmail is using ```

Using gpg executable /usr/bin/gpg2 to encrypt and decrypt
``` 
and the pubring.gpg file is in ```
~/.gnupg
```

---

### Post by matt_symes on 2015-04-15
Hi

I would wait to see what happens when you next update Thunderbird and/or Enigmail and/or gpg :)

Kind regards

---

