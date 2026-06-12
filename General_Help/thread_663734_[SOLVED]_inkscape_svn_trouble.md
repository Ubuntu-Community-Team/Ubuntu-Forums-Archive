---
title: "[SOLVED] inkscape svn trouble"
date: 2008-01-10
forum: General Help
---

### Post by sloggerkhan on 2008-01-10
I'm trying to install inkscape from SVN. ([http://www.inkscape.org/svn.php?lang=en](http://www.inkscape.org/svn.php?lang=en) )

I am not 100% if ./configure is working correctly because it has a lot of lines of 
```

config.status: creating share/gradients/Makefile
sed: -e expression #1, char 339: unknown option to `s'

```
for different dirs.

It does end with 
```

Configuration:

        Source code location:     .
        Destination path prefix:  /usr/local
        Compiler:                 g++
        CPPFLAGS:                 
        CXXFLAGS:                 -Wall -Wformat-security -W -Wpointer-arith -Wcast-align -Wsign-compare -Woverloaded-virtual -Wswitch -D_FORTIFY_SOURCE=2 -Wno-unused-parameter -g -O2
        CFLAGS:                   -Wall -Wformat-security -W -D_FORTIFY_SOURCE=2 -Wno-pointer-sign -g -O2
        LDFLAGS:                  

        Use Xft font database:    yes
        Use gnome-vfs:            yes
        Use openoffice files:     yes
        Use MMX optimizations:    yes
        Use relocation support:   no
        Internal Python:          skipped
        Internal Perl:            skipped
        Enable LittleCms:         yes
        Enable Inkboard:          no
        Enable SSL in Inkboard:   no
        Enable Poppler-Cairo:     yes
        ImageMagick Magick++:     yes
        Libwpg:                   yes

```

whick seemed okay, I don't want to use inkboard.

but make does:
```

redice@opbox:~/source_&_beta/inkscape$ make
make: *** No targets.  Stop.

```

So I'm kinda lost.

I'm trying to install so I can see if a bug from the  Inkscape 0.46~svn20080104 for Gutsy from the Inkscape website is there or not.

---

### Post by sloggerkhan on 2008-01-10
They aren't using bazaar now that they're on launchpad, are they?

---

### Post by sloggerkhan on 2008-01-10
I solved this problem.
The issue is that I have been keeping source folders, precompiled binaries, and svn checkouts and such in :
~/source_&_binary/
and something in the build tools or compile script would trip up on the '&' char in the directory name.

So from now on I will not be using '&' in folder names.
Now what I'm wondering is that's a total newb thing, or if it shouldn't have caused an issue.

---

