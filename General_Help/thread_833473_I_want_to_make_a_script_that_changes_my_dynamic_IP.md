---
title: "I want to make a script that changes my dynamic IP"
date: 2008-06-18
forum: General Help
---

### Post by pb_online on 2008-06-18
I used to go into my router's page, disconnect, wait 5 seconds and reconnect to get new IP.

I want to write a script, click on it and make the same.

I don't know how. If someone can tell me the commands I would apreciate it.

I can give you all the info you need about my router e.t.c.

---

### Post by ktrnka on 2008-06-18
If I understand you correctly...

You could use dhclient.

Run

```
sudo dhclient
``` inside of a terminal

You could also right click anywhere on the panel at the top of your screen.

Select "Add to Panel"
Select "Custom Application Launcher"
Where it says "Type" -> select Application in terminal from the menu.
Where it says "Name" -> DHCP Renew
Where it says "Command" -> put "sudo dhclient" without the quotes
Click ok

Then all you have to do is click the launcher and provide your sudo password and you will have your new ip address.

Hope this helps

---

### Post by pb_online on 2008-06-18
When I type this command, I see many lines. At the last line I see this:

renewal in 933660209 seconds

Long time :)

---

