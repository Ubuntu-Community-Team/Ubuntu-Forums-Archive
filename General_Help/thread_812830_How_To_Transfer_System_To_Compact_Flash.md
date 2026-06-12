---
title: "How To Transfer System To Compact Flash ?"
date: 2008-05-30
forum: General Help
---

### Post by Raptor Ramjet on 2008-05-30
Hello,

I've been playing at making a mini-itx based MIDI file player/sequencer for live use.  To this end I've installed Ubuntu-Studio onto a hard drive for testing.

I'm now at the point where the system works well enough that I'd like to try it out at our next rehearsal.  But.. I have the small problem that the EIDE hard drive doesn't fit in the case (when I built the system it was the only spare drive I had) 

Since then I've manged to get both a laptop drive and a compact flash card plus EIDE to flash adaptor.

First off I'd therefore like to transfer the system from the EIDE disk on to the laptop disk.

At a later point I'd also like to transfer the system onto the compact flash card but I can't do this now as I need to fabricate a "holder" to support the compact flash adaptor securely (I need some parts for this including a new drill bit etc. etc.)

I would therefore be grateful to know how I can do these transfer ?  

I suspect I'll be able to do soemthing like "dd" but I a small complication is that the EIDE disk is 20 gb, of which 4Gb is used in a single "/" partition, the laptop drive is 10Gb and the compact flash is 8Gb.

With the latter two drives I'll be using 512Mb swap partitions.

Any top tips are most welcome !

Cheers.

---

### Post by mattress on 2008-05-30
I'd go for the dd option. It's the easiest method and can even be done with ssh and pipes...

```

dd if=/dev/EIDE | ssh user@server "of=/dev/FLASH"

```

It all depends on how you want to do it really...

m

---

### Post by Raptor Ramjet on 2008-06-03
Thanks for the reply.

However dd just didn;t do the job as it kept complaining about errors on the source disk (there are some mapped out sectors 'cause it's an almost junked test disk)

So I ended up getting bored and just reinstalled from screatch.

But thanks anyway.

---

