---
title: "can't install plugins for pidgin 2.4.1 in Hardy Heron (8.0.4)"
date: 2008-06-26
forum: General Help
---

### Post by kedmond on 2008-06-26
Hey guys,
    I've been using Ubuntu since 7.0.4.  I upgraded from 7.10 to 8.0.4 recently.  I am using Pidgin 2.4.1 that came with the upgrade.  I used to have many plugins installed, but now I have 9 installed, none of which I need.  Plus, I'm totally unable to install new plugins.  I went to Synaptic and installed the plugin-pack and have followed different how-tos online.  I don't know why plugins aren't showing up for me.

I really just want to install the history or enhanced history plugins.  Thanks.

-Kazem

---

### Post by kedmond on 2008-06-26
I just figured out the problem.  The default plugins were all installed in /usr/local/lib/purple-2/ but synaptic was installing them in /usr/lib/pidgin/

I just did a change of permissions of the plugin files (chmod 744) and cp'ed all of them to /usr/local/lib/purple-2/

Hope that helps anyone else who has this problem.

-Kazem

---

### Post by UAA on 2008-09-24
Yes, thanks it helped. some one should file a bug.

---

