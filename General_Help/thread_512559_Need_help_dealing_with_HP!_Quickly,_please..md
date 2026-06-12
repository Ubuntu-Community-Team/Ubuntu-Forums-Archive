---
title: "Need help dealing with HP! Quickly, please."
date: 2007-07-29
forum: General Help
---

### Post by Old *ix Geek on 2007-07-29
Here's the scenario: My 3-month-old HP dv6000 laptop died a few days ago...just died.  No warning, no problems leading up to it, it just had no power.  I tried all the normal things (removing the battery, discharging static, reseating memory cards, etc.), to no avail.

When I contacted HP via e-mail, they were great about everything, until I mentioned that I will NOT send the hard drive in with the computer.  (Their disclaimer about repairs states that they "may do a system restore..." as part of the process, and that means wiping my drive and putting windoze back on it.)  We've been running around in circles for two days now, with them telling me to "back up your data because the Linux partitions will be erased," and me telling them "since there's no power, I CANNOT back up my data and I WILL NOT ship the hard drive to them."

(For anyone interested: The blue light where the AC cord plugs into the computer DOES light up, as does the wireless light (although it's orange instead of its usual blue), and the blue power indicator light also comes on when I plug in the cord (this light is next to the hard drive indicator light). However, NONE of the top panel lights light up, and pressing the power button does absolutely NOTHING.)

Finally, I told them last night that I want this issue escalated up the ladder to a supervisor, and last thing I heard from them was that it has been forwarded and I'll be contacted within 3 business days.

I just need some help/ideas/suggestions/advice on how to deal with them!  I am simply NOT WILLING to send my hard drive--which contains 3 months worth of tweaking settings, getting wireless to work blazingly fast (with the dreaded Broadcom 4311), fine tuning my Ubuntu system, AND all of my web site-related stuff--to a bunch of windoze jerks who will wipe it and put 'doze back on it, but they're telling me it's NECESSARY to include the hard drive.  I've already explained to them that this is a POWER issue, not a hard drive issue, and there's no reason they can't pop a drive in there for testing purposes, fix the power problem, take out the dummy drive, and send the computer back to me.  (Can you tell I have 20+ years of experience as a sysadmin?!)

By the way, HP gave me a list of companies who are "HP authorized repair centers," and yesterday I took my laptop into two of them: Circuit City and Radio Shack (thinking, at least if it's local, I can have better control over removing the hard drive).  Guess what? NEITHER of them actually does HP warranty work unless you buy the computer FROM THEM.  So I'm less than thrilled with HP right now for sending me on a wild goose chase AND wanting to wipe my hard drive if I send in the laptop.

---

### Post by FleetAdmiral74 on 2007-07-29
omg thats a lot of text...can you reduce it? Like give us less of the story? Would make it MUCH easier for me and others to focus on it IMO

---

### Post by rillip on 2007-07-29
> **FleetAdmiral74 said:**
> omg thats a lot of text...can you reduce it? Like give us less of the story? Would make it MUCH easier for me and others to focus on it IMO

That's just pathetic.  I'm not going to justifty that further.

In regards to the OP, good luck!  I work in a service center so keep in mind, most of the resistance you are getting are people trying to follow policy, not trying to be unhelpful.  Be patient.

Do you have a friend with a laptop? You could swap in the hdd, move it over ethernet to some other device or an external usb drive or something, then put it back.  You might also be able to find an external inclosure that will let you use the laptop hdd outside of the laptop.

Good luck!

---

### Post by Tobster on 2007-07-29
I always believe that HP are Linux friendly.   All there hardware tends to work on Linux and HP printers work perfectly on Linux so that does surprise me.  

Why cant the big hardware businesses just give in a support just all 3 main OS (Windows, Ubuntu and SUSE Enterprise) rather then just Windows...

Thanks

Toby

---

### Post by seamless on 2007-07-29
Your best best is to get an adapter for your laptop drive to usb (something like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812119017") for example). Plug the drive into another computer and make an image of the drive using [Clonezilla]("http://clonezilla.sourceforge.net/") (use the gparted-clonezilla [LiveCD]("http://clonezilla.sourceforge.net/gparted-clonezilla/")). Then send the computer complete with hard drive to HP. When you get it back restore the image to the drive.

---

### Post by AlexThomson_NZ on 2007-07-29
No external backups?  No seperate partition for your vital data?

If you have trouble tweaking to get the bits working, keep notes and create scripts, etc., especially if it has taken months to get right.

I can understand your frustration in that they shouldn't NEED the hard-drive to fix the power problem, but your PC is screwed, so cut your losses, and accept that they MAY need to wipe the partition, IMHO.  Especially as they have you over the barrel (no power is not something you can really work around is it!?)

---

### Post by kerry_s on 2007-07-29
hit craigslist see if you can find a cheap laptop drive to use for the repairs. other wise just byte the bullet & and get your self the enclosure. i hope you learn from this & back your stuff up externally from now on. 20+ years and you never learned to think ahead, boy scouts moto "always be prepared". i never met a system admin who never backed up there stuff, nice to meet you. :)

---

### Post by Old *ix Geek on 2007-07-29
I guess I inadvertently gave the impression that I have no backups, which is NOT true.  I back things up frequently.  But the time and effort put into tweaking the OS to get it just the way I wanted is not something I thought about backing up.  I mean, really, each tweak along the way I was supposed to back up somehow?  I don't think so.  The whole point here is that HP--which is normally quite *nix friendly--wants to force me to let their windoze-only "repair" staff wipe *MY* drive and put *THEIR* idea of an OS back on it.  In my opinion, that's not right.  I am, after all, the customer.  It's no different to me than letting a mechanic stick a Yugo engine in my Toyota. ;)

The comment about "No seperate partition for your vital data?" is moot, since they're going to WIPE the entire drive.  Note in my OP how I said HP told me "the Linux **partitions** will be erased."

---

### Post by cssutto on 2007-07-29
This probably is of no help at all, but I had a screen problem with my older Thinkpad.

I sent it to IBM's repair center in Memphis without telling them that it would not have a hard drive.  Just took it out and sent it.

There was never any comment made about it by them, they just fixed it and returned it.

Maybe your mistake is in giving them a choice.

Just take the drive out and send it.

Every security expert I have ever read advises against sending your hard drive in to a service center.  Too much information on it that no one has any business seeing, and wiping is not an option when the computer is broke.

Just send it.

Deal with a different person so your past communications do not haunt.

CSSJR

---

### Post by kerry_s on 2007-07-29
> **Old *ix Geek said:**
> I guess I inadvertently gave the impression that I have no backups, which is NOT true.  I back things up frequently.  But the time and effort put into tweaking the OS to get it just the way I wanted is not something I thought about backing up.  I mean, really, each tweak along the way I was supposed to back up somehow?  I don't think so.  The whole point here is that HP--which is normally quite *nix friendly--wants to force me to let their windoze-only "repair" staff wipe *MY* drive and put *THEIR* idea of an OS back on it.  In my opinion, that's not right.  I am, after all, the customer.  It's no different to me than letting a mechanic stick a Yugo engine in my Toyota. ;)

The comment about "No seperate partition for your vital data?" is moot, since they're going to WIPE the entire drive.  Note in my OP how I said HP told me "the Linux **partitions** will be erased."


yes, any tweak you can't remember you should back up. i use just a plain old 512 key for quick backups, just save the file you changed, it's not that hard & takes less than 5 sec's, just have the key plugged when your tweaking. you never know when a tweak will screw something up. i back up as soon as i make a change & to external hd when my drive gets full or cluttered.

---

### Post by AlexThomson_NZ on 2007-07-29
> **Old *ix Geek said:**
> (Their disclaimer about repairs states that they "may do a system restore..." as part of the process, and that means wiping my drive and putting windoze back on it.)

Sorry, I got the impression they MAY do a session restore.

> **Old *ix Geek said:**
> (Can you tell I have 20+ years of experience as a sysadmin?!)
Not really

I wonder if you say "I don't have a Windows license", whether they can legally reinstall it on your Laptop?  Worth a shot?

---

### Post by Old *ix Geek on 2007-07-30
> yes, any tweak you can't remember you should back up. i use just a plain old 512 key for quick backups, just save the file you changed, it's not that hard & takes less than 5 sec's, just have the key plugged when your tweaking. you never know when a tweak will screw something up. i back up as soon as i make a change & to external hd when my drive gets full or cluttered.
I've long been in the habit of saving configuration files as **filename.orig** before editing them.  Any time something I've tweaked has screwed things up, it's just a simple matter of restoring the original file.  What I HAVEN'T done is save copies of those files anywhere but the hard drive.

> Sorry, I got the impression they MAY do a session restore.
Um, yeah, that's what I said.  And that's what I don't want.
> I wonder if you say "I don't have a Windows license", whether they can legally reinstall it on your Laptop? Worth a shot?
I don't know.  I mean, I bought the laptop directly from HP, and they know they shipped it to me with a windoze license for the Vi$ta that came on it...so I don't know. :confused:

---

