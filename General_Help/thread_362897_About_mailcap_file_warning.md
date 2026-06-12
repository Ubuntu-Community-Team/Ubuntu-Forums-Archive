---
title: "About mailcap file warning"
date: 2007-02-16
forum: General Help
---

### Post by frankabel on 2007-02-16
Hi all!

Each time that I start pgAdmin II I get the following warning:

"Mailcap file /etc/mailcap, line 63: incomplete entry ignored."

When I look on that file at the line 63 appear the following:

line 63: "application/x-sc"
line 64: "gnumeric '%s'; edit=gnumeric '%s'; description="SC/XSpread spreadsheet";....."

All seem that is true, the mailcap line 63 is incomplete, but I never had touch that file so what can be that? What can I make to repair that file? Can anybody showme his mailcap file line 63?

Thanks in advance

Salute
Frank Abel

---

### Post by JamieC on 2007-02-16
Merge the two lines to look like this:
```

application/x-sc; gnumeric '%s'; edit=gnumeric '%s'; description="SC/XSpread spreadsheet"; test=test -n "$DISPLAY"; nametemplate=%s.sc

```

---

### Post by frankabel on 2007-02-16
That work for me... Thanks... can you tell what is the cause of that the mailcap file get bad?

Salute
Frank Abel

---

### Post by parktownprawn on 2007-02-18
I think its a bug with gnumeric:

[https://launchpad.net/ubuntu/+source/gnumeric/+bug/61263](https://launchpad.net/ubuntu/+source/gnumeric/+bug/61263)

---

### Post by frankabel on 2007-02-18
Thanks all.

Salute
Frank Abel

---

### Post by fred the wise on 2007-06-12
I have a problem every time I use Audacity and try to open a file ..it says that in line 99 there's an incomplete entry ignored, and then crashes...

but my line 99 is:   application/x-sc 

how can I fix it?
 thanks_

---

