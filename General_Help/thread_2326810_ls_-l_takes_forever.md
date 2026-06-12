---
title: "ls -l takes forever"
date: 2016-06-05
forum: General Help
---

### Post by willem8 on 2016-06-05
Recently I accidentally typed "ls -l" in the /usr/bin directory (it should have been in another directory). It is a big directory so I expected it to take some time. But it showed about a dozen a minute and literally took hours. In the end I had to close down my computer before the console with the connection to the server had finished the job.

Is this normal? What could have caused this?

---

### Post by steeldriver on 2016-06-05
Hello and welcome to the forums

No it is not normal imho

Since you refer to a "console" and a "connection to the server" I assume you are running ls over some sort of remote connection (possibly SSH)? If so, other factors might be involved, like

[LIST]
[*]the connection bandwidth / reliability
[*]other i/o heavy processes running on the server (perhaps belonging to other users)
[/LIST]

It *could* be a symptom of a failing drive or bus (although in that case I'd expect more general flakiness / errors)

---

