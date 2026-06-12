---
title: "Laptop Compatibility for Ubuntu with Unity"
date: 2013-10-10
forum: General Help
---

### Post by craig10x on 2013-10-10
A friend of mine is considering getting a low priced Toshiba 17" laptop...because it's pretty low priced, here are the specs it has: intel celeron processor with intel mobile graphics...500 gb hard drive and 4 gb ram...This is a brand new (2013 model)...i was wondering if unity would run smoothly and fast on it...he likes ubuntu and likes unity so that would be his preference...he plans on wiping off windows 8 and replacing it with ubuntu as he likes linux...

Would especially like to hear from anyone using a fairly current laptop with an intel celeron and runs standard ubuntu w/unity...thanks :D

---

### Post by DuckHook on 2013-10-11
There is a wide range in Celerons and a further range in Intel mobile graphics, so your info is not complete enough to make a full assessment. To do so, it would be better to cite the actual Celeron model and the mobile graphics chip. This info is readily available by Googling the Toshiba make/model + "specifications".

A flying guess at it would be: any modern laptop that can run Win 8 should also have the horsepower to run Ubuntu (current versions). However, also a good idea to Google "Ubuntu compatibility" + "Toshiba model #" because a number of newer laptops are known to have problems with any OS except Win8.

---

### Post by craig10x on 2013-10-11
@Duckhook:  Thanks for your input....i checked on the specs...perhaps this will help...they do give a description for the processor but for the graphics it just says integrated graphics...not sure if this helps....
Yeah, i kind of figure that if it can run windows 8 it ought to be able to handle ubuntu with unity...true? ;)
I heard about problems sometimes because of windows 8 although he would not be dual booting...he would wipe windows and install ubuntu on the entire drive...

[LIST]
[*][FONT=inherit]Intel® Celeron® Processor 1005M (3M Cache, 1.90GHz)[/FONT]
[/LIST]

---

### Post by elliotn on 2013-10-11
run a LiveCD and you will know if it will work or not

---

### Post by DuckHook on 2013-10-11
> **craig10x said:**
> ...i kind of figure that if it can run windows 8 it ought to be able to handle ubuntu with unity...true?Only true from a theoretical perspective. Unfortunately, some manufacturers hard-wire the Win8 certificate-signature into their mobo. Result: it only runs Win8.> I heard about problems sometimes because of windows 8 although he would not be dual booting...he would wipe windows and install ubuntu on the entire driveYou are referring to Win8 and "secure boot" + "fast boot", I believe. In general, if these are turned off, then Ubuntu should install with no problems. But can they be turned off? Even if they can be, has the manufacturer otherwise crippled his mobo to be compatible only with Win8? Personally, I dunno. Just suggesting that you further research this to be sure.

---

### Post by craig10x on 2013-10-11
Thanks guys...though i thought i read that ubuntu was supposed to be able to disable secure boot...and even if it doesn't that on most computers you can turn it off in the bios settings...

---

### Post by oldfred on 2013-10-11
Microsoft requires that the user can turn off secure boot in UEFI/BIOS.  
But vendors have implemented different ways. Some work like it should and you just turn off secure boot and it works for Windows or any other system in UEFI or CSM/BIOS/Legacy mode. 
Others only boot Windows with secure boot on or only boot other systems in CSM mode. But if reinstalling that should not matter. It just will be whether you can or want new UEFI or BIOS legacy booting. 
Some systems may work better with UEFI as it has newer drivers or some may work better with BIOS as legacy drivers have fewer issues.

---

### Post by craig10x on 2013-10-11
Thanks oldfred...the link is very informative :D

---

