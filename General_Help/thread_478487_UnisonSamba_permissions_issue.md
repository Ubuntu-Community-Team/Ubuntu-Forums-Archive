---
title: "Unison/Samba permissions issue"
date: 2007-06-19
forum: General Help
---

### Post by W. Irving on 2007-06-19
I need to sync the home directories on two machines, one running XP (named Engels) and the other 7.04 (called Trotsky), using Unison (running on Trotsky). I've mounted the Engels share on Trotsky, so I'm basically looking to do a local sync between two dirs.
The problem arises when Samba mounts the Engels share with root as owner and group, which means Unison needs to run as root too, to be able to send files to Engels. Fair enough, I run Unison as root, but did not realise until after the first sync that any file brought over from Engels to Trotsky would retain its permissions. So I now have files in my home dir on Trotsky that are owned by root.

At first I thought of configuring Samba to mount the Engels share not as root, but as my primary user on Trotsky, but that's probably a poor move considering the security implications.
What I want is Unison to properly chown and chgrp any file copied from Engels to Trotsky so that I have access to it without having to sudo. But how?


Solved.
For future generations: share your home dir separately, and use the gid and uid smbmount options to point to your primary user. Results; permissions should look the same in both /home and the mounted home dir. Satisfaction guaranteed.

---

