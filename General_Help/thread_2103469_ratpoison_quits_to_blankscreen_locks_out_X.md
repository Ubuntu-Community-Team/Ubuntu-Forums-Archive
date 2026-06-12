---
title: "ratpoison quits to blankscreen: locks out X?"
date: 2013-01-10
forum: General Help
---

### Post by stabu on 2013-01-10
Hi,

I'm using Ubuntu 12.04 Server edition and have installed xinit and ratpoison which works correctly.

The only thing wrong is unfortunately rather nasty: when I quit ratpoison using the appropriate keys, it exits to a blank-screen, and none of my keys work anymore, leaving the only option of hard shut down, so that's why I say nasty.

What I would have expected is that X is terminated and I go back to login console (which is how I start ... I need to type "startx" each time I bootup ... but that's what I want). Now, if this was desktop edition, I would expect gdm to be interfering here, but this is server edition.

I've had this with more one machine now and googling this error gives very little info ... I think because it's not a particularly widely used wm.

Has anybody come across this?

Cheers!

---

### Post by stabu on 2013-01-10
OK.. well, I discovered this problem is not specific to ratpoison: icewm also has this problem.

I am now thinking that it's specific to ubuntu server ... clearly it can't be a very X-ready distribution, so I've got to thinking I'm missing an X package ... there are so many, I don't know which to choose.

There may be an xorg-exit-x-session package of some sort.

Is there any way the mods can transfer this post to the Server edition forum?

---

### Post by stabu on 2013-01-10
Well ... no reply from mods ...

Anyhow ... I went and installed lightdm-gtk-greeter, to see if it would help.

However ... the new coloruful login screen only gave me icewm as an option, and even at that, the same problem occurred. So, it was not what I was looking for.

So I decided to get rid of it with "apt-get purge" ... but this was not effective. Because lightdm itself was installed, and this was not purged. 

The result: worse than before. The entire system unoperable. A live CD enabled me to purge lightdm (although this did not get rid of everything, particularly the /etc/lightdm directory).

This is all very sloppy packaging.

---

