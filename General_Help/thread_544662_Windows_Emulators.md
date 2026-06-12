---
title: "Windows Emulators"
date: 2007-09-06
forum: General Help
---

### Post by Squee3 on 2007-09-06
I'm taking a C++ class, and I don't think that the compiler I need to use for the class will run on Ubuntu.  What emulator would you suggest?  I've tried WINE but I can't get anything to work in it, and it's HowTo isn't very helpful.

---

### Post by tszanon on 2007-09-06
> **Squee3 said:**
> I'm taking a C++ class, and I don't think that the compiler I need to use for the class will run on Ubuntu.  What emulator would you suggest?  I've tried WINE but I can't get anything to work in it, and it's HowTo isn't very helpful.
If it does not run under wine, I suggest using virtualization. Have you thought about vmware or virtualbox?

---

### Post by Squee3 on 2007-09-06
Well, my problem with wine is that I can't get ANYTHING to run in it.  Even starcraft.  I know that starcraft is supported by wine because they have a screenshot of it being used on wine's website.  And as for virtualization, I never had considered it.  which one of those two would you suggest getting?

---

### Post by SomethingUniqueHere on 2007-09-06
Wine can be tricky to setup, i would start looking around the gaming forums since Wine is their bread and butter.  One thing to consider is using the G++ compiler at home and transporting your source to class and recompile there.  Assuming you don't need to access any windows API in your code, the source should compile on both systems.  Perhaps its not an ideal solution since compilers can be finicky and you might have a few hiccups when moving between compilers but something to consider doing in the short run.

---

### Post by Squee3 on 2007-09-06
Well, on the gaming forums they seem to prefer Cedega, which you have to pay for.  I did consider using a different compiler at home, but I wasn't sure if the programs would work in both.  I think I'll try that and see how it turns out for now.  The worst case scenario is that I'll have to start using my Windows partition again, so it's not necessary for any of this to work.  It'd just be my preference if I didn't have to use windows.  Also, the complier we're using at school is 10 years old.  So I'm not even entirely sure that it would work with an emulator.

---

### Post by tszanon on 2007-09-06
> **Squee3 said:**
> Well, my problem with wine is that I can't get ANYTHING to run in it.  Even starcraft.  I know that starcraft is supported by wine because they have a screenshot of it being used on wine's website.  And as for virtualization, I never had considered it.  which one of those two would you suggest getting?
I've used vmware server. It's free of charge. It's available in Feisty repositories, and you can download the latest one at [http://www.vmware.com](http://www.vmware.com).

I've seen people here suggest VirtualBox. I never used it, but they say it's very good too. And it's FOSS.

Both will let you use windows in Ubuntu. So I guess it's up to you to decide which one will be better. :)

---

### Post by trippinnik on 2007-09-06
What is the name of the compiler you have to use? Check what libraries you'll be using for the class you are taking, there is a very good chance that they'll be the same using gcc.  Like some else mentioned writing your code at home and compiling and then comparing the results when you compile at your school is a good idea.  Using Wine or Cedaga dones't really sound necessary for this, but using virutalization will be your best bet for full compatibility.  That means installing Windows inside Linux and not using a compatibility layer.  There is a lot of information about this if you search the forums for virutalization, virtual box, vmware and qemu.

---

### Post by onewyldmustang on 2007-09-07
sqee3, were you able to get those programs to work?  I am also trying to find some type of program on my Ubuntu to work with some of my Windows programs.  I'm new to Ubuntu and like you, would rather not deal with Windows.  Can you tell me which program worked for you so I can install it myself as well?  Thanks

---

### Post by clownius on 2007-09-07
Im not sure how old you machine is but i got XP working using KVM the other day.  Wasnt all that hard and seems reasonably fast.  No good for games though as i cant seem to get 3d graphics to work.

---

