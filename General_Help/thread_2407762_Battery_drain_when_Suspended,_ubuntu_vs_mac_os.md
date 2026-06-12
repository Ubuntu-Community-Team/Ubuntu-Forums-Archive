---
title: "Battery drain when Suspended, ubuntu vs mac os"
date: 2018-12-09
forum: General Help
---

### Post by welars on 2018-12-09
Hello,

I have some general questions regarding the battery power consumption of ubuntu and mac os laptops while suspended. 

I have an asus ux430 running ubuntu and macbook pro 2016. Recently I discover that the battery life of ubuntu can only last for about 8 hours in suspend mode, while my macbook can go way beyond that. I am wondering why that is the case.

Also, since I am used to the "open the lid, start right away, while consuming less battery life" nature of macbook, is there a way I can configure my ubuntu to achieve this? I am currently putting my ubuntu into hibernation, but the wake-up time is kind of driving my crazy...

Thanks for the help!

---

### Post by HermanAB on 2018-12-09
Note that a Macbook has an enormous Li-ion battery, so your Asus will never be able to equal it.  That being said, you should check whether the Asus correctly power down everything when it goes into suspend.

You can also set the power management to go into suspend first, then when the battery becomes critical, go to hibernate.  This way, you can normally just close/open the lid and be on your merry way immediately.

---

### Post by welars on 2018-12-09
> **HermanAB said:**
> Note that a Macbook has an enormous Li-ion battery, so your Asus will never be able to equal it.  That being said, you should check whether the Asus correctly power down everything when it goes into suspend.

You can also set the power management to go into suspend first, then when the battery becomes critical, go to hibernate.  This way, you can normally just close/open the lid and be on your merry way immediately.


Thank you for your suggestions!! They are really helpful. :D

I think I have found an adequate solution: use suspend-then-hibernate mode to replace the default suspend mode. This is basically the same as the suspend mode, but after a set period of time, the machine will hibernate (hence consumes less battery, but of course, it wakes up slower). If anyone wants to try this out, follow the second solution in the post below:


[COLOR=#1155CC][FONT=Arial]https://askubuntu.com/[/FONT][/COLOR][COLOR=#1155CC][FONT=Arial]questions/145443/how-do-i-use-[/FONT][/COLOR][COLOR=#1155CC][FONT=Arial]pm-suspend-hybrid-by-default-[/FONT][/COLOR][COLOR=#1155CC][FONT=Arial]instead-of-pm-suspend[/FONT][/COLOR]

---

### Post by kurt18947 on 2018-12-09
If you haven't done so, consider installing TLP. I did that on a ThinkPad X201 and it made a significant difference in run time. I'm not really sure about extended suspend, I usually shut down if I'm not using the machine for more than a few hours. With an SSD I can go from off to working in less than a minute so no need for extended suspend time. I didn't think hibernate was reliable, has that changed?

---

