---
title: "Quick 'n Painless Question"
date: 2005-09-19
forum: General Help
---

### Post by Havoc on 2005-09-19
Ok, I'm getting a Kernel Panic, ok?

It started happening after I "found" a bug in Dr-DOS which destroyed all my partitions, all right?
So, I reinstalled from scratch, and I found that something in the bootup had changed, somehow, got it?
I was getting kernel panics after some time, so I said, what the #!$#@, I'll reinstall, understand?
I reinstall, and I thought that all the problems were away, I even got multiple sounds with Rythmbox and games playing sounds together, you follow?

But that's not important.What's important is, where do I find a log, or something that tells me WHY IN THE NAME OF LUCIFER IS THIS HAPPENING ALL OF A SUDDEN!??

Oh, and I *AM* crazy.They recently gave away Apple Powerbooks in my psychiatric ward, and I was one of the winners.Well, not really, but It would be fun, no?

They gave us Sony Laptops.  :wink:

---

### Post by bsussman on 2005-09-19
There is nothing painless about this.

You might not find this real satisfying but...

Many of the logs that contain useful info are in /var/log

if you:

 ```
>cd /var/log
> ls -latr
``` 

you will see a list of them in sorted order so that you can determine conveniently which were written to last.

Since you are rebooted, this may or may not help you to identify the right logs to look at.

I would look in messages, system, auth and daemon for suspicious things. try to find the messages at the time of the panic. note that there will be a gap, when the panic occurred.

The problem is to guess at what might be suspicious.  Ask questions.

---

