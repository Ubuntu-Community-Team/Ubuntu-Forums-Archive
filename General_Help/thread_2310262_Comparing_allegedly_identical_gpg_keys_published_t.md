---
title: "Comparing allegedly identical gpg keys published through different channels"
date: 2016-01-17
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2016-01-17
I'm trying to learn the whole gpg thing and practice using it correctly. A crucial step is verifying that a public key does in fact belong to the party it is supposed to. In the absence of a chain of personal contacts, the obvious thing is to get multiple copies from different sources and verify that they are identical. I never can seem to do that. I suspect that part of the problem lies in newlines, carriagereturns, spaces, tabs, and other characters invented by the SCOPTDLRFI (Secret Conspiracy Of Programmers To Drive Lew Rockwell Fan Insane). Here is an example where I'm fairly sure the keys ARE identical, but I can't come up with a procedure to prove it.

Veracrypt team key from the MIT keyserver:
[https://pgp.mit.edu/pks/lookup?op=get&search=0xEB559C7C54DDD393](https://pgp.mit.edu/pks/lookup?op=get&search=0xEB559C7C54DDD393)

Veracrypt team key from the Veracrypt site:
[https://www.idrix.fr/VeraCrypt/VeraCrypt_PGP_public_key.asc](https://www.idrix.fr/VeraCrypt/VeraCrypt_PGP_public_key.asc)

I've downloaded both directly. I've copied and pasted both into text files. I've stripped away the preambles and the endings, leaving blocks that each begin with the same gibberish and end with the same gibberish. 

I've run them through all sorts of tr filters, like:
```
 cat file | tr -d '\040\011\012\015' > file-tred
```
The one from MIT is still a lot bigger file.
I've loaded them into gedit and I can copy substantial chunks of one and search for that chunk in the other and find an identical substring, but not with the whole file.

This isn't an isolated example. MIT isn't unique. It's just the first one I checked. Here is the second:

[http://pgp.surfnet.nl:11371/pks/lookup?op=get&fingerprint=on&search=0xEB559C7C54DDD393](http://pgp.surfnet.nl:11371/pks/lookup?op=get&fingerprint=on&search=0xEB559C7C54DDD393)

It appears to have the same issue. Nor is Veracrypt a special case. I've run into this every time I've resolved to learn to do gpg the "right way" and beat my head against the same wall for a few days before giving up. Is there some reason these things aren't published in a standardised form? Is there some way to make this easy? Am I missing something obvious? What makes that MIT file so big?

---

### Post by matt_symes on 2016-01-17
Hi

Don't compare the keys directly.

Compare the key fingerprints.

From here:

[https://www.idrix.fr/Root/content/category/7/32/60/](https://www.idrix.fr/Root/content/category/7/32/60/)

> 
All VeraCrypt released files are PGP signed with a key available here.
This key is also available on major key servers using ID=0x54DDD393. Please check that its fingerprint is **993B7D7E8E413809828F0F29EB559C7C54DDD393**.

and here....

[http://pgp.surfnet.nl:11371/pks/lookup?op=vindex&search=veracrypt&fingerprint=on](http://pgp.surfnet.nl:11371/pks/lookup?op=vindex&search=veracrypt&fingerprint=on)

> pub  4096R/54DDD393 2014-06-27            
	 Fingerprint=**993B 7D7E 8E41 3809 828F  0F29 EB55 9C7C 54DD D393 **

Check the dates of the keys to ensure they match.

You can check the fingerprint of the last key you linked yourself.

Remember, when you have imported a key into your keyring, you can be get key's fingerprint with

```
gpg --fingerprint
```

or

```
gpg --fingerprint <key>
```

Kind regards

---

### Post by Dreamer Fithp Apprentice on 2016-01-22
Thank you. Yes, as a practical matter that works. Also, I've discovered, I can just import the key from multiple places & it will be compared automatically to earlier versions. So pragmatically, it's solved. But I'd still like to know why it doesn't work the other way. Presumably there is another linefeed/carriagereturn-like character I haven' accounted for.

---

