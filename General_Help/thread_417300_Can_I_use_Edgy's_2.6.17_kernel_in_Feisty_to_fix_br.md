---
title: "Can I use Edgy's 2.6.17 kernel in Feisty to fix broken suspend?"
date: 2007-04-21
forum: General Help
---

### Post by Bastanteroma on 2007-04-21
Suspend doesn't work on my computer using Feisty's kernel, but there are enough improvements that I want to stick with Feisty.

  Would it be possible to briefly change my software sources to add the Edgy repos, install the Edgy kernel, install the Nvidia driver from their site (I don't need any other restricted module), and maybe fix suspend?

---

### Post by skip27 on 2007-04-21
You should be able to boot into the 2.6.17 kernel anyway, without having to mess with Synaptic/apt-get. Just make sure Grub points to one of the old kernels (/boot/grub/menu.lst).

I will tell you this, however: suspend doesn't work on my laptop (Compaq R3120US). Never has, and I'm not sure it ever will. Was suspend working on yours out-of-the-box before you upgraded? Just wondering, since I'd like to get my setup fixed up.

---

### Post by Bastanteroma on 2007-04-21
Suspend worked perfectly in Edgy, but I fresh installed so I don't have the old kernel available.  Also, the old kernel would have the old restricted modules, and so the old nvidia driver, correct?  In which case it wouldn't work with Compiz and Beryl in their default setups.

---

### Post by hardyn on 2007-04-21
what hardware are you using?

I have been able to get my machine to suspend in both edgy and feisty, with some work mind you.

---

### Post by Bastanteroma on 2007-04-21
Suspend broke when I first upgraded from Edgy to Feisty:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83095](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83095)

I've tried playing with VBE options in other cases, but here the computer won't even power down.  I also tried using binary suspend or the usswsusp as a replacement with no success.

---

### Post by hardyn on 2007-04-21
I have resume working on my Asus z71 w/ nvidia (which i think is motherboard identical to a few sonys), by doing the following...

adding VGA=791 to boot string,

and in /etc/default/acpi-support

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

works pretty well... but not at all with compiz or beryl.

good luck.

---

### Post by Bastanteroma on 2007-04-22
I went ahead and installed the old kernel from the Edgy repos, then used Envy to install the Nvidia driver, and now suspend works.

Except that the network is down after resuming, which may be because I have disabled network manager in my session, though I imagine I can fix this by unloading and reloading something, though I don't know how.

Also, running Beryl I restore to a black screen with a cursor, and when I ctrl-alt-backspace I see the desktop for an instant before GDM loads.  Is there a workaround for this too, automatically loading metacity before suspending and reloading Beryl on resume?

---

### Post by hardyn on 2007-04-22
I think that somebody has done something like this... I remember bumping into a script.

somebody on lauchpad was also talking about patching compiz until nvidia get on this, however i understand that this problem has existed in the nvidia driver longer than compiz and beryl have been projects ;S, so it doubtful we will see a fix soon.

good luck.

---

