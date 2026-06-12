---
title: "Connecting Sharp GX-10i cell phone via USB"
date: 2008-06-14
forum: General Help
---

### Post by tbraun on 2008-06-14
Hello!

I have a Sharp GX-10i cell phone and its special USB connector cable. Plugging it in, however, it doesn't seem to be recognized by Ubuntu (7.10). Does anyone know if there are any drivers/software I could install that would allow me to contact the phone?

Thank you very much...

---

### Post by rraj.be on 2008-06-14
Just plug your phone and type this is terminal

lsusb

This will list all your usb devics connected.

Make sure your phone is connected.

There are no drivers required for connecting mobile.

You can install applications that communicate with phone like wammu gammu phone manager etc.

To install type this

```
sudo apt-get install wammu
```

```
sudo apt-get install gammu
```

Then you have to configure it a bit befor working.

---

