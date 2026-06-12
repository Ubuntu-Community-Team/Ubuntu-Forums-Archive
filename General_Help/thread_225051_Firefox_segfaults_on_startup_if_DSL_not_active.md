---
title: "Firefox segfaults on startup if DSL not active"
date: 2006-07-29
forum: General Help
---

### Post by Books on 2006-07-29
I upgraded to Firefox 1.5.0.5 on Dapper-Kubuntu, and now Firefox segfaults on startup if the DSL link isn't active.

Coming from Windows, I don't like to leave my DSL connection on all the time unless I'm at the machine. I set 'pon dsl-provider' and 'poff dsl-provider' as two icons on the Panel that I can click to turn on and off the DSL. If poff has been set and I start Firefox, it immediately is killed. If pon is set Firefox starts normally. I tried starting Firefox in the terminal to see what the output would be and it said "Segmentation fault."

Before the upgrade it didn't do this; Firefox started normally regardless of the status of the DSL.

Any ideas what is going on?

Thank you!

---

