---
title: "&quot;Booting in insecure mode&quot; after nVidia drivers installation"
date: 2016-12-04
forum: General Help
---

### Post by ijhm86 on 2016-12-04
Hi everyone,

I am running Ubuntu 16.04. I recently bought a GTX 1050Ti and I installed the drivers in Win10 (dual boot) without a problem. The thing is that in order to install them in Ubuntu I had to kill the X Server and to disable secure boot. So now, every time I start my computer I get the following message: "booting in insecure mode". There are many threads which tell you how to re-enable it again. But I would like to know what are the practical consequences of having it disabled. Is it a problem? Also, would re-enabling the secure mode disable the graphics card? 

Also, now whenever I open Google Chrome I get the annoying keyring popup. How do I get rid of it without having an empty password as many threads suggest? I have been using Ubuntu 16.04 for a while now and I had never been asked to provide any password when I started my computer or opened Chrome. What did I do wrong when I installed the nVidia drivers? 

Thanks for your help.

---

### Post by saito2 on 2017-01-02
> There are many threads which tell you how to re-enable it again. But I  would like to know what are the practical consequences of having it  disabled. Is it a problem? Also, would re-enabling the secure mode disable the graphics card?

Secure boot is used to prevent anything that isn't signed with a certified key to boot. This in theory helps to prevent malware from booting on your system. Many question it's usefulness and many don't even think twice before disabling it.

I, unfortunately, do not want to disable secure boot and still struggle to find an answer to your first question. As to whether enabling secure boot will disable the graphics card - sort of. It renders the proprietary nvidia driver useless if it even runs or lets you log in. You can fall back to the noveau driver and use it with secure boot enabled. 

However, the noveau driver doesn't work well on my gt720 and I know the proprietary driver works great. I'm not willing to disable secure boot and it seems there is no solution so far. 

This is my second day trying to figure out how to use nvidia proprietary drivers with secure boot enabled. If anyone has the answer, please share!

---

### Post by Autodave on 2017-01-02
Have either of you installed the Nvida driver from the repositories or did you go to Nvidia's site and download them?

---

### Post by saito2 on 2017-01-02
I've only used the repositories. Is the signing any different from Nvidia's site?

---

### Post by oldfred on 2017-01-02
[https://wiki.ubuntu.com/SecurityTeam/SecureBoot#Introduction](https://wiki.ubuntu.com/SecurityTeam/SecureBoot#Introduction)

If you read the above, part is about how Ubuntu's Secure Boot is more to enable a system to boot, not to harden your system. They suggest if you want to really harden your system, you need to compile your own kernels & use your own keys.

But issue with many drivers is that Canonical cannot verify the drivers are Secure since just binary blobs provided by vendor. 
Nvidia is updating drivers to be secure, but then they need the dpkg/dkms process to verify that the driver is Secure. 
AMD elected to drop fglx proprietary driver and work on just open source. 
But there are other drivers also that sometimes must be included.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security 

I believe it is mostly Marketing. You have Software that every time it is mentioned, there is discussion of virus and other issues.
So you come out with a version called Secure Boot. Solves all your problems, right? 
It just is the only major Boot virus was with BIOS and from Sony, to prevent you from running Sony Music without license. 
Microsoft also updated its own virus software so issue is not as bad, so the secure boot version has solved your problems,   not.

Eventually we may need secure boot, but I do not turn it on for now.

Edit, another link.
 Why disabling &#8220;Secure Boot&#8221; is enforced policy when installing 3rd party modules
[http://askubuntu.com/questions/755238/why-disabling-secure-boot-is-enforced-policy-when-installing-3rd-party-modules](http://askubuntu.com/questions/755238/why-disabling-secure-boot-is-enforced-policy-when-installing-3rd-party-modules)

---

