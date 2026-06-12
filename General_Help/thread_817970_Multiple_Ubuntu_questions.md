---
title: "Multiple Ubuntu questions"
date: 2008-06-04
forum: General Help
---

### Post by shakyj on 2008-06-04
Got ubuntu hardy heron a few weeks ago. Started playing around with different session managers and finally decided on XFCE.
The problem I have now is can I get rid of gnome and kde from my system? If so how?

I have also noticed XFCE has a startup option to load gnome services on startup? Do I need these services? What do they actually do?

XFCE also has a problem where it doesn't always start when I log in. It just sits there and I have to Ctrl+Alt+Backspace and restart my PC to get it to start. Sometimes three or four times. Where is the XFCE log so I can try see whats wrong with it?

(N00b question) I have had 3 kernel updates since using ubuntu and they are all showing in my grub menu. I know how to remove them from grub. But does that mean there are 3 kernels installed on my PC or not?

---

### Post by sisco311 on 2008-06-04
> **shakyj said:**
> Got ubuntu hardy heron a few weeks ago. Started playing around with different session managers and finally decided on XFCE.
The problem I have now is can I get rid of gnome and kde from my system? If so how?

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by ardvark71 on 2008-06-04
> **shakyj said:**
> 
(N00b question) I have had 3 kernel updates since using ubuntu and they are all showing in my grub menu. I know how to remove them from grub. But does that mean there are 3 kernels installed on my PC or not?

Hi...

No, I don't believe so. That would be a recipe for confusion for the OS. ;)

Best Regards...

---

### Post by zvacet on 2008-06-04
```
sudo tasksel
```

Uncheck desktops you want to remove.

---

### Post by shakyj on 2008-06-04
I was thinking that it would be a very silly thing for Ubuntu. But I have come from windows where silly things happen on a daily basis

---

### Post by zvacet on 2008-06-04
@ **shakyj**

I overlooked your second question.If you see kernels in grub that mean they are installed.You can remove them from synaptic by typing **linux-image** in search box and delete ones with lower number.In short you should have 2.6.24-16 and 2.6.24-17 as Hardy kernels.You can remove other kernels if you find them.

---

### Post by ardvark71 on 2008-06-04
> **zvacet said:**
> @ **shakyj**

I overlooked your second question.If you see kernels in grub that mean they are installed.You can remove them from synaptic by typing **linux-image** in search box and delete ones with lower number.In short you should have 2.6.24-16 and 2.6.24-17 as Hardy kernels.You can remove other kernels if you find them.

Whoops, my mistake.:(

So the default kernel the system looks for is always the highest kernel?

Best Regards...

---

### Post by shakyj on 2008-06-04
That seems abit silly that it keeps them? I can understand having 2. But i have 3 at the moment 16/17/18

---

### Post by kpkeerthi on 2008-06-04
> **ardvark71 said:**
> Whoops, my mistake.:(

So the default kernel the system looks for is always the highest kernel?

Best Regards...

Not exactly. Look for the line that reads **default n** in /boot/grub/menu.lst. 

n = 0, First grub entry.
n = 1, Second grub entry and so on.

If you have **default 1**, GRUB boots your second kernel entry by default.

---

### Post by ardvark71 on 2008-06-04
> **kpkeerthi said:**
> Not exactly. Look for the line that reads **default n** in /boot/grub/menu.lst. 

n = 0, First grub entry.
n = 1, Second grub entry and so on.

If you have **default 1**, GRUB boots your second kernel entry by default.

Thank you kindly! :)

I just learned something new about Ubuntu this day! :KS

Best Regards...

---

### Post by zvacet on 2008-06-04
@ **shakyj**

> But i have 3 at the moment 16/17/18

Then you can delete 16 if you are sure that at least 17 work properly.And you are right,no need for more then two kernels.

@ **ardvark71**

> So the default kernel the system looks for is always the highest kernel?

Yes,but as **kpkeerthi** said you can change that.

---

