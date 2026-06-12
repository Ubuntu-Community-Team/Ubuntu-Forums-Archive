---
title: "Turn off/ restart button disappeared"
date: 2008-05-29
forum: General Help
---

### Post by lash9420 on 2008-05-29
I am new to Linux and started using Ubuntu just a few weeks ago. Recently I have noticed that my turn off and restart button have disappeared. The only way to turn off the computer is to press the power button on the tower. How would I get them back? Anyone else had this problem?

Thanks!

---

### Post by Zorael on 2008-05-29
I'll just lash out blindly here, but do you have the [FONT="Courier New"]xserver-xgl[/FONT] package installed? It can cause what you're describing. Pop up Synaptic and check.

---

### Post by lash9420 on 2008-05-29
Yes, xserver-xgl is installed. What does it do? Do I need to remove it?

---

### Post by MythosLegend on 2008-05-29
Have you tried right clicking on the panel, add to panel, add quit icon?

---

### Post by lash9420 on 2008-05-29
That doesn't work for me, MythosLegend....If I hover my mouse over it, it even says power off the computer; but yet the icons are not there when I click on the power symbol.

---

### Post by Zorael on 2008-05-29
edit: Yes, remove that package.

See [htp://www.freesoftwaremagazine.com/articles/accelerated_x](htp://www.freesoftwaremagazine.com/articles/accelerated_x) for an article on [AIGLX](http://en.wikipedia.org/wiki/AIGLX) vs [XGL](http://en.wikipedia.org/wiki/XGL). Suffice it to say that Nvidia, ATI and Intel cards (at least) doesn't like XGL. Things will be, well, software-rendered.

So you don't want it at any rate.

---

### Post by lash9420 on 2008-05-29
It just really messed things up....FF now scrolls really slowly and it logged in weird.....

---

### Post by prinknash on 2008-05-29
> **lash9420 said:**
> I am new to Linux and started using Ubuntu just a few weeks ago. Recently I have noticed that my turn off and restart button have disappeared. The only way to turn off the computer is to press the power button on the tower. How would I get them back? Anyone else had this problem?

Thanks!

[Wrong fix previously set out here - see below.]

---

### Post by lash9420 on 2008-05-29
Alrighty! I'm gonna reboot a couple of times...
Any idea why my system is going extremly slow now? It happened after I did what Zorael suggested. I thought I reinstalled it....

---

### Post by prinknash on 2008-05-29
> **lash9420 said:**
> Alrighty! I'm gonna reboot a couple of times...
Any idea why my system is going extremly slow now? It happened after I did what Zorael suggested. I thought I reinstalled it....

Sorry, lash9420 - that was the wrong fix. (It's the one to 'solve' all the Network Manager error messages that appear on shutdown.)

The one you want is also a System/Administration/Login Window one, but all you need to do is make sure that the "Show Actions Menu" box is ticked in the "Local" screen. 

The one I gave you earlier will do no harm.

p

---

### Post by lash9420 on 2008-05-29
Where is that box? The "Show actions Menu" one

And what should I do about my system going extremely slow?

---

### Post by prinknash on 2008-05-29
> **lash9420 said:**
> Where is that box? The "Show actions Menu" one



On the "Local" screen, towards the bottom.

Don't know why your machine is running slowly, I'm afraid.

p

---

### Post by lash9420 on 2008-05-29
Ahhhh! Yes!! It got my buttons back! Now all I need is for my computer to run at normal speed.

---

### Post by Zorael on 2008-05-30
Well, you could try reinstalling xserver-xgl again, but it confuses me how performance *dropped* by removing it. Then again, perhaps you'd need to make alterations to your /etc/X11/xorg.conf to enable AIGLX for your videocard.

Intel: [http://wiki.compiz-fusion.org/Hardware/Intel](http://wiki.compiz-fusion.org/Hardware/Intel)
ATI: [http://wiki.compiz-fusion.org/ATI%20with%20AIGLX](http://wiki.compiz-fusion.org/ATI%20with%20AIGLX)
Nvidia: [http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA)

For other makes you may just be better off with xserver-xgl.

---

