---
title: "removing wine menu entries for windows apps"
date: 2007-02-06
forum: General Help
---

### Post by SpanishFranks on 2007-02-06
I've just uninstalled various windows apps using the wine uninstaller. All the files are gone, but there is still a 

wine -> Programs -> *program entries*

entry in my main menu. How can I remove this?

---

### Post by loserboy on 2007-02-06
in dapper under applications>accessories is alacarte menu editor, you can do it that way.

it should be there in edgy but my edgy comp is at home so dunno

Edit: ok its called menu layout in edgy and its under system>preferences

---

### Post by kraftmayo on 2007-02-08
I've got the same issue.  Alacarte doesnt show the wine folder under the applications menu.

---

### Post by ramjet_1953 on 2007-02-08
That's odd!!

I can add and delete apps fine on my system!
The wine folder is there when I start-up the Alacarte Menu Editor.

Roger8)

---

### Post by kraftmayo on 2007-02-08
Actually, I just figured it out.

Apparently Alacarte chokes and dies forever if you ever run it as sudo, which I did.

To get rid of them without it, remove the folders and subfolders from ~/.local/share/applications/****

Restart X and you're money.

---

### Post by ahsile on 2007-02-11
Thanks for the tip. This one was driving me crazy! I kept looking in /usr/share/applications and couldn't find anything.

---

