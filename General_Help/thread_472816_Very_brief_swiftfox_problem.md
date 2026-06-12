---
title: "Very brief swiftfox problem"
date: 2007-06-13
forum: General Help
---

### Post by HIFH on 2007-06-13
It seems like a very easy problem, but I'm no good with problems, so rather than joining swiftfox I'm hoping someone here will know :)

The wee problem is is that when I open Swiftfox, rather than showing my home page it shows file:///home/username. So it shows the directory listing. In preferences, the "When Swiftfox starts" option is set to "homepage". I've looked through the settings and found no reason why SF would open the directory instead of my homepage.

Cheers,

Alex

---

### Post by HIFH on 2007-06-13
Uh, hate it when this happens. The solution pops right in my head a minute after posting.

In the preferred application preference menu, after Swiftfox was selected as the default browser (via the command /usr/lib/swiftfox/firefox), for some reason a "%s" was attached to the end. Deleting this solved the problem.

Sorrysorrysorry for wasting any time :)

---

