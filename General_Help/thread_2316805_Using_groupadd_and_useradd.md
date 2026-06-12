---
title: "Using groupadd and useradd"
date: 2016-03-11
forum: General Help
---

### Post by ian105 on 2016-03-11
I need to create 3 new groups:
cs
math
science

This I'm pretty sure I can create basic groups. Then I was asked to do the following:

Create 2 new users named “steve” and “lucy” with the following attributes:

[LIST]
[*]default shell is /bin/bash
[*]comment (GECOS) field contains full names (Steve Smith / Lucy Goosey)
[*]steve primary group = math additional group = science
[*]lucy primary group = cs additional group = science
[/LIST]

I'm not sure what Im being asked to do or how to do it.

---

### Post by QIII on 2016-03-11
Has your instructor given you guidance?  When is this assignment due?

---

### Post by ian105 on 2016-03-11
Its not due until Tuesday of next week but there is more to the assignment than just this. Most of the time the instructor has a hands on video that gives us a general idea of how to do it using the commands needed but there wasn't one this time. I can get bit and pieces on the net and youtube but I haven't been able to find anything that helps yet.

---

### Post by steeldriver on 2016-03-11
The manual pages for the useradd command is pretty comprehensive - can you not find what you need there?

If you are permitted, consider using adduser instead - it provides a somewhat higher-level interface

---

### Post by QIII on 2016-03-11
The [Ubuntu Forums Rules]("http://ubuntuforums.org/misc.php?do=showrules") links to the [Posting Guidelines.]("http://ubuntuforums.org/showthread.php?t=2158945")  The latter has this to say:

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.

Closed.

---

