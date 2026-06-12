---
title: "Fiesty freezes extremely often, Toshiba Laptop, ATI Radeon 9100"
date: 2007-04-21
forum: General Help
---

### Post by se2131 on 2007-04-21
So I had this problem w/ the beta version, and I was hoping it would be fixed by now.  Basically, the computer freezes at very random points (I don't know how to duplicate it).  The mouse is responsive, and the keyboard is somewhat responsive, but I can't do anything (minimize windows, open applications, etc.).

There have been some other thread's like this also, but they all seem to be dealing w/ NVIDIA drivers.  I have an ATI Radeon 9100.  My laptop is a Toshiba Satellite. 

With Edgy, the computer would freeze every once in a while, but it wasn't so bad.  Now it's doing this every 20-30 minutes at least.  

Thanks in advance

---

### Post by elephant007 on 2007-04-21
In my experience with Linux, most of the time when the OS freezes it is due to hardware failure.  If I were you I would run diagnostics on your hardware, particularly the hard drive.  Since the freezing happened on two different versions, I would say it is most likely some hardware failure.

---

### Post by se2131 on 2007-04-21
What would be the best way to go about doing diagnostics on the hardware?  Also, I don't understand why the hardware would be fine (relatively) for Edgy and Windows, but so terrible for Fiesty.  Are the sys-requirements really that different.  Thanks for your help.

---

### Post by KrazyPenguin on 2007-04-22
> **elephant007 said:**
> In my experience with Linux, most of the time when the OS freezes it is due to hardware failure.  If I were you I would run diagnostics on your hardware, particularly the hard drive.  Since the freezing happened on two different versions, I would say it is most likely some hardware failure.

Why would it be a hardware failure??

Why wouldn't the hardware fail in Linux and NOT in XPsp2??

Why would lots of people be experiencing hardware failure with Feisty??


With Desktop Effects turned off the freezing happens less frequently.
It froze in screensaver mode for me once, when I wasn't using the computer.
I'm using Intel, so I know it isn't just a NVidia problem.
Could be some kind of x problem, and I am wondering if going to Kubuntu would produce the same results.
It should since the "engine" is the same.

I will try it anyway.

---

### Post by se2131 on 2007-04-22
A quick follow-up: I put in the "noapci" argument into my kernel statement, and now it's been working perfectly fine.  I did notice that I had a "8254 timer error, not connected to IO-APIC", and now it's fixed.  Just in case somebody else has this too.

EDIT: Sorry, that should read "noapic"

---

### Post by elephant007 on 2007-04-22
> **KrazyPenguin said:**
> Why would it be a hardware failure??

Why wouldn't the hardware fail in Linux and NOT in XPsp2??

Why would lots of people be experiencing hardware failure with Feisty??


With Desktop Effects turned off the freezing happens less frequently.
It froze in screensaver mode for me once, when I wasn't using the computer.
I'm using Intel, so I know it isn't just a NVidia problem.
Could be some kind of x problem, and I am wondering if going to Kubuntu would produce the same results.
It should since the "engine" is the same.

I will try it anyway.

All I was suggesting was to test hardware to eliminate the possibility of it being a hardware problem. 
I didn't know 'lots of people' were experiencing problems with Feisty.

---

### Post by KrazyPenguin on 2007-04-22
Ya, these threads are popping up everywhere.

Should be renamed "FREEZY FAWN"

:shock:

---

### Post by dawv on 2007-04-22
ya im having the same problem.. i can even INSTALL it before the damned thing locks up.. then i to restart my computer the hard way, and try again.. usually re-partitioning my hard drive into smalled and smaller peices becasue for somereason i can delete or combine any... with feisties weird partitioner... so my hard drive is in about ten peieces... this is a HUGE bug that SERIOUSLY needs to get wored out...
 
It may be the nVidia drivers.. but Edgy worked fine for me (cept my wireless) but this wont... but it does detect my wireles... so thats a plus..
 
but so far ubuntu hasn't givenme much. operating system wise... so i guess im stuck with the broken windows for now...\
 
plz forgive my typos...

---

### Post by Safder on 2007-04-23
> **se2131 said:**
> A quick follow-up: I put in the "noapci" argument into my kernel statement, and now it's been working perfectly fine.  I did notice that I had a "8254 timer error, not connected to IO-APIC", and now it's fixed.  Just in case somebody else has this too.

EDIT: Sorry, that should read "noapic"

Hi,

I am facing this exact problem, and I also see a similar error when ubuntu starts up on my laptop. I am a Linux newbie, so I am not sure how you put in the "noapic" argument into my kernel statement. Could you please give me a step by step on how you do that. Thank you...

---

### Post by se2131 on 2007-04-23
I'm not sure how to do this the 'proper' way (editing the #defoptions line in /boot/grub/menu.lst is what I've been seeing, but the option never shows up the way it should when I do this), but here's what worked for me:

First do:

```
sudo nano /boot/grub/menu.lst
```

and scroll down until you see the line: ## ## End Default Options ## ##

After this, you will see lines that begin w/ title, root, kernel, initrd, and maybe quiet or savedefault.

What you need to do is find the kernel that you are using and edit the "kernel" line.

This is what my edits look like:

```


title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c8d81b8b-4a0a-4acb-b18f-6aa156583253 ro quiet splash **noapic**
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault


```

Make sure that you edit the kernel that you are planning to use.  If anyone knows how to make this option stick for all kernels, please provide your insight.

---

### Post by Safder on 2007-04-24
Make sure that you edit the kernel that you are planning to use.  If anyone knows how to make this option stick for all kernels, please provide your insight.[/QUOTE]
hey thanks....i dont get that error message anymore in the beginning, my computer hasn't frozen in the first few minutes..of using it, so things are looking good...Thanks a million...

---

### Post by bartaz on 2007-04-24
I don't know if this is the same problem here, but check this thread:
[http://ubuntuforums.org/showthread.php?t=408524]("http://ubuntuforums.org/showthread.php?t=408524")

---

