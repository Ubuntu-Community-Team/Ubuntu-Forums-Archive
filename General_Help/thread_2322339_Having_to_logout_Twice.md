---
title: "Having to logout Twice"
date: 2016-04-27
forum: General Help
---

### Post by speartip on 2016-04-27
Clean installed & fully updated Ubuntu 16.04LTS.
When I click Logout in Top Right corner, the usual Lock/Logout box comes up, click logout & nothing happens.
I have to repeat the process again for it to work.
Anyone else having similar issues?

---

### Post by chainedgx on 2016-04-30
I have the same issue. At times the theme changes after the first logout.

---

### Post by speartip on 2016-05-01
If anyone else is having this problem were first attempt to logout fails, please subscribe to this bug. The more that do the more likely it will get resolved.
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1574054](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1574054)

---

### Post by will1982 on 2016-05-01
I am experiencing this as well on a newly updated 16.04 system. Most of the time, I simply spam the logout command in the terminal and it'll log me out after a few minutes

---

### Post by speartip on 2016-05-08
OK. I found the cause of my problem, after a fresh install & process of elimination. I had installed a program called diodon from the repos. It is a clipboard manager that sits in the panel. For some reason this caused the hang on logout. after uninstalling it & replacing it with clipit, my problem has been solved.
 It might not be the same for others, but try disabling panel apps one by one and see if the problem gets resolved.

---

### Post by blackblooded on 2016-09-16
I solved it disabling diodon application

---

