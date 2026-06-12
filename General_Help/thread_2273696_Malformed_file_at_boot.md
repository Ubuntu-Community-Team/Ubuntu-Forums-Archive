---
title: "Malformed file at boot"
date: 2015-04-14
forum: General Help
---

### Post by will_s2 on 2015-04-14
When I boot into Ubuntu 14.04 LTS I get an error message  “Malformed file : press any key to continue” and then if I press a key or after a length time my login /password screen  will appear. No major dramas here but am curious as to what is causing this problem and how I can fix it.
 

 

 I have Ubuntu on a separate SSD and Win7 on another SSD and it boots into Windows unless I hit the F12 screen and then from that list I select my Linux hard drive  and paragraph 1 happens. Basically it suits me not having the Ubuntu Bootloader or whatever its called and using the Motherboards options through the F12 key

---

### Post by cariboo on 2015-04-14
You could check dmesg to see if anything shows up. Open a terminal and type the following command:

```
dmesg | grep Malformed
```

---

### Post by will_s2 on 2015-04-17
came back to check for answer and since I selected the 2nd option in boot table I didnt get a malformed file message and it jts booted into Linux

---

### Post by janvdhurk3 on 2015-05-23
I have this problem also and have read about it from many users. To me it seems something strange in grub.cfg generated from /etc/default by grub-mkconfig.
This member has a structure of a shell script bur within it there seems to be a function called recordfail, there is a wrong logic structure, in other words the if's and corresponding fi's do not match. Easy to see if you use VIM for this. I have just tried to let grub remeber the last choice with parms GRUB_DEFAULT and GRUB_SAVEDEFAULT and I noticed that this saved last choice which as I understand should be rememberred in grubenv is net well stored.
In fact the file grubenv is rubbish, and it seems to explain why this feature is not working all right. My gues is that these things are related. Spanish?

I solved my problem without special actions. I have got updates automatically and I think there were updates for grub that did it. After the grub uodates the remeber last choice works now, and as I expected i have also no more messages about malformed file any longer. So if you think why bother about this message which takes may be 10 seconds boot time, this is an effect you can perceive. 
Grub is not using its grubenv file as designed and if you should bother depends on your demands.

---

