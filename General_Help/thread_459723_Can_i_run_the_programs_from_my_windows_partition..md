---
title: "Can i run the programs from my windows partition."
date: 2007-05-31
forum: General Help
---

### Post by reggierabbit on 2007-05-31
Im dual booting Kubuntu and windows xp, and i don't want to change OS, just to run one of the programs ive already installed. is there anyway of running the programs off my windows partition instead of installing them on Kubuntu and emulating them, or can i emulate them straight off the windows partition.

Thanks

---

### Post by meng on 2007-05-31
If using wine to run these programs, you're probably better off installing them again rather than running them off the Windows partition.

---

### Post by reggierabbit on 2007-05-31
That won't work because, ive got 20gb worth of Programs and i don't want to install them all over again, plus ive got all the settings and saves for my games. And, i want to be able to run the programs from windows aswell.

thanks anyway

---

### Post by meng on 2007-05-31
I see - so you're intending to run **any** of the games taking up that 20 GB from Ubuntu? Even so, be aware that wine (or Crossover or Cedega) does not run Windows apps/games perfectly. Look at [www.winehq.com](www.winehq.com) (AppDB) or [www.cedega.com](www.cedega.com) (games list) to find out which ones run best.

You could certainly TRY running the games on your Windows partition:
(from a terminal do this)
wine /path/to/app/on/windowsdrive

e.g., could be
wine /media/windows/Program\ Files/Microsoft/(blahblah)

but I couldn't guarantee that
1) it would work
2) it wouldn't bork your saves or something else nasty

---

### Post by reggierabbit on 2007-05-31
I tried it and it works BUT its as if the programs have just been installed, so no settings, serial numbers or anything installed. Anyway, its close enough, ill just find alterantives for the ones i commonly use and ill use windows when i need to play games or something.

---

