---
title: "Synaptic does not start from launch icon"
date: 2008-07-02
forum: General Help
---

### Post by Amalaye on 2008-07-02
System->Administration->Synaptic Package Manager does not work. I cannot start it graphically. I can start it from a terminal.

What is the fix for this. I am using 8.04 LTS

---

### Post by soccerboy on 2008-07-02
if you go to System>Preferences>Main Menu and in the GUI go to System Tools>Administration>Synaptic Package Manager and double click on its launcher,
make sure its command line says ```
gksu /usr/sbin/synaptic
```
Is that the fix?

---

### Post by Amalaye on 2008-07-02
It says that and I even use try gksu from a terminal ...  it seems to hang ... nothing is happening

---

### Post by soccerboy on 2008-07-02
can you use gksu on anything? if not, it may be a problem with your gksu command.  That is beyond my level of linux.

---

### Post by bapoumba on 2008-07-02
What is the error output in the terminal when you run:
```
gksu /usr/sbin/synaptic
```

---

### Post by Amalaye on 2008-07-02
It turns out I edited my /etc/hosts file and added the localhost.localdomain line and now everything works better  ... I also added the alias to the full system name ... I am happy now.

As a sanity check (and off the thread topic) how do I see if my swap space is being used and if it is on???

---

### Post by bapoumba on 2008-07-02
> **Amalaye said:**
> It turns out I edited my /etc/hosts file and added the localhost.localdomain line and now everything works better  ... I also added the alias to the full system name ... I am happy now.

As a sanity check (and off the thread topic) how do I see if my swap space is being used and if it is on???
Glad it's solved for you.
Run:
```
free
```

---

