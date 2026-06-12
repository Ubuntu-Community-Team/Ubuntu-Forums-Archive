---
title: "Font rendering - infinality patches"
date: 2013-03-22
forum: General Help
---

### Post by dias75 on 2013-03-22
There is a PPA  [https://launchpad.net/~no1wantdthisname/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Eno1wantdthisname/+archive/ppa?field.series_filter=")  with patches Infinality &#1086;n freetype and cairo for 11.04  11.10  12.04  12.10  13.04
But the updates are done only 12.10 and  13.04
At 12.10 and 13.04 patches imposed only on freetype 

I want to update the packages.
How to impose these patches ?
+ I want to apply a patch to Cairo at 12.10 and 13.04

[There is  ]("http://www.infinality.net/forum/viewtopic.php?f=2&t=77#p794")**[How to Enable Infinality Font Rendering]("http://www.infinality.net/forum/viewtopic.php?f=2&t=77#p794")**

But can not I to apply it. I get an error.  

Can anyone will make a detailed how - to ?

PLEASE !

---

### Post by no1wantdthisname on 2013-03-23
Patching freetype:
```

mkdir /tmp/workspace/
cd /tmp/workspace/
apt-get source freetype
cd freetype-*/

cp /tmp/somewhere/*infinality*.patch debian/patches-freetype/

nano debian/patches-freetype/series
# Remove enable-subpixel-rendering.patch
# Add freetype-enable-subpixel-hinting-infinality-*.patch -iN
# Add freetype-entire-infinality-patchset-*.patch

nano debian/rules
# Comment out "export DEB_CFLAGS_MAINT_APPEND := -Werror"

dpkg-gensymbols -pfreetype6 -Odebian/libfreetype6.symbols

export DEBFULLNAME="John Doe"
export DEBEMAIL="foo@bar.com"
dch -i
# change version add notes

debuild -S -sd

cd ..

dput my-ppa *changes

```

---

### Post by dias75 on 2013-03-23
Thank you very much !
How to patch cairo ? 
Could you please write it ? PLEASE !

---

