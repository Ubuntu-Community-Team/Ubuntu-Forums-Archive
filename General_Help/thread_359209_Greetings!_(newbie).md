---
title: "Greetings! (newbie)"
date: 2007-02-11
forum: General Help
---

### Post by error404 on 2007-02-11
Greetings,
I just started using Linux for first time.

So far so good! I was really impress how easy was to set it up. 

Best of all, I didn't had to type a single key or serial!!! :D 

Anyway, I do have a few questions, 

1. Has anyone been able to run Autocad on Linux? 
I tried SagCAD and QCaD but they were not what I was looking for.

2. Is it possible to access a network hard-drive that it's format as NTFS? (I would like to do something similar to "mapping a network drive" in windows)

2.b If I was able to access data from this network-storage... would I be able to save files in it?

3. I have been playing with some downloaded themes \\:D/  and installed gDesklets. How can I make desklet to load automatically when I boot the pc?

3.b how can I make my windows semi-transparent like some of the themes that I saw in the gallery.

I'm sure most of this are newbie  questions, so I'll be doing a long search in this forum trying to find the answers myself.... but I won't mind some help and guidance 


leo

---

### Post by PgR on 2007-02-11
Well there are certainly some questions there!

I [think I] can answer 2a and b. I think you're suggesting that the disk is in another machine, elsewhere on the network. In that case, the answer to both questions is "yes." Use the samba client (smbclient)

To see the manual pages for smbclient either install it "sudo apt-get install smbclient" and then type "man smbclient" in a terminal, or else google for "man smbclient"

---

### Post by kalikiana on 2007-02-11
I'd like to mention two keywords for two ways of accessing a remote filesystem.
. pyNeighborhood, a graphical frontend (not only) for Samba.
. fusesmb, a virtual filesystem allowing you to use network shares.

Good luck in the linux world! :popcorn:

---

### Post by error404 on 2007-02-12
thanks!

I was reading a little the manual in samba...  and it says it kind of like a FTP

does that means that when I'm working on a file in linux andther pc could open the same file up and not get any warnings that two pcs are editing the same file? :confused: 

leo

---

### Post by PgR on 2007-02-12
> **error404 said:**
> 
does that means that when I'm working on a file in linux andther pc could open the same file up and not get any warnings that two pcs are editing the same file? 

Good question. Well phrased. Ask me another... Don't know - but I'll try to find out.

---

