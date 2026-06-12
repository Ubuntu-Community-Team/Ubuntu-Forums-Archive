---
title: "can't install to home directory"
date: 2013-05-17
forum: General Help
---

### Post by shinigamikris on 2013-05-17
I'm trying to install planeshift but every folder i choose to install to returns an error as per screenshot.

Any ideas on how to fix this?

---

### Post by matt_symes on 2013-05-17
Hi

> **shinigamikris said:**
> I'm trying to install planeshift but every folder i choose to install to returns an error as per screenshot.

Any ideas on how to fix this?

/home is not writeable by your current user, whereas /home/<user_name> is (<user_name> being your username)

You could change the path to

```
/home/<user_name>/planeshift
```

where you replace <user_name> with your actual username or you could use

```
gksudo ...
```

to install it.

How are you current trying to install ? Are you typing commands in a terminal ?

Kind regards

---

### Post by shinigamikris on 2013-05-17
I'm just launching the installer by double clicking on the file... I will try these things you mentioned. Thanks.

Edit:

So I changed directory to username/home/ and it worked. Again, thanks

Edit: oops I think I did that wrong. I can't find where it installed to  now :(

---

### Post by matt_symes on 2013-05-17
Hi

> **shinigamikris said:**
> I'm just launching the installer by double clicking on the file... I will try these things you mentioned. Thanks.

Edit:

So I changed directory to username/home/ and it worked. Again, thanks

Edit: oops I think I did that wrong. I can't find where it installed to  now :(

It sounds like you installed it in your home directory.

Look in your home directory to find it.

Kind regards

---

### Post by shinigamikris on 2013-05-17
I did look but i couldn't see it in there... I'll have another look. Maybe do a search for it.

Edit - It installed inside my downloads folder for some reason :/ Maybe because thats where the install file resides??

---

