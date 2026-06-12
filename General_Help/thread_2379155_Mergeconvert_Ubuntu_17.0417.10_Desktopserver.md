---
title: "Merge/convert Ubuntu 17.04/17.10 Desktop/server"
date: 2017-12-01
forum: General Help
---

### Post by realm174 on 2017-12-01
[COLOR=#333333][FONT=&quot]First of, I'm a somewhat amateur-ish user of Ubuntu. I can get a bit technical, I'm not afraid of the command line (I actually don't have a GUI installed) but I'm definitely not an expert. What I'm looking for is some ideas on how I should proceed with the task at hand. Reference material, checklists, recommendations is what I would like.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I currently have 2 computers running Ubuntu: Desktop 17.04 and Server 17.10. Both are headless. Both run MySQL, the Desktop has FTP/Apache. They both have Samba with shared folders. I'm probably forgetting a few things, and this is where a checklist would be nice.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]The goal: I need to retire the "desktop" machine. It's old, noisy, slow, completely locks up every couple of weeks.  The "Server" machine is newer, faster, has more RAM, more disk space, etc... so what I would like to do is merge them. In other words, everything I have running on the one to be retired would need to be installed/copied to the other one.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Samba shares is the easy one. Create the folders, modify smb.conf with the additional folders/permissions, move the files over.
[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]MySQL: I believe I can move the databases/tables from one to the other using mysqldump. I would then need to figure out users/permissions.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Can anyone recommend a checklist (as in, what else do I need to migrate that I am possibly forgetting about) or plan of attack on how I should proceed with that task?[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]thanks![/FONT][/COLOR]

---

