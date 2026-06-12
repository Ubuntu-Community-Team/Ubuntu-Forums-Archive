---
title: "permission problem"
date: 2013-02-03
forum: General Help
---

### Post by DonTommy on 2013-02-03
Hey there.
I got a permission problem, trying to send sms trough gammu and my old cell phone which is connected via usb cable, i can do it trough wammu if I run it as sudo/root

But when I try sending sms trough gammu I get a "Error opening device, you don't have permissions."

so I guess i have to add some permissions some where, but have no clue where? Anybody that knowns what the problem is?

I am using Ubuntu

Thanks

---

### Post by DonTommy on 2013-02-04
And I have added my user to the group dialout, which I understand is the user for modems, phones etc, but that dosnt do the trick?

---

### Post by btindie on 2013-02-04
What is the name of the device you have in your config file?

Does your user account / group membership give you permission to read+write to it?? ```
ls -l /dev/<device_name>
```

---

### Post by DonTommy on 2013-02-05
Ahh yes, that did the trick actually, chmod the device to 777 and it worked :)

So thanks a bunch :)

---

### Post by Warren Hill on 2013-02-05
Don't forget to mark this thread Solved if it's now fixed.

---

### Post by DonTommy on 2013-02-05
Where do I do that, can seem to find that button?

Got it ;)

---

