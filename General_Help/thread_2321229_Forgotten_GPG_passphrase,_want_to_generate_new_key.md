---
title: "Forgotten GPG passphrase, want to generate new keys etc"
date: 2016-04-21
forum: General Help
---

### Post by t0p on 2016-04-21
I have forgotten the pass-phrase of my gpg secret key.  I want to create a new key-pair, using the same Gmail account and the same name.

Is this possible: using the same gmail address and the same name?  If so, is there anything else I need to to first?  I've read stuff about "revocation certificates" but as I have forgotten the passphrase maybe it's too late to think of revoking the old key?

Thanks.

---

### Post by T.J. on 2016-04-21
You should ALWAYS generate a revocation certificate at the  same time  you make your new key, and then store it in safe place.  If you didn't,  then I'm afraid it is a  case of "sour grapes", as there is not anything  you can do about it  unless you remember your passphrase.

As a consolation, you only need a revocation certificate if you have uploaded the key to a  public keyserver, such as MIT; a developer server, or the key is still in use by others you haven't met or the  general public. You can simply tell the people you know to no longer use the old key.  I always set an expire date of 1 year after a key's creation, as a safety measure.  So even if the revocation certificate is lost, the key becomes expired in 1 year automatically.  I NEVER use a permanent key without an expire date in case my computer is stolen or tampered with.


If you aren't storing anyone else's keys on your existing keyring, backup the old keyring ( the .gnupg folder)*,* and delete it so you have no future problems.

Then generate a new key and keyring[I]. 

gpg -- gen-key. [/I]

You can create a revocation ceritificate with: 

[I]gpg --output revoke.asc --gen-revoke <mykey>
[/I]
Store the revoke.asc file in a safe place.  I'd also make a copy of your keyring - the .gnupg folder - and then store it elsewhere. 

If you don't mind another suggestion, use no less than a 4096 bit key. It is highly recommended that you use nothing less when governments are looking for new ways to break or undermine PKI systems.

---

### Post by t0p on 2016-04-21
Thanks for the reply! I will certainly generate a revocation certificate when I set up my new GPG keys.

Something I need to know: can I use the same gmail address when creating new key, and the same name (eg "Joe Bloggs") or does it need to be a new one (like "Joe Bloggs")?  The question as to whether I can use the same email address as the old one is particularly important, as I want to use my main email address.

Cheers!

---

### Post by Habitual on 2016-04-21
> **t0p said:**
> Something I need to know: can I use the same gmail address when creating new key, and the same name (eg "Joe Bloggs") Yes, you can re-use them in the new key pair.

---

### Post by t0p on 2016-04-21
Thanks Habitual.

---

