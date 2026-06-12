---
title: "stubborn first character in gnome terminal history"
date: 2007-12-11
forum: General Help
---

### Post by johnmuir on 2007-12-11
When I press the up-arrow to recall the last command and try to edit the line, the first character is protected and I can't edit it (sometimes - not always)
I'll try to explain
enter: foo
press enter, response: 'unknown command'
press up-arrow, response: 'foo'
press backspace _3_ times: see 'f' i.e. I can't overwrite the 'f'
press enter, response: (nothing, i.e. the f is not 'seen')

I'm fascinated & frustrated as I can't use the history.

My PS1 is
PS1="\t [\u] \w\n\r"

---

### Post by matthewcraig on 2007-12-11
Strange.  This doesn't happen on my system.  Does it happen when you work from the service console (CTRL-ALT-F1 for example) ?

---

### Post by johnmuir on 2007-12-12
Hi and thanks for helping... yes it also exhibits this behaviour in the service console...

---

