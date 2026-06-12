---
title: "Need to remove RESTRICTED EXTRAS (help)"
date: 2008-07-07
forum: General Help
---

### Post by durkhrod chogori on 2008-07-07
I installed them in order to overcome a bug that stops me from viewing YouTube material, and as a result things got worse as I can't open Synaptic.

So, does anyone know the command to run the removal procedure in Terminal?


Thanks.

---

### Post by durkhrod chogori on 2008-07-07
Anyone?

---

### Post by Seisen on 2008-07-07
Try going to System>Administration>Software Sources then you can remove them from there and then reload your source list.

---

### Post by danwood76 on 2008-07-07
I'm assuming you mean by restricted extras the actual package not the repository.

In the terminal do this:
```

sudo apt-get purge ubuntu-restricted-extras

```
Though I highly doubt this package would break synaptic.

---

### Post by oldos2er on 2008-07-07
> **durkhrod chogori said:**
> I installed them in order to overcome a bug that stops me from viewing YouTube material, and as a result things got worse as I can't open Synaptic.
  

 Ubuntu-restricted-extras isn't going to break Synaptic; you've got some other problem. Do you see any error messages when trying to open Synaptic? What about running aptitude or apt-get in a terminal?

---

### Post by nikgare on 2008-07-07
Restricted extras will not beak synaptic - something else has.
Please run synaptic from a terminal by running this command:
```
sudo synaptic
```
Please post any stuff that appears in the terminal.

You also haven't said in what way synaptic is broken!

---

