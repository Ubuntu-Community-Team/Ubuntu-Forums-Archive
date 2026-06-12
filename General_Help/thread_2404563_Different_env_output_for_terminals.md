---
title: "Different env output for terminals?"
date: 2018-10-25
forum: General Help
---

### Post by again? on 2018-10-25
Why do I get different env output for xfce4-terminal and xterm?
Xubuntu 18.04

---

### Post by again? on 2018-10-25
Worked out what it was.
I had pinched a python script from bunsen labs that runs as a daemon and allows you to configure hot corner actions.
One of the hot corner actions was to initiate xfce4-terminal --drop-down
I decided to start the script as a systemd --user service
You need to set environment variables with systemd which I'm not to sure how to do
so I have now just placed the script in startup applications.

---

