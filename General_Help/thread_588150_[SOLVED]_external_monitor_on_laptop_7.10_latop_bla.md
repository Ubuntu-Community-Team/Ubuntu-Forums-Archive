---
title: "[SOLVED] external monitor on laptop 7.10 latop black help"
date: 2007-10-23
forum: General Help
---

### Post by dutchbo2 on 2007-10-23
While setting up external monitor with 7.10 I thought setting were correct. I asked me to restart when I did my laptop monitor goes black after ubuntu load screen. I can not see to fix problem. How do I get my laptop monitor back? Help

Thanks 
Bill

---

### Post by dutchbo2 on 2007-10-24
Fixed problem.
esc at startup
started in recover mode and entered my root password.

Then ran following

sudo dpkg-reconfigure xserver-xorg

Followed prompts and questions and restarted.

Monitor came back to life.

---

