---
title: "how to erase the list of ran commands when using alt+f2"
date: 2008-06-02
forum: General Help
---

### Post by adhuvi on 2008-06-02
When using the alt+f2 Run Command application, there is a list of (recently?) ran commands. how do i delete or edit this list?

---

### Post by NetworkGuy on 2008-06-02
I believe everything is stored in .bash_history 

I **_think_** you can delete the file and it will be recreated.

---

### Post by adhuvi on 2008-06-02
.bash_history seems to be the history of the commands i've run in the konsole. 

When you type alt+f2 a different windows comes up, it is like a different application. i don't know the name, it only says Run Command, and it has it's own history i think. That is what i want to delete.

---

### Post by Mguel on 2009-01-12
I was wondering this same thing (using kde 3.5.10)... how to delete run history (of Run Command, Alt + F2 dialog)

---

### Post by Yashiro on 2009-01-12
Open a new program using alt+f2 then search for files written to during this time.

---

### Post by Mguel on 2009-01-12
Found the answer:

You have to edit:

~/.kde/share/config/kdesktoprc

under the section: [Minicli] there is a History[$e] line... after deleting the wrong commands its necessary to restart X to have the deleted commands to stop appearing on the run command autocomplete alternatives.

Cheers,
Mguel


> **Yashiro said:**
> Open a new program using alt+f2 then search for files written to during this time.
:confused::confused::confused::confused::confused::confused::confused:

---

### Post by meindian523 on 2009-01-14
Anyone know how to do this in GNOME?

---

