---
title: "Anti-virus?"
date: 2006-10-20
forum: General Help
---

### Post by shallow on 2006-10-20
being a linux newbie some one asked me does linux or ubuntu have anti-virus software?
i had no idea how to answer the questions
i have been reading a lot lately about linux but i have never read anything on anti-virus software

doesn linux or ubuntu have anti-virus software
if so what is a good one please

if not why doesnt linux or ubuntu need one?

---

### Post by adwait on 2006-10-20
Thera re a few antivirus softwares for linux, but mostly linux doesn't need it becase
1)There are very small no. of viruses for Linux
2)In order to execute a file, a uer needs to give it executable permissions etc. so only experienced users can do that. It can't happen automatically..
3)Even if somehow a user executes a virus, it will affect only his home directory, not the entire system.

---

### Post by blanks on 2006-10-20
I agree with adwait that there are a small number of viruses targeting linux.  Additionally, I think the open source development model helps reduce the number of viruses.  When more people are able to review the code, security holes are discovered and patched faster.  
I disagree however with point 2:
> In order to execute a file, a uer needs to give it executable permissions etc. so only experienced users can do that. It can't happen automatically..

I don't think it's difficult for any user to figure out how to change permissions.  I would think that an experienced user would be the one who had permissions properly configured in order to minimize possible damage from a virus.  An inexperienced user would be more likely to have permissions misconfigured.  Also, an inexperienced user is more likely to be running programs as root (effectively bypassing all permissions...)

As far as point 3:
> Even if somehow a user executes a virus, it will affect only his home directory, not the entire system.
I disagree.  Viruses often use a tecnique called privilege escalation in which they are able to execute as a more privileged user.  If you're interested in virus research, try web sites like phrack.org or check out Virus Research and Defense by Szor.

Like adwait said, there are a few AV products for linux.  A quick web/forum search should turn up a few good ones.  I encourage you to try them out, especially because as linux gets more popular, there will be more viruses targeting it.  It's better to have AV installed and never discover a virus than to have no AV installed and get your system hosed...

---

### Post by frequenicity on 2006-10-20
I believe both AVG and Avast have Linux ports.

---

### Post by mmcmonster on 2006-10-20
> **adwait said:**
> 3)Even if somehow a user executes a virus, it will affect only his home directory, not the entire system.


Actually, this is not exactly a good thing.  I am *much* more worried about losing information in my /home/ directory than totally crashing my system.


Yes, privledge escalation is a real thing, so theoretically a linux virus can install a key logger and steal login information or other such stuff.  But for the vast majority of users, it's the ability of a virus to delete things from their home directory or (worse) emailing files from their home directory that is a worry.

That being said, it's nice not having a lot of viruses targeted at my Ubuntu box. :-)

---

### Post by Ubuntist on 2006-10-20
There are anti-virus tools for Linux.  I use ClamAV.  It does seem though that viruses are very rare in the Linux world.  The only time ClamAV ever found a virus on my system was when I had copied a file from my Windows partition to Linux.

---

### Post by Perfect Storm on 2006-10-20
There's ome howto's on AVG and F-prot anti-virus in our howto section.

---

### Post by bionnaki on 2006-10-20
you can install an anti-virus, but all in all, you dont really need one.

---

### Post by aysiu on 2006-10-20
Even if anti-virus were necessary in Linux (it's not, unless you're trying to prevent accidental infection of your Windows-using friends' computers), it would probably be the least of your worries.

It's far more likely (though also probably not going to happen) that someone tries to brute force her way into your system because you've opened ports you shouldn't have and haven't secured them and have chosen weak passwords... than that you'll accidentally get infected by some Linux-targeted virus (which many people contend are all proof-of-concept and not "in the wild").

It's also far more likely (though I've never heard of such a thing... yet) that someone would create a .deb for "cool software" that you download off an untrustworthy website and then double-click and give full privileges to install malware on your computer.

Honestly, though, the most likely scenario (which I **have** seen a lot) is that you'll have no idea what you're doing and accidentally delete a whole bunch of files you shouldn't have (system files or personal files).

Instead of anti-virus...
1. Make regular back-ups of your important personal files
2. When you have Ubuntu working exactly the way you want it, make a disk image of it using [PartImage](http://www.psychocats.net/ubuntu/partimage)
3. Use strong (hard-to-guess) passwords
4. Install software from only the repositories
5. Use the NoScript extension in Firefox
6. Don't click on links in emails

---

### Post by helpdeskdan on 2006-10-20
I'd be more concerned with rootkits.  If you are paranoid, rkhunter is the program for you!
[http://www.rootkit.nl/](http://www.rootkit.nl/)

---

### Post by helpdeskdan on 2006-10-20
FYI - a nice article on the subject:
[http://librenix.com/?inode=21](http://librenix.com/?inode=21)
Already have heard some very good comments though!

---

### Post by moore.bryan on 2006-10-20
[I]good info throughout this thread... 
the only time anyone in the forums has suggested an antivirus program is when one is using both windows and linux stuff (i.e. usbstick, dual-boot).  out of experience, i'd suggest clamav... 
[/I]

---

### Post by alecjw on 2006-10-20
You only need antivirus if you download software from the internet. If you download all of your software from the repos suing apt (aptitude, synaptic etc) you won't get any viruses. Unless Mark doesn't like you.:)

---

### Post by mmcmonster on 2006-10-23
The problem is deciding what "software" actually is.  In theory, what you said is correct.  In practice, there are numerous MSOffice .doc and .ppt files laden with viruses that get passed around.

Fortunately, these will not cause viruses to spread to Linux.  However, in theory at least, similar issues can develop with other open formats (ie: a buffer overflow within a .jpg file that is only noticed with a particular .jpg viewer).

---

### Post by Ubuntist on 2006-10-24
> **aysiu said:**
> 
4. Install software from only the repositories


On this point, how much risk does one take by including the universe and the multiverse among one's repositories?

---

### Post by az on 2006-10-24
> **Ubuntist said:**
> On this point, how much risk does one take by including the universe and the multiverse among one's repositories?

Everything in universe is free-libre open source.  It is uploaded there as source code and gets compiled by the autobuilders.  Not just anyone can upload to the repositories.

It is highly unlikely that someone who tried to upload something malicious could get away with it for very long.  It is therefore highly unlikely that there is malware in universe.

As for multiverse, it contains a lot of binary-only software.  It is thouroughly tested, but non one can know for sure if it is spying on you or not.

It depends on how paranoid you are.

As well, to add to the security question, it is essential to keep up-to-date with software updates from the repositories.  New vulnerabilities are discovered and patched every day.  That is a very important way to keep your computer safe.

---

### Post by Wiebelhaus on 2006-12-10
> **Ubuntist said:**
> There are anti-virus tools for Linux.  I use ClamAV.  It does seem though that viruses are very rare in the Linux world.  The only time ClamAV ever found a virus on my system was when I had copied a file from my Windows partition to Linux.


lol.

---

