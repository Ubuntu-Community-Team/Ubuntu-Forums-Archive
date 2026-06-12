---
title: "Vuze-vs crashes"
date: 2019-04-29
forum: General Help
---

### Post by yoramdavid on 2019-04-29
Hi,
I have Vuze-vs installed, every time I launch it it comes with an error message:
"The folder "/snap/vuze-vs/3/opt/vuze" is not writable.

I tried to [HTML]sudo chmod 775 -Rv /snap/vuze-vs/3/opt/vuze[/HTML]
No luck.

I purge vuze-vs, delted the snap folder and reinstalled, still no luck. The snap folder is created but the same error comes up again.

Any help would be appreciated.
Thank you.
David.

---

### Post by casey4 on 2019-05-03
I am having the same issue, and received the error message again after applying the fixes mentioned above. Now it no longer displays the "[COLOR=#000000]The folder "/snap/vuze-vs/3/opt/vuze" is not writable."[/COLOR] message but instead freezes on "initializing core" dialogue. I am using Xubuntu 18.04.

---

### Post by Holger_Gehrke on 2019-05-03
The directories '/snap/<package-name>/<version-number>/' are used as mount points for the read-only compressed filesystem images which sit at the core of every snap-package. If a program installed as a snap tries to write there then the person who packaged the program has not done his job right.

Holger

---

### Post by casey4 on 2019-05-03
Uninstalled the snap package and reinstalled manually using [tar.bz2 file]("https://www.vuze.com/download.php"). No more error message but still having issues with freezing on speed test and other dialogues.

---

