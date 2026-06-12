---
title: "64-bit or 32-bit Operating System better when running 32-bit apps?"
date: 2016-01-10
forum: General Help
---

### Post by lewis12 on 2016-01-10
I have tried to find the answer to this online unsuccessfully, but I have a core 2 duo laptop, it was one of the first 64-bit capable processors released (T5800) with 3GB ram.
I was wondering if getting the 64-bit version of Ubuntu or Lubuntu would result in a 32-bit program running slower under the OS than if it was running on a 32-bit Linux distro of the same type?

Also, if running a 64-bit app on 64-bit Ubuntu, would it be faster than running the same app (but the 32-bit version) on the 32-bit version of that same OS?

---

### Post by tgalati4 on 2016-01-10
Welcome to the forums.

You would have to test a specific Use Case.  In general, if you have a 64-bit processor, use the 64-bit OS.  64-bit can be 10 to 40% faster for certain algorithms and for large memory manipulation.  Don't know about any speed difference running 32-bit code on a 64-bit OS.  Intel processors support 32-bit in a 64-bit OS quite well, so unless you have a specific workload to test, it's hard to make a generalization.

Run your code in a Live session.  You can boot 64-bit, run your 32-bit code and log the results.  Then boot 32-bit and run your 32-bit code.  If your code requires a lot of hard disk access (because it won't run in 3GB of RAM), then set up a dual-boot system.  Be sure to make two swap partitions, one 32-bit, one 64-bit, since swap space can't be shared across different word-length systems.

One test is worth a thousand expert opinions.

---

### Post by oldfred on 2016-01-11
Just install the 64 bit.

I am running 64 bit on my 2006 laptop with Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz. It only has 1.5GB of RAM and I can only run one larger app like Firefox and a couple of smaller apps like terminal or it does start using swap. With 3GB of RAM, you should not have issues.
It does not have enough video horsepower to run Unity, so I run gnome-panel/flashback/fallback.

With 16.04, they were discussing discontinuing 32 bit. Any system that has to have 32 bit is so old or so lightweight that it cannot run Unity. But they elected to just offer 32 bit as minimal support and downplay its availability.
 Developer's discussion of deemphasis of 32 bit Ubuntu - Nov 2014 
[http://www.phoronix.com/scan.php?page=news_item&px=MTgzODE](http://www.phoronix.com/scan.php?page=news_item&px=MTgzODE)
[http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/](http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.

---

### Post by Dennis N on 2016-01-11
My valuable 32 bit games won't start when installed on 64 bit version of the OS, so it's not better for those. I keep a 32 bit version installed as well. 

Tried one with 15.10, 64 bit, but still no go. If it's possible to run them with some extra magic, it should work out of the box.

---

### Post by XBNCPRk on 2016-01-11
> **Dennis N said:**
>  If it's possible to run them with some extra magic, it should work out of the box.

Im sorry, but I disagree. Not everyone wants a bunch of 32 bit libraries on their machine that may very well likely never get used. No offense intended and it's certainly understandable that you have programs youre attached to in one way or another, but it's the digital equivalent of keeping a set of Encyclopedia Britannica around instead of just googling it. If you absolutely need it, great, you can get it, but its not in any way necessary for everyone. 

That said, I would assume that the programs will run within a performance precentage point or two, if not identically.

---

### Post by Dennis N on 2016-01-12
@XBNCPRk

The thing is there are no 64 bit versions offered for those games and they are timeless and valuable. So I keep my 32 bit OS on a BIOS computer. It's been no problem at all for me to do that. I just wonder how many mB it would really add to include those libraries? Is there one package to add all that's required to run 32 bit apps on a 64 bit OS?  

EDIT: I found a solution. These 32 bit programs will run on 64 bit UEFI Manjaro without the user needing to add anything extra. Obviously, Manjaro has the necessary libraries included when it's installed. Now, I can use these 32 bit applications on my UEFI computers, and when my BIOS computer becomes obsolete, there is a way to keep them going.

---

