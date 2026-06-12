---
title: "Evolution : can't remove accounts"
date: 2013-04-04
forum: General Help
---

### Post by andreaolivato on 2013-04-04
I have two accounts in evolution that I'm not able to remove nor from the program itself neither from the online account panel.


In evolution the "Delete" button is disabled when I select those two accounts


In Online Accounts they are not present in the list so I can not remove them.


The accounts I wish to remove are the ones with the half-globe icon in the attached screenshot.

Please also note that I can not find [FONT=Ubuntu Mono]/apps/evolution/mail/accounts[/FONT] under [FONT=Ubuntu Mono]gconf-editor[/FONT] and also I can not find them doing "grep" in the .config directory

Where can I find the configuration files to remove these manually?

[IMG]http://i.stack.imgur.com/xPdGJ.png[/IMG]

---

### Post by Zeklandia on 2013-08-16
> **andreaolivato said:**
> I have two accounts in evolution that I'm not able to remove nor from the program itself neither from the online account panel.


In evolution the "Delete" button is disabled when I select those two accounts


In Online Accounts they are not present in the list so I can not remove them.


The accounts I wish to remove are the ones with the half-globe icon in the attached screenshot.

Please also note that I can not find [FONT=Ubuntu Mono]/apps/evolution/mail/accounts[/FONT] under [FONT=Ubuntu Mono]gconf-editor[/FONT] and also I can not find them doing "grep" in the .config directory

Where can I find the configuration files to remove these manually?

[IMG]http://i.stack.imgur.com/xPdGJ.png[/IMG]

I have the exact same issue, but also with Contacts, Calendars, and Emails. I have removed the accounts from both Online Accounts providers in the GNOME Control Panel, and I have tried purging the packages and reinstalling numerous times. Where does Evolution store this data?

---

### Post by r-senior on 2013-11-20
Sorry to drag up an old thread, but this was so hard to find as the solution to the above.

[https://bugs.launchpad.net/ubuntu/+source/gcr/+bug/1044549/comments/14](https://bugs.launchpad.net/ubuntu/+source/gcr/+bug/1044549/comments/14)

Moving that file eliminated my undeletable accounts after upgrading to 13.10. I had to set up my other accounts in Evolution again so make sure you know their details before going down this path.

---

