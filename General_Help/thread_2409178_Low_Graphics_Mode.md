---
title: "Low Graphics Mode"
date: 2018-12-28
forum: General Help
---

### Post by 64mgb on 2018-12-28
Lately (the last couple of months) I have been getting this one or two time per week
[ATTACH=CONFIG]282032[/ATTACH]
I don't know for sure, but my guess is that this started happening after the 18.10 upgrade.  The only way I've found to resolve it is to reboot.  I've seen sites that recommend reinstalling GDM or some such thing, but that fixes nothing.  I've not been able to isolate any actions that cause the problem, and absolutely NOTHING has changed with my hardware setup.  This doesn't happen on startup, as some people have reported.  This happens when my system is running.  Any idea what causes this and how I can fix it?

Thanks!

Rich

---

### Post by jefrin on 2018-12-31
You need to update your graphic resolution mainly all the current system upgraded by new generation,Update the OS also .

---

### Post by Autodave on 2018-12-31
I have found that upgrading versions generally does not work well, if at all.  I only do clean installs and I stick with the LTS releases only.

---

### Post by clementc on 2019-01-01
Hi Rich,

In addition to what [**jefrin**]("https://ubuntuforums.org/member.php?u=2114587") and [**Autodave**]("https://ubuntuforums.org/member.php?u=917298") have mentioned, I think that a good start would be to check your RAM to make sure it is not faulty.

Please follow the instructions listed on [this page]("https://help.ubuntu.com/community/MemoryTest") and report back the result.

---

### Post by NM5TF on 2019-01-01
@64mgb....we need more information....

please post the output of 

```
inxi -G
```

also post the output of

```
xrandr
```

tommy

---

