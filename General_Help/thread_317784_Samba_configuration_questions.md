---
title: "Samba configuration questions"
date: 2006-12-13
forum: General Help
---

### Post by Mr. Picklesworth on 2006-12-13
I finally got Samba running somehow!

Thanks go out to those people here who take so much effort to help others, and explain things as they do it. I can't remember everyone who did, but it was a great help.
I think my problem was that I didn't know what WINS or that Master Host thingy was. I still don't, but when I had the courage to turn them on and off, things started working.

Anyhow, now that Samba is working I am hoping to get a bit more out of it.

-I have a rather simple home network going here, so security isn't an issue, but it would be nice if I could block writing files to my home folder unless someone logs in, but still have it completely readable otherwise. Is this possible, or must I have it set to only allow logging in or only allow access by anyone?
What I'm hoping to avoid there is how sometimes I'll write files to my home folder from Windows (*sigh*) and end up having them belonging to Nobody.

-Is it possible to tell Samba to simply not tell the other system about hidden files?

Thanks in advance!

---

### Post by tenjin on 2006-12-13
Hi,

Options to try on your homes share:

1. "guest ok" to "false", "browseable" to "true"

2. You could also force the "read list" and "write list" to certain user accounts.

The easiest way to look at this stuff is to install Swat from the repositories. The "advanced" view will show you what you need.

Cheers

D.

---

