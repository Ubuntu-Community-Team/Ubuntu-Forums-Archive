---
title: "Connect to a shared Windows 10 printer that's using microsoft account credentials"
date: 2015-12-24
forum: General Help
---

### Post by a.vlachos@radiokiss.gr on 2015-12-24
[COLOR=#000000]Hi all, [/COLOR]

[COLOR=#000000]I am trying to connect to a windows 10 shared printer. [/COLOR]
[COLOR=#000000]The windows machine has users that are using microsoft accounts, so each user has a username@domain credentials.[/COLOR]

[COLOR=#000000]After a little forum search i found that in order to connect to the windows machine's shares, i have to put in the "USER" field the username without the domain, and the domain name (without the "@") should be in the "DOMAIN" field in which i was putting the workgroup name in previews windows versions which had local accounts. [/COLOR]

[COLOR=#000000]So when adding a new printer, i am entering the machine with the shared printer using the above method (it asks for username, domain and password). I am choosing the drivers and the printer is added normally.[/COLOR]

[COLOR=#000000]The problem is that when the system authenticates for the printer it only asks for username and password, not domain. If i put username@domain in the username field, its not working and asks me again in an endless loop (the same applies in all things when trying to connect to the windows machine but in the others it ask for the domain). [/COLOR]

[COLOR=#000000]I have tried various combinations for username/domain but none worked... so i can't print. [/COLOR]

[COLOR=#000000]Is there a possible solution or a way to add a default domain for that operation?[/COLOR]

---

### Post by Morbius1 on 2015-12-24
That's a good question. I don't have printers attached to the Win10 machine so I can't speak from experience so here are some possibilities (?):

If you go to /etc/cups/printers.conf and search for the lines that describe your printer you should see a line that looks something like this:
> DeviceURI smb://username: password@WORKGROUP/win10-name/printer-name
Try replacing "WORKGROUP" with the domain of your email account.

A better suggestion would be to create a local user on Win10 ( I use the name smbuser since I'm not very creative ) and give it a password. Make sure the printer is accessible by that user and when asked for credentials pass smbuser and smbuserpw and avoid the whole @domain issue.

---

