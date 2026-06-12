---
title: "Ubuntu 14 killed my computer Help, please."
date: 2014-04-22
forum: General Help
---

### Post by davidoff-ss on 2014-04-22
del

---

### Post by davidoff-ss on 2014-04-22
del

---

### Post by oldfred on 2014-04-22
Please do not post duplicate threads. Merged.

Can you boot live installer in live mode?

Why cannot you not put in password? It does not show you typing it, you just have to correctly enter it.

---

### Post by davidoff-ss on 2014-04-22
del

---

### Post by QIII on 2014-04-22
As I write this from "this terrible software" it occurs to me to ask if you checked the md5sum to be sure you had a good image downloaded.

---

### Post by davidoff-ss on 2014-04-24
del

---

### Post by sudodus on 2014-04-24
I don't think your computer is suffering from an infected Ubuntu download.

Please try to take it easy and listen to the tips and advice :-) You can check step by step, what is the problem, and then try different solutions until you find what is best for you.

The md5sum is checked with the linux program md5sum versus the listed value at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- So, from a terminal window, run the command

```
md5sum filename.iso
```

and compare the output with the value from UbuntuHashes.

This check is primarily done to avoid problems due to failed downloads because of transfer errors (which is rather common). An alternative is to use a torrent, where the md5sum is checked automatically.

- What tool did you use to create the install drive?

- Did you use any special character in the password, that might be interpreted differently in the password parser compared to the installer?

---

