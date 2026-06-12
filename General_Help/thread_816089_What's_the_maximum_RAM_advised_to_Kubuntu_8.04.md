---
title: "What's the maximum RAM advised to Kubuntu 8.04?"
date: 2008-06-02
forum: General Help
---

### Post by ruipedroca on 2008-06-02
Hi,

Can someone please tell me what's the maximum RAM advised to Kubuntu 8.04?
If you can, also post the advised respective swap space.


Regards

---

### Post by kpkeerthi on 2008-06-02
Are you running a 32-bit computer?

---

### Post by Kevbert on 2008-06-02
For a 32 bit PC and 32 bit Hardy 3Gb.  For a true 64 bit machine and 64 bit Hardy (AMD2, some Intel multicore, but not Macbook Pro) 4Gb.  Any more than that it's probably a waste of time unless you're using it with professional graphics programs.
If you have a 64 bit PC running 64 bit Hardy you need to check in the bios that you can access the memory hole (some Macbook Pros - it seems cannot).  Swap space should be twice the RAM memory size, but not much more than 4Gb required.

---

### Post by R3VAMP3D on 2008-06-02
Yeah, any more than 4 gigs on either architecture is a waste unless you're a hardcore video/image editor. Or if you deal with a lot of transcoding.

---

### Post by ibuclaw on 2008-06-02
2GB is usually more than enough. Its the de facto to have on modern PCs.
Although I have a wonderfully quick system on a 2GHz single core processor, 1GB RAM and 512MB Graphics card...

But I probably haven't seen the true light yet (duo and quad core, hmm...)

[EDIT]
And as for swap space, if you have lots of RAM, then little swap is needed.

As I meantioned before, I have 1GB RAM, but I rarely fill my 2.5GB Swap up to more than 250MB...

But since all systems are different, it's probably best to advise somewhere between 512MB and 1GB for swap.

Regards
Iain

---

### Post by Kevbert on 2008-06-02
> **tinivole said:**
> 
As I meantioned before, I have 1GB RAM, but I rarely fill my 2.5GB Swap up to more than 250MB...

But since all systems are different, it's probably best to advise somewhere between 512MB and 1GB for swap.


The community link on swap is [here]("https://help.ubuntu.com/community/SwapFaq")
It's been suggested that you mainly need a swapfile if you're likely to put the system in hibernation (eg for fast bootup) and also if you run out of RAM during a process, so swap should be at least the RAM size.

---

### Post by ruipedroca on 2008-06-02
Hi,

First, i'd like to thank everybody that posted!

Second, just to clarify:
-intel celerom 1.6ghz, 32-bit
-RAM 3gb
-swap 962mb (at the time i first installed the OS i only had 1gb RAM)
-kubuntu 8.04, 32-bit
-i pretend to install vmware server with 3 servers: two "fedora 7" (first 512 RAM, second 1gb RAM)  and one "SME Server 7.3" (512 RAM)
-hard drive with 500gb

I gess i should increase swap to 3gb, minimum.
Would it be better to have a faster processor or more RAM (4gb)?
Any other ideas would be appreciated!


Regards

---

### Post by Kevbert on 2008-06-03
It's not work you increasing your RAM beyond 3Gb as your 32 bit processor and 32 bit OS can't see anything much more than 3Gb and at least 800Mb would be waisted (you could even get potential memory conflicts, though I've never seen this).

---

### Post by ruipedroca on 2008-06-03
Ok, guys i get, there's no use in using more than 3gb.

This leaves me with the option of getting a faster processor, if i want to get more perfomance.

Thanks to all!

---

### Post by ruipedroca on 2008-06-28
Just to post feedback:
I've made a test with 4gb RM (2x2gb 667mhz) and everything went fine for a few days.
Now, i've got a kubuntu server with 3 virtual machines on it, already in production. So far, everything runs ok!

However, it seems in System/kinfocenter/memory that the 4th gb doesn't give ram a big boost, but it also seems that other readings have improved, because i see a greater area or light green in the charts. 

Sorry for not being 100% accurate, but my knowledge doesn't allow me to draw much conclusions.

---

### Post by hyper_ch on 2008-06-28
you can have more than 4gb ram on a 32-bit system... if the mainboard and processor support PAE you can use up to 64gb. You'll just need to customize your kernel or install the server kernel.

---

