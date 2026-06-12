---
title: "Autorun processes"
date: 2007-10-01
forum: General Help
---

### Post by jasonlfunk on 2007-10-01
What are all the things that can Autostart a process on boot?

---

### Post by scruff on 2007-10-01
There are several methods that vary depending on application. Can you give me some examples of the types of services you are referring to?

---

### Post by jasonlfunk on 2007-10-02
I would just like to know what they all are. Are there any resources out there? I could not find them.

---

### Post by scruff on 2007-10-02
If it's a service you want to add, use:

```

**EXAMPLE:**
sudo /etc/init.d/apache2 default

**LIST AVAILABLE SERVICES:**
ls /etc/init.d/

```

If it's an application, Gnome has an integrated method:
System -> Preferences -> Sessions -> Startup Programs -> Add

Or, you can create a script to do it. I use an ~/.xsession file that has a few apps in it. [See this link]("http://www.acm.uiuc.edu/workshops/cool_unix/xinitrc.html").

There's other ways as well, but that should get you started.

---

