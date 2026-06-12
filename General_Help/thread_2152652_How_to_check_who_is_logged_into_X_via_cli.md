---
title: "How to check who is logged into X via cli"
date: 2013-06-08
forum: General Help
---

### Post by apollothethird on 2013-06-08
Can someone tell me how to tell who is logged in to X via a terminal command line?

At present I use this:

```

ps h -fC gnome-session | awk '{print $1}'

```

However this commandline is assuming that the person is using gnome-session for the environment (which is currently being used by Ubuntu 13.04).

Is there a more efficient method that might work even if a person is using a different login manager?

Thanks in advance for any comments on this.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

