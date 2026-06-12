---
title: "[SOLVED] SOLUTION: missing /sbin/init causes boot to exit to busybox/initramfs prompt"
date: 2007-06-06
forum: General Help
---

### Post by Co.Sinecure on 2007-06-06
Hi All,

I had an issue today with my edgy install at work. After being up for several days (meaning, I'm not certain what could have cause it), and restarting this morning, I found that I could not boot into Ubuntu properly, and instead was presented with the busybox prompt ('[FONT="Courier New"]/bin/sh: Can't access tty; job control turned off[/FONT]' etc).

After trying other kernel versions (only had one other), the safe mode/repair mode boots contained the line '[FONT="Courier New"]target filesystem doesn't have /sbin/init[/FONT]'

I searched these forums for a clue, but most of the related issues were to do with a live CD, or mismatch of hdd ids between fstab and menu.lst. My install has been up and running for at least 6 months.](*,)

I got hold of a 6.0.6 live cd and was able to startup in that, mounted my ubuntu disk, and verified that the [FONT="Courier New"]/sbin/init[/FONT] was indeed missing from my installation!
I had basically resolved to reinstall overnight (and use windows in the meantime :-( ), and had nothing to loose (backed up everything..), so I simply copied over the init file from the CD to my install (I suspected that it may not work, different versions etc). but **it worked!** :cool: So now I'm able to boot into Ubuntu again, but there are other sbin files missing (like shutdown ..err).

Now, the issues I have remaining: 
:arrow: I have no shutdown script. I can probably survive, but does anyone know if its possible to rebuild the sbin directory?
:arrow: my /sbin/init may be out of date, and I have no idea if there are any incompatibilities. I looked in synaptic to anything relating to 'sbin'. I found *sysvinit* and *upstart* that both replace init. Can anyone tell me if I should be concerned about installing one of them?

I hope these bits of information might help others... :D

---

### Post by Marcolin on 2008-03-16
I also got the target filesystem doesn't have /sbin/init error.

I tried what you said and got my system up and running again. Did you ever notice any negative side effects?

I actually took it a step further... I noticed that my sbin directory was missing 20 files, so i copied them all. I haven't noticed anything bad yet.

---

