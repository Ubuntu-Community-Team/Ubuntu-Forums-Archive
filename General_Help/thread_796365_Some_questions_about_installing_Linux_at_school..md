---
title: "Some questions about installing Linux at school."
date: 2008-05-16
forum: General Help
---

### Post by StevenRoose3 on 2008-05-16
Hi all, maybe a get permission to install Ubuntu on the computers of our school.
But i have some questions about this:

1. I heard that it's better and faster to install once and use an image to install on computers of the same type => how?

2. How can I set up a school-network?

3. Our school also has some very old non-Ubuntu-capable computers (less than 256 RAM, sometimes even less then 128). I am looking for a usefull distro for this computers, but i can't find a good one. We tried DSL, but that's a bit to bad. We also tried SlackWare but this gave an error, and it's not free, and i don't think our school wants to pay for it... Maybe you know a good distro for this PCs

thanks in advance,
Steven

---

### Post by DieB on 2008-05-16
as for the lack of ram there is the LTSP (linux Terminal Server Project).

Organizations like linux 4 africa uses that to employ schools with low-end computers like PII or PIIIs.

And I would try to contact the ubuntu guys directly, due to the fact that they look forward to support schools.

They even try to have an addon for schools, called edubuntu (see [http://www.edubuntu.org/](http://www.edubuntu.org/) ).

---

### Post by StevenRoose3 on 2008-05-16
that's an answer of my third question i think, the most important one was the first...

but I think the PCs are PIII, 600MHz, I' not sure. But I just found Fluxbuntu, I'll try that next monday, it would normally work, and it really looks good. I'll maybe test it on a old PC here.

but can anyone solve question 1 and 2, please

EDIT: PS: edubuntu, i just never find info about it, does it use GNOME? and what's special about it? it looks for little kids, not for a secundary school, but the Schooltool calendar looks usefull.

---

### Post by decoherence on 2008-05-16
*1. I heard that it's better and faster to install once and use an image to install on computers of the same type => how?*

There are a ton of ways. The most direct is to get the system set up as you like, then boot it from a live CD, hook up an external drive and use the command

dd if=/dev/sda of=/media/YOUREXTERNALDRIVE/yourDiskImage

This assumes the drive you want to take the image from is sda (it should be if it's the only drive)

Next, boot the computer you want to act as the clone from the live CD, hook up the external drive and basically do the same thing in reverse 

dd if=/media/YOUREXTERNALDRIVE/yourDiskImage of=/dev/sda

It is also possible (and extremely cool) to do away with the external drive and run the cloning over the network by combining dd with netcat. If you'd like more info on that, let me know. I've written up some documentation for the guys at my work.

*2. How can I set up a school-network?*

What kind of network? You can simply do the install on a bunch of machines, then go to Places -> Network and see what you can see. Quite possibly Ubuntu's zeroconf will make a peer-to-peer network quite easy. If you want more of a server/client setup, you'll need to be more specific as to what role you want the server to play.... file serving? authentication? network address translation?

*3. Our school also has some very old non-Ubuntu-capable computers (less than 256 RAM, sometimes even less then 12. I am looking for a usefull distro for this computers, but i can't find a good one. We tried DSL, but that's a bit to bad. We also tried SlackWare but this gave an error, and it's not free, and i don't think our school wants to pay for it... Maybe you know a good distro for this PCs*

I see you've already found Xubuntu. If it works for you, go with that. Other considerations are Puppy, Vector Linux, Fluxbuntu.... but Xubuntu is the nicest of these, imho (though still more hoggish than some of the others.)

Also, you don't have to pay for Slackware. Perhaps someone is selling a support package for it?

---

### Post by StevenRoose3 on 2008-05-16
many thanks!
1. I can do it with a external drive, but what size does it has to be, maybe its possible with my 4GB USB? if not, maybe you can send me that info by email, or maybe we could chat about it (jabber? skype? msn?)

2. actually it just have to be a shared folfer like thing, from one central pc or with every single pc by id

3. u tried xubuntu, but that didn't worked i think, but i just discovered fluxbox, and i hope thatone would work.

---

### Post by decoherence on 2008-05-16
1. The needed size depends on your system. I don't know off hand what a default install is, but yes you should be able to do it with your 4GB USB (though if it's a pen/thumb drive I'd be careful... i don't trust them entirely)

To find out for sure, run the following froma terminal on the system once it's set up the way you want

df -h

You'll be looking for the "Used" column of /dev/sda1 (using the device names from the previous example). Add to that the size of your swap partition and that's how big your drive must be.

taking off from work now, but i'll touch on the other ones when i get home.

---

### Post by StevenRoose3 on 2008-05-16
is there a manual or something about how to do that?
because with only an image that's not all, the partition have to be formatted to, or is it possible just format it with LiveCD and then using that one command u told. that would be nice!

---

### Post by decoherence on 2008-05-19
sorry for the wait.

yes, there are manuals. type man dd and man nc in the terminal. there are also a ton of howtos on google.

The image is of the entire device (/dev/sda) with partition map and all. There is no need to prepare the target drive in any way -- the command will just blow away whatever's already on there and create the same partitions that were on the source device.

---

### Post by sparrowkc on 2008-05-19
I don't know much about it, but active directory is supported in 8.04.  Active directory is what lets one login work on multiple computers, and is a windows thing.  If your school is using that for their windows computers, it would be a good option for the network part of your question.  Someone here could probably help you with it.

Good Luck, I'm looking at doing some similar things next year when my school upgrades hardware and transfers windows licenses.

---

### Post by Cap'n Skyler on 2008-05-19
you can try anything from live cd's to full on distros.i have a 10 year old comp that works really good with Puppy linux.
it has a 9 GB hard drive ....it was a win 98 comp.
Ubuntu has a minimalist cd image you can try.you can then just add the things you like or think would be good for your purpose.what kinds of apps do you think you will need?:popcorn:

---

### Post by StevenRoose3 on 2008-05-20
> **decoherence said:**
> sorry for the wait.

yes, there are manuals. type man dd and man nc in the terminal. there are also a ton of howtos on google.

The image is of the entire device (/dev/sda) with partition map and all. There is no need to prepare the target drive in any way -- the command will just blow away whatever's already on there and create the same partitions that were on the source device.

that's not that good, because the computers are running XP now, and Ubuntu has to be installed on the second partition. The XP may not be damaged.
Isn't there an option to select a partition (/dev/sda2 is the installation partition)

--

that active directory thing don't i understand...

--

Puppy Linux, never thought about. TY! I'll first try Fluxbuntu, because when the newer PC's get Ubuntu, and the older Fluxbuntu, the pupils will understand faster how it works, the interfaces really looks a bit the same.

---

