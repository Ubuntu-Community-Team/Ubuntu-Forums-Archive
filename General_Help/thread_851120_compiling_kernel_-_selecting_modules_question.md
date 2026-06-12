---
title: "compiling kernel - selecting modules question"
date: 2008-07-06
forum: General Help
---

### Post by Arrowx7 on 2008-07-06
Hello, I was compiling the newest kernel 2.6.25.10 to get better drivers.
I copied the .config file from the old kernel (one installed through package manager), to /usr/src/linux-2.6.25.10 directory, but then ran the compile command and it asked me to check off the modules anyway.

I wanted to keep everything default, but then I came across this:

Intel Wireless WiFi 4965AGN (IWL4965) [N/m/?] (NEW) 

This is my wireless card, I kept it default, but should I have pushed "m" what is "?" anyway?

I'm confused.  Should I redo the compilation or just continue (I kept it default to 'N'). does this mean it won't install the newest driver for my wireless card?

Thanks!

---

### Post by PmDematagoda on 2008-07-06
If you compile that driver with option "m" then the driver is only compiled as an optional module which I think would not be loaded by default, when you choose "Y"(or similar) then the module is loaded by default.

---

### Post by Arrowx7 on 2008-07-06
What is the question mark in the option list?
thanks

---

### Post by hal8000 on 2008-07-06
> **Arrowx7 said:**
> Hello, I was compiling the newest kernel 2.6.25.10 to get better drivers.
I copied the .config file from the old kernel (one installed through package manager), to /usr/src/linux-2.6.25.10 directory, but then ran the compile command and it asked me to check off the modules anyway.

I wanted to keep everything default, but then I came across this:

Intel Wireless WiFi 4965AGN (IWL4965) [N/m/?] (NEW) 

This is my wireless card, I kept it default, but should I have pushed "m" what is "?" anyway?

I'm confused.  Should I redo the compilation or just continue (I kept it default to 'N'). does this mean it won't install the newest driver for my wireless card?

Thanks!

The ? displays help on each kernel module. If you answer Y then any kernel driver is compiled into the kernel, m compiles the driver as a loadable module, and n is the option for no support
However its not simply enough to compile the module as you will have to build the kernel and then make the modules. You will also have to create another initial ramdisk if you are creating a kernel with the default ubuntu options.
When copying the .config to /uar/src/linux your first step is to run
make oldconfig this compiles the kernel using the options in the .config file and then prompts you for to create a module, builtin support or no support for any new kernel drivers.
If you've not recompiled a kernel before then make sure you dont delete your original kernel as you are in danger in borking your system.

---

### Post by Arrowx7 on 2008-07-06
great, thanks for your help hal

---

### Post by hal8000 on 2008-07-06
> **Arrowx7 said:**
> great, thanks for your help hal

You're welcome. This page may help you in your quest:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

