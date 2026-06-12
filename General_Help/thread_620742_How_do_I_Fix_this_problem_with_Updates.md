---
title: "How do I Fix this problem with Updates?"
date: 2007-11-23
forum: General Help
---

### Post by mulletsteve on 2007-11-23
Every time I try to update, I get an error that reads:

"E: tzdata: subprocess post-installation script returned error exit status 10
E: util-linux: dependency problems - leaving unconfigured"

How would I go about fixing this?

---

### Post by zippy028 on 2007-11-23
I am not an expert but I do not believe any harm would be done by issuing these commands

```
sudo apt-get --fix-broken
```

```
sudo apt-get --fix-missing
```

Please post your results and if this does not repair the problem hopefully someone more knowledgeable can help.

---

