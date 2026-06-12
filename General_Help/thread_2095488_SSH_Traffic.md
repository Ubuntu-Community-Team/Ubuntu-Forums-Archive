---
title: "SSH Traffic?"
date: 2012-12-17
forum: General Help
---

### Post by rucker222 on 2012-12-17
Hi guys,

Today I used ssh from a remote laptop using my mobile hotspot to log into a home PC and using rsync told it to do an update of some files.  

As I was using my mobile hotsopt, it got me wondering how much of an effect it was having on my mobile data allowance.  The files I was backing up were on the home PC and were just being backed up to an external HDD which was plugged into that PC.  

The question I have (as I'm fairly new to using ssh) is does all the traffic i.e. the backup files travel to the laptop I was logging in from and back again to the home pc's external HDD, or does it all just happen back at home locally (I hope so otherwise I may get a shock when I get my next bill :shock:) and just send the details to the terminal on my laptop?

I only started wondering about this as it appeared to be taking longer than i would usually expect for those files to be copied from one spot to another had I been at home and physically transferring a copy them from one spot to another myself.  

Cheers,

Lee.

---

### Post by drmrgd on 2012-12-17
No, the files won't have been transferred to your laptop and then back to the external drive.  They should have gone directly to the external drive just as if you were sitting at that computer and did the transfer from there.  SSH just allows you to remotely log into that computer and work with that computer.

---

### Post by chadk5utc on 2012-12-17
you are simply sending the commands to the remote and monitoring the progress very minimal as far as data.

---

### Post by 3rdalbum on 2012-12-17
Yes, with SSH you merely told the computer at home what to do.

If you'd used Samba instead, you'd be looking at a massive internet bill.

Since I was a kid I noticed that using Appletalk to copy a file from an internal to external hard disk on the same computer would cause the file to be transferred across the network needlessly. I thought "Why don't they have some little way where the client can tell the server to just do the copy itself?". I'm still disappointed that Samba doesn't work this way.

However you're okay, you used SSH.

---

### Post by rucker222 on 2012-12-17
Thanks heaps guys, I really appreciate the replies.

That clears that one up nicely for me.  I thought/hoped that was the case but had to be sure and ask some people much smarter than myself :p

Cheers,
Lee.

---

