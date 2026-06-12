---
title: "Dos apps under Wine"
date: 2008-05-19
forum: General Help
---

### Post by gandalf458 on 2008-05-19
Is it possible to run DOS applications under Wine? I have successfully installed Wine and my application (which has a Windows installer although it's just a plain old DOS app.)

I usually run the app from a batch file as the application has a couple of parameters.

Thanks

---

### Post by zvacet on 2008-05-19
You can install **dosbox **for that.It is in synaptic.

---

### Post by gandalf458 on 2008-05-19
Thanks. Yes, I had a look at DOSbox but I could make much sense of it. It seemed I needed to use mount to create a directory but when I tried it told me it didn't exist. Guess I'll just have to persevere a bit more. It was a dream the way Wine installed my app too.

Cheers G :)

---

### Post by prshah on 2008-05-19
> **gandalf458 said:**
> Thanks. Yes, I had a look at DOSbox but I could make much sense of it. It seemed I needed to use mount to create a directory but when I tried it told me it didn't exist. Guess I'll just have to persevere a bit more. It was a dream the way Wine installed my app too.


The dosbox mount command mounts a directory to a local drive letter; eg Start DosBox, then the code below ```
mount c ~
``` will mount your home directory as "c:"

---

### Post by gandalf458 on 2008-05-19
Cool. Thanks.

G :)

---

