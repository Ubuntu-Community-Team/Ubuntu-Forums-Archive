---
title: "Tooltips barely unreadable in Opera 12.02 on Quantal"
date: 2012-10-29
forum: General Help
---

### Post by bovender on 2012-10-29
Running Opera 12.02 with 12.10 Quantal, tooltips on mouse hover are almost unreadable due to the color scheme.

The tooltip in this screenshot reads "New tab (Ctrl+T)":

[IMG]http://i45.tinypic.com/x1fzw2.png[/IMG]

How do I change the font color of these tooltips?

---

### Post by PaulW2U on 2012-10-29
Are you using the latest build - Opera 12.02.1629?

See [http://my.opera.com/ruario/blog/index.dml/tag/12.02](http://my.opera.com/ruario/blog/index.dml/tag/12.02).

If you're not running the latest build then you should upgrade. If you are then the bug hasn't been fully fixed and needs to be reported.

A work around is to change the toolkit that Opera uses by putting [opera:config#Dialog%20Toolkit]("opera:config#Dialog%20Toolkit") into the address bar and changing the option to 4. After restarting Opera you should find that your tooltips are readable.

I'm afraid I can't test this for you as I use Kubuntu 12.10 and Lubuntu 12.10 where the problem doesn't exist but the work around should provide a temporary fix. Opera won't be themed correctly but it will be fully usable again.

---

### Post by bovender on 2012-10-29
I'm running build 1629.

Not sure though if this is the same issue as described in the blog post and the bug report referenced therein. I'll report it.

Thanks for pointing out the toolkit option. It's less pretty now, but at least I can read the information.

---

### Post by PaulW2U on 2012-10-29
> **lazy_leukocyte said:**
> I'm running build 1629.

Not sure though if this is the same issue as described in the blog post and the bug report referenced therein. I'll report it.

Thanks for pointing out the toolkit option. It's less pretty now, but at least I can read the information.

Glad to have helped. 

I was running Ubuntu 12.10 for a while and ran into the same problem but wasn't sure exactly what had been fixed in the latest build of Opera 12.02.

---

