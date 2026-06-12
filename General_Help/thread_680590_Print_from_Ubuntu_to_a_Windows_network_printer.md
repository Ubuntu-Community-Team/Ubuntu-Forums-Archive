---
title: "Print from Ubuntu to a Windows network printer"
date: 2008-01-28
forum: General Help
---

### Post by errolgreer on 2008-01-28
I have Ubuntu loaded on one computer which is connected to several others on a Windows peer to peer network. The printer is a Samsung 2010. How to I get Ubuntu to see the network ? If I search for printers it fails to find one.

---

### Post by RudolfMDLT on 2008-01-28
I had the same problem  - As far as I am concerned SAMBA has been a pain in the *** in the last 2 Ubuntu releases.

Here is my solution, it may seem a pain, but it's the most hassle free.

At the Computer that the samsung is plugged into, open the network manager and assign the computer a fixed IP address. If you don't know how to do this, post back and I'll help you step by step.

Then, on the same PC, open up the Printers folder in control panel. Righclick on samsung that you wish to share and rename it to a short, no spaces name, for example, **samsung**  VS Samsung ML 2010. Also, under the sharing tab, enable sharing and use the same name here for the "Share as" text box as you did with the printer name.

Make sure that all the PC's on the lan are on the same WorkGroup, default is MSHOME. Is your Ubuntu machine on the same work group? paste this command in the terminal and see:

> cat /etc/samba/smb.conf | grep workgroup


Now, on the Ubuntu machine, click System->Admin->Printing. Click New Printer.

Select Windows Printer Via Samba.

now type in the following, substituting my bold for the true name:

smb://**WORKGROUP**/**ipADDRESSofPC**:4145/**samsungprintername**

Press the Forward button after you have read and reread that the information entered is correct. Continue selecting drivers. You might get a dialog asking you how to handle different page sizes - Select the scale to option otherwise your printer might need you to press a "continue" button for each document printed.

This should work, but might not. Post back and we'll get you printing. ;)

---

### Post by RudolfMDLT on 2008-01-28
getting bored with the studying....

> smb://WORKGROUP/ipADDRESSofPC:4145/samsungprintername

What will be easier, and I believe should work(does for me) is this; as soon as you have assigned the fixed IP to the Samsung computer, you can first try this line:

> smb://ipADDRESSofPC/samsungprintername

I just thought of it now - because you are specifying an IP address you don't need to specify a workgroup or a user. The random 4145 number is just a port allocation that samba doesn't seem to use in my setup.

and then if that doesn't work, use the top line. If none work, please post back and lets see what we can do.

---

### Post by stchman on 2008-01-28
> **errolgreer said:**
> I have Ubuntu loaded on one computer which is connected to several others on a Windows peer to peer network. The printer is a Samsung 2010. How to I get Ubuntu to see the network ? If I search for printers it fails to find one.

I recommend putting the printer on the Ubuntu machine.  It is a snap to share printers with Ubuntu.  Here is a tutorial.

[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

The printer will be able to be used by Windows machines as well.

As far as getting Ubuntu to use a printer that is attached to a Windows machine I personally have never had any luck with that.  You will have to futz around with Samba.

---

### Post by danwood76 on 2008-01-28
if you setup your smb.conf properly it will allow you to see your windows printers as if you were using a windows based machine.

here is my example smb.conf:
```

[global]
	netbios name = [YOUR PC NAME GOES HERE]
	server string = [PC DESCRIPTION HERE]
	workgroup = [WORKGROUP NAME HERE]

	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

	ntlm auth = no
	lanman auth = no

	wins support = no

	syslog = 1
	syslog only = yes

```

if you replace your smb.conf with this one and add your PC name and workgroup you should get it working properly, I can even print to vista PCs fine with this setup.

regards,
Danny

-- edit --

Forgot to say, make sure you backup your smb.conf first.
btw it can be found /etc/samba/smb.conf if you dont know

---

### Post by bodhi.zazen on 2008-01-28
Well, it depends on what you mean by a "Windows network printer"

I use a nework enabled HP printer (the printer plugs into the network, not a computer, it has a 10/100 card, and it's own unique IP address). I use the ipp protocol. This has nothing to do with samba.

---

### Post by RudolfMDLT on 2008-01-29
@danwood76,

I'll give that a shot later - I really HOPE it works!

---

### Post by danwood76 on 2008-01-29
If it doesnt my smb.conf has a few extra fields in it which I will post for you.

Ive found also that samba behaves better if libgnomevfs2-0 is installed, although sometimes it is installed by default.

regards,
Danny

---

### Post by oodlesOfmoodles on 2008-01-31
> **bodhi.zazen said:**
> Well, it depends on what you mean by a "Windows network printer"

I use a nework enabled HP printer (the printer plugs into the network, not a computer, it has a 10/100 card, and it's own unique IP address). I use the ipp protocol. This has nothing to do with samba.

Hey! That is my school's set up. Our domain is AHA-NET but we also have five servers. Can you give me some tips on IPP? I have been unsuccessful printing on this campus and it would be a great step for getting ubuntu supported here.

Thanks!

---

