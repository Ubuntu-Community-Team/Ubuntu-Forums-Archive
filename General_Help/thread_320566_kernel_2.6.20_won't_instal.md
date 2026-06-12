---
title: "kernel 2.6.20 won't instal"
date: 2006-12-17
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-12-17
Good afternoon community:D   I'm trying to install kernel 2.6.20 and I have checked everything in synaptic. But when the setting up part comes along it has problems setting up the kernel and when I reboot the kernel is a no show in the grub menue. I any one can put me in another direction to install the kernel thanks

---

### Post by hanzomon4 on 2006-12-17
You may get more help in the Feisty subforum, but I'll try to help you out. Could please post the error you get when trying to install the kernel

---

### Post by IusedTObeSOMEONEelse on 2006-12-17
How can I re-create the error for you? Thank you for reply

---

### Post by IusedTObeSOMEONEelse on 2006-12-17
Is there a way to add kernel from terminal?

---

### Post by Hossie on 2006-12-17
I'm suggesting you are trying to install a .deb file with 2.6.20rc1 kernel. You can install that on the command line with:

```
sudo dpkg -i mykernel.deb
```

---

### Post by PriceChild on 2006-12-17
After release, a distribution is put in a freeze.

Only bugfixes and security updates are applied.

Just because there is a new kernel out doesn't mean we update Dapper/Edgy with it. Just because the kernel is of a higher version doesn't mean it is better for you.

Pricey

---

### Post by hanzomon4 on 2006-12-17
> **MustangSallydd said:**
> How can I re-create the error for you? Thank you for reply

Just try to reinstall it, you can do it from the terminal like this: ```
sudo apt-get install name-of-thekernel
```

---

### Post by IusedTObeSOMEONEelse on 2006-12-17
[QUOTE=PriceChild;

Just because there is a new kernel out doesn't mean we update Dapper/Edgy with it. Just because the kernel is of a higher version doesn't mean it is better for you.

Pricey[/QUOTE]

I new that was coming sooner or later. I have made a machine for testing/playing and I am well aware of what the dangers are of playing around. I would like to install that kernel to see what kind of reaction my machine throws at me

---

### Post by IusedTObeSOMEONEelse on 2006-12-17
I have tried it through synaptic. The terminal tells me it can't find the package?

---

### Post by Hossie on 2006-12-17
How did you create that package?

---

### Post by IusedTObeSOMEONEelse on 2006-12-17
Maybe you could create it for me? ;) Sally

---

### Post by Hossie on 2006-12-17
Did you do it like [so](http://www.howtoforge.com/howto_linux_kernel_2.6_compile_debian)?

---

### Post by hanzomon4 on 2006-12-17
That's because there is no 2.6.20 kernel in the edgy repos and I think fiesty's is 2.6.19

---

