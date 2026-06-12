---
title: "How to load a microsoft exchange email account to Evolution"
date: 2016-07-07
forum: General Help
---

### Post by flashgordon2 on 2016-07-07
I am a newbee and have just purchased a new Asus Zenbook and taken the plunge and loaded the latest Ubuntu software and Evolution email.  From searching the posts it would appear that Evolution is required for an exchange email account.  However, all the threads on this subject are outdated and I cannot get my email to work.  Can anyone help me?

---

### Post by btindie on 2016-07-07
You might have better luck using Exchange EWS Provider for Thunderbird - [https://github.com/Ericsson/exchangecalendar](https://github.com/Ericsson/exchangecalendar) instead of Evolution when wanting to connect to exchange.

Download the latest release and install that in Thunderbird [https://github.com/Ericsson/exchangecalendar/releases](https://github.com/Ericsson/exchangecalendar/releases)

---

### Post by flashgordon2 on 2016-07-07
Thanks, I am trying this now

---

### Post by mastablasta on 2016-07-07
from wiki:
> [h=3]Connecting to Microsoft Exchange Server[[edit]("https://en.wikipedia.org/w/index.php?title=Evolution_(software)&action=edit&section=3")][/h]Depending on which version of Microsoft Exchange Server is used, different packages need to be installed to be able to connect to it. The documentation recommends the *evolution-ews* package (which uses [Exchange Web Services]("https://en.wikipedia.org/wiki/Microsoft_Exchange_Server#Clients")) for Exchange Server 2007, 2010 and newer. If *evolution-ews* does not work well, it is advised to try the *evolution-mapi* package. This supports Exchange Server 2010, 2007 and possibly older versions supporting [MAPI]("https://en.wikipedia.org/wiki/Messaging_Application_Programming_Interface"). For Exchange Server 2003, 2000 and possibly earlier versions supporting [Outlook Web App]("https://en.wikipedia.org/wiki/Outlook_Web_App") the package *evolution-exchange* is recommended.[SUP][[SIZE=2][[/SIZE]]("https://en.wikipedia.org/wiki/Evolution_(software)#cite_note-evo-exchange-18")[/SUP]


---

### Post by flashgordon2 on 2016-07-07
I am unable to download the EWS provider for Thunderbird as it is an unsigned add on and Firefox will not accept it...............

---

### Post by btindie on 2016-07-07
> **flashgordon2 said:**
> I am unable to download the EWS provider for Thunderbird as it is an unsigned add on and Firefox will not accept it...............
You need to add it to Thunderbird and not FF.

Tools -> Add-ons. Click the tool icon next to the search box and select "Install Add-on From File..."

---

