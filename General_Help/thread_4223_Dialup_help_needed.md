---
title: "Dialup help needed"
date: 2004-11-12
forum: General Help
---

### Post by Arnb on 2004-11-12
Installed Warty on Laptop with PCMCIA modem which I setup in System Configuration --> Networking and connected to an ISP but am unable to get Firefox, e-mail, ping etc out onto the net, nor visually monitor the status of the connection. I searched the wiki and forums but did not find anything a Linux nubie such as myself can understand. 

Could some one please post details or a link on how to get dialup to work on Ubuntu and if possible how to visually monitor the connection.

Thank you

---

### Post by az on 2004-11-12
Open a root terminal and do
tail -f /var/log/messages

as you connect.  Show the output.

---

### Post by Arnb on 2004-11-12
Thanx, that gave me something to look at. 

However I'm now experiencing some sort of connection problem that causes constant hangups with no connect. The messages are
pppd 2.42 started by root
Serial connection established
using interface ppp0
Connect: ppp0 <--> /dev/modem
[at this point the connection breaks]
Serial line is looped back
connection terminated
Terminating on signal 15

Is there any way to see the connection progress messages to know what is wrong?

Thankx

---

### Post by az on 2004-11-13
How exactly are you connecting?

What model modem is it?

Have you tried other ways of connecting?  (pppconfig with pon/poff, wvdial...?)

---

### Post by Arnb on 2004-11-13
[QUOTE=azz]How exactly are you connecting?

What model modem is it?

Have you tried other ways of connecting?  (pppconfig with pon/poff, wvdial...?)[/QUOTE]

My primary machine is connected via cable using dual boot Win Xp / 98 and hopefully Linux in the future. The system with the problem, a Dell 7000 Laptop, is being used by me to learn Linux.  Eventually it will be given to a friend who will use dialup.

Modem: 3Com 3CXM556 PCMCIA card using dialup functions only. It can also connect by cell. 

Other methods of connection
Tried Wvdial (it took off using the data I entered in the GUI), it dials but the ISP keeps rejecting the username/password pair, which I triple checked.  The weird thing is it did manage to connect earlier in the day using the Ubuntu GUI but it always took a few tries. To be 100% certain it was not hardware, I booted XP/Sp2 on the test machine and successfully connected on the first try  I'm new to Linux so I'll search for instructions for using Pon/Poff.

---

### Post by sb73542 on 2004-11-13
[http://ubuntuforums.org/archive/index.php/t-346.html](http://ubuntuforums.org/archive/index.php/t-346.html)

But why in the world isn't there any good dialup software already included?  Broadband is still a rare commodity in most areas of the world, where it's often a luxury to have dialup.

---

### Post by Arnb on 2004-11-14
I agree the dialup support must be straight out of the box for Ubuntu to make it in the real world of users. 

Now back to my problem

With much perseverance I found the WVDIAL.CONF file(yes I'm a Linux nubie) and discovered the Ubuntu Network Gui does not delete old entries in this file so it would never try my new settings ](*,) . 

After editing and correcting WVDIAL.CONF, making a connection with WVDIAL,
 then seeing --> looks like a Logon request
 followed by sending [email]xxxxxxx@foo.net[/email]  
the ISP keeps returning unable to recongnize username pair, however they are correct. I dont see the request for the password.  Anyone have any suggestions.

---

### Post by sb73542 on 2004-11-14
[QUOTE=Arnb]I agree the dialup support must be straight out of the box for Ubuntu to make it in the real world of users. 

Now back to my problem

With much perseverance I found the WVDIAL.CONF file(yes I'm a Linux nubie) and discovered the Ubuntu Network Gui does not delete old entries in this file so it would never try my new settings ](*,) . 

After editing and correcting WVDIAL.CONF, making a connection with WVDIAL,
 then seeing --> looks like a Logon request
 followed by sending [email]xxxxxxx@foo.net[/email]  
the ISP keeps returning unable to recongnize username pair, however they are correct. I dont see the request for the password.  Anyone have any suggestions.[/QUOTE]
 Did you try gnome-ppp yet, as the link mentions?  It's a wvdial frontend, looks similar to kppp.

---

### Post by zenwhen on 2004-11-14
Ubuntu should include gnome-ppp in hoary. It makes configuring dialup as easy as it should be. Also, the initial user should be added to the "dip" group in /etc/group. 

Then they could just put a launcher for gnome-ppp in the "Internet" menu initially with the name "Dialup".

There would be no further dialup questions and no one put off by the initial configuration of an internet connection that is required for all subsequent steps.

---

### Post by Arnb on 2004-11-15
Regarding Gnome-ppp: That's catch22; it's not installed (AFAIK) on the base Ubuntu release and I could not get dial up to work. 
 
Now the good news , It's  Working 

After editing Wvdial.conf with instuctions found on ATT's site
[http://www.wurd.com/instcon_linux_wvdial.php](http://www.wurd.com/instcon_linux_wvdial.php)

The two things I changed that made it work

1. changed the user name to from
[email]123456789@att.net[/email] to
[email]123456789@worldnet.att.net[/email]
(no idea why the former works in windows but not Windows Hiperterminal or Linux)

2.  adjusted  as follows
Stupid Mode = 1 (this was there)
Auto DNS = 1   (added this one ,resolves the DNS servers)
If they are not there, add them or make other appropriate changes so they are there. With Stupid Mode turned on, wvdial will bring up pppd right away.

Fired up WVDIAL and it worked(what a surprise) I could use Firefox to get out on the net, then tried activating with Sytem Configuration --> Networking and that worked but my manual changes don't show in the profiles.  

Question: Anyway to get the diaup configuration to show in Computer Networking or the status to show someplace?  I had to go back into System Configuration--> Networking to drop the connection.  

Frankly the average computer user would have lost it simply trying to setup dialup. This must change for Ubuntu to make it in the real world of users. 

Arn

---

### Post by zenwhen on 2004-11-15
I submitted the concerns raised in this thread to the Ubuntu Devs mailing list.

---

