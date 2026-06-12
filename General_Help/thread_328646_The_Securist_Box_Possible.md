---
title: "The Securist Box Possible"
date: 2006-12-31
forum: General Help
---

### Post by titancomputing on 2006-12-31
I'm about to reinstall Ubuntu Edgy Eft, and I want to do so in the most secure way possible. I'd like encrypted hard drives, intrusion detection, firewalls, the works. Basically, I'm looking for the ideal paranoids system. I'd really like to have it to where if someone tries to log into my system while I'm gone over a certain number of times, the main drive completely wipes itself. The only problem I'm having is I need to be able to run BitTorrent and the Internet in my secure box. Is this all possible? I know Windows can't handle this kind of lockdown, and I really need it to be as safe as possible, considering the files contained on it are VERY confidential. Thanks for the help.

---

### Post by Mike'sHardLinux on 2006-12-31
You can do all of that stuff. Actually, you can do that in Windows, too. It is a myth that you can't lock down Windows. It's just that by default, it is not locked down. Anyway, not to start another debate ....

When you want to do that level of security, you need to know that there's always compromises: security vs convenience and security vs performance. The most secure box, will most likely be the least convenient. As far as performance, that's probably not as much of an issue, but it can be. 

There's a point of diminishing returns for security, too. For example, you can put a password in your BIOS, but if you're the only one in your house, what good would that do? Besides, it's easy to get around that. Some steps you take, while adding a layer of security, may not be worth the time, effort, or inconvenience.

You can google and search the forums without my help. I don't know if there is a step by step how to on setting up a system with ALL of those things.

A few thoughts:
[LIST]
[*]Ubuntu comes with a firewall (IPTables). If the commandline is too much for you at this point, you could install a GUI frontend like Firestarter to make configuration more manageable.
[*]You can make sure to shut down ALL unused services, and that can help lock it down.
[*]There's a few choices for filesystem encryption. Search the forums and use google.
[*]There's a sticky thread about security tools, like intrusion detection: 
[http://www.ubuntuforums.org/showthread.php?t=9836]("http://www.ubuntuforums.org/showthread.php?t=9836")
[*]I seem to remember there is at least 1 Linux distro whose purpose is the ultimate locked down system. I am afraid I don't remember the name. Look at distrowatch.com.
[*]If you have a spare system, you can build a honeypot...a non-critical system setup to lure the bad guys away from the "real" system. I assume you could also do this same idea inside a virtual machine if you only have one machine.
[*]You can run bittorrent inside a virtual machine. That would limit its "reach" on your computer. You can also do all your internet browsing within a virtual machine(Now, that's REALLY paranoid!!)
[*]Security is often more about people than about hardware/software. Stay informed about bugs/vulnerabilities and the latest security threats.
[*]Only use the trusted software repositories. If you just go googling and find software, how can you know if it's safe? Just because you install from source doesn't really guarantee anything unless you go through the code and can verify it's clean.
[*]Another approach is to learn some hacking skills. There's a few books out on the subject. There's even a relatively new certification you can get, "Certified Ethical Hacker." If you learn how to break into systems, that will give you another perspective on your approach to security.
[/LIST]

:-k  I feel like I am missing some things.....it's past my bedtime. :mrgreen: 

Before someone comes in here and starts flaming away saying this isn't necessary, remember, the OP wants security to the point of paranoia.

That's a lot of stuff to deal with at one time if you don't have much experience. You might try to tackle 1 or 2 things at a time. Or better yet, do as much research as you can rather that just formatting your hard drive and saying "OK, tell me what to do," as so many people on this forum seem to do.

---

### Post by fredster001 on 2006-12-31
are you a spy or something???

---

### Post by Lord Illidan on 2006-12-31
Also consider its physical location. At a certain point it is easier for someone to break in your house and haul the whole thing away than to remotely hack it.

> are you a spy or something???

That's none of your own business. If he wants critical level security, then he can have it.

---

### Post by fredster001 on 2006-12-31
was only a joke...

---

### Post by hikaricore on 2006-12-31
in soviet linux, system secures you!

---

### Post by slimdog360 on 2006-12-31
There should be easier ways to secure your porn stash

---

### Post by hikaricore on 2006-12-31
> **slimdog360 said:**
> There should be easier ways to secure your porn stash

files with no extentions (mime types in ubuntu take care of this issue) in a hidden directory owned by root (non-world readable), inside a temp folder owned by root (non-world readable)

should do the trick, as long a you use a secure root password different from your normal password lol

anyone puts the drive in another system and manages to locate the hidden folder which should remain so even under windows, has a pile of files with no file extensions to dig through.

sudo nautilus = ftw

---

### Post by Lord Illidan on 2006-12-31
> **hikaricore said:**
> files with no extentions (mime types in ubuntu take care of this issue) in a hidden directory owned by root (non-world readable), inside a temp folder owned by root (non-world readable)

should do the trick, as long a you use a secure root password different from your normal password lol

anyone puts the drive in another system and manages to locate the hidden folder which should remain so even under windows, has a pile of files with no file extensions to dig through.

sudo nautilus = ftw
still not secure enough.

---

### Post by hikaricore on 2006-12-31
eh i was going to suggest password protected archives inside password protected archives, but that's the point where secure becomes annoying :)

---

### Post by Lord Illidan on 2006-12-31
Just use encryption....that's the most secure.

---

### Post by insane_alien on 2006-12-31
securist setup would be to have two computers have one connected to the internet and download everything to that. using an external drive, transfer the files you download to the second box which isn't connected to the net. on the second box you can have all the encryption stuff you want.

seriously this is EXCESSIVE. i honestly don't see what purpose this could serve outside a government (and they have better ways of securing everything i suppose)

---

### Post by titancomputing on 2007-01-07
Thanks for all the great responses guys. I've come quite a ways on securing the internet side of things. Basically, touching my system from the web will be more trouble than it's worth. To answer the question, no, I'm not a spy, but I do have some files that are VERY vital and confidential to their owners, so I want them good and safe. My only part left is the local computer. It's in a cabinet that has a good strong lock on it, so taking it won't be easy, but in the worst case scenario, I want to be prepared for that too. Is there a way to make it to where even if someone did have my system in their possession, it would be unusable to them? I'd like it to where if they got the system powered up, they'd come to the login screen. After attempting to guess my password more than 3 times, all three of my hard drives would be completely formatted. The only thing I can think that that leaves open is removing the drives from the system, and I think I can encrypt them to fix that? Is what's left possible? I can deal with inconvience for the security issue.

---

