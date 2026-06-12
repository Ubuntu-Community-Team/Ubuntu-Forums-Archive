---
title: "Running Slow"
date: 2014-05-10
forum: General Help
---

### Post by Kirk_McMillan on 2014-05-10
Hi, Just installed ubuntu to try and learn a bit about it. 
I've put it on  not-very-fast computer, but even so it's so slow
it takes about a second just to show a letter in Dash. (I was trying to type terminal)
The install appeared to go OK and it's the latest (14.04 ?)
The screen displays very slowly too. not fading in but with in very noticeable steps 

Is this normal?  Can I improve it - or is the answer it just needs a faster computer ?

Thanks, Kirk

---

### Post by LastDino on 2014-05-10
We can't answer any of that unless we know what exactly you're saying when you say ''not-very-fast'' computer. What are the specs?

---

### Post by coffeecat on 2014-05-10
Perhaps you could give us some details of your hardware, including the graphics. It would be impossible to judge without knowing what you mean by "not-very-fast". Also - did you install Ubuntu to its own partition or did you use wubi, the Windows installer?

---

### Post by Kirk_McMillan on 2014-05-10
Thanks for your comments - I can understand the need for that info.  Unfortunately my install overwrote Windows (which was intended) but being
completely unfamiliar with ubuntu (or Lynix) I don't know (yet) how to use it and see the specs.   The HD is 80GB (prob 5400rpm), single partition which I imagine ubuntu uses all of. 
The motherboard is Asus A8V-MX and Graphics GEForce FX 5200. I built it up but can't remember how much RAM or what the CPU speed is.  It was running XP and preformed OK.

I downloaded ubuntu-14.04-desktop-i386.iso  993,280 KB and burned this to disk; booted from it and followed all the default prompts.  I noticed entering data into the dialog boxes was painfully slow but thought it was probably because drivers etc. not yet installed.

Appreciate your advice. If need be I can upgrade the machine without too much trouble.

Thanks, Kirk

---

### Post by mörgæs on 2014-05-10
Your motherboard has socket 939, which supports a 64 bit AMD processor. Graphics card is OK, but a little to the slow side. 

I suggest a fresh install of Lubuntu 14.04. If you have more than 1 GB of memory the 64 bit version is preferred.

More advice in the link in my signature.

---

### Post by coffeecat on 2014-05-10
The GeForce FX5200 is an old card and the Unity desktop is somewhat heavy on the GPU so that could be part of the problem. I agree with mörgæs that a lighter derivative of Ubuntu would suit that machine better. While you still have Ubuntu installed, this is how you can see how much RAM you have. You’ll have to be patient seeing as how sluggish your system is!

Click on the cogwheel icon top-right. Choose System Settings. Under "System" click on "Details". With overview highlighted in the left pane, the right pane will tell you how much memory there is in GiB.

If that takes too long, open a terminal with ctrl-alt-t. Run this command:

```
top
```

What is the figure in "KiB Mem:   xxxxxxx total"?

---

### Post by Kirk_McMillan on 2014-05-10
I did click on the cog icon in the Launcher. Got a white screen with a purple bar at the bottom...  25 mins later nothing had appeared on it !
The terminal s/cut worked. KiB Mem:766088 total 683728 used 82524 free.
You don't have a link to Lubuntu, please?

---

### Post by LastDino on 2014-05-10
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Your graphic card is weak but it's fine, your RAM needs improvement.

---

### Post by coffeecat on 2014-05-10
> **Kirk_McMillan said:**
> I did click on the cog icon in the Launcher. Got a white screen with a purple bar at the bottom...  25 mins later nothing had appeared on it !

You definitely need a lighter version!:)

> The terminal s/cut worked. KiB Mem:766088 total 683728 used 82524 free.

That's under 1GB. My guess is that you've got either one 512MB stick and one 250MB, or perhaps 3x 250MB sticks. You should be able to run Lubuntu with that amount of RAM, but if you could find second-hand sticks to add that would be useful - brand-new ones of such an old design would be very expensive.

---

### Post by Kirk_McMillan on 2014-05-10
Guess I should have checked out system requirements before jumping in!  I'll try the light version and also
look around for another motherboard (gruntier) with more economical DDR3 RAM. mörgæs, thanks for the links - good
reading and I will come back to the them. 
Thank you all for the quick and informative replies.
Cheers - Kirk

---

### Post by mörgæs on 2014-05-10
You're welcome.
If you follow all advice, especially in the 'performance tuning' section, it's not a given fact that you need to buy a new motherboard.

For a more detailed answer about memory please post the results from 
```
sudo lshw -sanitize -C memory
```
in CODE tags.

---

### Post by Kirk_McMillan on 2014-05-10
I noticed while installing ubuntu and the lite version, an option to co-exist with another OS.
This makes me wonder if it'd be better installed to my Win7 machine.  This has 8GB of RAM,
GeForce GT610 graphics, an Intel m/board and Core 2 Duo E4400 CPU.

There's a 120GB SSD with 71GB free and a 230GB slave almost empty. Which would be best for ubuntu?

Is running it like this as good/same as a standalone install?  
Do you call ubuntu from Windows or can you choose the OS at switch-on time somehow ?

Hope that's not too many questions! (I'd prefer ubuntu to lubuntu as I found an interesting tutorial for it.)
Thanks, Kirk

---

### Post by Kirk_McMillan on 2014-05-10
Hi mörgæs

Ran into a snag with that command you gave. A large display resulted and I could right click-Copy
but after that couldn't see how/where to paste it. (It's not on this machine of course.)

Perhaps the alternate machine (described last message) is a much better solution?

I bought a raspberry pi for media streaming.  I'd heard of Lynix but never seen it.  I wanted to copy
and edit a keymap file for the remote and discovered I had no idea how to do that. So I got 'Linux For
Dummies' and figured I should start at the beginning (thus resurrected this old machine). 
I am, or was familiar with pre-Windows DOS. All looks quite intriguing.

---

### Post by Yellow Pasque on 2014-05-10
You do have a swap partition, right?
```
free -m
```

---

### Post by Kirk_McMillan on 2014-05-10
Only what the install would have done.

[IMG]https://dl.dropboxusercontent.com/u/49222457/100_1726.jpg[/IMG]

---

### Post by mörgæs on 2014-05-11
> **Kirk_McMillan said:**
> 

Ran into a snag with that command you gave. A large display resulted and I could right click-Copy
but after that couldn't see how/where to paste it.

Just paste into the advanced text editor here in Ubuntuforum as part of your post (and use CODE tags, as mentioned).

---

### Post by Kirk_McMillan on 2014-05-11
[**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075"), not sure how I manage that as it's generated on a different computer. Past into a file and copy that to a flash drive, to read in this machine (Windows)? 
That's how I'd appraoch it but don't know how to yet. But it won't be necessary if I install ubuntu on the Win7 machine.
Did you see Msg #12 in this thread.  Any comment?  Depending on that I could get started.

---

### Post by LastDino on 2014-05-11
That other computer of yours can run Ubuntu smoothly. And I'm talking about flagship version: Ubuntu Unity 14.04 LTS 
So, yeah, you can dual boot it if you want, but make sure to take a backup. It will be better if you install it on that slave and avoid possible headache.

---

### Post by Kirk_McMillan on 2014-05-12
Ok Thanks. Will put it on the slave drive.  Can you give me a link to the right ISO please?
I'll backup first too.  Only thing I'm unclear on is how do I dual boot ?
Hope you can set me right on that one.

---

### Post by LastDino on 2014-05-12
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) 

 As far as whole process of dual booting with different drives, I advise you to give some time and go through youtube vids and tutorials or even threads on this very forum before you actually attempt to do it. 

Just a quick check list for you to have a look at
 >Find out what partition scheme Linux requires. Make list of partitions you plan to make with sizes in case you forget once installation starts.  
>Find out about bootlaoder and its configuration.
 >Download the ISO, check MD5 sum to see if it is downloaded properly or not. 
>Then make a bootable DVD or USB Live and try the thing out. See if it is running smoothly. 
>Then hit the install, make sure you've a good idea of which drive you want to install  Ubuntu and select that only, after selecting ''something else''. If you want to select default selected option, it's probably good idea to keep win7 drive disconnected. However, if you don't, installer will detect it and then **PLEASE DO NOT click on ''replace'' option**. It will replace the existing W7. In this case you want to select ''something else'' and manually format the extra HD you plan to install Ubuntu to. Then format it as you like or according to the list you made earlier. Installation process itself is quite easy, my 13 year old cousin can do it quite easily  once he understood partitioning scheme.   


If you need to to know anything specifically, do post back here, we are happy to help you.

---

### Post by Kirk_McMillan on 2014-05-12
Thanks very much LastDino, that's excellent advice and I'll work through it all carefully.

---

### Post by Kirk_McMillan on 2014-05-13
Thanks LastDino,

Pretty sure I can follow all that and I'm OK selected the boot drive and backing up etc.

I intend to split the slave drive in 2 and use one half for Ubuntu. I presume this half will show as unallocated and the 
Ubuntu install program will show this for me to select ?

I'm following the instructions here 
[http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/?ALLSTEPS](http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/?ALLSTEPS)

and the only gray area is Step 9.  It says[I] 'Upon bootup, you will now see a choice between Windows and Ubuntu Linux.'

[/I]Will I ?  How does it know that ?

Thanks, Kirk

---

### Post by Kirk_McMillan on 2014-05-13
OK I'm partway through the install and have 3 options:
1. Install Alongside Windows 7
2. Replace (which I know not to do)
3. Something else

I think I want 3 to use my newly-created partition. In there I see my 104 MB SSD
and a few things called /dev/sda1 - sda2 and sdb 1 and free space.

Free space looks like the right one for the new partition but the only option under 'Device for Boot Loader installation' is the SSD  (C Drive).

I have another comp (this one) so can just leave that sitting until I know what to do.  Will google around but hope you'll advise!!!   Thanks.

---

### Post by Kirk_McMillan on 2014-05-13
Thanks for all previous advice.  But too complicated and binning the idea of trying Lynix.

---

