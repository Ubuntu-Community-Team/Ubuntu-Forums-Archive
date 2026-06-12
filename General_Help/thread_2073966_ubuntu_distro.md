---
title: "ubuntu distro"
date: 2012-10-20
forum: General Help
---

### Post by IAMTubby on 2012-10-20
Hey,
I want to install an ubuntu version on my system. First, can you suggest me a non-unity stable version. I'm using 11.10 currently and I just don't like the unity interface.

I am currently downloading the 10.10 from [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)
But here again I have a question. Mine is a 64-bit intel PC(Dell Inspiron 1545).

So which of the 2 options am I supposed to download
a)PC (Intel x86) desktop CD
b)64-bit PC (AMD64) desktop CD

Thanks.

---

### Post by sgage on 2012-10-20
> **IAMTubby said:**
> Hey,
I want to install an ubuntu version on my system. First, can you suggest me a non-unity stable version. I'm using 11.10 currently and I just don't like the unity interface.

I am currently downloading the 10.10 from [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)
But here again I have a question. Mine is a 64-bit intel PC(Dell Inspiron 1545).

So which of the 2 options am I supposed to download
a)PC (Intel x86) desktop CD
b)64-bit PC (AMD64) desktop CD

Thanks.

Either of those will work with your system. Pick the AMD64 version if you have more than 4 GB RAM. I use the 32-bit version (x86) even though my machine has a 64-bit processor. I think a while back there were some issues with 64-bit versions wrt drivers and such, which are long since resolved, but I still use the 32-bit version for some reason. :KS

---

### Post by IAMTubby on 2012-10-20
> **sgage said:**
> Either of those will work with your system. Pick the AMD64 version if you have more than 4 GB RAM. I use the 32-bit version (x86) even though my machine has a 64-bit processor. I think a while back there were some issues with 64-bit versions wrt drivers and such, which are long since resolved, but I still use the 32-bit version for some reason. :KS
thanks sgage . okay, but ideally I want a 64-bit version which says Intel. Why doesn't such a combination figure in the list ?

It says either 32-bit Intel or 64-bit AMD.
As I said, I want a 64-bit Intel.

---

### Post by AlexDudko on 2012-10-20
> **IAMTubby said:**
> thanks sgage . okay, but ideally I want a 64-bit version which says Intel. Why doesn't such a combination figure in the list ?

It says either 32-bit Intel or 64-bit AMD.
As I said, I want a 64-bit Intel.

amd64 will work on both Intel and AMD it shows only the architecture type.
If you don't like Unity you can try Gnome-shell, KDE, XFCE, LXDE... There are Gnome Classic and Gnome Classic (No Effects) versions of Gnome DE as well.

---

### Post by sgage on 2012-10-20
> **IAMTubby said:**
> thanks sgage . okay, but ideally I want a 64-bit version which says Intel. Why doesn't such a combination figure in the list ?

It says either 32-bit Intel or 64-bit AMD.
As I said, I want a 64-bit Intel.

AMD64 is the name of the instruction set used by both 64-bit Intel and AMD chips, so don't worry about it. There is no corresponding INT64 for Intel's mainstream processors of today. 

Intel's first 64-bit chips (Itanium) used an entirely different architecture/instruction set from i386 (IA-64), so AMD rushed to market with something more similar to the old school i386, but 64-bits. It was adopted very quickly...

I believe Intel refers to it as the x86-64 architecture, but the instruction set is the same AMD64.

---

### Post by howefield on 2012-10-20
Given that 10.10 has reached end of life and is no longer supported, have you considered using a current version but with a non unity desktop environment ?

Xubuntu for example ?

---

### Post by sgage on 2012-10-20
> **howefield said:**
> Given that 10.10 has reached end of life and is no longer supported, have you considered using a current version but with a non unity desktop environment ?

Xubuntu for example ?

Or Gnome Classic, which really works quite nicely now, and is really quite similar to the old-school Gnome. I use Gnome Classic often, most often I use Gnome Shell.

---

### Post by IAMTubby on 2012-10-20
> **AlexDudko said:**
> amd64 will work on both Intel and AMD it shows only the architecture type.

> **sgage said:**
> AMD64 is the name of the instruction set used by both 64-bit Intel and AMD chips, so don't worry about it. There is no corresponding INT64 for Intel's mainstream processors of today. 

Intel's first 64-bit chips (Itanium) used an entirely different architecture/instruction set from i386 (IA-64), so AMD rushed to market with something more similar to the old school i386, but 64-bits. It was adopted very quickly...

I believe Intel refers to it as the x86-64 architecture, but the instruction set is the same AMD64.
AlexDudko,sage,
Can you explain that once again, why does Intel call it's 64-bit architecture also by the name AMD64 ? Would like to try and understand.


> 
If you don't like Unity you can try Gnome-shell, KDE, XFCE, LXDE... There are Gnome Classic and Gnome Classic (No Effects) versions of Gnome DE as well.

> **sgage said:**
> Or Gnome Classic, which really works quite nicely now, and is really quite similar to the old-school Gnome. I use Gnome Classic often, most often I use Gnome Shell.
Are you saying that even in Ubuntu 11.10 I can install Gnome Classic ? Okay, I shall try googling that. 


> **howefield said:**
> Given that 10.10 has reached end of life and is no longer supported, have you considered using a current version but with a non unity desktop environment ?

Xubuntu for example ?
Thanks for the suggestion howefield

---

### Post by sgage on 2012-10-20
"Can you explain that once again, why does Intel call it's 64-bit architecture also by the name AMD64 ? Would like to try and understand."

You are confusing a company's name for their architecture with the instruction set that that architecture operates under. Indeed, Intel calls its 64-bit ARCHITECTURE x86-64. It uses the same INSTRUCTION SET as AMD64 architecture chips - and they were there first...

You see, it's historical. Intel's first 64-bit chip was the Itanium (it was not very successful, especially in early days - hence the nickname "the Itanic"). Intel actually had hopes that it would supercede the i386 (32-bit) line - it could emulate the instructions that i386 chips used, but only very (ridiculously) slowly. It was a whole new architecture AND instruction set, requiring strange new compilers to be written and so forth. Turned out to be more difficult than they planned, for a number of reasons. Google Itanium if you care.

AMD jumped on the opportunity and quickly developed 64-bit processors that used an architecture and instruction set very similar to previous 32-bit i386 chips. They dubbed their architecture and the instruction set AMD64. It caught on very quickly with developers, and Microsoft adopted it and supported it. Intel was forced to market chips that could use this instruction set. Since then, Intel's mainstream 64-bit chips utilize the AMD64 instruction set.

That's why the 64-bit version of Linux you use is called AMD64. It's what AMD and Intel 64-bit chips understand. I'm sure Intel would love if it was generally called x86-64 (that's what they call it), but AMD was there first. 

Myself, I have only ever used Intel chips...

---

### Post by sgage on 2012-10-20
"Are you saying that even in Ubuntu 11.10 I can install Gnome Classic ? Okay, I shall try googling that. "

Yes you can - just

```
sudo apt-get install gnome-panel
```

But then, you might as well use the latest Gnome Classic under 12.10. It works very well, very fast.

---

### Post by The Cog on 2012-10-20
> **howefield said:**
> Given that 10.10 has reached end of life and is no longer supported, have you considered using a current version but with a non unity desktop environment ?

Xubuntu for example ?

+1 for Xubuntu 12.10. 
I'm slapping it on all my PCs and I'm loving it.

---

### Post by IAMTubby on 2012-10-20
> **sgage said:**
> 
You are confusing a company's name for their architecture with the instruction set that that architecture operates under. Indeed, Intel calls its 64-bit ARCHITECTURE x86-64. It uses the same INSTRUCTION SET as AMD64 architecture chips - and they were there first...

Thanks a lot sgage for the great explanation.
What I understand is, doesn't matter what the hardware of the processor, here we are talking about the architecture/instruction set.
Intel's first 64-bit architecture called Itanium didn't do well, and so AMD seized the initiative and came up with their own instruction set called AMD64. Microsoft started making Windows for this architecture and it started doing well, so Intel too, had to stick with the AMD64 architecture if it wanted it's chips to be compatible with OS's. So, AMD64 is an instruction set/standard that can be used by any chip manufacturing company in the world; not something restricted to AMD alone.

Just 2 more questions, 
1)So, do i3, i5, i7 all still work on the AMD64 instruction set ?

2)If yes, why is Intel a huger brand as compared to AMD ? If Intel uses the instruction set developed by AMD, what is it that makes Intel stand out ?

Thanks.

---

### Post by sgage on 2012-10-20
> **IAMTubby said:**
> Thanks a lot sgage for the great explanation.
What I understand is, doesn't matter what the hardware of the processor, here we are talking about the architecture/instruction set.
Intel's first 64-bit architecture called Itanium didn't do well, and so AMD seized the initiative and came up with their own instruction set called AMD64. Microsoft started making Windows for this architecture and it started doing well, so Intel too, had to stick with the AMD64 architecture if it wanted it's chips to be compatible with OS's. So, AMD64 is an instruction set/standard that can be used by any chip manufacturing company in the world; not something restricted to AMD alone.

Just 2 more questions, 
1)So, do i3, i5, i7 all still work on the AMD64 instruction set ?

2)If yes, why is Intel a huger brand as compared to AMD ? If Intel uses the instruction set developed by AMD, what is it that makes Intel stand out ?

Thanks.

Question 1) Yes, yes, and yes. They all do, they all have to!

Question 2) Because once Intel saw the writing on the wall, they threw everything they had at the issue, and could make chips that out-performed AMD's at a given price point. Though for a while, there, it see-sawed back and forth. I have generally felt that Intel made the superior hardware.

Intel also has had a huge range of support chips, graphics chips, etc. Just generally a huger company to begin with - ever since IBM chose an Intel chip for its "PC", back in the day. I remember it well. I go back a while with this stuff - I remember when Microsoft's main (only?) product was a BASIC interpreter! And Intel's processor rival was Zilog (I loved programming the Z-80 in assembler, and was good at it, if I do say so!).

But anyway, Intel was so much bigger to begin with, they had the R&D to put out new chips that ran faster, cooler, lower power consumption, smaller die-size, etc. (all, of course, running the AMD64 instruction set). Intel and AMD did not start out from the same place in the market, and Intel was quick to see what was going on - quick enough, at any rate.

Intel also had huge deals with lots of PC manufacturers, so had locked in volume customers, with the associated economies of scale.

It's really a fascinating history!

---

### Post by IAMTubby on 2012-10-20
> **sgage said:**
> 
It's really a fascinating history!
Thanks a lot sgage :)

---

### Post by sgage on 2012-10-20
> **IAMTubby said:**
> Thanks a lot sgage :)

I'm glad you were interested - and it is kind of fun for me to think back on the last 30+ years of "microcomputers", as we used to call them. :KS

---

