---
title: "Use a PIN user code for Office Printer"
date: 2019-09-15
forum: General Help
---

### Post by cathect2 on 2019-09-15
[COLOR=#242729][FONT=Arial]I'm trying to set up a networked printer (a Konica Minolta Bizhub c558) that uses a four digit pin to authorize printing. I've set up the printer (using ipp://) and edited the printers.conf to try and hard code the PIN, but it isn't working. It seems that CUPS expects a username and password. But I just have a four-digit PIN. I've even gone into the CUPS server at localhost:631 to examine it, but there is no setting there for this purpose either. What am I missing here?
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The printer worked as expected before the PIN was introduced. I just need to add the authorization somehow.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've tried to set the printers.conf file to "negotiate" so that it will bring up a dialog for the PIN, but it won't accept a blank user.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What am I to do? There is no setting in the printer GUI to add a user code for printing. Help![/FONT][/COLOR]

---

