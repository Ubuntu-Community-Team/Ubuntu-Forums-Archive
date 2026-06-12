---
title: "Firefox and name lookups..."
date: 2008-03-19
forum: General Help
---

### Post by Replicon on 2008-03-19
I've noticed (not just recently, but with my previous linux installs) that, side-by-side, Firefox in Linux tends to spend a lot more time doing name lookups than FF in Windows. Both my Ubuntu and Windows versions are 2.0.0.12. Is there a cache setting in FF that for some reason is very short in the standard Ubuntu install or something? Almost every time I hit google, I see "looking up google", which is just unnecessary.

I found a similar question in [this](http://ubuntuforums.org/showthread.php?t=13738) thread, but it's from 2005, and I'd think they'd have fixed it by now.

---

### Post by erginemr on 2008-03-19
I cannot utter a direct reply to your question, but can suggest two tricks to circumvent this problem:

1. You can write "google" in Firefox and press Ctrl+Enter to have it add "www." and ".com" automatically. This way, Firefox will not look so long to resolve the DNS address for Google. This trick will work for other sites, too.

2. You can configure your Internet connection to use OpenDNS for supposedly faster DNS lookup. To configure it in Ubuntu, you may refer to:
[http://ubuntuforums.org/showthread.php?t=716601&highlight=opendns](http://ubuntuforums.org/showthread.php?t=716601&highlight=opendns)

---

### Post by Replicon on 2008-03-19
Come to think of it, it's not just FF, but internet connections in general. I'll give opendns a shot :)

---

