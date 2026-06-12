---
title: "System settings lost after Ubuntu updates"
date: 2015-05-11
forum: General Help
---

### Post by davidlillie23 on 2015-05-11
I ran ```
[COLOR=#111111][FONT=Consolas]sudo apt-get upgrade[/FONT][/COLOR]
``` and ```
[COLOR=#111111][FONT=Consolas]sudo apt-get upgrade[/FONT][/COLOR]
``` and now my system settings are no longer present.  Attached are all the system settings currently available in the menu.  Any ideas on what happened or how to get my settings back?  Let me know what other info is needed, not sure what would be relevant in this case.  Thanks in advance.

---

### Post by sammiev on 2015-05-11
Hi and Welcome,

Usually folks will use this or update from the software updater.

```
sudo apt-get update
```

and then

```
sudo apt-get upgrade
```

Your also best to post what version and flavor of Ubuntu you are using so the folks can help.

---

### Post by davidlillie23 on 2015-05-11
Sorry about that.

```
3.16.0-37-generic #51~14.04.1-Ubuntu SMP Wed May 6 15:23:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

I ran each of those and still no settings.  I ran dist-upgrade to but no improvement.

---

### Post by sammiev on 2015-05-12
> **davidlillie23 said:**
> Sorry about that.

```
3.16.0-37-generic #51~14.04.1-Ubuntu SMP Wed May 6 15:23:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

I ran each of those and still no settings.  I ran dist-upgrade to but no improvement.

Hi,

Have you tried this yet?

```
sudo apt-get install ubuntu-desktop
```

---

### Post by davidlillie23 on 2015-05-13
> **sammiev said:**
> Hi,

Have you tried this yet?

```
sudo apt-get install ubuntu-desktop
```

That worked perfect, everything's back.  Thanks.  Any ideas on what may have happened?  Im relatively new to Ubuntu and instead of coming to the forums all the time, I'd like to learn what I'm fixing.

---

### Post by sammiev on 2015-05-13
It has happen to me as well on an update not too long a go. Likely a bad update, but my screen looked the very same as yours and not just once.

---

### Post by davidlillie23 on 2015-05-13
If it happens again, I can re-run the previous commands and see if that resolves it.  If it doesn't, that would mean something wrong with the update packages, maybe a bug?  Maybe I'm wrong.  Either way, thanks for the help.  Appreciated.

---

### Post by sammiev on 2015-05-14
> **davidlillie23 said:**
> If it happens again, I can re-run the previous commands and see if that resolves it.  If it doesn't, that would mean something wrong with the update packages, maybe a bug?  Maybe I'm wrong.  Either way, thanks for the help.  Appreciated.

I have many computers and test many flavours. Two of them were running Unity and it happen to both over a few days.

Just once to each and they have been good other wise. Likely you will not see it again.

---

