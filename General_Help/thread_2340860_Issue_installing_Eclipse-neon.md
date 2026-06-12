---
title: "Issue installing Eclipse-neon"
date: 2016-10-22
forum: General Help
---

### Post by bingasedu on 2016-10-22
I just installed eclipse-neon and ran into two issues. (I'm running Ubuntu 16.04 LTS.) First, I wanted a system-wide installation of eclipse, but setting the install path to /opt ran into problems with the installer wanting to put some config files under /root. I've had to settle for installation in my home directory. Second, although I added $HOME/eclipse/cpp-neon/eclipse to my PATH in .profile, the command "eclipse" still runs the ancient version on eclipse in /usr/bin. For some reason my .profile isn't being read, even though there's no .bash_profile present. How can I do a system-wide install of eclipse-neon? Thanks for any help, and my apologies if this is the wrong place for this post.

- Jon

---

### Post by bingasedu on 2016-10-22
Just an update that the .profile issue was simply me forgetting that terminals don't run login shells and therefore don't run .profile on startup. I'm still _very_ interested in how to do a system-wide installation of eclipse-neon.  - Jon

---

