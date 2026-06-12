---
title: "How show months/dates/ weeks labels not in native language ?"
date: 2020-09-27
forum: General Help
---

### Post by petrogromovo on 2020-09-27
Hello,
Under Kubuntu 18 I set my regions settins [https://prnt.sc/uon173](https://prnt.sc/uon173)
and with it all all months/dates/ weeks labels are in ukrainian language,
but I need to have them english.

How can I do it?

Thanks!

---

### Post by SeijiSensei on 2020-09-27
On my 20.04 machine I would go to System Settings > Regional Settings > Formats.  Check the "Detailed Settings" box and pick an English version for the date.

---

### Post by &amp;wP*!) on 2020-09-27
On command line look at the environment variables by
```
env | grep LC
```
For more information [https://www.thomas-krenn.com/en/wiki/Configure_Locales_in_Ubuntu](https://www.thomas-krenn.com/en/wiki/Configure_Locales_in_Ubuntu)

---

