---
title: "Restrict access to applications"
date: 2007-07-03
forum: General Help
---

### Post by thebrotherofasis on 2007-07-03
Hello, 

Is there any way that I can restrict access to a certain user on running a specific application?

For example, if I want some user not to be able to use "Gaim Internet Messenger", is it possible for me to forbid his access to this program, or for example set an access password?

Thank you.

---

### Post by kuja on 2007-07-05
The way I would go about that would be to create a new group. Lets say we call the group gaim. Add users who are allowed to access it to the group gaim.

Now, run chgrp gaim /usr/bin/gaim to change the group it belongs to.
Next run chmod 750 /usr/bin/gaim

It should now only be executable by people in the gaim group (or root).

---

### Post by hikaricore on 2007-07-05
If you need a more advanced permissions system this thread has some info:

[http://ubuntuforums.org/showthread.php?t=480218](http://ubuntuforums.org/showthread.php?t=480218)

And some old links I posted:

[http://ubuntuforums.org/showpost.php?p=2338952&postcount=3](http://ubuntuforums.org/showpost.php?p=2338952&postcount=3)

---

