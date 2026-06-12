---
title: "[SOLVED] Sound Juicer update dependency problem?"
date: 2007-11-13
forum: General Help
---

### Post by FuturePilot on 2007-11-13
There's an update for Sound Juicer however
```
sound-juicer:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed

```
I take it the new libpango just hasn't been uploaded to the servers yet? Am I the only one seeing this?:confused:

---

### Post by Perpetual on 2007-11-13
I don't have any updates available.  Maybe hasn't hit my repos yet.

---

### Post by zaomaster on 2007-11-13
> **FuturePilot said:**
> There's an update for Sound Juicer however
```
sound-juicer:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed

```
I take it the new libpango just hasn't been uploaded to the servers yet? Am I the only one seeing this?:confused:

yeah, it just hasn't been posted up to your repository yet.  I had the same thing, but then I accessed the repository " deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) sid main " and it upgraded just fine.  (though watch out if you do that because a million other things will say they are 'upgradable' but since they are "unstable" you just never know what might happen)

---

### Post by Perpetual on 2007-11-13
I will just wait for it to come down the normal way.  Sounds like there is no rush anyhow until the dep's are fixed.

---

### Post by posterboy on 2007-11-13
3:41 PM on the east coast, it just solved itself for me, using the us. repos.

---

### Post by FuturePilot on 2007-11-13
Yep, they seem to have fixed it.:guitar:

---

