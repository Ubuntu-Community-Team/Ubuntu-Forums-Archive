---
title: "GDM crashes after power down"
date: 2007-03-03
forum: General Help
---

### Post by foxy123 on 2007-03-03
My wife left my laptop running on a battery and I have not noticed it. When I switched to my account the laptop ran out of power and switched off. Now I cannot get neither into GDM login screen nor into my account. GDM tries to launch and then gives me the following message:

```
The display server has been shut down about 6 times in the last 90 minutes, it is likely 
that something bad is going on. Waiting for 2 minutes before trying again on display :0.
```

I can stop GDM and drop into shell, but startx does not work on my account. I cannot re-type everything it displays and I do not know where it logs it but it starts with:
```
xauth: creating new authority file /home/foxy/.serverauth.6110
```

Then usual stuff about X.

then
```
error opening security policy file /etc/X11/xserver/SecurityPolicy
```

Then some xkbcomp error, which it says is not fatal.

It it ends with
```
waiting for X server to shut down FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, 
should be 1; fixing
```

And I an again in shell.

I can log in in my wife's account and start X from there.

I think that something got corrupted after power down but I do not know what exactly. Any help will be highly appreciated.

---

### Post by PurplePenguin on 2007-03-03
You fscked it already?

---

### Post by foxy123 on 2007-03-03
> **PurplePenguin said:**
> You fscked it already?

no I have not... Let me do it and try again. Thanks for the suggestion.

---

### Post by foxy123 on 2007-03-03
no, it did not fix it :(

---

