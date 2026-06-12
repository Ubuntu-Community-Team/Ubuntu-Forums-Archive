---
title: "should I be using half of my ram while idle?"
date: 2013-01-09
forum: General Help
---

### Post by LLCoolJeff on 2013-01-09
according to "$ top" I am using about 2.6 of my 6gb total ram while my computer is just idling with firefox open. I was wondering if this sounds about average or high?

I think I read that the computer tried to keep as much ram used as possible, but I don't have much experience with these things, so I just wanted to double check...

---

### Post by Cheesemill on 2013-01-09
What is the output of...
```
free -m
```Can you post back the result in [noparse]```
 
```[/noparse] tags to make it easy to read please.

You may be getting confused between used, available and cached memory. For more info...
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by LLCoolJeff on 2013-01-09
> **Cheesemill said:**
> What is the output of...
```
free -m
```Can you post back the result in [noparse]```
 
```[/noparse] tags to make it easy to read please.

You may be getting confused between used, available and cached memory. For more info...
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

```
    
                     total       used       free     shared    buffers     cached
Mem:          5828       2551       3277          0        148       1339
-/+ buffers/cache:  1062       4765
Swap:         6001          0          6001

```

here it is. I straightened the columns up a bit

---

### Post by scratman on 2013-01-09
Well, it's not normal for me, I'm using about 40%, and have browser with many tabs, LibreOffice, Transmission and Spotify running



top - 22:05:32 up  1:05,  2 users,  load average: 0.48, 0.67, 0.86
Tasks: 155 total,   2 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.4%us,  5.1%sy,  0.0%ni, 83.7%id,  0.7%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   4079088k total,  1637092k used,  2441996k free,    60436k buffers
Swap:  4143100k total,        0k used,  4143100k free,   897208k cached

```
            total       used       free     shared    buffers     cached
Mem:          3983       2038       1945          0         63       1275
-/+ buffers/cache:        699       3284
Swap:         4045          0       4045
 
```

---

### Post by LLCoolJeff on 2013-01-09
> **LLCoolJeff said:**
> ```
    
                     total       used       free     shared    buffers     cached
Mem:          5828       2551       3277          0        148       1339
-/+ buffers/cache:  1062       4765
Swap:         6001          0          6001

```here it is. I straightened the columns up a bit

and they came out completely messed up, here is just a screenshot:

---

### Post by Cheesemill on 2013-01-09
If you had just put it in [noparse]```
 
```[/noparse] tags and not tried to straighten it up it would have been OK.

As it is you are using about 1GB of your 6GB of RAM (that's 18%), for more information read the link I posted earlier

---

### Post by LLCoolJeff on 2013-01-09
> **Cheesemill said:**
> If you had just put it in [noparse]```
 
```[/noparse] tags and not tried to straighten it up it would have been OK.

As it is you are using about 1GB of your 6GB of RAM (that's 18%), for more information read the link I posted earlier

ok, thanks, I read the link and I understand what it is saying. I closed out all my programs and ran $free -m again and it said I was using 860mb of ram just idling doing absolutely nothing.

I guess my question now is, does 860 while doing nothing but system tasks sound right on a plain 12.10 64 bit install?

---

### Post by Cheesemill on 2013-01-09
> **LLCoolJeff said:**
> ok, thanks, I read the link and I understand what it is saying. I closed out all my programs and ran $free -m again and it said I was using 860mb of ram just idling doing absolutely nothing.

I guess my question now is, does 860 while doing nothing but system tasks sound right on a plain 12.10 64 bit install?
Sounds fine to me.

---

### Post by howefield on 2013-01-09
> **LLCoolJeff said:**
> I guess my question now is, does 860 while doing nothing but system tasks sound right on a plain 12.10 64 bit install?

It isn't abnormal, mine boots using 500 but after using some applications and closing them will idle between 600 - 750, sometimes more. Nothing to worry about.

Unused RAM is a waste of money :-)

---

### Post by LLCoolJeff on 2013-01-09
ok, thanks guys. Mine has been running for a few days and has had many things open and close since booting.

Thanks for giving me a reference point, i'll check out what happens next time I do a fresh boot.

---

