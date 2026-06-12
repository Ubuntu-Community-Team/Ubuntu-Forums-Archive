---
title: "Virtualization Question"
date: 2007-04-23
forum: General Help
---

### Post by ajrich01 on 2007-04-23
I have a PC with the new Ubuntu 7.04 and Windows XP Pro dual booted.  What I am trying to do is find a way to boot my XP install inside of Ubuntu through virtualization.  I have looked into kvm but my processor does not support it. It looks like my only to options after that are QEMU or Xen.  From what I can see Xen does not support Ubuntu. Is this even a possible setup?  Any info pointing me in the right direction would be most appreciated.

---

### Post by ToucanSam on 2007-04-23
I like virtualbox, to tell you the truth it is the only one I have used. Its also open source.

Set up (not counting windows install) took me about 15 mins.

Bkkkkawwwk

---

### Post by dbqp on 2007-04-23
I too was tired of the dual boot so I set-up VM Ware Server within Ubuntu and installed XP. Runs like a charm and I can use the apps that require me to use Windows for...

dbqp

---

### Post by ToucanSam on 2007-04-23
Yeah, as a side note, in vmware you can save images of your machines, dont think virtualbox does that.

---

### Post by mdurham on 2007-04-23
> What I am trying to do is find a way to boot my XP install inside of Ubuntu
Nobody seems to have read this part of the original post, the answer is you can't do that.
You must install XP onto a virtual drive under vmware or vitualbox, I'd recommend virtualbox, I think the previous post is incorrect about virtualbox, you can save images of your machine.

---

### Post by ajrich01 on 2007-04-24
Thanks for the recommendations, I will give virtualbox a shot.  VMWare isn't free is it?

---

### Post by beerorkid on 2007-04-24
vmware server and vmware player are free.  Also there is a free convertor that will allow you to make a VM out of a metal OS.  That would help you get your XP virtualized.

---

