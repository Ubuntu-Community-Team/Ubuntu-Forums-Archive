---
title: "? Possibility: Linux on Samsung a900 ?"
date: 2007-01-23
forum: General Help
---

### Post by lotacus on 2007-01-23
I know how versitile linux is and can be, and I have witnessed it on numerous devices that were not meant for it.

I ask this question:

If having the right software, would it be possible to flash a samsung a900 with some sort of custom linux distro?

I know there are a lot of technicalities that may come to light, but getting down to the nitty gritty, would it be possible?

I am by no means experienced with linux, but what I do know, is that there would have to be a kernel that can recognize and be compatible with the different components in the phone. It would also have to be able to use the different features and control the phone as a phone, not just a mini-computer (though that would be interesting as well).

Now, if there was such a kernel available or in development, getting it on the phone would be another task. There is  well-known flashing software for these phones, and an attempt would be that the linux distro would have to be compiled in a .bin format and have spoofed? headers so that the bin could be unpacked as it's being uploaded to the phone.

But how do we go about doing that? One idea that I have roaming in my head is finding out what exactly is in the standard firmware that is packed as a .bin file. Find that out, would mean some disassembly or decompilation of an available firmware package. But then the question arises, what software will disassemble this firmware? and what was used to compile and package this firmware to begin with? My first choice would be C++, but I don't think there really is a way to find out. It could be ASM for all I know.

---

### Post by Kl4m on 2008-03-05
I know it's an old thread, but I post a reply in case someone comes here from a Google search such as I did earlier.

I found no such project. The closest thing I did was install a [ Java Mobile SSH client]("http://www.xk72.com/midpssh/") to connect to a remote Linux machine. Putting together a whole embedded Linux system to take advantage of all the features of this phone (think camera, Java apps, net access, and even the PHONE itself) under a usable GUI would be a huge endeavor, even if a custom firmware can be uploaded to it. I doubt it will ever be done.

Cheers

---

