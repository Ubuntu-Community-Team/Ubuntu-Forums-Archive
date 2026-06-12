---
title: "synaptic authentication"
date: 2007-02-28
forum: General Help
---

### Post by frogotronic on 2007-02-28
I'm getting an error with synaptic that non of the packages that i try to install can be verified.  Anyone else getting this error?

---

### Post by louis_nichols on 2007-02-28
You must have added some repositories without also adding their keys to apt. Good instructions about adding repos also contain the steps for adding to apt the key with which the packages are signed.

That's not a big problem, as long as you really trust the source of the packages. It would be best, though, to add the keys to apt. This is usually done using:

```
wget *URL-to-public-key* -O - | sudo apt-key add - 
```

---

### Post by frogotronic on 2007-02-28
okay, thanks  i'll fix it

---

