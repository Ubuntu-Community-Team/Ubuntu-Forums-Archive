---
title: "Please help: Looking for database software"
date: 2007-07-28
forum: General Help
---

### Post by Turningman on 2007-07-28
I'm looking for open-source database (i.e. free!) software to replace a current database which is old, corrupted and written in MS-Access. The database needs to be shared across 7 PCs, some running Windows XP and the remainder Ubuntu (Feisty Fawn). They're running on a peer-to-peer basis so no fileserver or web server available. Basically I'm after an open-source cross-platform solution similar to MS-Access. The client-server model (MySQL, PostgreSQL, Firebird etc.) seems a bit heavy-duty for what I need. I've had a look at OpenOfficeOrg Base but it's neither mature nor stable enough. The data I'm storing is essentially a glorified address book (around 800 records) which is used for printing labels for mailshots etc. MS-Access seems to be a fine solution apart from the cost (i.e. one licence per PC) and the fact that I can't use it from the Ubuntu machines. What are my options? Would keeping it on a spreadsheet (OOo Calc) and using OOo Writer to create merge-printed reports from it be a viable, and robust enough, option? The organisation I work for is a charity and we need to keep support costs down as much as possible - I'm their IT department and I'm employed in a voluntary capacity so I don't want to implement something which has me as it's single point of failure and which would require the organisation to spend money buying in support if anything happened to me.

Kind regards

Turningman

---

### Post by kuja on 2007-07-28
Outside of the client-server sorts I don't know of any that are cross-platform. WEll, 
Oh, Koffice's Kexi may be worth a try when KDE4 is out though. (It'll be cross-platform then)

You could try that OOo method out for a while and see how that works for you.

You could also try the client-server deal. Heavyweight though it may be, it still shouldn't be too hard I would imagine, and it's not too difficult to set up either.

---

### Post by Turningman on 2007-07-29
Thanks, Kuja. I'm amazed that there isn't really an open source cross-platform equivalent to MS-Access though, since Access has been so popular within the Windows community I would have thought there would have been a market for it. Thanks again for taking the time to reply.

Regards

Turningman

---

### Post by gary0 on 2007-07-29
MS Access is free to use (as opposed to MS SQL Server which isn't). MDAC_TYPE is a free MS download, MDAC=Microsoft Data Access Controls.

However, I use MySQL for my amateur radio logbook, and my contacts address book. It is qyite straight forward to set up, can be run as a service on an XP box, and accessed across the network. Well worth looking into.

Gary.

---

