---
title: "Bug freezes OS in creating folders in &quot;All&quot; in applications [20.04]"
date: 2020-04-20
forum: General Help
---

### Post by userhv on 2020-04-20
As soon as a folder is created with several applications, when we need to remove several applications from the same folder created, the system freezes and it is necessary to manually disconnect and connect to get back to work. I can't create any kind of report to post the bug using alt + f2 and using the ubuntu-bug option, how can I report at all?

---

### Post by QIII on 2020-04-20
We are close enough to release for this to be in the general forums.

> **userhv said:**
> As soon as a folder is created with several applications

What do you mean by this?

> when we need to remove several applications from the same folder created

And this?

> the system freezes and it is necessary to manually disconnect and connect to get back to work.

What do you mean by "disconnect"?

---

### Post by userhv on 2020-04-20
[QUOTE = QIII; 13948764] Estamos perto o suficiente para liberar isso nos fóruns gerais. 



O que você quer dizer com isso? 



E isto? 



O que você quer dizer com "desconectar"? [/ QUOTE]

Let's assume you are going to organize your apps into folders ok? You create a folder with several apps, when you need to remove several apps from that created folder the computer freezes and nothing else works, you need to manually turn it off.

---

### Post by userhv on 2020-04-20
Let's assume you are going to organize your apps into folders ok? You create a folder with several apps, when you need to remove several apps from that created folder the computer freezes and nothing else works, you need to manually turn it off.

---

### Post by QIII on 2020-04-20
"Folders" is a Windows term.  They are directories.

Why are you "organizing" applications in different directories?  Why aren't you letting them be installed as designed?  Linux has a well established directory hierarchy into which installed applications should be placed.

What applications are you installing?  Are you uninstalling the applications properly, or just removing the files?

---

### Post by userhv on 2020-04-20
> **QIII said:**
> "Folders" is a Windows term.  They are directories.

Why are you "organizing" applications in different directories?  Why aren't you letting them be installed as designed?  Linux has a well established directory hierarchy into which installed applications should be placed.

What applications are you installing?  Are you uninstalling the applications properly, or just removing the files?



[IMG]https://imgur.com/a/0BLga4N[/IMG]In the ubuntu dock there is "show applications", there are two tabs, "frequent" and "all", in the tab all are all applications right? If you drag an application with the mouse to another one it creates a "folder" where you can even name it to keep it more organized. When we need to remove apps from these folders the OS crashes and nothing else works.

---

### Post by QIII on 2020-04-20
You are not talking about the applications themselves, then?  You are talking about the arrangement of launchers/icons?

---

### Post by userhv on 2020-04-20
> **QIII said:**
> You are not talking about the applications themselves, then?  You are talking about the arrangement of launchers/icons?

I'm talking about this ...  [https://www.youtube.com/watch?v=dXIqt7z5e9U](https://www.youtube.com/watch?v=dXIqt7z5e9U)

---

### Post by deadflowr on 2020-04-22
If you feel it is a bug follow this on how to report it:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")
fwiw the package it should be reported against is gnome-shell.

ftr, I don't see this issue I can add and subtract apps from those dash folders without any crashing/freezing.
My only issue is that when creating a folder it usually marks the new folder as Untitled so it moves it to the bottom tier.
Which is a pain if you need to move apps to it from the top tier.

---

