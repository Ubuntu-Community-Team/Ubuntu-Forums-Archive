---
title: "For new build. How to choose Mobo that is UEFI compatible for Ubuntu?"
date: 2015-11-05
forum: General Help
---

### Post by mikodo on 2015-11-05
For new Desktop computer.

How to determine in advance which UEFI/BIOS will not be too difficult to  work with a singular Ubuntu 16.04 install next year? No Windows.

I want UEFI > GPT. Secure boot would be nice.

How do I do that?

Right now they are recommending for my simple needs (No high computational usage): Intel i-5 cpu is just fine.[URL="http://us.msi.com/product/mb/B150-PC-MATE.html"]

[/URL][http://ca.msi.com/product/mb/B150-PC-MATE.html#hero-overview]("http://us.msi.com/product/mb/B150-PC-MATE.html")

I'm going to stick your replies in my Next-Computer file for next-year.

Thanks.

---

### Post by TheFu on 2015-11-05
What will or won't work with 16.04 cannot be predicted.
However, a good guess would be a server from a reputable vendor that has proven history with Linux support. Supermicro.

GPT doesn't require UEFI. That is a Windows limitation, not a Linux one.  Have a few  systems here that only have GPT disks and boot in 'legacy mode'.  But you are correct in wanting SecureBoot, UEFI  and GPT. Those are part of the Linux Foundation's Secure Workstation recommendations.

Is this a server or a desktop? What will the workload be? The 2nd paragraph in #1 isn't clear. Can you try different wording  please?

---

### Post by mikodo on 2015-11-05
> **TheFu said:**
> Is this a server or a desktop? What will the workload be? 

                        Oh, I apologize. I seized a little time here, to ask a quick question. I will clear up the original post after this.

My machine is just going to be a *desktop. *Very light duty. No intensive computing at all.

(The place in town builds for personal desktops, to large server arrays, to large deployments of multiple workstations for companies. What I was trying to get at is, they are no, "mom and pop shop").

@ TheFu. You might see where I got the direction and inspiration for some of this:

My plan is this:

1. New Desktop Machine next year. See above.

2. Prepare the new "platter" drive with GPT, as I want.

3. Install with Ubuntu 16.04 Ubiquity with full disk encryption, (Dm-Crypt), using LVM, for the volume management.

4. Have one partition that I will move my "data" into, after the fact. 

5. From $home, symbolically link to my "data", for Documents, Music, etc,  that automounts in /mnt.

6. Backup the "data" with rsync, to two flash-drives. One in the bank and, one at home and change them out regularly. Those, I have chosen to encrypt with  ecryptfs so, I don't have to worry about messed up LUKS headers and will be always able to get to my "data-backups". ** Actually, I haven't decided if I should use flash-drives, or portable platters for this, (I have to read more Ecryptfs about protecting against data leaking from errant cells).

7. Install Vbox, and play with distro's as I like. Who knows, I might even eventually join the testers, for Ubuntu-next.

8. Divorce my wife.

9. Age gracefully. 

Honorable mention going to oldfred for, holding my hand while I learned how to have my "data" as, I do now.

:)

---

### Post by TheFu on 2015-11-06
Ok. I helped a good friend divorce her husband a few years ago. Takes guts.

Your needs and mine are very similar, so I'll share what I would get if someone else was paying for a "work" machine.  I'd try to select as much computer as possible, without looking greedy/extravagant.

* Core i5 - current-generation   ... basically, whatever CPU costs $200.
```

Intel Xeon X5670 @ 2.93GHz      8,163   $190.00
Intel Core i5-4590 @ 3.30GHz    7,222   $198.99
Intel Core i5-4570 @ 3.20GHz    7,019   $199.99
Intel Core i5-4590S @ 3.00GHz   7,018   $209.43
Intel Core i5-4690T @ 2.50GHz   6,802   NA
Intel Core i5-4460 @ 3.20GHz    6,636   $189.99
Intel Core i5-4570S @ 2.90GHz   6,621   $194.99
Intel Core i5-4570R @ 2.70GHz   6,456   NA
Intel Core i5-4440 @ 3.10GHz    6,436   $189.99
```
One of those probably, depending on the MB + DDR3 RAM. If any require DDR4, I'd avoid for now. Never be an early adopter for new RAM. Delay for 2+ years for pricing to drop. 
* Gigabyte MB that works with that CPU. Every MSI MB I've had was solid, but something was wrong - my current MSI has huge throughput issues with USB3 connected disks, even though they connect through an addon card.
* Non-Realtek NICs. Marvell works or any Intel PRO/1000 would be preferred. I want 2 ports, especially for a VM host.
* 8-16G of RAM, depending on budget.  G.Skill is fine.
* LVM for all disks, but **never** span LVs across physical disks, without an excellent, perfect, backup solutions.
* Consider rdiff-backup for backups. rsync usually isn't sufficient for versioned backups. rdiff-backup handles versioning, efficiently, with less hassle than rsync. [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) shows how easy it is.  A $40 USB3 external 2.5" disk can hold 500G of data and probably will not fail as quickly as flash disks written daily. rsync has many great uses, daily backups with versioning just isn't one of them, IMHO. A couple of 64G flash disks can work too. I would expect to replace them every other year due to write-wear. Should do longer than that, but being prepared is good.
* Only put temporary mounts under /mnt.  This is an admin thing and a file system standards thing. Permanent mounts belong exactly where you need them.  I am not against symbolic links.
* Can I recommend KVM + virt-manager and Spice display over virtualbox? Many reasons.  Virtualbox is easier,  but not nearly as efficient.  Plus nobody runs virtualbox in production environments where stability is needed. They use KVM. If you do virtualization, KVM is what you want to learn.

If I was paying.... I'd look for a $100 CPU in a $200 CPU+MB combo. 35W or less power required-trying to reduce my home power use slightly.
I haven't purchased a separate GPU in almost a decade. The onboard GPUs on Intel systems have fantastic Linux support. For average, non-gaming, needs, the intel IGP is great!  About 8 months ago, built a cheap $140 system around a Pentium G3258. It is an amazing $60 CPU - almost as fast as 1st-gen Core i5.  That box is a media server here  -  plexMS,  NFS, Kodi --- has 12TB of storage with enough power to transcode hidef video for any DLNA clients on-the-fly.

Of course, there are 500 different ways to do this stuff. Just how I'd do it above. There are definitely other solutions, some better, to be sure.

---

### Post by QDR06VV9 on 2015-11-06
Just for added info only

[Intel NIC vs RealTek NIC - Performance Testing]("https://forums.freenas.org/index.php?threads/intel-nic-vs-realtek-nic-performance-testing.10325/")

---

### Post by mikodo on 2015-11-06
Thank you, folks.

I guess, "I gets what I get", with firmware for BIOS/UEFI.

- rdiff-backup already is in my "New Projects" folder to learn. Someday. I still like rsync for quick data transfer, (moving it around). I don't regret learning it.

- KVM, I'll add it too. I always thought it was too "geeky" for this casual user but, I will start with your recommended reading.

- On hardware. Too much to discuss. I'll keep reading on the suggestions. I have already made some of the same decisions. Thanks.

- I like having my "data" outside the /root install to keep it separate. Though, I want it encrypted on the internal disk (in its' own partition), over the Dm-crypt layer. Backups outside the LVM and non-Dm-crypt. I am not willing to trust my data completely to LUKS Headers, that could fail on disks. This is where Ecryptfs will have to be sufficient.

Enjoy yourselves!

---

### Post by MartyBuntu on 2015-11-06
Honestly, I would just skip UEFI altogether.

---

### Post by mikodo on 2015-11-06
> **MartyBuntu said:**
> Honestly, I would just skip UEFI altogether.
Hi!

- With this, my only computer I have ever had, I am very comfortable with BIOS, a MBR and msdos partitions. So, I understand.

But,

1. CSM is not going to be available forever. Eventually I understand, it will go the way of the dodo.

2. I want try to incorporate "Secure-boot", for some added security against Bootkits, (Rootkits for the booting process).

3. Oldfred talks of other benefits that UEFI has, that I haven't experienced yet.

Thank you.

---

### Post by Dennis N on 2015-11-06
Asus boards are great. I have built two systems with them and am happy with those systems. One is BIOS (built in 2011) and the other is UEFI (built in 2014). The Asus UEFI firmware I found to be easy to work with. Both were 100% compatable with Linux - everything worked. I like UEFI better than BIOS. GPT better than MBR. I now use GPT any time I am starting with a new disk. 

I have another UEFI Zotac brand system which is a "barebones" system, meaning you add the memory and disk drive. The motherboard and processor come with it. It has also performed without any problems using Linux. Everything works.

---

### Post by mikodo on 2015-11-06
Thank you, Dennis.

> **Dennis N said:**
>  -All you said- "Asus boards are great. The Asus UEFI firmware I found to be easy to work with". 

Good to know!

---

### Post by TheFu on 2015-11-06
rsync is an amazing tool. Important to have in your toolkit, along with ssh and simple bash scripting. It is in my top-ten inventions of all time list. It can do much more than just copy data around.

If you use encryption, having excellent backups is mandatory. When important bits are corrupted, that entire encrypted block is gone. Depending on the block, it could be a minor inconvenience or lead to complete data loss for the volumes.

I use encryption on every portable device. Had one stolen once that wasn't encrypted and learned my lesson.

Anyway, seems you are making smart decisions based on the information available. Nice.

---

### Post by mikodo on 2015-11-06
> **TheFu said:**
>  or any Intel PRO/1000 would be preferred.** I want 2 ports, especially for a VM host**.

I didn't see why. 

I think this is the answer: [http://www.techpowerup.com/forums/threads/what-is-the-point-of-two-ethernet-ports-on-my-motherboard.168960/page-2](http://www.techpowerup.com/forums/threads/what-is-the-point-of-two-ethernet-ports-on-my-motherboard.168960/page-2)

#35: ... the number one reason there are two of  these (if not) more is that the vast majority of users running a single  guest OS or virtual machine want a dedicated ethernet port for that  machine.

Out of band KVM over ethernet is very much a server function, and in  that case the port is dedicated or becomes dedicated after an add-in  module is plugged in.

#36: ... You can dedicate single network adapters to a VM like how you can  dedicate a full hard drive or partition to a VM as opposed to just  providing it a virtual disk.

Addendum, after TheFu's post below: I guess I will see the benefit of having 2 ports for this KVM "Host Machine" when I start playing with it. For now, all I need to know is that I should do the same. Nuff said.

---

### Post by TheFu on 2015-11-06
Don't mix up KVM with,  er ...   KVM. ;)
a) virtual machine hypervisor
b) keyboard, video, and mouse device

I use both. ;)  Why have all those extra keyboards, monitors,  and   mice?

There are many reasons to have **at least** two network ports. Where I used to work every plain server always required at least 6 ports to be connected to the different networks. Any less and it wasn't allowed to be powered up until that was fixed.

---

### Post by mikodo on 2015-11-07
Thank you, everyone!

I was "down the rabbit hole" again, looking into KVM. I gotta stop that for a while. :)

Thing is, the thread is "solved" and I would have just done that without another post but,

When I was reading about virt-manager and spice-client in the Ubuntu Repos, I came across this on Spice:

  [http://www.ubuntu.com/usn/usn-2736-1/](http://www.ubuntu.com/usn/usn-2736-1/)

Anyone using 14.04 or 15.04 and Spice, needs to have a look. 

Mostly this note is for any casual user seeing this thread who, is using Spice with those.

---

### Post by Swagman on 2015-11-07
I just put online a "fresh build" using an Asus board.

I haven't built a new machine since about 2008 and was initially shocked at the new bios. I knew about UEFI and was initially concerned about getting a Linux compatible board but couldn't get an answer quick enough so I bit the bullet and ordered !!

The issues I had  with Secure Boot etc are solely down to me not having dealt with UEFI before.

My Ubuntu system boots off 250gb SSD and I installed Win 7 on a partition on a 2TB HD with the rest of that drive dedicated to /Home

I couldn't get grub to display and had to use F8 boot options to get into Ubuntu. Messing about in the Bios I noticed the SSD was there but not in the boot order list. 
I couldn't put it in that list either.

So I played around in the "Security" option and discovered the switching of secure boot enabled the system to load from SSD and subsequently get a grub screen.

Everything works a treat and to be honest.. I've no idea why I bothered to dedicate any space to windows as I rarely ever use it.
I also installed Vbox with Win7 in Ubuntu anyway because of the two reasons I use windows 1 is to view my CCTV on this system downstairs (main CCTV is upstairs). For some obscure reason The LINUX build O/s of the CCTV needs Explorer to view remotely !

The other reason is "DiskSort" for USB sticks (playing Mp3's in the order I tell it to)

System bits ... 

[http://i.imgur.com/PlIAdKD.jpg](http://i.imgur.com/PlIAdKD.jpg)
[http://i.imgur.com/yUC9uER.jpg](http://i.imgur.com/yUC9uER.jpg)

CCTV on previous build (Kubuntu) .. [http://i.imgur.com/w6Cs97v.jpg](http://i.imgur.com/w6Cs97v.jpg)

---

