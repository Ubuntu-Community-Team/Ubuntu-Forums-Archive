---
title: "synergy to ubuntu Heron firefox lag"
date: 2008-05-01
forum: General Help
---

### Post by kayakpete on 2008-05-01
Greetings

I am running ubuntu Heron on my right desktop with synergy.  If I start up firefox (2 or 3) as the regular user, I get horrible lag of the mouse on page load.  top does not show cpu max.  firefox2 and 3 both do this.

If I run firefox as root, I do not have a problem.

If I use the ubuntu workstation mouse, I do not have the problem.

Or to reword: synergy is horribly disrupted by firefox running as a regular user.  Not when run as sudo.

Almost sounds like a permissions problem to me?

Anyone have this problem and figure it out?

Thanks!

---

### Post by dro0g on 2008-05-05
> **kayakpete said:**
> Greetings

I am running ubuntu Heron on my right desktop with synergy.  If I start up firefox (2 or 3) as the regular user, I get horrible lag of the mouse on page load.  top does not show cpu max.  firefox2 and 3 both do this.

If I run firefox as root, I do not have a problem.

If I use the ubuntu workstation mouse, I do not have the problem.

Or to reword: synergy is horribly disrupted by firefox running as a regular user.  Not when run as sudo.

Almost sounds like a permissions problem to me?

Anyone have this problem and figure it out?

Thanks!

I reniced the process per this post [http://ubuntuforums.org/showthread.php?t=767236&highlight=synergy](http://ubuntuforums.org/showthread.php?t=767236&highlight=synergy) and everything's working great now.

---

### Post by kayakpete on 2008-05-05
> **dro0g said:**
> I reniced the process per this post [http://ubuntuforums.org/showthread.php?t=767236&highlight=synergy](http://ubuntuforums.org/showthread.php?t=767236&highlight=synergy) and everything's working great now.

Good catch, dro0g!  Thanks.  That works fine for me as well.

---

