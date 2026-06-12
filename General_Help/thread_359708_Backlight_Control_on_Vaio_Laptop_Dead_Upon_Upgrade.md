---
title: "Backlight Control on Vaio Laptop Dead Upon Upgrade to Edgy"
date: 2007-02-12
forum: General Help
---

### Post by SendDerek on 2007-02-12
Hello all!

I have sort of a strange problem with my Sony Vaio laptop that wasn't there before with Dapper.  My backlight cannot be controlled using the power management preferences.  I have installed a few packages in hopes that it would clear up, but no resolve.  Here are the packages:
> 
spicctrl
vaiostat-source


What would have happened from the update?  And just to be sure we're clear... this is a fresh install from the Edgy Desktop CD, not the upgrade.

Thanks for any help in advance.

-Derek

---

### Post by SendDerek on 2007-02-19
Bump! 

;)

---

### Post by SendDerek on 2007-03-25
Would anybody happen to know what would've caused this to happen with the update?  Is there something I can do to find the answer?

Thanks.

---

### Post by louistan3 on 2007-03-25
i thnk this also happend to me.. i have a sony vaio sz... 

uhhmm.. but i forgot what module i used to fix it..

might be sonypi? 

sorry.. il try and remember how i fixed mine.. 

check on yah later...

---

### Post by superatrain on 2007-03-25
Hey:
Sometimes new kernel versions cause issues. For example, with the upgrade to edgy, I went from the 2.6.15 kernel to the 2.6.17 kernel. On my laptop, that broke acpi, and the ability to sleep.

You can uninstall the new kernel (linux-image-2.6.17-version) or set the old one as default. You usualy wont loose much with a minor kernel change like that, ubuntu should work fine.

Good luck!

---

### Post by SendDerek on 2007-03-27
I just realized that I don't have sonypi installed... I'm gonna give that a go and see what happens.  Thanks for the suggestions ya'll!

---

