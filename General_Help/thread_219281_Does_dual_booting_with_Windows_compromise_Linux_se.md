---
title: "Does dual booting with Windows compromise Linux security?"
date: 2006-07-19
forum: General Help
---

### Post by Pelekophori on 2006-07-19
My apologies if the question to follow has been answered before, but if it has, I couldn't find the thread.

My computer dual boots Dapper Drake and Windows XP, with each system on a separate hard disk.  Both operating systems can see and access the disk used by the other: Windows has a program installed to allow it to use Ext2/3 filesystems  and Dapper mounts the Windows disk with read only permissions.   Naturally Windows does not respect Linux file permissions and will happily allow any file on the Linux disk to be created, modified or deleted.

Now, as a hypothetical situation, let's say that a rootkit or other nasty successfully installs itself on the Windows installation.  Does anything prevent the root kit from compromising the Linux installation if it is programmed so to do?  For instance could a hypothetical Linux aware root kit be programmed to recognise a Linux installation on another disk/partition and change critical system files to replicate its functionality on the Linux installation?  

If dual booting Windows does introduce such a vulnerability, is there any way to overcome it short of not having Windows (on the same machine)?  Obviously getting rid of the program which allows Windows to use ext2/3 filessytems is no help since the rootkit could (again theoretically) contain the necessary code itself.  

Of course there is a difference between theory and practice and no doubt a malicious programme as described above does not exist yet (even if it is possible).  But if Linux and by implication dual booting gains desktop share, presumably writing one will become a more attractive prospect.  So many thanks to anyone who can provide a reasonably definitive answer to this question.

---

### Post by halfvolle melk on 2006-07-19
If your PC is compromised with a Win root kit, it should be a trivial task (if you are running the compromised OS) compromising the Linux bit, with or without the ext2 tool; the cracker will install it. A decent hardware firewall would be a solution.

---

### Post by mlind on 2006-07-20
Even though it sounds unlikely or somewhat paranoid, it's possible yeah.
Picture a virus/malicious program that contains a driver for writing data on
foreign paritions. I don't think it's even that hard to do one using already
existing ext2/3.

But I don't think it much to worry about. Easier task for malicious program
is to wipe out the partition table or lowel format hdd's, regardless the
filesystems.

You basically need a good firewall and virusscanner **if** you plan to use
internet with windows machine.

---

### Post by AlphaMack on 2006-07-20
> **mlind said:**
> Easier task for malicious program is to wipe out the partition table or lowel format hdd's, regardless the filesystems.


Exactly, which is also why Apple's 'Boot Camp' solution is a joke.

It takes one piece of malware that can alter the partition table...game over.

---

### Post by Lunar_Lamp on 2006-07-20
I am far from a security or linux expert, but it seems to me there is a potential problem here.

The problem is that most (or at least significant numbers) of viruses nowadays aim not to damage the computer they infect, but to send out information about it.

So, as you described above (using the lack of file permission preservation), it would be possible to create a windows virus/rootkit that contained an ext2/3 driver (or utilised an already present one), and read/write files on the linux partition.  For example:
 - read the shadow file for root password(s) and send the password to the virus creator.  This could potentially be a significant security breach.
 - install a keylogger that only root can view to know about.


I would like to clarify again that I am far from an expert, and these are just my impressions.

---

### Post by RAOF on 2006-07-20
> **Lunar_Lamp said:**
> ...
 - read the shadow file for root password(s) and send the password to the virus creator.  This could potentially be a significant security breach.
 - install a keylogger that only root can view to know about.
...
For the first one, I believe the deal with shadow passwords is that the plain-text password is **never** recorded.  The password that you type in is hashed/encrypted/messed with, and the messed with password is checked against the messed with password saved in the password file.  So, while having the shadow password file is useful (you can just keep trying passwords until they match), it's not like you can just read out the password easily.

Anything that stores passwords in plaintext is broken from a security standpoint.  **Anything** that stores a sensitive will (or should) do so in some form of mangled state.  It's even easier than encryption, 'cause you never need to be able to unmangle it :)

For the second one, it's totally possible for a malicious program on the windows system to do whatever it likes.  It could replace your kernel, and there's nothing (very much) you could do to tell.

It is of course quite difficult to get that to work reliably.  Distros are a moving target, from a binary standpoint.  But if someone wanted to get at your system enough, they could do it from windows.

---

### Post by cssutto on 2006-07-20
I believe the only way to protect oneself is to run ckrootkt and rkhunter regularly, in addition to waching which ports are open and what traffic is using your modem.

Which brings up the question as to why rkhunter --checkversion tells me that I have 1.2.7 and the new version is 1.2.8 but Synaptic tells me that I am up to date?

How can we stay clean if we are using out of date tools?

Why the difference?

CSSJR

---

### Post by halfvolle melk on 2006-07-20
Use a good firewall and don't click on anakornikova.jpg.eml. Also don't run as administrator unless performing administrative tasks.

edit: also, don't buy Sony music CDs.

---

