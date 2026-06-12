---
title: "grub messes up menu.lst after kernel upgrade"
date: 2007-05-09
forum: General Help
---

### Post by DLGandalf on 2007-05-09
whenever there is a new kernel available through apt, grub automatically updates menu.lst
unfortunately it doesn't do a very good job. It keeps changing root (0,7)  to root(0,5)

the (0,5) was the destination where kubuntu was installed before I changed my partitions

so my real question is, where does grub get the information it should still boot from (0,5) instead of (0,7) and how can I change this

I hope it's understandable

(ps I didn't really know where to search for the answer, If this is a typically newbie question.. sorry)

---

### Post by jimbob on 2007-05-09
I feel your pain - it has happened to me many times.

What I do is save the current copy of menu.lst whenever I see that I am about to be blessed with a new kernel version and then put it back after the update and modify the kernel version in the original with the new one.

I haven't the foggiest idea where or how it generates the new menu.lst
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Bigbluecat on 2007-05-09
You can fix the defualt root so that this does not happen in your menu.lst.

Open menu.lst and look for groot (grub root)

Set it to your approporiate hd:

e.g. groot=(hd0,5)

The other item to check is updatedefaultentry.

Set this =true.

This way if your defualt boot kernel is not the first in menu.lst it will remain the default even if new kernels are added aheda of it.

---

### Post by DLGandalf on 2007-05-10
that's weird, the line with groot should be commented ('#') ?

But thanks! it works

---

### Post by DLGandalf on 2007-05-10
Cheered too early

It correctly updates root (hdx,x)

but the root paramater contains an old UUID, to fix this I just change this to root=/dev/sda8
But it'd like to see this changed correctly in the first place. 
I searched for a similar way like the root (x,x)  problem but found nothing in the menu.lst file

any ideas?

edit:
changing the option 
#kopt
has no effect after update-grub has been run

---

### Post by Bigbluecat on 2007-05-11
Can you post a copy of your menu.lst please? It would help me understand what may be going on.

Also have a read of this site:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Has pretty much everything you need to know about grub and is where I learned the ins and outs.

---

### Post by mdurham on 2007-05-11
I copied the grub directory to a separate partition where I also have my separate  home directory, this way the installer can mess around all it wants with the original and my version stays intact. If you do put it on another partition you must tell the Grub booter to use the new position.
Cheers

---

