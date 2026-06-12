---
title: "Meaning of warning messages."
date: 2013-04-03
forum: General Help
---

### Post by arroy_0209 on 2013-04-03
I am using ubuntu12.04 and while using firefox19.0.2 I noticed, on the terminal, this message was reporetd several times:
> (firefox:2102): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/roy/.local/share/recently-used.xbel', but the parser failed: Failed to open file '/home/roy/.local/share/recently-used.xbel': Permission denied. Can anybody please indicate what is implied by this and what I am supposed to do about this?
Another warning message appeared on the terminal only once (when firefox was running): > gnome-keyring:: couldn't connect to: /tmp/keyring-5OKa2x/pkcs11: No such file or directory What is being implied here and what a I supposed to do about it? This gnome-keyring also appears when I use printer. But so far this had remained unclear to me.

---

### Post by Bashing-om on 2013-04-03
arroy_0209; Hi !

Look at the file ownership of the file(s) in question:
```
  ls -la ~/.local/share/recently-used.xbel
```
example output from my system:
> sysop1@1204-a:~$ ls -la ~/.local/share/recently-used.xbel
-rw------- 1 sysop1 sysop1 26646 Apr  3 12:11 /home/sysop1/.local/share/recently-used.xbel
sysop1@1204-a:~$ 
Perhaps you have used "sudo or gksudo" inappropriately ??? and the ownerships changed to "root" .

Keyring may be a separate issue (??)

[INDENT=2]it's just a thought

[/INDENT]

---

### Post by arroy_0209 on 2013-04-03
I have checked file ownership and it is same as in your system. So where is the problem? I don't remember ever having changed file ownership etc for this using sudo.

---

### Post by Bashing-om on 2013-04-03
arroy_0209;
kind of odd then... how bout checking all the directories above that file. All should be owned by you.[INDENT=2]
we be look'n

[/INDENT]

---

