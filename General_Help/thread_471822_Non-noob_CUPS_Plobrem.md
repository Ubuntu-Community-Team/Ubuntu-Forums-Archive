---
title: "Non-noob CUPS Plobrem"
date: 2007-06-12
forum: General Help
---

### Post by whizbaby on 2007-06-12
HiZ,
my problem is:
I have a printserver (feisty) and multiple (400+) clients plus the printers, some attached locally and some networked. The hussle is with those locally connected printers (btw its not possible to connect them in another way). I want the server to spool (having filters and stuff) all jobs, so that I can easily administer the printing system. I DONT want to install filters to all clients (there are obvious enough reasons for that I think.). So I open cupsd.conf on client and add

ServerName     myservername
ServerBin           /my/server/bin/                                          (I replaced the real names)

The odd thing (for me) is that the server now stops looking for the printer on the client but starts looking at own ports, where the printer isnt connected.

So, to make it short, how do I configure CUPS to have:

1)spooling is done centralized properly so that
2)at the same time printers can be connected via USB/parallel

And yes, I've rtfm. ANY help would be appreciated.

---

### Post by JohnPhys on 2007-06-12
I'm not a cups expert by any means, so I might be misinterpreting your post.

If you want all of your clients to print through the print server, then I think you have to add

```
ServerName your.server.name
```

to the **client.conf** file on each client, either located in /home/username/.cups or /etc/cups/

You may have to create the client.conf file.

If I'm way off on what you're trying to do, just let me know.

---

### Post by whizbaby on 2007-06-12
Sry a typo I meant client.conf on clients. Set to spool is not the problem. My problem is that, as soon as I make the server spool jobs for a printer which is locally attached to another computer, the server wont be able to contact the printer anymore. Its searching its own USB/parallel ports for the printer. I want to have 'connection management' (dont know how you call that, its got to do with the deviceURIs) and spooling seperated.

To put an example of a 'working' system:
in lprng modify client printcap, lets say for an usb connected printer, add

:lp=/dev/usblp0

on the server, add a line to the printers section

:lp=lp@name_of_client

The server spools AND can see the printer. No filters needed on client. I guess its possible with CUPS, too. Its not a problem with networked printers of course.

Thx though

---

### Post by whizbaby on 2007-06-13
anybody?

---

### Post by whizbaby on 2007-06-16
I got it up and working. If someones interested howto do this (have only one machine with all filters installed to it and local printers on some client machines at the same time):

On the client, define the printer as a raw printer. You do this by not providing a .ppd file at printer creation, e.g. 

lpadmin -p NAME -v parallel:/dev/lp0

will create a raw printer with name NAME. On the server, create a printer with

lpadmin -p REALNAME -v ipp:/CLIENT/printers/NAME -P PATH_TO_PPD

All that you have to do now is hide the raw printer NAME, you can achieve this with the BrowseAllow and BrowseDeny options (on client).
Use REALNAME to print.

---

### Post by drpaul on 2007-06-16
Awesome. You should really try to archive this somewhere.

Paul

---

