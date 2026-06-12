---
title: "evolution version problem"
date: 2024-09-08
forum: General Help
---

### Post by bilkay on 2024-09-08
I have two laptops, both Ubuntu 20.04, but somehow they got different versions of evolution. one is 3.36.5-0ubuntu1, the other 3.44-0ubuntu2. I need to be able to access mail data from either, but when stored from the newer version, the older version can't read it. I tried to upgrade the older version, but it said I was already at the latest version. I'm at a loss as to what to do. Ubuntu is starting to **** me off!

---

### Post by deadflowr on 2024-09-08
Odd, 3.36.5-0ubuntu1 is the correct version for 20.04.
I have no idea where you got 3.44-0ubuntu2 since that has never been a package in 20.04.
(Or at least as far as I can tell)

Did you add a 3rd party repository or accidentally run a release upgrade?
I guess it's unclear where that second version is from.
I'd probably run
```
apt policy evolution
```
on both and compare the outputs.

---

### Post by Holger_Gehrke on 2024-09-09
Are you sure that both machines run 20.04 ? '3.44.4-0ubuntu2' is the current version of evolution on 22.04 ...

Holger

---

### Post by bilkay on 2024-09-24
I apologize for wasting anyone's time. The laptops were not both 20.04, one was 22.04 which I've reverted back to 20.04.

I solved the Evolution problem by exporting the mail folders from the newer evolution and then importing them into the older version.

---

