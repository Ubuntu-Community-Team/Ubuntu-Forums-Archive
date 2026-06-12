---
title: "Xubunto remote printing to Windows XP attached printeer"
date: 2007-05-01
forum: General Help
---

### Post by arferbeer on 2007-05-01
Hi all.

First experiences of Linux and I'm pretty impressed. I really like the community feel of it all and I'm hoping someone can help me with a remote printing problem.

Installed Xubuntu 7.04 a few days ago and been trying to get it to print to the HP Deskjet930C attached to my windows XP Pro machine ever since. I chose Xubuntu for my laptop 'cos it's only a PIII 600 Mhz box. If I can get this problem sorted I'll be a happy boy

I've searched the forums for this but not found anything to help greatly. What did look promising in search results usually turned out to be either not for this version or I didn't understand it or both.

Can someone please explain what to do to this newbie. I must admit that I am not that experienced with either Linux or XP, so the simpler the better please.

---

### Post by rax_m on 2007-05-01
Hi,

I had to the same with my HP Deskjet 840C the other day and it worked fine. 
Altho' I did this under Ubuntu.. i'm guessing it's pretty similar for you. 


1. Set up your printer as a shared printer in Windows XP. Should be a matter of right-clicking the printer and selecting sharing. Then enabling the option.
2. If you have a firewall on your windows box (like zonealarm) you may have to add your linux box as a trusted host. 
3. Go to X(ubuntu), Administration -> Printing
4. Add a new printer
5. Select Windows printer and fill in the details like host, username password etc. 
6. Then just follow the instructions and that should be it. 

Rax

---

### Post by arferbeer on 2007-05-01
Doh, I feel a bit of a fool now. It was the firewall stopping it all along, beginners mistake lol.

Many thanks for the remarkably swift response :)

---

### Post by rax_m on 2007-05-02
No problem.. just happenned to be at the right thread at the right time  (i.e. one I could actually answer :lolflag: )

I had also this working and then zonealarm switched from the full version to the free version and it suddenly stopped working.. took me a little while to figure it out.

---

