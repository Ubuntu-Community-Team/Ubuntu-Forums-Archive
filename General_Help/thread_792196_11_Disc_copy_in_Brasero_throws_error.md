---
title: "1:1 Disc copy in Brasero throws error"
date: 2008-05-12
forum: General Help
---

### Post by Aikon- on 2008-05-12
I have an existing DVD of home videos (actually, vacation videos) that has already been authored and works fine in our standalone DVD player.

When trying to make a 1:1 copy of this DVD using Brasero, I get the following error as soon as I start the process. I am on a laptop, with a single optical drive, therefore it has to first make a disc image on the hard drive before being able to burn the actual copy.

Error:
```
Session error : impossible to find a format for the temporary image (brasero_burn_record burn.c:2270)
```

Any ideas?

-Aikon

---

### Post by Aikon- on 2008-05-12
I got it to work by installing the restricted formats package:

```
sudo apt-get install ubuntu-restricted-extras
```

-Aikon

---

### Post by Gasten on 2008-05-31
Hm... I got the exact same problem. However, that package did not help me. Do you have any hints on where I can find more info?

---

### Post by HandyAndy on 2008-06-12
Same problem here. And the restricted packages didn't help me either.

Anyone got any ideas? I really hate having to give up and go into Windows to do it.

---

