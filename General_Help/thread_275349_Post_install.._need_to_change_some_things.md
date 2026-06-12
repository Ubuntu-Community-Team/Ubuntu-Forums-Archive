---
title: "Post install.. need to change some things"
date: 2006-10-11
forum: General Help
---

### Post by finalzero on 2006-10-11
Hi,

I have just finished installing the latest version of Ubuntu and I need to make some changes however I am unsure as to how Ubuntu works.

On Debian I would normally just populate the apt source list and then download the latest kernel, header and source for my machine (Dual P4 Xeon).

I would like to upgrade ubuntu to the latest kernel's with SMP support and install the nVidia driver for my grahics card.  Can I download these from the application manager in Gnome or will I need to fire up a shell and manually install these?

And finally can I remove the 386 kernel as I have no need for it, I am assuming I can simply deselect this from the app manager?

And one final question, where do I got to change the su password as I find Ubuntu is a bit handicapped in its current form and I really don't want sudo every command each time.

Thanks in advance,

Fz

---

### Post by finalzero on 2006-10-11
Okay noticed the Ubuntu images are named differently..

I have dual P4 Xeon system so which image should I be using:

2.6.15-27-686

or 2.6.15-27-server

cheers,

Fz

---

### Post by apjone on 2006-10-11
edit /etc/apt/sources.lst add whats need save and quit, run update manager. Then use synaptic to install what you need. I used envy to install my nvidia drivers, cant remember where i got it from now though.

Root password

do a sudo -s to become root and then change the root password as per usual

---

### Post by aysiu on 2006-10-11
If you edit the sources.list, I would recommend going with sources from here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

You can also Google source-o-matic.

Do not use Debian repositories. They will mess up your system eventually.

---

