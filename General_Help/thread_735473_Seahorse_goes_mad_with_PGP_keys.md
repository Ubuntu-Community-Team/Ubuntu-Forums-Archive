---
title: "Seahorse goes mad with PGP keys"
date: 2008-03-25
forum: General Help
---

### Post by scramasax on 2008-03-25
I've previously managed my GnuPG keyring from the command line, but i decided to install the Seahorse front end.

What's bizarre is that every time I look in the "Other Collected Keys" tab Seahorse seems to have grabbed the key for some other person I don't know from Adam and added them  to my keyring.

I feel like the Sorcerer's Apprentice, except that I've got PGP keys overrunning me not brushes and brooms.  And why I don't know -- all I did was install the program and start it.

Can anyone tell me why it's doing this and how to stop it?

---

### Post by Dr Small on 2008-03-25
I think that it has te do with a level of trust on the key.
I had this same bizzar thing happen to me before.

In SeaHorse, go to the properties on a Trusted Key > Trust Tab and see if "I trust signatures from "USER" on other keys" is selected. That is what imported a bunch of other keys into mine. Of course, you will have to go back and delete all the other keys that were imported in to get rid of them.

Dr Small

---

### Post by scramasax on 2008-03-25
> **Dr Small said:**
> I think that it has te do with a level of trust on the key.
I had this same bizzar thing happen to me before.

In SeaHorse, go to the properties on a Trusted Key > Trust Tab and see if "I trust signatures from "USER" on other keys" is selected. That is what imported a bunch of other keys into mine. Of course, you will have to go back and delete all the other keys that were imported in to get rid of them.

Dr Small

Thanks, Dr Small.

It can't be that in my case, because I haven't got any trusted keys and that tab is empty.

As you say it's bizarre.

---

### Post by scramasax on 2008-03-26
> **scramasax said:**
> Thanks, Dr Small.

It can't be that in my case, because I haven't got any trusted keys and that tab is empty.

As you say it's bizarre.

However, it seems likely that this is a case of keys pulling in keys that have been signed by them...

Deleting keys I didn't want made no difference -- they just re-appeared.

What I did in the end was to export the public keys of people I had myself collected earlier, or had searched for with Seahorse after installing it, and wanted to keep.  I then deleted all the keys.  I then imported each key from the exported .asc file.

After that the "Other Collected Keys" tab did NOT fill up.

So I think it must be the act of importing from the server with Seahorse that's doing it.  I've tried changing the default server in case this is something to do with the server.  The default was:

hkp://pgp.mit.edu:1137

I'm now using:

hkp://www.keys.pgp.net

and

hkp://subkeys.pgp.net

I've since imported a key from the remote server with no ill effects.

I can't claim to understand the problem and know what was causing it, but I thought I should add this post to the thread in case it is helpful to anyone else trying to resolve the same problem and finding this thread by searching the forums on "Seahorse".

---

