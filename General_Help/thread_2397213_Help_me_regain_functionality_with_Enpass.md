---
title: "Help me regain functionality with Enpass"
date: 2018-07-26
forum: General Help
---

### Post by lsutiger on 2018-07-26
I had a 16.04 install where I would ssh into my home computer from wherever I was and run Enpass over ssh. I would use the -XC options in my ssh command.
I bought a new computer, installed 16.04 and restored all of the settings with aptik. That was nearly flawless and save a lot of time.
But the problem I am having now is when I try to run Enpass over ssh I receive the error of:
QXcbConnection: Could not connect to display 

The command line I have always used for this is:
/opt/Enpass/bin/runenpass.sh %U

EDIT:
I do have X11FORWARDING set to yes in the sshd_config file
What should I check here?

---

