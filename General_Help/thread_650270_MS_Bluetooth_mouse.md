---
title: "MS Bluetooth mouse"
date: 2007-12-26
forum: General Help
---

### Post by skarosg3 on 2007-12-26
Hi all,
First i should say that I am new to linux, even though i have tried many times in the past to use it. Now it seems that things are looking better for me.
Now my problem, I have a MS bluetooth mouse with a bluetooth adaptor on my laptop. When i plug the adaptor the bluetooth icon appears on the panel, and it actually see the mouse on the bonded devices list. The problem is that i cant make it to work. I have "trusted" the mouse as well, it seemed that it was the right thing to do.
Anyhow, any ideas what i should do?
Thank
ilias

---

### Post by z0mbie on 2007-12-26
Usually most devices have a red button to activate the bluetooth synchronization process. Find that button.

**1**. Search for the device in terminal by typing:
```
sudo hidd --search
```

You will see  msg that says:

> Searching...
[B]
2[/B]. Press the synchronize buttons on the device.

If the sychronize is successful you should get a msg similar to bellow in terminal saying:

>         Connecting to device 00:07:61:32:64:93

Now you should have the device connected.

---

### Post by skarosg3 on 2007-12-26
Thanks for the quick reply Z0mbie,

I did what you said, but i got this message on the terminal 

        No devices in range or visible

I did it twice, once i pressed the button once and the second time i was pressing it till i got the message.
:(

---

