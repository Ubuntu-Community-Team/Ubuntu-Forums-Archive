---
title: "Share printer on Feisty home network"
date: 2007-08-25
forum: General Help
---

### Post by azdavef on 2007-08-25
I have a Dell desktop and two Toshiba laptops that are all running Feisty very nicely and print to my Canon printer very nicely when they are connected to it.  They share a linksys wireless router and it would be nice if I didn't have to connect the printer to the machine that wants to use it. I suspect that this is not a real hard thing to do.  I don't want or need to share files since my children most often use the laptops and I would not want to give them the impression that I could snoop in their stuff.

---

### Post by wjp.reg on 2007-08-26
Here's a HOWTO for [network printing with ubuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

good luck!

Sorry, made a few mistakes when I first entered the link :-)

---

### Post by azdavef on 2007-08-26
Thanx, do I use the IP address of the router, since the IP address of all of the machines seems to be the same, except it seems to change each day?

---

### Post by wjp.reg on 2007-08-26
> **azdavef said:**
> Thanx, do I use the IP address of the router, since the IP address of all of the machines seems to be the same, except it seems to change each day?

I'm assuming your printer is always connected to the desktop which is always on in order for the laptops to use the printer.

If this is not your intention then you need to get a router that has print server capability, and yes, you would use the IP for the router-based printer connection.

Otherwise you would use the IP or hostname for the desktop as it won't change.

Some recommend that you use static IPs instead of DHCP controlled by a router.  Either way, the above methods should both serve your purposes.

Cheers!

---

### Post by azdavef on 2007-08-26
Again thank you for your time and patience.  If I understand, in the directions below

Now on the client(s) open up the printer manager System->Administration->Printing and under the Global Settings check the Detect LAN Printers option.Then go to Printer->Add Printer check the Network Printer option and in the area marked URI write something like

  

      ipp://192.168.0.1/printers/<name of printer>

where 192.168.0.1 is your servers ip address and <name of printer> is the name you gave the printer when you set it up (usually the model of the printer).

I can substitute the hostname of the desktop for the ip address?

---

### Post by wjp.reg on 2007-08-26
You don't need to select "Detect LAN Printers".

Otherwise you described the client-side steps as indicated in the network printing link i referred you to earlier.

You don't need to use the IP, just the hostname will do.

In my case my HP laser 3015 printer, called "hplaser", is connected to a desktop called "Genoa", so I would configure it on my laptop with:

```
ipp://genoa/printers/hplaser
```

So it really doesn't matter what the IP is, does it :-)

That's it!

P.S. Just go ahead and try it, you can't break anything!!

BTW: Is the printer already marked as "shared" on the host computer?

---

### Post by azdavef on 2007-08-26
So the host machine is marked as "share printer" and the client machine opens the printer and tries to send the job, but nothing happens.  I use WICD as a connection manager and the router is WEP encrypted.  Could either of those be a problem?:)

---

### Post by wjp.reg on 2007-08-26
> **azdavef said:**
> So the host machine is marked as "share printer" and the client machine opens the printer and tries to send the job, but nothing happens.  I use WICD as a connection manager and the router is WEP encrypted.  Could either of those be a problem?:)

No, not if your laptops can already connect to it (the router).

Some of your language above" confuses me, sorry.  Did you mean your host machine is named "share printer", or did you mean that in System | administration | Printing that you have selected your printer and marked it as shared?  also, what do you mean by the client "opening" the printer?  Did you try and print some kind  of file?

After doing the network printer install, did you run a test print?  What happened?  You can run a test print right from the "properties" option of the printer in question.

---

### Post by azdavef on 2007-08-26
Sorry about that.  I marked the host machine in System to share the printer.  I tried the test page and the printer icon showed up on the client machine and said it was printing when I opened the icon window.  I did get an error on the General Tab of the printer properties:
Status: Unable to lookup host. Host unknown
I didn't change the Global Settings of the sending machine to Detect Lan Printer.

---

### Post by wjp.reg on 2007-08-26
Another thing just dawned on me -- do you have a network installed/defined?  After all, you can't very well share a network printer if there is no network. :redface:

---

### Post by wjp.reg on 2007-08-26
> **azdavef said:**
> Sorry about that.  I marked the host machine in System to share the printer.  I tried the test page and the printer icon showed up on the client machine and said it was printing when I opened the icon window.  I did get an error on the General Tab of the printer properties:
Status: Unable to lookup host. Host unknown
I didn't change the Global Settings of the sending machine to Detect Lan Printer.

Let's start over:

Do you have a network setup with users and passwords?

If so, what does the following terminal command return when entered on the host computer:

```
hostname
```

What did you call the printer (in preferences, connection tab)?

---

### Post by azdavef on 2007-08-26
Well....if I go into System, Administration, Network the first screen I see is blank without any configurations. When I click on the Location: box a location called MINE shows up with wireless configuration.  I don't remember doing anything in this function...

---

### Post by wjp.reg on 2007-08-26
how about Places | Network.  Anything there?

---

### Post by wjp.reg on 2007-08-26
> **azdavef said:**
> Well....if I go into System, Administration, Network the first screen I see is blank without any configurations. When I click on the Location: box a location called MINE shows up with wireless configuration.  I don't remember doing anything in this function...

There should be some kind of configuration unless you don't have any networking hardware installed in the host (wired/wireless).

---

### Post by azdavef on 2007-08-26
Nope...:)

---

### Post by wjp.reg on 2007-08-26
> **azdavef said:**
> Nope...:)

:lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

Better go get a network interface for your host print server 'cause we're all out of magic!!

Good Bye and Good Luck :-)

---

### Post by CatastrophicToad on 2007-08-26
go to [http://localhost:631/admin/](http://localhost:631/admin/) and check "share published printers connected to this system" to share a printer attached to a Linux machine.

---

### Post by danip on 2007-09-04
great how to. well written and clear.  didnt run into any problems myself :)

---

### Post by iitywygms on 2007-09-20
Why is this  not a how to?

---

