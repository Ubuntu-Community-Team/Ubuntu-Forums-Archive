---
title: "apt-get recommended/suggested package"
date: 2005-06-21
forum: General Help
---

### Post by Raccroc on 2005-06-21
Could somebody point me in the right direction toward an easy way to get apt-get to auto install (w/verification) the recommended/seggested packages?

I'd just assume it's not a global "always-on" option, but more oft than not I do want to install those things.

---

### Post by Kyral on 2005-06-21
Actually I would like to know how to do this as well

---

### Post by Xian on 2005-06-21
You can do this by installing the wajig package.

```
$ sudo apt-get install wajig
```
Then you would use the following commands based on your preference:

```
installr       Install package and associated recommended packages
installrs      Install package and recommended and suggested packages
installs       Install package and associated suggested packages
```
So, for example if you wanted to install the mozilla-thunderbird package with all suggested and recommended packages you would issue the following command:
```
$ sudo wajig installrs mozilla-thunderbird
```

Here's a more complete reference: [Wajig Overview](http://www.togaware.com/linux/survivor/Wajig_Overview.shtml)

---

### Post by Raccroc on 2005-06-21
Exactly way I was looking for.  Thanks! :)

---

