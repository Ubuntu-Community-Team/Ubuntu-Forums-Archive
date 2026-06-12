---
title: "Unable to update/install/add-repository: problem with GPG"
date: 2019-03-16
forum: General Help
---

### Post by poerland on 2019-03-16
Hi. When I try to update, I get errors like this:

```
The following signatures couldn't be verified because their public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32 
```

So I did

```
gpg --keyserver keyserver.ubuntu.com --recv [COLOR=#0000CD]3B4FE6ACC0B21F32[/COLOR]
```

which apparently worked. Then, I did

```
gpg --export --armor [COLOR=#0000CD]3B4FE6ACC0B21F32[/COLOR] | sudo apt-key add -
```

but gave me

```

Segmentation fault (core dumped)
Segmentation fault (core dumped)
Segmentation fault (core dumped)

```

which I think means that I have tried to access somewhere in my memory without permission. I couldn't find any other problems that look like this when using apt-key. Help! And thanks in advance. :) I use lubuntu 18.04.

PS: Error message translated from spanish.

---

