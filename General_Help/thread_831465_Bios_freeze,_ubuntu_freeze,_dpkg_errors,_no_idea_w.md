---
title: "Bios freeze, ubuntu freeze, dpkg errors, no idea what's causing it"
date: 2008-06-16
forum: General Help
---

### Post by Ruzarik on 2008-06-16
i would search, but it seems i only have about half a minute before it messes over...

ok, i am running hardy 64-bit ed. with a buncha problems, first, my BIOS freezes (which hints it's not the OS's problem) mid session, which sucks terribly, second, ubuntu freezes and i have to restart, hoping it even boots up after it begins to freeze, sometimes it just sits there, saying, starting... and then nothing...

ok, i was in an update package install last week, all i remember about the package was that it had a lot of S's in it. that is all, lol, and it just kept telling me for over half an hour, "generating kernel" and it would give the kernel version, and just keep entering that on lines over lines of my terminal, which then began the freezing, which then led to it not booting fully, which then led to my Bios freezing, which just now led to static in my case (i turn my PSU off and turn it on, and it flashes on for a second or 2 and dies off, and keeps doing that if i turn it on and of again...)

basically, i think this all began around the time when i was updating packages and it froze so i retsarted my comp, and now it wont install anything, if i go to system recovery in my boot options, it just repeats the same thing it did in the terminal infinitely...

i am dying here. quite literally.

i am on an asus mobo (M2N-SLI deluxe)
also, weird note, i thought that you need 4 GB ram to run 64-bit os, but i was on 64-bit ubuntu for about 2 weeks now, on 2 GB, i just thought that was weird...

Here's more info i got:

```
ruzarik@LOLWhut:~$ sudo aptitude install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

So i run it...

```
ruzarik@LOLWhut:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
ruzarik@LOLWhut:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
[B][I]and the above line just keeps going, and going... and going...
Until i stop it with CTRL + C[/I][/B]
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
dpkg: subprocess post-installation script killed by signal (Interrupt)
ruzarik@LOLWhut:~$ 



```

---

### Post by oldos2er on 2008-06-16
Try:

 sudo aptitude install -f

 sudo aptitude update && sudo aptitude upgrade

---

### Post by Ruzarik on 2008-06-16
nah, i tried -F, but that didn't work before, and the other one you said required me to have the DPKG files working I guess, but neither worked.

any idea on the Bios? because imma bout to crap my pants if there's some OTHER problem going on...

I am considering formatting, again, which sucks big time. but i'll do it.

i will format and reinstall soon this week, and get back on here and say if there's still bios problems.

if there is, :'( i need a new mobo.....

---

### Post by oldos2er on 2008-06-17
Well, I'm not sure what you mean by "bios freeze." You don't say how old it is, but try checking the manufacturer's website for any bios updates. That, or your cmos battery is failing.

---

### Post by mempman on 2008-06-17
If your bios is freezing, then you prolly won't have much luck getting any software running atop of bios to work.  If your bios is freezing, it may be because your processor (or ram) is overheating.  Check the appropriate fans and/or temp readings.

---

### Post by Ruzarik on 2008-06-18
ugh.... lol...

I have never looked into updating my BIOS, and when i say freeze, i mean FREEZE like windows freeze.

I guess I will look at the site for any upgrades, but I am using it with the same BIOS it came in a box with, also, what do I do about my CMOS battery if it is dying?

It seems as if it only freezes alot after it freezes once, like, if I don't use it for an hour or so, it wont freeze, but if i turn it on and then it freezes, if i keep restarting, it keeps freezing, unless i wait a while, and by freeze i mean at any point in boot up and in bios.

so it COULD possibly be ram or cpu over heat, i dont know... but why would it? all i'm ever doing is browsing the web or downloading something, in linux, so it never goes above 10% cpu useage or any where near the top of my ram useage...

I have a dual core 3.215 GHz AMD, and 2 GB RAM i think is either crucial or that other company that begins with a 'C'

---

### Post by alphaniner on 2008-06-18
Your CMOS battery is just a little button battery, you just pop it out and buy a new one from the store.

> It seems as if it only freezes alot after it freezes once...

This suggests a temperature issue.  Open your computer and make sure all your fans are running, and then go into your BIOS and there should be a page with temps and fan speeds and stuff.  Leave it on that page for a while and see what your temps are doing.

---

### Post by Ruzarik on 2008-06-20
> **alphaniner said:**
> This suggests a temperature issue. Open your computer and make sure all your fans are running.

All my fans are running, also, my computer is still giving me static (i switch off the PSU, and press ON, and my system flashes on for 2 seconds, then dies.) And I realized that the top of my heatsink is incredibly hot, hotter then when I remember maxing out in BF2 on Windows: MC. My RAM is pretty hot. and my GPU is very hot (when I say hot, I mean like almost unbearable to touch, I have no previous computer temp experience so I have no idea where they SHOULD be...) and my North Bridge or South Bridge, which ever it is, is directly under my GPU.

Basically everything is like a microwave, which makes me unhappy :)

> **alphaniner said:**
> Go into your BIOS and there should be a page with temps and fan speeds and stuff.  Leave it on that page for a while and see what your temps are doing.
I don't have a page with temperatures or anything like that in my BIOS, if there's a program that can tell me accurately for ubuntu, then I will try it... omfg, I forgot LOLOLOL, my DPKG is corrupted, I can't install anything :P eh when I get back Monday I will format and see what happens then. I will format back down to 7.10 (I have yet to receive Ubuntu 8.04 32-bit)

It seems that my computer is fine even though it has been on for the last 2 days, under no load though, and wasn't frozen. But after I went to see new replies in this topic, it froze, which was about 10 minutes after I started using it in the 2 days.

Looks like I need an air conditioner blowing directly into my PC :guitar:

Also, if it matters, when I was on windows in BF2 like I said before, after the first 3 times I played the game it began BSOD'ing me after 7 - 13 minutes of play, whether it was maxed out or not. (This is making me think it is a real temp problem)

---

### Post by avtolle on 2008-06-20
Try```
sudo dpkg --configure -a
```for the dpkg problem.

---

### Post by Ruzarik on 2008-06-20
> **Ruzarik said:**
> 
```
ruzarik@LOLWhut:~$ sudo aptitude install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

So i run it...

```
ruzarik@LOLWhut:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
ruzarik@LOLWhut:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
[B][I]and the above line just keeps going, and going... and going...
Until i stop it with CTRL + C[/I][/B]
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
dpkg: subprocess post-installation script killed by signal (Interrupt)
ruzarik@LOLWhut:~$ 



```

> **avtolle said:**
> Try```
sudo dpkg --configure -a
```for the dpkg problem.

Tried. Unfortunately I was considering booting up from (I know) Windows, and downloading some temp monitoring thingie... and try my best to find out if that is what the problem is. If it is, i will fill a fish tank up with veggie oil and throw mah PC in there. Or make some machine-like thing that mounts an Air Conditioner to the side of my computer... trust me I will do it... of course then, with my luck, my computer will subconsciously find a way to freeze literally.

---

### Post by robklg on 2008-06-20
I know maybe it sounds stupid. You probably already checked this.

But everytime crazy things like that happened to me, it turned out my root partition was just full..

So if you hadn't checked... check it;

df -h

and your memory;

free -m

vmstat

---

### Post by VMC on 2008-06-20
Type this:

```
dmesg|grep ACPI
```

Look for any errors. Specifally look for this: 

> "ACPI: Looking for DSDT in initramfs... error"

You mentioned that the fans were running. Maybe not fast enough. If you have Windows installed does it run cooler?

---

### Post by Habbit on 2008-06-20
You might want to re-check whether or not your BIOS has a page with the temperatures thingie: it's usually called "PC Health status", "Health monitoring" or something like that. If you don't find it you can try to install hardware monitoring software in Ubuntu, like the "lm-sensors", "sensord" and "xsensors", though if you haven't resolved your dpkg issue there's little you can do apart from booting from the Live CD and installing the sensors packages to its virtual environment. In order to get your sensors detected and configured, the "sensors-detect" app (from lm-sensors) will be helpful.

---

### Post by horcruxerz on 2008-06-20
I have this problem when I tried to update my Ubuntu when there was updates available :
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to run 'dpkg --configure -a', but terminal said it need superuser privilege, how can i enter the superuser mode?
 
agung@agung-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
agung@agung-desktop:~$ 

Please help, i'm very newbie in this area

---

### Post by xdavidx on 2008-06-20
> **horcruxerz said:**
> I have this problem when I tried to update my Ubuntu when there was updates available :
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to run 'dpkg --configure -a', but terminal said it need superuser privilege, how can i enter the superuser mode?
 
agung@agung-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
agung@agung-desktop:~$ 

Please help, i'm very newbie in this area


sudo dpkg --configure -a

---

### Post by Anvariel on 2008-12-04
I have a similar problem to this and unfortunately I have not found the solution anywhere so far. I hope it's not out of line to post the question in this thread since it seems very much related to the previous entries.

I try to run synaptic but get the message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

OK, so I try to run sudo dpkg --configure -a. It freezes at this point:

anjjo53@anjjo53-desktop:~$ sudo dpkg --configure -a
Setting up language-pack-sv-base (1:7.10+20080205) ...
Generating locales...
  sv_FI.UTF-8... 

I cannot shut the process down by ctrl-c but can shut down the terminal. So what do I do now? I've tried the following:

sudo aptitude install -f
sudo aptitude upgrade
sudo aptitude install dpkg

Nothing seems to help. Any hints?

/Anvariel

---

