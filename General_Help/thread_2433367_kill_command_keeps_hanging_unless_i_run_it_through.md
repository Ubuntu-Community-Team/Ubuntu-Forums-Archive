---
title: "kill command keeps hanging unless i run it through strace"
date: 2019-12-18
forum: General Help
---

### Post by Skaperen on 2019-12-18
the [COLOR=#0000cd][FONT=courier new]**kill**[/FONT][/COLOR] command (to kill one process with SIGTERM) was hanging ... every time i used it.  it was even blocking ^C and ^Z.  so i ran it under [COLOR=#0000cd][FONT=courier new]**strace**[/FONT][/COLOR].  it works fine under [COLOR=#0000cd][FONT=courier new]**strace**[/FONT][/COLOR]. any guesses?

---

