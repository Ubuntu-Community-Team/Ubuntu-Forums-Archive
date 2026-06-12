---
title: "Ubuntu 12.10 is not starting"
date: 2012-11-10
forum: General Help
---

### Post by ahazra on 2012-11-10
[B]ubuntu  12.10 is not starting ..... after selecting ubuntu at grub(btw there is  no "recovery mode" option in the grub...I do not know how to get  that...but that is another issue) ...the page which shows ubuntu 12.10  with 5 dots is showing....then there is a black screen ... then a long  wait ....I hoped primarily due to some reasons ,it is taking a long time  then...I understood that this is going to be eternal... and "this  requires action " and it is complicated by the fact that there is no  "recovery mode" in the grub... there is no solution posted for this  problem in internet ...(only good thing about this whole irritating  situation is that I have found a new problem :P).... 
[/B]

---

### Post by 2F4U on 2012-11-10
What are your hardware specs, graphics card etc.?

---

### Post by bogan on 2012-11-10
Hi!, **ahazra,**

With Grub2, v2.00 Boot Menu, in 12.10, you should have an entry for 'Ubuntu' and another: "Advanced Options for Ubuntu". Select the second - it is the title of a sub-menu - and press 'Enter'.

You will get two lines, the first is the same as the normal Ubuntu boot line. The second is the recovery mode - select the one you want.

Similarly for any other previous OS's you have installed.

Chao!,** bogan**.

---

### Post by BlastDV on 2012-11-13
Hello there! I'm having the same problem here. I don't think this is a hardware problem, cause my Ubuntu was running perfectly till I tried to change some permissions to a MicroSD memory and after rebooting there was no more Ubuntu.

I used something like this:

```
chmod -R 7777 /MicroSD
```

Yeah, four '7', after that I just shutdown my system, and when it was killing all the open processes a lot of error messages started to show off.  I remember it said something about not found files or something like that.

I had to boot from a 12.04 Live CD and what I found is that my whole Linux partition had a stunning "Not Reading" permission activated.

I think that my system is not starting because of that, cause nothing in there can be read. I tried changing Owner with chown and then the permissions again, but it stills no working. Any Idea? I don't want to format my partition!
I think that my system is not starting because of that, cause anything in there can be read. I tried changing Owner with chown and then the permissions again but it stills no working. Any Idea? I don't want to format my partition!

---

