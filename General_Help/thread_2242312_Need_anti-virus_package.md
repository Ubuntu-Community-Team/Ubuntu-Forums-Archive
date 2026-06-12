---
title: "Need anti-virus package"
date: 2014-09-01
forum: General Help
---

### Post by sofasurfer on 2014-09-01
Whats the best anti-virus I can put on ubuntu without going through hell to get it? As you can tell I am desperate.

---

### Post by mastablasta on 2014-09-01
antivurs in ubutnu scan for windows viruses only. otherwise ClamTK could be in repos.

there are also avira, bitdefender and i am sure there are a few others free and with linux client. mostly they have command line and manually scan not on access can. they are ment to be run on mail servers to throw out windows virus before they get to users.

if you plan to do some windows cleaning it is best to download and use Avira or bitdefender rescue disk. Bitdefender seems to have found more when I scanned. anyway you download it, burn the is, boot form it, it will download latest virus definitions and do the scan after which you can decide what to do (if it find anything)

edit: yeah there are a few others: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by stalkingwolf on 2014-09-01
> otherwise ClamTK could be in repos   It is  I install it with each fresh install.

---

### Post by oldos2er on 2014-09-01
> **sofasurfer said:**
> Whats the best anti-virus I can put on ubuntu without going through hell to get it? As you can tell I am desperate.

We might be able to help you better if you explain your desperation.

---

### Post by sofasurfer on 2014-09-01
I don't know if there is a virus. Latley my pc has been acting goofy. Running slow, mail disappearing, book marks and history disappeared. Just want to be sure this is not a virus. Everyone says that linux users never have to worry about virus but is I was a virus writer I would take that as meaning the linux users are wide open for the infecting and I would meet the challenge. We have be riding the "no viruses for linux" train for too many years.

---

### Post by christopher9 on 2014-09-01
Have you tried reformatting the HDD and doing a fresh install of the OS ?

---

### Post by sofasurfer on 2014-09-01
Actually, this stuff started happening after I put 14.04 on a new hard drive. It has been getting more frequent.

---

### Post by oldos2er on 2014-09-01
Viruses on Linux aren't impossible, just unlikely. Other types of malware and social engineering are a bit more common.

Have you ruled out failing hard disks, faulty RAM, or other hardware problems?

---

### Post by ThatBum on 2014-09-01
The issue is academic. Viruses for Linux exist, but they can't really propagate well due to how Linux permissions work, so there aren't really any in the wild. It's not from lack of trying, since a large amount of servers run Linux. What I'm saying is the best antivirus would be common sense.

Anyway, you'd have to be deliberately running something suspicious with root permissions to do any real harm to your system. You could have some kind of hardware issue, overheating perhaps, or maybe RAM going bad. OR, there's simply too much running in the background and you're running out of resources. Can't think of why mail and bookmarks would disappear, though...

---

### Post by Habitual on 2014-09-02
easy-peasy.... create a new user on the system and login as that new user.
Do the problems remain?

---

### Post by oldos2er on 2014-09-02
> **ThatBum said:**
>  Can't think of why mail and bookmarks would disappear, though...

I was thinking hard disk failure, or pre-failure. It's not unknown for new hard disks to have manufacturing flaws.

---

### Post by ThatBum on 2014-09-02
> **oldos2er said:**
> I was thinking hard disk failure, or pre-failure. It's not unknown for new hard disks to have manufacturing flaws.

If that were the case, wouldn't everything else be going wrong too? Very unlikely that only the parts of the disk containing his bookmarks and mail would go bad. Many BIOSes do a SMART check during POST as well. The slowness could be explained by excessive reallocated sectors however.

Still, the OP should install [FONT=courier new]gsmartcontrol[/FONT] and see if their disk is still okay. Also check the memory, hold Shift while the machine is booting and run Memtest86+

---

### Post by stalkingwolf on 2014-09-03
what disappeared or became non functioning would depend on what sectors failed.  might try hirens HDD regenerator

---

### Post by JKyleOKC on 2014-09-03
> **oldos2er said:**
> I was thinking hard disk failure, or pre-failure. It's not unknown for new hard disks to have manufacturing flaws.I spent almost 25 years as a tech writer with what is now a part of Seagate and learned quite a bit about disk engineering during that time. One of the most important things I learned was that all designs exhibit what is known as the "bathtub curve" when plotting failure rate against lifetime. Initially the failure rate is quite high, then it drops almost to zero and stays there for a long time. Eventually it begins to climb gradually as the hardware wears out, and goes to infinity when wear-out becomes total. The plot looks like a longitudnal cross-section of an old iron bathtub, hence the name.

That's why burn-in of new hardware is so important. Back in the early days we did that at the factory before shipping the units, to eliminate those early failures and minimize DOA happenings. Now that most actual manufacture has moved offshore, and the engineering has improved more than a bit, burn-in may not be so necessary -- but the bathtub curve, like the Pareto Principle, is just a fact of nature and still applies.

---

### Post by nadrach on 2014-09-03
Have you been running Bleachbit? I found it took away a few unexpected things (passwords, bookmarks, mail directory settings ... interesting things like that) when I set it to clear everything ... a learning curve or two later I have it working just fine.

---

