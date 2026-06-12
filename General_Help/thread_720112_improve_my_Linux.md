---
title: "improve my Linux?"
date: 2008-03-09
forum: General Help
---

### Post by jesusfreak107 on 2008-03-09
Hey, I am a teenager who is planning on a career in Linux, and, for my teen/college years, I am going to be doing tech support, specializing in keeping both Windows and Linux installations running, and running GOOD.  I also like to use Linux's speed to convice my friends to choose it over Wimpdows.  So... I was wondering if any of you, from your personal experience, have any ways for an intermediate Ubuntu user to improve speed/boot time/Internet speed on a machine?  I already learned about disabling ipv6, to make the Internet run faster, and I am looking for other posts to help in other areas.  any help, people?
:guitar:

---

### Post by Gen2ly on 2008-03-09
Nicethought for a career.  Not many would choose such an ambitious goal.  As for lightening Ubuntu the best help any user can do to help their pc is more Ram.  If thats not possible or are maxed take a look lighter distros like Xubuntu.  Alot of tweaks can be done to light ubuntu but ubuntu not's really made for that, its make to be as utilitarian as possible.

Good luck convicing your friends. :)

---

### Post by Tatty on 2008-03-10
Generally Ubuntu is shipped to be as optimised as possible.  But there are a few things you can do to try speeding it up:

1. Try profiling your boot by adding the word "profile" to the grub line for a boot.  (do not add it to your menu.lst file, just add it one off when booting)  This helps the readahead of important files.

2. You could try lowering the swappiness of the system (ie. how likely it is to put something into swap).

3. You could try compiling your own custom kernel for your computer - I have never done this myself but most people who do would swear by it.

---

### Post by jesusfreak107 on 2008-03-10
I've got an old Gateway 700 MHz computer, maxed out at 512 MB RAM, so that is not an option for me.  Also, I am rather looking at free ways to do it.  And, yes, I'm using Xubuntu.  Thanks for the encouragement! 
Oh, and, I like your quote!

Also, as an add to the original post, I learned yesterday that, at a nearby community college, I can take a course (while still in high school), and get a license that will enable me to either start my own tech support service, or work for a company such as Geek Squad.  Also, since we have, or will by next week(another one is on it's way) 8 computers in the house, and my Dad is tired of being Tech support, I am now officially the house tech support for our family, and Dad is paying me on a weekly basis, and on a per-job basis.  So, my "career" in tech support is off to a wonderfull start!

---

### Post by jesusfreak107 on 2008-03-10
> **Tatty said:**
> Generally Ubuntu is shipped to be as optimised as possible.  But there are a few things you can do to try speeding it up:

1. Try profiling your boot by adding the word "profile" to the grub line for a boot.  (do not add it to your menu.lst file, just add it one off when booting)  This helps the readahead of important files.

2. You could try lowering the swappiness of the system (ie. how likely it is to put something into swap).

3. You could try compiling your own custom kernel for your computer - I have never done this myself but most people who do would swear by it.
add profile to grub line?  what do you mean, if not adding it to the menu.lst file?  do you mean just doing that for one boot, to see if it helps, and, if it does, adding it to the menu.lst file?

---

### Post by jesusfreak107 on 2008-03-10
> **Tatty said:**
> 
2. You could try lowering the swappiness of the system (ie. how likely it is to put something into swap).

3. You could try compiling your own custom kernel for your computer - I have never done this myself but most people who do would swear by it.

How do I lower the "swappiness"?  

and, I am not nearly advanced enough to create my own kernel, although that is a future project of mine.  I think my Dad is creating his, though.

---

### Post by Gen2ly on 2008-03-10
512 is actually a good amount of Ram, for most tasks your pc will do well in linux.  Changing swapiness can speed up linux.  Swapiness is the input/output priority of swap.  To measure the current value:

```
cat /proc/sys/vm/swappiness
```

To change the swap priority (lower value means less swapping):

```
sysctl vm.swappiness=10
```

• to use this value permanently add it to /etc/sysctl.conf

```
vm.swappiness=0
```

Swap will be used still even if set to 0.  A 0 value will tells Linux to use swap when it absoluty needsto.

---

