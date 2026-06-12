---
title: "Computer slowing down- help? (3rd try)"
date: 2008-04-16
forum: General Help
---

### Post by FoxfirePoet on 2008-04-16
I got this computer 3 weeks ago and it ran fast as it should, and now ir's slowed down drastically, taking several seconds to open anything. Help me speed this thing back up? 
( This is my 3rd try to get help on  this. Every other time, people just go quiet after they ask for my specs, which i don't know what means. Help!?)

---

### Post by silvagroup on 2008-04-16
If you don't know your specs you probably ought not be trying to hop up the goober on the cpu, maybe that's why it's slow, you may have damaged the cpu.
By the spcecs they probably want to know what cpu you have, in detail. Your mother board and system memory altough probably not required maybe helpful, or if it's a packaged system you can just give the manufacturer and model number and they can take it form there.
I can't help any more than that because I've never tried cranking up the cpu. Sorry.

---

### Post by FoxfirePoet on 2008-04-17
I don't want to change anything on the CPU- I just want to know how to clean it up- cookies, temporary internet files, clean out the trash, etc.

---

### Post by avik on 2008-04-17
> **FoxfirePoet said:**
> I don't want to change anything on the CPU- I just want to know how to clean it up- cookies, temporary internet files, clean out the trash, etc.

The next two paragraphs assume you're using Ubuntu, and not Kubuntu or Xubuntu.  If that's not the case, wait for someone else to help you out on these two issues.

Unlike Windows, Ubuntu shouldn't have too much of a problem with temporary files, etc.  To clean up the trash, open up Nautilus (the file browser) and select Trash on the left-hand side.  Alternately, go to the location "trash:" (without quotes).  Click the "Empty trash" button.

To find the specifications of your computer (that is what type of hardware you have), go to System->Administration->System Monitor.  Tell us what it says under Hardware in the System tab.  If know how fast your processor is, that would be great, but if not, that's fine too.

Now, have you been doing anything special that would cause a slowdown?  Have you been editing a lot of images or using extensive multimedia?  We just want some more information so we can help you out better.

---

### Post by FoxfirePoet on 2008-04-17
Thank you very, very much, and sorry for the tardiness of my reply. I haven't been doing anything 'special' with it, other than modifying GAIM to run Xfire. Specs:

Pentium 4 Processor 2,00Ghz
Memory: 250 MB
Available Disk Space 16.2 Gig's

---

### Post by jocko on 2008-04-17
> **FoxfirePoet said:**
> Memory: 250 MB

I would guess that's your problem. If you want things to go faster, you need more memory.

---

### Post by FoxfirePoet on 2008-04-17
> **jocko said:**
> I would guess that's your problem. If you want things to go faster, you need more memory.

Right, but 3 weeks ago it ran beautifully on the memory it has.

---

### Post by lingnoi on 2008-04-17
Maybe it's running exactly the same but your perception of how it was running has changed?

---

### Post by Pijits_1 on 2008-04-17
I had a problem with an app called trackerd that ran in the background and took up way too much memory and cpu (even though its designed not to). If you want to try disabling it you could enter 

sudo trackerd -mn

This essentially makes it so that trackerd runs in low memory mode and doesn't index anymore. oh ya forgot to mention that its an indexing tool, i never found it useful since i usually know where all my files are.

If you get an error with that code you could try just -n without the m.

hopefully that solves it. It doesn't hurt to check your system monitor to see what may be taking up cpu.

---

### Post by FoxfirePoet on 2008-04-17
Are you suggesting, good sir, that where I think my computer has slowed, I have,in fact, increased in speed?
...Somehow I still think it's a technical issue. XP

Pijits, I tried what you suggested and it gave this error:
sudo: trackerd: command not found

---

### Post by ryanhaigh on 2008-04-17
What changes have you made since that time. Some things which may help improve your performace:
-disable desktop effects if they are enabled
-turn of tracker indexing
-use lighter apps (abiword instead of open office writer for example)
-try xubuntu (it uses a lighter desktop environment than ubuntus default which is gnome)

But to get the best performance out of that machine the number one reccomendation would be to buy more memory. Given that you don't seem to know too much about pcs I would say take it to a store and have them do the memory upgrade for you (its quite simple and shouldn't cost too much). You should get at least another 256 or 512MB ontop of what you already have to get the best performance.

---

### Post by FoxfirePoet on 2008-04-17
> **ryanhaigh said:**
> What changes have you made since that time. Some things which may help improve your performace:
-disable desktop effects if they are enabled
-turn of tracker indexing
-use lighter apps (abiword instead of open office writer for example)
-try xubuntu (it uses a lighter desktop environment than ubuntus default which is gnome)

But to get the best performance out of that machine the number one reccomendation would be to buy more memory. Given that you don't seem to know too much about pcs I would say take it to a store and have them do the memory upgrade for you (its quite simple and shouldn't cost too much). You should get at least another 256 or 512MB ontop of what you already have to get the best performance.


I changed the background to a picture of meself and some friends, installed MSN messenger, upgraded GAIM to use XFire messenger, installed Azureus (which I never run but I dunno how to get rid of)

---

### Post by Pijits_1 on 2008-04-17
Hmm, could be that its not installed or running. If thats the case i'm stumped. sorry can't be too much more help here. Is there some background application running at all?

Lol maybe time has sped up for you.

---

### Post by FoxfirePoet on 2008-04-17
> **Pijits_1 said:**
> Hmm, could be that its not installed or running. If thats the case i'm stumped. sorry can't be too much more help here. Is there some background application running at all?

Lol maybe time has sped up for you.

How do I find out if anything is running in the background?

---

### Post by jocko on 2008-04-17
> **FoxfirePoet said:**
> How do I find out if anything is running in the background?

To see which processes are running and how much memory they use, you can run the command 'top' in a terminal or the system monitor (System --> Administration --> System Monitor).

---

### Post by FoxfirePoet on 2008-04-17
The leading one seems to be Firefox, but it ran fine before....

---

### Post by avik on 2008-04-17
> **FoxfirePoet said:**
> The leading one seems to be Firefox, but it ran fine before....

First of all, try sorting by Memory or Resident Memory if you haven't already.

Also, have you installed any extensions?  Are you using Flash or Java more now?  Either of those two plugins (which aren't installed by default) use quite a bit of memory.

---

### Post by FoxfirePoet on 2008-04-17
Unless I did it wrong, it's sorted by memory, and firefox is still the lead contender.

It's funny you mention flash- flash is the only thing that runs promptly and correctly- like animations and the like

---

### Post by ryanhaigh on 2008-04-17
Does your pc still run slow when you are not using firefox, have you installed any extensions? For me when firefox is using flash on some sites cpu usage can get pretty high although I don't really notice except for the increase fan speed because im not doing anything in the background that would be effected.

---

### Post by FoxfirePoet on 2008-04-17
yes, it still runs slow

---

### Post by forumache on 2008-04-20
Which version of Linux are you using?

Thanks,
Dan.

---

### Post by sailor2001 on 2008-04-20
two things in your browser:  in address bar type about:config (if you're using firefox) and filter search ipv6.. click on that to disable....2nd. in firefox add-ons/extensions search add-block +

---

### Post by sailor2001 on 2008-04-20
> **sailor2001 said:**
> two things in your browser:  in address bar type about:config (if you're using firefox) and filter search ipv6.. click on that to disable....2nd. in firefox add-ons/extensions search add-block +

as an after thought: Firefox has become quite bloated. Try a lighter browser, such as ICEAPE which is in your synaptics.

---

### Post by forumache on 2008-04-20
> **sailor2001 said:**
> as an after thought: Firefox has become quite bloated

au contraire, Firefox 3 is lighter and snappier than Firefox 2.

---

