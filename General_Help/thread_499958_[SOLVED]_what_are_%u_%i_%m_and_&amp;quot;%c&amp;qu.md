---
title: "[SOLVED] what are %u %i %m and &amp;quot;%c&amp;quot; ?"
date: 2007-07-13
forum: General Help
---

### Post by undecidable on 2007-07-13
I have noticed that many commands in the Ubuntu and Kubuntu menus have some or all of the following parameters:
%u %i %m "%c"

eg the entry in the menu to start Firefox is
Firefox %u

Now I know what the command line parameters for firefox are,
and %u is not one of them.

So who interprets %u, %i %m and "%c",
and what values are assigned?

Searched everwhere I can think of and can't find anything. 

thanks

---

### Post by lisati on 2007-07-13
I recall seeing a post a week or so back about firefox trying to load a web address [www.%u.com](www.%u.com) - I can't remember where exactly it was, but it turned out that the launcer had put in the command "firefox %u" or something.......

anyone?

---

### Post by undecidable on 2007-07-13
If you try to launch:
firefox %u
from the run command, you will get that behaviour.
It is interpreting %u as a pure url, as specified in the firefox startup params, see:
[http://kb.mozillazine.org/Command_line_arguments](http://kb.mozillazine.org/Command_line_arguments)

However if you use:
firefox "%u"
it seems to work the same as  when run from the menu,
ie something is preprocessing %u and putting something in there
which of course is then passed to firefox as a command line param.

so the question remains:
who interprets %u  (and %i %m and "%c")
and what values are assigned?

---

### Post by kerry_s on 2007-07-13
My guess is gnome is putting it, most likely for drag & drop support. for example you drop a html on the firefox icon it will open with it. there a similar setting for rox("$@") that also supports drag & drop, with out it, it does nothing. i'm sure the others do something similar, there called macros.

---

### Post by undecidable on 2007-07-13
Thanks for the ideas.   May not be gnome, as the params are also in kubuntu/kde,
so either they are general to linux or to (k)ubuntu.
(I haven't used any other Linux distro, so can't say)

The screenshot you provided seems specific to emelfm, though the concept is likely to be the same - giving the started program access to some environment or startup parameters, some set for example (as you say) by a drag and drop.

The menu entry for kopete starts it with "%c" %i %m %u
firefox just with %u, thunderbird with nothing, openoffice with %U
kpdf with %U %i %m -caption "%c"
etc etc.

Now if we could just find a similar list for whoever is interpreting these params.  Certainly &u, %i etc don't apear in bash.



.

---

### Post by undecidable on 2007-09-25
At last, stumbled upon the answer to this question from July, for anyone else who may have wondered:

[http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html)

It was referred to in the kde tutorial for creating service menus:

[http://developer.kde.org/documentation/tutorials/dot/servicemenus.html](http://developer.kde.org/documentation/tutorials/dot/servicemenus.html)

Hope this helps some other soul.

---

