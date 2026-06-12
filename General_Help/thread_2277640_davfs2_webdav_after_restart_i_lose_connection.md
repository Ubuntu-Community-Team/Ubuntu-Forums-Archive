---
title: "davfs2 webdav after restart i lose connection"
date: 2015-05-10
forum: General Help
---

### Post by capitan.noobgmail on 2015-05-10
[COLOR=#333333][FONT=Helvetica Neue]Hello everyone, I correctly configured via davfs2 my [/FONT][/COLOR][COLOR=#BFA522][FONT=Helvetica Neue]webdav[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue] but each restart I lose connection.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]How do I make permanent access from the command line? Thanks for the support.[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]These are the commands used:[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]sudo apt-get install davfs2[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]sudo mkdir /mnt/dirtest[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]sudo mount.davfs2 [/FONT][/COLOR][https://]("https://mio/")my[COLOR=#333333][FONT=Helvetica Neue]d[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]omain[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]-ip:2078 /mnt/dirtest[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]This is the command that I am writing after every reboot:[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]sudo mount.davfs2 [/FONT][/COLOR][https://]("https://mio/")my[COLOR=#333333][FONT=Helvetica Neue]d[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]omain[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]-ip:2078 /mnt/dirtest

[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]On sudo nano /etc/fstab I wrote:[/FONT][/COLOR]
[https://]("https://mio/")my[COLOR=#333333][FONT=Helvetica Neue]domain-ip:2078 /mnt/d[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]irtest[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue] davfs user,noauto,uid=user@[/FONT][/COLOR]my[COLOR=#333333][FONT=Helvetica Neue]d[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]omain[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue].com,file_mode=600,dir_mode=700 0 1


[/FONT][/COLOR]

---

