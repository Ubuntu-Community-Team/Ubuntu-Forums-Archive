---
title: "new kernel doesn't work"
date: 2007-07-10
forum: General Help
---

### Post by stepan2 on 2007-07-10
Hi guys. i decided to compile kernel 2.6.22  but ounce i compiled it and restarted , it didnt work. In grub i chose  the kernel , it said uncompressing linux...Ok booting the kernel . then it just stopped. I have no idea what i did wrong. I followed the instructions on [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) . i am running kubuntu 7.04 feisty fawn on an intel core 2 duo e6300 machine with 2gb of ram and an intel 3300 graphics accelerator.

---

### Post by destructchaos on 2007-07-10
go back to using the old kernel until the ubuntu devs put it in the repos.

---

### Post by stepan2 on 2007-07-10
That isnt a good anwser. I dont like being dependant on someone. And it is good to learn. That anwser seems like a microsoft way/ if something doesnt work , pray and hope it is fixed in  a newer version

---

### Post by stepan2 on 2007-07-10
update: I tried reinstalling and i just saw that i got the following errorwhen isntalling the kernel:
find: /lib/firmware/2.6.22-custom: No such file or directory
find: /lib/firmware/2.6.22-custom: No such file or directory
find: /lib/firmware/2.6.22-custom: No such file or directory
find: /lib/firmware/2.6.22-custom: No such file or directory
find: /lib/firmware/2.6.22-custom: No such file or directory

---

### Post by information_entropy on 2007-07-10
stepan2 said:

> i am running kubuntu 7.04 feisty fawn on an intel core 2 duo e6300 machine with 2gb of ram and an intel 3300 graphics accelerator.


I am reading your thread with great interest because I have almost the same system.
Are you doing this because:

1.you want dual core sensors support
2.you want better x3000 graphics support
3.you just want to learn how
4.you have way to much free time on your hands.
5.Other ?

I was just thinking about trying to get the new intel graphics driver to work with Fiesty
I saw that it is being tested in Gutsy

I was hoping that someone would figure out the kernel and graphics drive upgrade
and post a nice howto.  Looks complicated. ;)

I am currently waiting for a hard drive to arrive so I can image my system before trying
the video driver and/or the kernel.  That way if I totally screw it up, I won't be totally screwed. 

I await your[COLOR="Lime"] success[/COLOR] post:)

---

### Post by stepan2 on 2007-07-10
the reason i am doing it is because i am going to remaster ubuntu and i want to know how. i dont udnerstand why the error came up. I also tried installing linux headers first but it didnt work

---

### Post by stepan2 on 2007-07-10
i sincearly apologize for bumping but i feel that this topic is getting lost

---

### Post by stepan2 on 2007-07-10
Please people , i strongly encourage you to help me . again i am bumping but with the ammount of concurrent posts , it will be lost

---

### Post by bobshowrocks on 2007-07-10
Have you tried other options in the GRUB menu?

---

### Post by stepan2 on 2007-07-10
?what do oyu mean? If i choose another option then my custom kernel then there is no point..

---

### Post by jocko on 2007-07-10
> **stepan2 said:**
> update: I tried reinstalling and i just saw that i got the following errorwhen isntalling the kernel:
find: /lib/firmware/2.6.22-custom: No such file or directory
find: /lib/firmware/2.6.22-custom: No such file or directory
find: /lib/firmware/2.6.22-custom: No such file or directory
find: /lib/firmware/2.6.22-custom: No such file or directory
find: /lib/firmware/2.6.22-custom: No such file or directory

I got the exact same error when I installed my kernel, but mine is working fine, so I don't think this is your problem.
Do you get any error messages? I think the file /var/log/dmesg.0 should contain messages from your previous boot.
My guess is that you missed something in the configuration of the kernel, which means you will have to start over from the beginning.
I compiled my kernel from the instructions here: [The Master kernel thread]("http://ubuntuforums.org/showthread.php?t=311158").

---

### Post by stepan2 on 2007-07-10
You will be ahppy to know that i fixed the problem!!! Since i built my kernel , it didnt have my default options like acpi=off and it wouldntboot . But it behaved like every other kernel then ubuntu's one . read my thread here :[http://ubuntuforums.org/showthread.php?t=498039](http://ubuntuforums.org/showthread.php?t=498039)

---

