---
title: "Wanting to report a big bug, but no idea where to start"
date: 2013-03-09
forum: General Help
---

### Post by pouzzler on 2013-03-09
Hello,
I am using i3wm on an Asus ux31a computer, under Ubuntu 12.10. At one point, my computer refused to boot normally, either telling me I could proceed in low graphics mode, or showing a fully black screen, sometimes with the mouse pointer, sometimes not.

This bug is experienced by many people, and possible solutions are found here: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1066410](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1066410) .

I found the solution of replacing lightdm by gdm, and have not had a problem since. However, while I was affected by this bug, and hadn't found a real solution, I used to switch to tty1, kill xorg, upon which I would instantly find myself on lightdm's login screen, and everything would work.

What I didn't know until an IRC friend told me, is that *everything I typed in tty1* was mirrored in the topmost window of tty7 which happened to be Opera on my regular IRC channel. I am absolutely certain I make no mistake on this, I didn't do some stupid cut & paste, my friend saw each line I typed in tty1 as exactly one line of irc chat, precluding the cut & paste scenario, unless I did about five of these in a row unwittingly.

Therefore, every person on the irc channel was treated to my ps | grep, my sudo kill -9... and my password.

That's a pretty big security problem, however I have no idea who I should report this to, nor how to determine this. Does anyone know of steps I could take to identify a specific component as the likely culprit?

i3 windows manager
lightdm
opera 12
kernel  3.7.1-030701-generic
(something that I don't know that manages the) ttys
other

Having your password in clear in any window you didn't intend to type it in is a pretty major problem, only I have no idea who to report it to. Thank you for any help you can provide, and

best regards,
Sébastien

---

### Post by schragge on 2013-03-09
Very strange, indeed. TBH, I have not the slightest idea. Do you have some acessibility software enabled? Could you inadvertently run [open]("http://manpages.ubuntu.com/manpages/precise/en/man1/openvt.1.html") on the console? Do you also use some command line IRC client like [ii]("http://manpages.ubuntu.com/manpages/precise/en/man1/ii.1.html")? Or an IRC proxy like [nadoka]("http://manpages.ubuntu.com/manpages/precise/en/man1/nadoka.1.html")? [cnee](http://manpages.ubuntu.com/manpages/precise/en/man1/cnee.1.html)/[xnee](http://manpages.ubuntu.com/manpages/precise/en/man1/xnee.1.html)? Another wild guess: maybe some weird [uwiki]Plymouth[/uwiki] issue? Would you still experience this if setting *GRUB_GFXPAYLOAD_LINUX=text* in */etc/default/grub*, then ```
sudo update-grub
``` and reboot?

Or, even more radical, by renaming the plymouth upstart script
```
sudo mv /etc/init/plymouth.conf{,.disabled}
```

If Plymouth is not guilty, rename it back afterwards:
```
sudo mv /etc/init/plymouth.conf{.disabled,}
```

---

### Post by pouzzler on 2013-03-11
Hello,
thank you for your answer, which I saw you edited and bettered several times. I have absolutely no time to reinstall the malfunctionning DM, and harness a friend's help to help me diagnose if they still see my tty1 in tty7's IRC, but I most certainly shall as soon as I can, and will of course keep you posted here.

Best regards,
Sébastien

---

