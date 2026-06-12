---
title: "Manually edit filters in evolution"
date: 2008-04-08
forum: General Help
---

### Post by kpsmith on 2008-04-08
I've been having issues with evolution in that I want it to pipe my e-mail out to clam av for some mail scanning however using the latest version in hardy or previous version in gutsy the pipe to filter doesn't let you specify options i.e -e dev null etc after the program selection however I've heard there is a way to manually edit the filters xml file to add these bits in to make the filters work properly e.g for spam assassain and clam av. 

I've tried to find said file but can't does anyone know where it will be lurking?

---

### Post by ramjet_1953 on 2008-04-08
This link may be of use to you:

[http://www.novell.com/documentation/evolution24/index.html?page=/documentation/evolution24/evolution24/data/usage-mail-organize-filters.html](http://www.novell.com/documentation/evolution24/index.html?page=/documentation/evolution24/evolution24/data/usage-mail-organize-filters.html)

---

### Post by kpsmith on 2008-04-08
cheers for that, usefull document will certainly help out with certain aspects but doesn't get round the issue that although you can spec which program you want to pipe the e-mail to and what you want it to do based on the return value you still can't put any optional commands on for the program you pipe the mail to.

---

### Post by dcstar on 2008-04-08
> **kpsmith said:**
> cheers for that, usefull document will certainly help out with certain aspects but doesn't get round the issue that although you can spec which program you want to pipe the e-mail to and what you want it to do based on the return value you still can't put any optional commands on for the program you pipe the mail to.

You don't need to, you pipe to a script with whatever you want in it.

Evolution will just pipe the body of the e-mail, anything else is up to you.

Here is the code I use to scan my e-mails for viruses with ClamAV:

```
#!/bin/bash
# Fred Blaise <chapeaurouge AT madpenguin DOT org>
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston,
# MA 02111-1307 USA

FILE=/tmp/$$_outclam.tmp
clamdscan - 1>$FILE

if [ $? -eq 1 ]; then
STRING=$(grep "FOUND" $FILE |cut -d: -f2)
zenity --warning --title="Evolution: Virus detected" --text="$STRING" &

exit 1
fi

exit 0
```

The attached screenshot is the Evolution filter that calls it.

---

### Post by kpsmith on 2008-04-09
ahh I see now, that makes sense, i'll do it that way then saves alot of messing about. Slowly getting to grips with customising stuff in Ubuntu.

---

