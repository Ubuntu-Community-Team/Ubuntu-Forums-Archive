---
title: "Files sometimes freeze on double clicking icon"
date: 2019-05-16
forum: General Help
---

### Post by kesetyan on 2019-05-16
On my Lubuntu 18.04 64 bit system (set as dual boot with Windows 7), occasionally when I double click a file icon to open it, it freezes.  Something similar sometimes happens with ClamTK too when I click to check for any available updates.  The resolution is either to right click the file's icon on the toolbar and select 'Close' which eventually brings up a message indicating the file is not responding and asking whether to force it closed or to restart the system - the former is not 100% reliable but the latter does always work.

I don't know if the issue is caused by the double clicks on the mouse not always registering or if there is something amiss in the file manager or the system itself.  It's not too major an issue as I can get around it but it is a nuisance so I'd be grateful for any comments or advice.  Thanks.

---

### Post by kesetyan on 2019-06-17
4 weeks have passed without any views let alone responses - if anyone out there does have any suggestions (not rude ones please) or advice, I would be grateful.

Thanks.

---

### Post by deadflowr on 2019-06-17
> **kesetyan said:**
> 4 weeks have passed without any views let alone responses - if anyone out there does have any suggestions (not rude ones please) or advice, I would be grateful.

Thanks.

Unfortunately the view count is broken, so it's unclear how many total have viewed it.
You're allowed to BUMP a thread about once or twice a day or so (anywhere between 12 and 24 hours)
which will bring the thread back up to the top of thread listings.

I don't use Lubuntu so cannot help beyond my own similar issues in past with hanging file managers can sometimes be related to an errant storage device.
Such as an improperly unmounted (or even improperly mounted) hard drive/storage device or a hard drive/storage device that is in critical failing state.
Could also be a very dirty file system which needs cleaning.

Being this isn't some consistent thing it might be a failing hard drive as strange things like inconsistent actions seems to be a hallmark of that.
(or at least that is something I've seen with slowly failing hard drives)
You might check the SMART status of your hard rives to see whether or not there are any issues:
[SMART on Ubuntu]("https://help.ubuntu.com/community/Smartmontools")

SMART isn't a foolproof thing but will give good reliable info most of time. 

Again I don't use Lubuntu and these things I think it could be could be the issue or could not be the issue.
Really it's just trowing pasta at the wall and seeing what sticks, if anything.

---

### Post by kesetyan on 2019-06-22
Hi Deadflower,

Thanks for your reply.  I don't think it is a failing hard drive (the system is only 1 year old and dual boots with Windows 7 where no problems occur) - I have just run a scan of the drive and all was good with that.  I'll keep chucking the pasta.

Cheers.

---

### Post by dino99 on 2019-06-22
you might glance at 'journalctl -b' output after getting such freeze, to know about warning/error logged at that time or so. Then you will be able to dig further about the problem.

---

### Post by kesetyan on 2019-06-22
Hi Dino,

Thanks for your input - yes I'll try your suggestion next time it happens.  The problem is so erratic I can go weeks before it occurs - it seems to relate to the double click of the mouse when it happens but that might be just because the double click is used to open a file and it is the file opening that causes the problem.  (Does that make sense?)

Cheersa.

---

### Post by dragonfly41 on 2019-06-22
*&#8220;Once you eliminate the impossible, whatever remains, no matter how improbable, must be the truth&#8221;.*

                                                                                                                  Arthur Conan Doyle

I would start by eliminating the mouse. Does another mouse have same symptoms? Does mouse work in Windows 7?

Next. What PC are you using?

Would it be Ryzen, perchance?

[https://ubuntuforums.org/showthread.php?t=2421203](https://ubuntuforums.org/showthread.php?t=2421203)

And so on to sharpen your detective skills.

---

### Post by kesetyan on 2019-06-23
Hi Dragonfly,

The mouse works in Windows 7 with no problems.  I have used another mouse and the behaviour is the same.  I stress that the file freezing happens only occasionally *(and I can use 'ALT' + 'PRTSCR' + 'REISUB' to free up the system if necessary when it happens although usually right clicking the file's taskbar icon, selecting 'Close' a few times brings up a message to allow me to force close the file)*.

My PC is a Zoostorm Evolve Desktop Model 7290-3089 with AMD A8-7650K Kaveri CPU in an ASUSTek A68HM-Plus (FM2+) motherboard, 8GB RAM, Integrated Radeon R7.  I purchased the computer last year with no operating system and installed Windows 7 Professional (I do not want Windows 10 and intend to disable the internet in Windows 7 next January when Microsoft support for Windows 7 ceases).  I decided to add Lubuntu in a dual boot setup in order to keep internet capability available after next January.

---

### Post by kesetyan on 2019-09-18
UPDATE:
This is a late additional comment but may be useful for others.  I was never able to fully resolve the issue I reported when I initiated this thread.  That is, I was not able to resolve it while I used the default LXDE Desktop Environment with the Lubuntu operating system.  I was seriously thinking about switching from Lubuntu to Linux Mint to dual boot with my Windows 7 system.  That could have been a bit of a headache with all the setting up required including my free Dropbox account as I had the maximum of three permitted devices (including Lubuntu).  

I then thought it might be worth trying a different desktop environment in Lubuntu.  I played with Gnome initially but then tried Mate. The latter has proved to be the answer to my problems: it's quite speedy on my computer, adaptable and has run smoothly without mouse problems or lockups while I've been testing it over the last few days.  The mouse double clicks which were a bit unreliable in LXDE have been spot on in Mate and as the lockups I experienced, usually happened when a double click failed, I've experienced no lockups with Mate.

It's early days perhaps and I mustn't count my chickens, but things are looking better.

---

