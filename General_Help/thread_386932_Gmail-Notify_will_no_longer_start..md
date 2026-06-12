---
title: "Gmail-Notify will no longer start."
date: 2007-03-17
forum: General Help
---

### Post by ScottRosier on 2007-03-17
I installed Gmail-Notify perhaps a month ago, and it's been working fine, and I got it to start up when Ubuntu starts. Recently, maybe about a week ago, it stopped starting up; it won't even run from the Applications->Internet menu.

This is my first post on these forums, so I may be lacking necessary information in this post, but if anyone could help me get this up and running again it'd be greatly appreciated. If I need to supply any more information, I'll do so ASAP.

Thanks in advance.

---

### Post by xopher on 2007-03-18
Maybe it's configuration file is corrupted or something, try killing it, then running it. If that doesn't help, try completely removing it, and the reinstalling.

```
sudo apt-get remove --purge *packagename*
```

---

### Post by ScottRosier on 2007-03-18
No dice, still won't come up. I checked the processes running and gmail-notify isn't in there, if that helps at all.

---

### Post by ScottRosier on 2007-03-24
Oh wow, I finally got smart and tried to run it in terminal; turns out I had an issue with GTK. I had to edit the first line of the script from "#!/usr/bin/env python" to "#!/usr/bin/env python2.4".

---

