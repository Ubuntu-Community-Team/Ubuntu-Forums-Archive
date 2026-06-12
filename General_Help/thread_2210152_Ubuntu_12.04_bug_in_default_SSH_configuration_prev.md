---
title: "Ubuntu 12.04 bug in default SSH configuration preventing X11 Forwarding?"
date: 2014-03-09
forum: General Help
---

### Post by fermulator on 2014-03-09
Good day,

Recently I upgraded my server from 10.04 to 12.04 LTS.

Since then, for a long while, I was unable to use X11 forwarding. (previously it worked just fine).

Today finally I spent the time to research/investigate this.

Some basic links describing the problem:
 - [http://www.linuxquestions.org/questions/ubuntu-63/can%27t-open-display-882197/](http://www.linuxquestions.org/questions/ubuntu-63/can%27t-open-display-882197/)
 - [http://askubuntu.com/questions/141240/cant-open-display-even-after-access-with-xhost](http://askubuntu.com/questions/141240/cant-open-display-even-after-access-with-xhost)

Adding:
{{{
AddressFamily inet
}}}
to /etc/ssh/sshd_config and restarting SSH did the trick.

Do we have a bug somewhere in default configuration?

This problem was very obscure and difficult to solve.

---

