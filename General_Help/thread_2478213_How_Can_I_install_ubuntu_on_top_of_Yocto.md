---
title: "How Can I install ubuntu on top of Yocto"
date: 2022-08-19
forum: General Help
---

### Post by ellienou on 2022-08-19
Hi,


I am using some embedded platforms that requires Yokto. 
Is there anyway I can use Ubuntu in Yokto environment?



Thank you,

---

### Post by tea for one on 2022-08-19
No idea really.
But have you seen this info:-
[https://ubuntu.com/blog/embedded-linux-project-i](https://ubuntu.com/blog/embedded-linux-project-i)

---

### Post by grahammechanical on 2022-08-19
The usual way in Linux to run one operating system on another OS is to install the second OS in a virtual machine or Linux container. Does Yocto provide Linux Containers?

On this forum when someone says "Ubuntu" we think of Ubuntu desktop or Ubuntu server. I do not think that either of these are suitable for hardware that is only capable of running an embedded Linux - too large. This is why Ubuntu developers have come out with Ubuntu Core. It is a much smaller OS.

According to official Yocto documentation you should be running Yocto on Ubuntu.

> The examples in this paper assume you are using a native Linux system running a recent Ubuntu Linux distribution.

After building the Yocto kernel it is then run in Qemu. 

> **Simulate Your Image Using QEMU:** Once this particular image is built, you can start QEMU, which is a Quick EMUlator that ships with the Yocto Project:

[https://docs.yoctoproject.org/brief-yoctoprojectqs/index.html](https://docs.yoctoproject.org/brief-yoctoprojectqs/index.html)

Regards

---

