---
title: "Terminal prompt placeholders not interpreted"
date: 2014-10-16
forum: General Help
---

### Post by ellvee2 on 2014-10-16
Dear forum,

I edited ~/.profile to customize the prompt of the terminal.

PS1="\u@\h:\w> "

But when I start the terminal, this is literally what is displayed, i.e. the prompt is
\u@\h:\w>
The \u is not replaced by my username.
I am using Ubuntu 14.04 with Gnome.

I dont know whether it is relevant, but at first I had issues to change the prompt at all. I created .bashrc, .bash_profile and .profile in my home dir with the above line, but all of them were ignored. The .profile was finally read when I activated
Profile Preferences>Title and Command>Run command as login shell
whatever that means.
I have a suspicion that it might be related with me being loggeed in as administrator. The terminal also starts in / and not in ~/, but I am just a beginner.

---

### Post by col48 on 2014-10-16
In my home directory, a comment in the .profile file refers to /etc/.profile
This file certainly sets PS1 in some circumstances (which I guess will either always be the case or never) - you could have a look at that.

---

