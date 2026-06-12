---
title: "Reliable Partitioner"
date: 2008-01-12
forum: General Help
---

### Post by MarCustomized on 2008-01-12
I'm @$#&ing tired of GParted!  All of my experiences with it have been bad.  It has a habit of overlapping my cylinders so I get errors when I try to use cfdisk.](*,)  I'm dd'ing my HD now and just starting from scratch.  Can any of you guys recommend a RELIABLE partitioner?  I'm sick of these issues.  I hear cfdisk can be reliable if I start with it and stick to it.

---

### Post by Herman on 2008-01-12
My opinion is that GParted and the rest of the 'parted family of partiitoners are very reliable if we start with those, (which are the default for the Ubuntu installers), and we stick with them. 
I have a few computers and do a lot of partitioning work and perform lots of installs I have only used GParted for years, since it's alpha stage, and I have never had a problem. 
The only time I had trouble was when I mixed different partitioners for an experiment to try them all out, and one other time when some dust got on a lens in an optical drive.

cfdisk doesn't seem to get along with GParted, I don't think it would be a good idea to use them alternatingly at all. 
I didn't know anyone still uses cfdisk for anything, is it still maintained?
Does it have any home page and web forum?
According to the Wikipedia, it's an old dinosaur from way back in 1992, [http://en.wikipedia.org/wiki/Cfdisk](http://en.wikipedia.org/wiki/Cfdisk)

Regards, Herman :)

---

### Post by MarCustomized on 2008-01-12
I'd like to stick to GParted but every time I make a logical partition, it overlaps at the beginning and end.  Also, I have a habit of trying whatever Distro I can get my hands on, and so many use different partitioners.
I was under the impression that cfdisk was very reliable considering the Distros that use it.

---

### Post by Herman on 2008-01-12
Oh, I see, well maybe you have a good case for sticking with cfdisk then,  here is something interesting I found when trying to understand why partitioners seem not to all agree with each other, 
**[HIW: [B]Partition Tables**]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fata-atapi.com%2Fhiwtab.htm&ei=HGaIR7iaJ6PgpgS59OHjDA&usg=AFQjCNEQrzjI9R0B6HZxw3msiTxJudgBBQ&sig2=yY_E4vZiRw6v1symJ2xvdQ")[/B]

According to that link,>  [FONT=Arial]there are NO written rules and NO    industry standards on how FDISK should work but here are some    basic rules that seem to be followed by most versions of    FDISK[/FONT]

To me, that implies we should avoid mixing different partitioners, and that's the way things seem  to be. 

Regards, Herman :)

---

### Post by MarCustomized on 2008-01-12
Good read.  Thanks!:)

---

