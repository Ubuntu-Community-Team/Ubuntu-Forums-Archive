---
title: "Package manager and &quot;custom installed&quot; packages"
date: 2007-06-16
forum: General Help
---

### Post by Ruskie on 2007-06-16
Hello,

A couple of days ago aMSN told me a new version was available, and since it has a feature I wanted I decided to install it. Unfortunately Dapper repository hasn't got that version, so I can't use Synaptic to upgrade.
I could download the package from the internet and manually install it, but I wonder: what happens to the automatic management granted by Synaptic? Would that be screwed up if I install a package that he does not has in repository? And if I install a program which is not supplied in form of package??

Thanks
Marco

---

### Post by avik on 2007-06-16
If you install manually, that application won't be picked by the APT package manager.  That's all.  Nothing else will happen.

If you're installing a .deb file that's not in the repositories, then it'll be picked up by APT, but it won't find any updates for it.

There are plenty of programs people install manually.  It's no big deal.

---

### Post by Ruskie on 2007-06-18
Thanks for the answer.
Yeah, I've installed a lot of programs manually in the past and with other (generally rpm based) distributions. I do know it's no big deal.

Instead, it would have been a big deal if package manager was in some way able to understood when a new version is installed. But ok, we can live with that.

---

### Post by mcduck on 2007-06-18
> **Ruskie said:**
> Thanks for the answer.
Yeah, I've installed a lot of programs manually in the past and with other (generally rpm based) distributions. I do know it's no big deal.

Instead, it would have been a big deal if package manager was in some way able to understood when a new version is installed. But ok, we can live with that.

As long as you install using .deb packages the package management will know that you have installed a new version. And you would get updates also, if there would be any (most likely there won't).

If you install new software in any other way than using .deb packages then package mangement won't know about it.

---

