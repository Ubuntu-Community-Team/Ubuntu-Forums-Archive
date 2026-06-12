---
title: "Must I use swap Memory if I don't have to? Doesn't that slow things down?"
date: 2008-02-11
forum: General Help
---

### Post by bobleny on 2008-02-11
:) This is a fun one...

I am running Kubuntu 6.10 on a computer with 376MB of RAM and 980MB of hard drive space allocated to swap...

Now, from my understanding, swap is a lot slower than RAM, if this is so, then it would be best not to use swap at all if you don't have to, right?

-------------------
```

[FONT="Courier New"]
bob@George:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           376        360         16          0          5         93
-/+ buffers/cache:        261        115
Swap:          980         17        963
[/FONT]

```
If you look at the above table, I am using 17MB of swap (this number is usually higher, depending on current activities...), when I clearly have plenty of available RAM (115MB)...

OK, so the question is....
Is there a way to tell the computer not to touch the swap until there is less than 60MB of RAM left?

Thanks!

---

### Post by jken146 on 2008-02-11
You have less free RAM than swap used.

---

### Post by bobleny on 2008-02-11
No, not from my understanding....

What I was told that Linux takes as much RAM as necessary and stores it in a buffer(Don't ask me)...... Then, when you need to use the RAM, you are actually pulling it from the buffer.

In this case, it has buffered 360MB of my total RAM. This means that I now have 360MB of RAM to use. I am only using 261MB of  RAM leaving me with at least 115MB of RAM available. So since I am only using 261MB, I still have another 115MB to go. What I want the computer to do is, think, "hmmm. There is 115MB of RAM left, so I don't need to use the swap space."

So, is this something even worth doing? I mean since I've typed my first post. this is the free repot...
```

[FONT="Courier New"]
bob@George:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           376        244        132          0         13        108
-/+ buffers/cache:        121        255
Swap:          980        169        810
[/FONT]

```

I don't fully comprehend how the RAM is utilized, but is it really necessary to use 196MB of swap when I have 255MB of available RAM????

If I am wrong at all in any way, please tell me!

---

### Post by kerry_s on 2008-02-11
376MB ram and your running kde, trust me you need swap, no swap and that sucker will lock up like crazy or it will just be even more slower than it is.
:lolflag:

---

### Post by Rocket2DMn on 2008-02-11
You can adjust how likely the system is to use swap: [http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

---

### Post by fragos on 2008-02-11
To use less swap you need to add memory.  With 1MB you will rarely access swap.  There is also a parameter "swapiness" which can be set to use swap less frequently but you still need more memory to improve performance when you switch processes and add more. Not running as many processes can also help you.

---

### Post by Jay Jay on 2008-02-11
> **kerry_s said:**
> 376MB ram and your running kde, trust me you need swap, no swap and that sucker will lock up like crazy or it will just be even more slower than it is.
:lolflag:

Out of curiosity how much RAM do you feel KDE requires to run adequately?

---

### Post by kerry_s on 2008-02-11
> **Jay Jay said:**
> Out of curiosity how much RAM do you feel KDE requires to run adequately?

i would go with about 512mb at least, more if you like it pretty. i know it can run on less, i've run it on my 450mhz 256ram laptop, but it gets very limiting on how much you can do at once and of course slower due to swapping.

for kde i think swap is needed, kde has a lot of parts that run, those don't get swapped, that means anything not kde can be pushed off to swap, so those might feel slower.

---

