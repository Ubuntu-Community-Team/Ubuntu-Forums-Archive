---
title: "Amarok SVN Install Problems"
date: 2007-04-14
forum: General Help
---

### Post by cubanresourceful on 2007-04-14
I am having problems. I am using the "amarok-svn.sh" script, but it errors out saying I do not have Ruby installed, when in fact, I do. If anyone can help, please do.

I have read guides on to what I need to have pre-installed, and my computer meets all the requirements. I am running Ubuntu Edgy.

If someone can help, or a .deb package already available for the newest SVN version, that would be great. But, I'd rather know how to fix the compile error, so I can always readily get the newest svn version and compile. THANKS!

---

### Post by goldaryn on 2007-04-20
I have used this thread many times to install amarok from SVN.
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=80492&highlight=amarok+svn]("http://ubuntuforums.org/showthread.php?t=80492&highlight=amarok+svn")
[/LIST]

Ensure you have an up-to-date sources.list before you start. Since you are using Edgy:

[LIST]
[*][http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories")
[/LIST]
The power of search!

g.

---

### Post by eatOsha on 2007-05-22
I had the same problem, and I fixed it by installing the ruby1.8-dev package, which I guess contains the necessary ruby header files.  I tried installing ruby1.9 and ruby1.9-dev package, but when you install ruby using the method in the tutorial, i guess ruby1.8 is used by default.  i didn't try removing ruby to see if the script would check for the 1.9 headers instead, so you might want to give that a try also.

---

