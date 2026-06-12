---
title: "Evolution Busted in Ubuntu 8"
date: 2008-07-04
forum: General Help
---

### Post by GJS on 2008-07-04
Since upgrading to 8, Evolution asks for the default keyring password the first time it starts.  I have auto login set and Evolution is set to auto startup.  Obviously, with Evolution asking for a password the auto login is pointless.

Does anyone know how to fix this and get it back to where is was in ubuntu 7?

Thanks.

PS  I tried the "screens and graphics" app but that has no effect.

---

### Post by tobinlam on 2008-07-08
The same thing is happening to me except it started last week, well after I upgraded.

---

### Post by lamego on 2008-07-08
Please file a bug report at [https://bugs.launchpad.net/](https://bugs.launchpad.net/) , hopefully it will be fixed.

---

### Post by 4partee on 2008-07-10
I am having the same problem.  I reported a bug:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/247250](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/247250)

HTH;
John

I just noticed that this has already been reported and REJECTED as a bug by the Ubuntu team:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264)

to wit:

 <Sebastien Bacher wrote on 2008-06-23: (permalink)

did you read the previous comments? the previous setup was not really secure, you can set a blank password for your gnome-keyring if you don't care about security though but ubuntu is not going to change back to a non secure default>

No explanation why.  I do care about security, but exactly what is the threat?

HTH;
John

---

