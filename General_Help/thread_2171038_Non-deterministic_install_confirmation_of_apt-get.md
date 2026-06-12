---
title: "Non-deterministic install confirmation of apt-get"
date: 2013-08-28
forum: General Help
---

### Post by vdeepakkumar on 2013-08-28
I see that apt-get install sometimes ask for 'press y to confirm' after displaying amount of disk space used. But sometimes it just displays the message and goes further without waiting. Is it some minimum size condition that is checked by it?

An example of install-without-wait is below:

[IMG]https://my.bitcasa.com/download-send/726b0e9c520dd1b0d2a46447cc258c09fb2175ed7619c100f2f2bb1d50a5b8ff/36c3dade0968be987ff7ddaaa05a9f83db2a0792118b73dc0ca2d2ddbe0bcd4e/bash.png[/IMG]

---

### Post by qamelian on 2013-08-28
I think you'll find that apt-get will ask if it's okay to proceed if additional packages need to be installed (or removed) in order to resolve dependencies or conflicts. If there are no additional packages to be added or removed, it should just continue without prompting.

---

