---
title: "Ubu on Pi 5 - Am I able to install software that doesn't have a package for me?"
date: 2024-05-24
forum: General Help
---

### Post by schwim-dandy on 2024-05-24
Hello everyone!

This is my first time playing around on a device that uses ARM-specific software and am finding a lot of my regulars are not offered in this architecture.  As an example, I'm looking at the megasync download page offering only X64.

Am I just out of luck for these apps or is there a way to install these in a container of some sort that would allow me to use them?

Thanks for your time!

---

### Post by TheFu on 2024-05-25
You are out of luck, unless you want to port them to the ARM CPU.  Good luck with that.  Non-scripted software is compiled for a specific architecture (except Java). That means it expects a specific CPU model/family and a specific OS to provide OS services to the program.

This is why Java programs, perl, python, ruby, bash, javascript are inherintly cross-platform - assuming they aren't using custom optimized parts that are created for a specific CPU architecture.

Containers are the same.  They only allow programs from the same host CPU architecture/OS to be run.

Some virtual machines will allow different architectures to run, but there's almost always a huge performance hit doing that.

Why not just run the programs remotely on your x86-64 computer and have the window displayed on your pi5?  This has been built-into X/Windows over 40 yrs.  It works.  Heck, my web browser that I'm typing this into is running on a computer on the other side of the house, but it feels local to me.  It works.  No remote desktop, just a remote window, which is very light.  Best not to use wifi, but it can be used if the connection isn't bad.  Wired ethernet is always best.

[https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) - look at the section: "ssh tunneling X/Windows" - that's what you want.

---

### Post by Holger_Gehrke on 2024-05-25
For the mega application(s) - megasync and megacmd -  compiling from source should be possible since it's cross-platform (Linux/Mac/Windows) and Macs have been Arm since 2020/2021. The source can be found on [https://github.com/meganz](https://github.com/meganz) . For all other applications you can't live without you might want to take a look at qemu - specifically qemu-user. This program provides a mix between virtualization and emulation and the qemu-user variant emulates the userland code but recognizes system calls and executes them natively (and does some magic before and after the system call to make the parameters and results usable). As far as I know it should be almost transparent once it's set up, but of course there's a hefty performance penalty. Expect Raspberry Pi 1 performance levels for x86 programs running on a Pi 5.

Holger

---

