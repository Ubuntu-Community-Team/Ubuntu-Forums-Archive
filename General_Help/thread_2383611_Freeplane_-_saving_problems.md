---
title: "Freeplane - saving problems"
date: 2018-01-27
forum: General Help
---

### Post by sterator on 2018-01-27
I recently installed mind mapping software Freeplane using the terminal. The installation went fine, software runs fine, but when I try to save a file, it constrains me to the /usr directory with no option to save in another location, such as in my documents where it’ll be backed up.

 I don’t see anything in prefs that gives control over the save-to destination.

hoping someone here who uses Freeplane can offer insight.

thank you!

---

### Post by cruzer001 on 2018-01-27
You could use a simple backup tool like grsync.

[https://help.ubuntu.com/community/rsync#Grsync](https://help.ubuntu.com/community/rsync#Grsync)

---

### Post by sterator on 2018-01-27
> **cruzer001 said:**
> You could use a simple backup tool like grsync.

[https://help.ubuntu.com/community/rsync#Grsync](https://help.ubuntu.com/community/rsync#Grsync)

Thank you.. I am using rsync, but I keep my to-be-backed up files in Documents because that makes sense to me.

could there be something about a program such that it doesn’t “like” to save documents where thenuser wants them? ...or that a program would be programmed to save files it creates in /usr?

neither of those make sense to me.

---

### Post by Impavidus on 2018-01-28
No program should ever save user files in /usr. /usr is meant to install user programs (as opposed to OS programs and some system admin tools), along with their data and settings. Only root has permission to write there and something like Freeplane should never be run with root permission (it's based on Java...), so it can't even save files in /usr. Not all applications allow the user to save files where they want, but they should always save files in the user's home directory.

I don't use Freeplane myself, so haven't tested it.

---

### Post by sterator on 2018-01-28
thank you. two questions come to mind:

[LIST=1]
[*]why would such an app with this incorrect behavior be allowed in the ubuntu repository, and
[*]have I comprised my system by installing it?
[/LIST]

sounds like I should un-install it immediately, assuming that can be done harmlessly.

---

### Post by Impavidus on 2018-01-28
It's in the repositories, so I assume it's reasonably safe. But there must be a way to make it save files in your home directory (/home/username/something/...). Maybe it's not very obvious and you missed it. When you try to save something in /usr, it should give an error.

You have not compromised your system simply by installing this, I've enough confidence in Canonical's quality control for that. Java doesn't have a particularly good security track record and it's a vector for malware that attacks both Windows and Linux, so if you don't need it, don't install, but it's not so bad that it should be avoided at all cost.

---

### Post by lianmovie on 2018-01-28
[COLOR=#000000]Check the folder[/COLOR][[COLOR=#000000].[/COLOR]]("http://lianmovie.com/")[COLOR=#000000]s access level[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by sterator on 2018-01-28
i&#8217;ve had fails and successes when saving.

ill look again in the prefs but i don&#8217;t think there&#8217;s anything offering control over the save path

---

### Post by sterator on 2018-01-28
> **lianmovie said:**
> [COLOR=#000000]Check the folder[/COLOR][[COLOR=#000000].[/COLOR]]("http://lianmovie.com/")[COLOR=#000000]s access level[/COLOR][COLOR=#000000]
[/COLOR]

can you please explain what this means?

---

