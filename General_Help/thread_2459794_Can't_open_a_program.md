---
title: "Can't open a program"
date: 2021-03-26
forum: General Help
---

### Post by grxgghxrpxr on 2021-03-26
Hello everyone, I hope everyone is doing well at the moment.

I'm currently trying to open GRUB Customizer on Ubuntu Budgie, but it isn't opening. When a program doesn't, what I normally do is try to open it from the Terminal and respond to any errors that come up, usually by installing a file or program that the program depends on that isn't installed through apt. 
When I type 'grub-customizer' in the Terminal it says 'grub-customizer: error while loading libraries: libgtkmm-3.0.so.1: cannot open shared object file: No such file or directory'. 
I have used apt to search for this ('apt search libgtkmm-3.0') & 5 results came up: 'libgtkmm-2.4-dev', 'libgtkmm-2.4-doc', 'libgtkmm-3.0-1v5', 'libgtkmm-3.0-dev' & 'libgtkmm-3.0-doc'.
I have installed all these packages, but it's still coming up with the same error - I've tried using search with a few less letters of the name to see if there are any more packages available, but nothing is coming up.

Could I have some help with this please?

Thanks
Gregg

---

### Post by TheFu on 2021-03-26
What did libgtkmm-3.0-1v5 install?  It might just need a symbolic link from libgtkmm-3.0-1v5.so --> libgtkmm-3.0.so.1    in the same directory.

---

### Post by grxgghxrpxr on 2021-03-26
> **TheFu said:**
> What did libgtkmm-3.0-1v5 install?  It might just need a symbolic link from libgtkmm-3.0-1v5.so --> libgtkmm-3.0.so.1    in the same directory.

I honestly have no idea, I'm not sure what this is all about

---

### Post by Holger_Gehrke on 2021-03-26
On 20.4 and later grub-customizer is in the repositories and should have pulled in all it's dependencies when installed with 'sudo apt install grub-customizer'. How did you install grub-customizer ? If you downloaded it as a binary from somewhere, are you sure it's for the right architecture (amd64 vs i386) ? You can check for what architecture an installed binary is compiled using the 'file'-command ('file /usr/bin/grub-customizer').

@TheFu : the package libgtkmm-3.0-1v5 installs the library /usr/lib/x86_64-linux-gnu/libgtkmm-3.0.so.1.1.0 and creates a link /usr/lib/x86_64-linux-gnu/libgtkmm-3.0.so.1 in the same directory.

Holger

---

### Post by Frogs Hair on 2021-03-26
What version of UB ? The gurb customizer sometimes doesn't work with the development version until the final release. Is this the PPA or application from the repository?

---

### Post by grxgghxrpxr on 2021-03-26
I installed it from the software centre. I then uninstalled it and tried installing with apt and I'm getting the same result.

---

### Post by grxgghxrpxr on 2021-03-26
Ubuntu Budgie 20.10, just the usual, stable consumer version

---

### Post by Frogs Hair on 2021-03-26
Similar error on 21.04 , but GC did work with 20.10. If you need to change the boot order it can be done manually.

PPA , use at your own risk and remove any installed versions first.


[https://linoxide.com/install-and-use-grub-customizer-on-ubuntu/](https://linoxide.com/install-and-use-grub-customizer-on-ubuntu/)

---

### Post by ActionParsnip on 2021-03-26
By any chance are you dual booting and want to make Windows the default option? If so then you can do this with command line very easily...

---

