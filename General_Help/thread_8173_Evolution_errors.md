---
title: "Evolution errors"
date: 2004-12-14
forum: General Help
---

### Post by bob k on 2004-12-14
Iv'e been getting these type of Warnings in my xsessionn-error file. I have Googled the errors and it looks like it is a bug. I would like to know if anybody has tried Tbird on Ubuntu?

Here are the Evolution errors

(evolution-2.0:7993): camel-WARNING **: Invalid root: '/home/bobkirkp/.evolution/mail/local/Drafts.ibex.index'

(evolution-2.0:7993): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution-2.0:7993): camel-WARNING **: block size: 1024 (1024) OK

(evolution-2.0:7993): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution-2.0:7993): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution-2.0:7993): camel-WARNING **: flags: unSYNC
Error: No running window found
auto selected locale: en-US
 load http 0 now=0

(evolution-2.0:8071): camel-WARNING **: Invalid root: '/home/bobkirkp/.evolution/mail/local/Drafts.ibex.index'

(evolution-2.0:8071): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution-2.0:8071): camel-WARNING **: block size: 1024 (1024) OK

(evolution-2.0:8071): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution-2.0:8071): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution-2.0:8071): camel-WARNING **: flags: unSYNC
 load http 0 now=0
Error: No running window found
auto selected locale: en-US

(evolution-2.0:8535): camel-WARNING **: Invalid root: '/home/bobkirkp/.evolution/mail/local/Drafts.ibex.index'

(evolution-2.0:8535): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution-2.0:8535): camel-WARNING **: block size: 1024 (1024) OK

(evolution-2.0:8535): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution-2.0:8535): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution-2.0:8535): camel-WARNING **: flags: unSYNC
requesting object classid: attachment.0x8200cb8.3650.mixed.1
object_found: 1
loading error file /usr/share/evolution/2.0/errors/addressbook-errors.xml
loading error file /usr/share/evolution/2.0/errors/e-system-errors.xml
loading error file /usr/share/evolution/2.0/errors/shell-errors.xml
loading error file /usr/share/evolution/2.0/errors/filter-errors.xml
loading error file /usr/share/evolution/2.0/errors/mail-composer-errors.xml
loading error file /usr/share/evolution/2.0/errors/calendar-errors.xml
loading error file /usr/share/evolution/2.0/errors/mail-errors.xml
Error: No running window found
auto selected locale: en-US



*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
requesting object classid: attachment.0x8200cb8.3650.mixed.1
object_found: 1
looking for type: got text/plain

---

### Post by bob k on 2004-12-21
Ok I have made some headway with these errors.

> (evolution-2.0:7993): camel-WARNING **: Invalid root: '/home/bobkirkp/.evolution/mail/local/Drafts.ibex.index'

(evolution-2.0:7993): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution-2.0:7993): camel-WARNING **: block size: 1024 (1024) OK

(evolution-2.0:7993): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution-2.0:7993): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution-2.0:7993): camel-WARNING **: flags: unSYNC
These errors are exlained in a Debain bug report 280662 bad pointer to an alloc.

> *** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
These errors are from Libsvg and are due to SVG menus or icons. These are considered benign errors and should not effect system operation.

> Error: No running window found
auto selected locale: en-US
I haven't seen a bugzilla on this one but I wouldn't be suprised if it is related to libart or libgtk and the devs know about it. Anyhow it's not crashing anything. I would debug it but all my computers and disk are in use right now and Warty is fixin to go production.

---

### Post by jdong on 2004-12-21
The last one (en-US) is benign, too. It's saying:

1. There's no currently running copy of Evolution. That means I'll launch a fresh copy of the program, as opposed to instructing the current copy to open a new window (or bring focus to the running copy)

2. No locale was specifically chosen for Evolution. I've detected that your system uses en-US as the default locale, so I'll go with that.

---

### Post by Rancoras on 2004-12-21
[QUOTE=bob k] I would like to know if anybody has tried Tbird on Ubuntu?[/QUOTE]

Yup, that's all I use.  I have no need for all the extra features of evolution.  Thunderbird fits my needs perfectly and runs like a charm.

---

### Post by jdong on 2004-12-21
Yep, proud TBird 1.0-0-4.10ubp1 user -- go backports!

---

### Post by bob k on 2004-12-21
I went with Tbird also and use the calender gdesklet thats about all I use other than contacts, and half of them require MS Office files. The last strong holds on my system. some day it will come true.

Any way I traced the errors down to make sure there wern't any problems down the road (if you really wont to know the truth IT WAS FUN).

Bob

---

