---
title: "Giving user root access with SFTP"
date: 2013-02-28
forum: General Help
---

### Post by goldingroup on 2013-02-28
[COLOR=#333333][FONT=Lucida Grande]Hello,[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I want to disable root login for SSH connections to my server with latest version of Ubuntu. In SSH I can get temporary root access by su/sudo. My problem follows next. [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I use SFTP instead of FTP for file transfers and I want my user account to get root access to the files through SFTP. As I am aware of, my SFTP application (Transmit, I'm on a Mac) won't do su/sudo. The user belongs to the root group, yet that doesn't help when the files only are readable by the root group. What is the best solution for this? Is it a good idea to chmod everything to the user? Will that effect any scripts run by root (crons for instance).[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Any input is very appreciated![/FONT][/COLOR]

---

