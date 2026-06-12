---
title: "no sudo after Kernel up- and downgrade"
date: 2006-11-08
forum: General Help
---

### Post by bmhm on 2006-11-08
[FONT="Verdana"]Hi!

I recently compiled my own 2.6.18.2 - worked well, but bcm43xx still refused working. Since my standby didn't work anymore (S3 didn't wake up properly on my Acer Aspire 5024), I uninstalled my new Kernelpackage.

I now have got the original kernel back.

But now I can't do sudo anymore, and I can't access ANY root-function. I can't start Synaptic (no permission) etc. - I didn't found a group wheel and I'm on the group "sudo".
Any Ideas?

Ubuntu 6.10
Standard Kernel (after up- and downgrade)
Laptop installation - worked brilliant so far!
Acer Aspire 5024WMLi
No sudo/root, just fakeroot.[/FONT]

---

### Post by bmhm on 2006-11-08
Anyone? Please?

urgent...

---

### Post by bsussman on 2006-11-08
> **bmhm said:**
> [FONT=Verdana]
But now I can't do sudo anymore, and I can't access ANY root-function. I can't start Synaptic (no permission) etc. - I didn't found a group wheel and I'm on the group "sudo".
Any Ideas?
[/FONT]

Not sure without looking.

Do you have a root password set?  This is an example where having a working root account is a good idea.  You can just 'su -' if you do.  Not recommended for normal use :)

I am assuming that sudo is giving you an error.

You probably should boot from a rescue cd and look at the /etc/sudoers file.

This line should be in it:

%admin  ALL=(ALL) ALL

And you should be a member of the admin group.  I am not a member of the sudo group and I have no problem with sudo!

---

### Post by bmhm on 2006-11-08
> **bsussman said:**
> Not sure without looking.

Do you have a root password set? 
[FONT="Verdana"]I didn't set one on my own. Just kernel up- and downgrade.[/FONT]

> This is an example where having a working root account is a good idea.  You can just 'su -' if you do.  Not recommended for normal use :)
[FONT="Verdana"]no. Authentification failure.[/FONT]

> I am assuming that sudo is giving you an error.
[FONT="Verdana"]No, it just does nothing. Not even asking for a Password!! gksude gives an error (no permission).[/FONT]

> You probably should boot from a rescue cd and look at the /etc/sudoers file.

This line should be in it:
[FONT="Fixedsys"]%admin  ALL=(ALL) ALL[/FONT]
[FONT="Verdana"]Found the line.[/FONT]

> And you should be a member of the admin group.  I am not a member of the sudo group and I have no problem with sudo!
[FONT="Verdana"]TAHT was the point!! :D Now it works again!! :D *jumping around happily* Thank you soooo much :D *bighug* :D


So now I just need to fix the following problem: I returned to my 2.6.18.2-Kernel, but now S3 doesn't work anymore. When I try to resume, my screen stays black, HDD is loading sth, don't know what. Pushing PWR for 5 sec doesn't turn my Notebook of, it switches on by its own automatically again - lol *wants to live* ?

Any clues? :)[/FONT]

---

### Post by bsussman on 2006-11-08
You should open a different topic about the S3 problem since it is now buried in this topic

---

### Post by unlokia on 2006-11-08
Surely if it is THAT urgent, you'd be busy doing a clean install and not sitting online waiting for replies. Sorry to sound harsh but that is what I'd do!

---

### Post by bmhm on 2006-11-09
Well, no. I want to keep my system. really. I put so much work into it.
Well everything works but S3, so I will now open a new thread.

Thanks for your first answer!

---

