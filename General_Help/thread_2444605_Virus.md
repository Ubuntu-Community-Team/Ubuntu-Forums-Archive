---
title: "Virus?"
date: 2020-06-01
forum: General Help
---

### Post by curbie1 on 2020-06-01
I've only been back to this forum a few times since I switched to xUbuntu in 2013, haven't needed to much more then that... Ubuntu just works, but I've had some more issues. I know any computer can be subjected to viruses, but has Ubuntu had any abnormal up-tick in viruses? Anyway to verify a system? 

I'm running on my backup system, which isn't a bad or real old system, but I don't want to attach my backup drive, until I can verify it's contents.

Any suggestions?

---

### Post by TheFu on 2020-06-01
Sure.  Know that backup you made BEFORE getting the virus?  Use those to compare against the current system files.
Lacking that, best to wipe and start over.  

Nuke it from orbit. That's the only way to be sure.

---

### Post by curbie1 on 2020-06-01
"Nuke it from orbit. That's the only way to be sure." 
If that's not an "Aliens" reference, it's certainly a "Aliens" coincidence. 

Backup this morning, but IF there is a virus, when did I get it and is there a anti-virus software to verify both IF and WHEN?
Nuking 40 years of data may be "the only way to be sure", but is not an option.

---

### Post by TheFu on 2020-06-01
Nope.  There is no sure way for any computer except to have backups from BEFORE the machine was compromised.  Obviously, people will happily sell you stuff and make all sorts of claims about it.  Seldom are those claims useful a proof for an uncompromised system.  AV on Windows is usually 50% effective.  if you run the top 10 AV tools on the same system, then about 80% effectivity is estimated.  That's 20% left to chance.

Nuke it from orbit if you have any doubts.

---

### Post by Autodave on 2020-06-01
What makes you think that you have a virus?

---

### Post by curbie1 on 2020-06-01
Autodave,

I have some virus-like weirdness, don't know what it is, but want figure out how to rule out virus, before I attach drives to my known good backup system and potentially pollute that.

---

### Post by QIII on 2020-06-02
OK ... describe the "weirdness".  Not all that is weird means virus.  With some details, we may be able to lend a hand.

By the way, if it should happen to be a compromise, nuking from orbit is the only option.  And yes, that is definitely a reference to *Aliens*.

---

### Post by curbie1 on 2020-06-02
QIII,

I was deliberately trying to avoid talking about the weirdness, I was swamped, and don't clearly remember non-important (at time they happened) events. My best recollection is: my relatively new (3 months) main drive (a 1gb SSD) would boot but no xfce4-panel or desktop, useless but no big deal, I have some boot-able xUbuntu install thumb drives. Clean install and same thing, still no big deal could be hardware(SSD), so get and old 500gb hard drive, clean install and same thing, still could be hardware, but at this point I needed to consider other potentials, and make a plan before proceeding and prompted the question about xUbuntu's current virus status, used to have to punk-out on root passwords or skip logins, and ask for a virus to get one, how is xUbuntu currently, and decent AV stuff other than clam-bake which I have and used to bail out friends.

---

### Post by CatKiller on 2020-06-02
> **curbie1 said:**
> My best recollection is: my relatively new (3 months) main drive (a 1gb SSD) would boot but no xfce4-panel or desktop, 

That doesn't suggest a drive issue and it certainly doesn't suggest a virus. Misconfigured graphics stack is the likely source.

---

### Post by HermanAB on 2020-06-02
The only virus to worry about a little bit nowadays is Covid19, but you have about 50% chance that you already had that one without even knowing it.

As for computer viruses - relax and enjoy your Ubuntu system.
(Whenever there is a real Linux/BSD virus, it is fixed in about 30 minutes to an hour by someone.  Viruses are not left to fester like in Windows)

---

### Post by Autodave on 2020-06-02
You most likely do not have a virus.....at least your PC doesn't! :-)

Can you give us some info on your setup?  Especially the graphics card.   What version of 'buntu are you running?

---

### Post by TheFu on 2020-06-02
Installing over an existing system without a format isn't the same as wiping.

I've seen weirdness some times with a laptop here.  Turned out the finger oil was staying on the touchpad and just needed to be cleaned off.

XFCE is one GUI. Did any others show problems?
Have you created a brand new account and seen the same problems under it?  That would rule out config issues since a new account would only have the new config settings from the current release.

Until you check the log files, assume it is hardware or drivers.

If there's a virus, nuke it from orbit is the only answer for someone who cares about security.  Recovery of data, settings from BEFORE any virus was noticed is also the only option if you care about security.  How might the system have gotten a virus?  Any high-risk activities like leaving javascript enabled, using flash for games online, using PPAs from untrusted sources or probably the worst is installing a .deb file or snap?

---

### Post by curbie1 on 2020-06-02
Autodave, it's a bone stock gigabyte 78LMT, 16gb mem, on-board graphics, biggest cpu it can handle, 1tb SSD main drive loaded with v19.??, 4 tb backup drive, don't do games.

TheFu, only XFCE I've used it for 7 years and have been happy with it, I created a brand new account on a different drive, with fresh OS and same thing, which log files should I be looking at and for what?

---

### Post by HermanAB on 2020-06-02
BTW, if you ever find a Linux virus, please email it to me.

---

### Post by TheFu on 2020-06-02
> **curbie1 said:**
>  TheFu, only XFCE I've used it for 7 years and have been happy with it, I created a brand new account on a different drive, with fresh OS and same thing, which log files should I be looking at and for what?

All the logs under /var/log/
I’d use **egrep** to search for warnings and errors.

There's a way to use **journalctl** to search, but that's the extent of my knowledge about that. There may be some sort of log viewer for point-n-click people. Don't know anything about that.

if the issue happens with a different account on the same OS, that means 1 thing.
if the issue happens on a different OS (try Lubuntu) then it is probably HW or drivers.  **AND it isn't a virus.**

You can boot from a flash drive into a "Try Ubuntu" desktop, install whatever backup tools you like, connect the "backup storage and make a backup from the *perhaps* virus infected storage. This is safe, provided the OS that may be infected isn't booted.

---

### Post by curbie1 on 2020-06-02
Herman, if you help rid the world of punks, 3 cheers for you, btw, exactly how would one safely and non-maliciously email a virus?

TheFu, I assume egrep is an enhanced grep, I'm familiar with grep from the stone-age. Thanks... this is now on the todo plan, the "Try Ubuntu" boot and backup happened yesterday.

---

### Post by HermanAB on 2020-06-02
The last time there was an attempt at a Linux virus, Linus had to modify the kernel to support the virus and assist it to actually run and then it still wasn't able to do anything.

I am pretty sure that any Linux virus will get to me safely, without buggering up either Windows (since it is a Linux virus), or BSD/Linux (since it won't actually work).

---

### Post by curbie1 on 2020-06-02
Herman, Oh, the email post was facetious, but thanks for the "The last time post..." confidence to order a new motherboard and SSD.

---

### Post by curbie1 on 2020-06-05
when the hardware i ordered came in, i swapped back from my backup system, to my main machine and tried to isolate the bad part by reloading all the original parts with the intention of swapping possibly bad parts for known good ones. After a total reload, system ran fine and i couldn't isolate a problem, let alone "the" problem. Maybe a thermal issue, is been real hot lately, anyway thanks to all that helped.

---

### Post by HermanAB on 2020-06-06
Maybe just rusty connectors?

---

### Post by ActionParsnip on 2020-06-06
Curbie:
[https://www.zdnet.com/article/this-new-ransomware-is-targeting-windows-and-linux-pcs-with-a-unique-attack/](https://www.zdnet.com/article/this-new-ransomware-is-targeting-windows-and-linux-pcs-with-a-unique-attack/)

---

### Post by curbie1 on 2020-06-07
ActionParsnip,

Thanks! "[https://www.zdnet.com/article/this-n...unique-attack/]("https://www.zdnet.com/article/this-new-ransomware-is-targeting-windows-and-linux-pcs-with-a-unique-attack/")" or something like it. i found a folder i didn't recognize while polishing up my system after reloading...

---

