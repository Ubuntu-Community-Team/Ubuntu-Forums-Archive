---
title: "nrg2iso command lines?"
date: 2008-07-01
forum: General Help
---

### Post by DanseNoir on 2008-07-01
I'm trying to convert an .nrg file to an .iso, but not having much success.  I installed nrg2iso, but either (a) it's not working or (b) I'm not entering the correct command lines in Terminal.

Here's what I've tried:

```
cd /foldername
nrg2iso filename.nrg filename.iso
```

When I enter that, I get this:

```
Segmentation fault
```

What am I doing wrong?

---

### Post by Slim Odds on 2008-07-01
How did you "install" it?

I'd recommend compiling from source

---

### Post by DanseNoir on 2008-07-01
```
sudo apt-get install nrg2iso
```

---

### Post by Slim Odds on 2008-07-01
Sorry, I did not realize that one was in the repositories.

What happens if you run it without any arguments?

BTW: It works fine for me......

---

### Post by DanseNoir on 2008-07-01
I tried using Kiso instead and through an extremely complicated set of actions, finally managed to convert.

---

