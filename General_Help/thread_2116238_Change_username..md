---
title: "Change username."
date: 2013-02-15
forum: General Help
---

### Post by kleenex on 2013-02-15
Hi, I have a question about changing username to new one. Home directory is encrypted and there is only one user of the system. How to do it best? Should I use [COLOR=Blue]menu[/COLOR]==>[COLOR=Blue]system[/COLOR]==>[COLOR=Blue]users[/COLOR] [COLOR=Blue]and groups[/COLOR] (remove existing user and creating a new one) or using  [COLOR=Green]usermod[/COLOR] command?
```
[COLOR=Red][~][/COLOR][COLOR=Green]$[/COLOR] usermod -c "[COLOR=Blue]current_name[/COLOR]" -l [COLOR=#ff0000]new_name[/COLOR] [COLOR=#0000ff]old_name[/COLOR]
```[COLOR=#0000ff] [COLOR=Black]After change username, everything will work? I mean login, home directory encrypted etc. Frankly, I do not want to create a new user. Username change could(?) affects many parts of the system e.g. [COLOR=Green]/etc/group[/COLOR] and [COLOR=Green]/etc/passwd[/COLOR] files, [/COLOR][/COLOR][COLOR=#0000ff][COLOR=Black]path to the user directory in [COLOR=Green]/home/user [COLOR=Black]etc. What about encrypted home directory? After change username this directory still will be encrypted? No files will be deleted? Also password will not be changed? I'm sorry for such naive and really stupid question, but I don't know how to change username correctly. Thanks.[/COLOR][/COLOR][/COLOR]  [/COLOR]

---

### Post by sudodus on 2013-02-15
The user name is not really meant to be changed. Instead you should make a new user. You are aware of potential risks. ***Why do you want to change it?*** And do you intend to change the password too?

Your encrypted home directory won't unfold with a new password. This is a security property because it is easy to change the password for someone with physical access to the computer or drive. I don't know the effect of changing user name, but I would not try without a very good backup of all your personal files and settings (in the home directory).

---

### Post by schragge on 2013-02-15
@sudodus Wait, what's the problem with changing the user name if the UID stays the same? AFAIK, nothing in the system uses the username directly.

[highlight]Update.[/highlight]
Obviously, you'll need to rename your home directory, /var/mail/[COLOR=green]username[/COLOR], /var/spool/cron/crontabs/[COLOR=green]username[/COLOR],  etc. Look at the output of
```

sudo find ~ /var -name '*[COLOR=green]username[/COLOR]*'

```

---

### Post by pqwoerituytrueiwoq on 2013-02-15
[usermode](apt:usermode) will give you a GUI to change name and password in xubuntu in the settings maannger

---

