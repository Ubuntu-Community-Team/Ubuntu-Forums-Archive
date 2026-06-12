---
title: "UDF Files"
date: 2007-01-22
forum: General Help
---

### Post by GONZO29 on 2007-01-22
I am new to Ubuntu having just installed 6.10.

I have several data CDs formatted using Nero's InCD under Windows XP and I need to access and edit them.

Can anyone tell me which programme I should use (obtain) in order to read and write UDF files please.

Many thanks

---

### Post by paparucino on 2007-01-22
> **GONZO29 said:**
> I am new to Ubuntu having just installed 6.10.

I have several data CDs formatted using Nero's InCD under Windows XP and I need to access and edit them.
Can anyone tell me which programme I should use (obtain) in order to read and write UDF files please.


Check if in your ** /etc/fstab** if you have something like this

```

/dev/scd0 /media/dvdrw [COLOR="Red"]udf[/COLOR],iso9660 user,noauto 0 0

```

If OK you can use all programs you prefer.
if NOT OK, I'm not really sure, I think you must recompile ypur kernel enabling the UDF module

---

### Post by GONZO29 on 2007-01-22
PAPARUCINO,

OK many thanks for that I'll give it a try

---

