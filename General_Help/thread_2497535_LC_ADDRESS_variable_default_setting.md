---
title: "LC_ADDRESS variable default setting"
date: 2024-05-09
forum: General Help
---

### Post by dragutsan-alexandr on 2024-05-09
Hi there!

I was wondering on how [FONT=&amp]$LC_ADDRESS[/FONT] environment variable was set(default to *uk_UA.UTF-8 )*.

```
 # grep -irl -- lc_addre /etc/etc/ltrace.conf
/etc/default/locale
# grep -ril uk_ua /etc
/etc/default/locale
/etc/locale.gen
```

And that surprised me a bit:
```
# grep -ir uk_ua /etc
/etc/default/locale:LC_NUMERIC=uk_UA.UTF-8
/etc/default/locale:LC_TIME=uk_UA.UTF-8
/etc/default/locale:LC_MONETARY=uk_UA.UTF-8
/etc/default/locale:LC_PAPER=uk_UA.UTF-8
/etc/default/locale:LC_NAME=uk_UA.UTF-8
/etc/default/locale:LC_ADDRESS=uk_UA.UTF-8
/etc/default/locale:LC_TELEPHONE=uk_UA.UTF-8
/etc/default/locale:LC_MEASUREMENT=uk_UA.UTF-8
/etc/default/locale:LC_IDENTIFICATION=uk_UA.UTF-8
/etc/locale.gen:# uk_UA KOI8-U
/etc/locale.gen:uk_UA.UTF-8 UTF-8
```

```
# stat $(grep -ril uk_ua /etc)
  File: /etc/default/locale
  Size: 230           Blocks: 8          IO Block: 4096   regular file
Device: 805h/2053d    Inode: 1442340     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-05-09 08:54:40.732827545 +0300
Modify: 2021-12-21 19:00:56.028681258 +0200
Change: 2021-12-21 19:00:56.028681258 +0200
 Birth: 2021-12-21 19:00:56.024681169 +0200
  File: /etc/locale.gen
  Size: 9454          Blocks: 24         IO Block: 4096   regular file
Device: 805h/2053d    Inode: 1444801     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-05-09 13:20:14.683016470 +0300
Modify: 2024-04-22 01:00:03.862743608 +0300
Change: 2024-04-22 01:00:03.862743608 +0300
 Birth: 2024-04-22 01:00:03.862743608 +0300
```

```
grep -ri -- lc_addre /etc/etc/ltrace.conf:string setlocale(enum(LC_CTYPE=0, LC_NUMERIC=1, LC_TIME=2, LC_COLLATE=3, LC_MONETARY=4, LC_MESSAGES=5, LC_ALL=6, LC_PAPER=7, LC_NAME=8, LC_ADDRESS=9, LC_TELEPHONE=10, LC_MEASUREMENT=11, LC_IDENTIFICATION=12), string);
/etc/default/locale:LC_ADDRESS=*uk_UA.UTF-8*

```

Now I'm curious about the following, can you please bring me an idea on:

1) Why 2.35-0ubuntu3.7 triggered update on ***/etc/locale.gen ***file? (Birth: 2024-04-22 01:00)
Looking at apt log:
```
3429 Setting up locales (2.35-0ubuntu3.7) ...^M
3430 Generating locales (this might take a while)...^M
3431   en_AG.UTF-8... done^M
3432   en_AU.UTF-8... done^M
3433   en_BW.UTF-8... done^M
3434   en_CA.UTF-8... done^M
3435   en_DK.UTF-8... done^M
3436   en_GB.UTF-8... done^M
3437   en_HK.UTF-8... done^M
3438   en_IE.UTF-8... done^M
3439   en_IL.UTF-8... done^M
3440   en_IN.UTF-8... done^M
3441   en_NG.UTF-8... done^M
3442   en_NZ.UTF-8... done^M
3443   en_PH.UTF-8... done^M
3444   en_SG.UTF-8... done^M
3445   en_US.UTF-8... done^M
3446   en_ZA.UTF-8... done^M
3447   en_ZM.UTF-8... done^M
3448   en_ZW.UTF-8... done^M
3449   ru_RU.UTF-8... done^M
3450   ru_UA.UTF-8... done^M
3451   uk_UA.UTF-8... done^M
3452 Generation complete.^M
3453 Setting up libldap-common (2.5.17+dfsg-0ubuntu0.22.04.1) ...^M
3454 Setting up xxd (2:8.2.3995-1ubuntu2.16) ...^M
3455 Setting up libc6-dbg:amd64 (2.35-0ubuntu3.7) ...^M
3456 Setting up libklibc:amd64 (2.0.10-4ubuntu0.1) ...^M
3457 Setting up mutter-common (42.9-0ubuntu7) ...^M
3458 Setting up linux-headers-6.5.0-28-generic (6.5.0-28.29~22.04.1) ...^M
3459 Setting up libgnutls30:amd64 (3.7.3-4ubuntu1.5) ...^M
3460 Setting up vim-common (2:8.2.3995-1ubuntu2.16) ...^M

```

2) Why it was initially set like that in GNOME default Settings - Regional and Lang - Login Scree - Formats?
 Was it set to UK_UA when I have mistakenly installed additional Ukrainian Language from GNOME Settings?

---

### Post by coffeecat on 2024-05-10
*Thread moved to **General Help**.*

---

