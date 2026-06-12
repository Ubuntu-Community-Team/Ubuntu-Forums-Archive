---
title: "Can't update 12.04"
date: 2013-08-20
forum: General Help
---

### Post by henry17 on 2013-08-20
I can't update ubuntu 12.04 and I keep getting this error message.  When I go to the sources.list i can edit but not save the edits [something about permissions]
[IMG]http://imgur.com/VDlq5jg[/IMG]

[http://imgur.com/VDlq5jg](http://imgur.com/VDlq5jg)

---

### Post by ibjsb4 on 2013-08-20
To edit your sources list, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
gksudo gedit /etc/apt/sources.list
```

If you want to use nautilus to navigate to it:

```
gksudo nautilus
```

---

### Post by henry17 on 2013-08-20
Worked perfectly.  Thank you very much.

---

### Post by ibjsb4 on 2013-08-20
And welcome to the forums :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

