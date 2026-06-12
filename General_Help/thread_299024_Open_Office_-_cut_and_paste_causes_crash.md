---
title: "Open Office - cut and paste causes crash"
date: 2006-11-13
forum: General Help
---

### Post by benmoreassynt on 2006-11-13
Has anyone else encountered this problem?

Ubuntu Edgy - a new bug. When trying to cut from Open Office and paste elsewhere (eg Evolution email) or cut from elsewhere and paste into Open Office a crash occurs. The 'Bug report' tool does not come up, but I am able to recover the crashed document.

I have noticed this most in OO Writer, but that may be because it's the one I use most often. I think it happened in Calc as well.

This never happened in Breezy or Dapper. Have no idea where to begin to sort it out. Thanks for any thoughts.

BMA

---

### Post by kh4nh on 2006-11-17
I cut and paste into Firefox and it crashes too.

---

### Post by earobinson on 2006-11-17
same, we should see if its been reported as a but, if not report it

---

### Post by earobinson on 2006-11-17
its a bug [https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/62432](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/62432)

---

### Post by mattskr on 2006-11-17
Add this to your /etc/apt/sources.list

```
deb http://people.ubuntu.com/~doko/ubuntu/ edgy/$(ARCH)/
deb http://people.ubuntu.com/~doko/ubuntu/ edgy/all/
```

Then update, newer packages of openoffice, does not crash for me anymore.

---

