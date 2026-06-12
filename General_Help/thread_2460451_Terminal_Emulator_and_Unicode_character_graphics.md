---
title: "Terminal Emulator and Unicode character graphics"
date: 2021-04-10
forum: General Help
---

### Post by frrobert on 2021-04-10
Good morning,

I have a Ubuntu 20.04 desktop that will display some Unicode character graphics but not all.  For some characters I get a small rectangle.

I have a Ubuntu 18.04 laptop that will display all Unicode character graphics.

The issue occurs on the 20.04 machine occurs with several terminal emulators and fonts:

For testing I am using XFCE-4 emulator and Ubuntu Mono Regular on both machines.

The locale for both machines is the same and is at the bottom of the post.

My guess is there is some library or package that is missing on on the 20.04 machine.

Any ideas what might be missing?

Thanks.

LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

---

### Post by frrobert on 2021-04-10
Installing either of these fonts fixed the issue Google Noto Color Emoji or EmojiOne Android.

---

