---
title: "Printer sharing over network"
date: 2014-12-08
forum: General Help
---

### Post by philromford-q on 2014-12-08
I am trying and failing to set up printer sharing over my network. I have 3 printers connected to a laptop with Ubuntu 14.04, I am trying to share these printers with another laptop with Ubuntu 12.04 installed.

I have tried setting up the server from the server/settings tab but get a message that there is cups server error. On the tab server/connect I don't know which it should connect to.

I have gone round in several circles and am now totally confused. Could someone please guide me through this in very simple terms.

Thank you

---

### Post by ajgreeny on 2014-12-08
Did you follow this sequence?

HOST SERVER WITH PRINTER ATTACHED
1    On the server machine (the one the printer is attached to),
    open System -> Administration -> Printing
2    Select Server in the menu bar, and then Settings.
3    Check the second box:    Publish shared printers connected to this server 
4    Right click the printer and check the Shared option, if not checked yet 
5    Go to Properties and "allow printing for everyone"

CLIENT MACHINE TO PRINT FROM
6    Now let's configure the client (the Ubuntu computer from where you want to print):
7    Open System -> Administration -> Printing
8    Add - Network printer
9    Click Find network printer and specify the host computer IP address (192.168.0.#).
10    Click Find

---

### Post by philromford-q on 2014-12-08
No Luck I'm afraid.

I presume that firstly in the dialogue box with listed printers I  highlight the one I wish to network, then go to Server/Settings. When I  do this I get an overlay:-

CUPS server error
There was an HTTP error:Not found

I  can't see a way of getting out of this loop. I would like to be able to  restore the defaults and start from scratch with the information you  previously gave me.

Could you possibly tell me how to get out of this?

---

### Post by ajgreeny on 2014-12-08
Are these printers connected to a machine by USB cable or are they perhaps wireless?

If they're wireless you don't need to share them, but can just connect via their local IP address which you can probably find from the router admin page showing **Attached devices**.

---

### Post by philromford-q on 2014-12-09
All connected by USB, gave up on wireless.

The LAN is by wireless, this is working correctly.

I really want to know how to reset CUPS to its default state so I can start again.

---

### Post by ajgreeny on 2014-12-09
I have no idea about that, and a search has not given me any clues.

However, it may be worth installing **synaptic** on your system if you don't already have it.  Synaptic used to be the default package manager for ubuntu until software-centre came along, and it much better in my opinion for managing software rather than just installing things.

Using that you can search by name for packages with "cups" in their name, of which there are 18 on my system.  Most of them can be purged without also removing any other important packages, and this is where synaptic is so useful as it gives you a list of other packages to be removed each time you ask it to do so, allowing you to cancel that particular removal if it is obviously taking other things you want to keep.  I could purge 16 of those 18 files on my system without problem and then reinstall all of them again.  To purge or "remove completely" as synaptic calls it, will also remove system configurations for cups, and thus you may be able to reinstall what has been removed and find that you now have default cups configuration.

There may be other ways to get to that by manually removing system files but I was unable to find it, and I admit I am a little scared about messing with system configs if I don't know exactly what I am doing.

---

### Post by philromford-q on 2014-12-09
I do in fact have Synaptic installed. I will have a look and try what you suggest.

Like yourself I don't mess with things I don't understand.

I'll let you know what transpires.

---

### Post by philromford-q on 2014-12-10
Well, I selected CUPS in Synaptic and saw that I too had a lot installed. I was invited to upgrade; which I did, I am now able to get into the printer server settings! Thank you, I should now be able to sort out the sharing when more awake.

---

### Post by philromford-q on 2014-12-10
That's it job done, all working properly.

Thank you so much for your suggestions, it's appreciated.

---

### Post by kurt18947 on 2014-12-10
I don't know if this is practical for you but I find sharing printers connected to a router simpler than sharing a printer attached to a PC. I don't have to leave a PC powered up in order to print. I have a couple old routers running DD-WRT and functioning as network switches/print servers/wireless access points.

---

### Post by ajgreeny on 2014-12-11
I am very happy that you have managed to get this working as you wanted.

When you say in post #8 that you upgraded do you mean the cups packages or the distro version, and if you mean just the cups packages, why were they not fully updated before; it is always a good idea to keep your distro fully updated; I don't mean to the latest distro version, but all the packages in whatever version you are running.

Please use the Thread Tools menu at the top to mark this as **SOLVED**

---

