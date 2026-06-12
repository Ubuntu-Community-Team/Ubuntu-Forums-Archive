---
title: "Please HELP!!"
date: 2008-07-07
forum: General Help
---

### Post by justjohn924 on 2008-07-07
So I had a pc at my house which I was running ubuntu on for quite some time. The Internet connection which is accessed via a cable connection was working just fine with firefox. I just got a new computer and it's working fine too. However when I took the old one to my mother-in-law's and tried to connect it to the internet there it wouldn't work! I don't understand why I didn't change any settings or anything before I moved it. Her Cable modem box is slightly different then mine but all the cables and hook-ups are the same so I don't understand why it won't work! Please help me.
justjohn924 is online now Report Post   	Edit/Delete Message

---

### Post by blackhatbrigade on 2008-07-07
Did you power cycle the cable modem?  Cable modems usually retain the MAC address of the last device connected to them and need to be powered off then back on to recognize a new device.

---

### Post by justjohn924 on 2008-07-07
yeah several times

---

### Post by Titan8990 on 2008-07-07
Does your mother-in-law's ISP use PPPoE?

---

### Post by justjohn924 on 2008-07-07
well I'm farely new to all this so don't really know. How would I know if she was?

---

### Post by blackhatbrigade on 2008-07-07
Is your NIC pulling an IP from the cable modem?  You can tell by going to xterm and typing "ifconfig"

if not, you can type "dhclient <iface>" and see if it pulls one.  That's assuming it's wired and not wireless.  If you only have one NIC, then <iface> should be eth0

This is all assuming your ISP isn't doing anything messed up (like mine) and only allowing one MAC address to be active for the internet connection.  It's also assuming your ISP is using DHCP and not static ip's.

---

### Post by snowpine on 2008-07-07
Some ISPs set up the connection to work with a particular computer's MAC address. I have Time Warner, and in order to get it to work with both of my computers, I had to set up my router so that it "fakes" the MAC address of the original computer. Just a suggestion.

---

### Post by blackhatbrigade on 2008-07-07
You did say a cable connection right?  This isn't DSL is it?  (which would be PPPoE)

---

### Post by Titan8990 on 2008-07-07
PPPoE more or less means that you need a username and password to get on the internet.

---

### Post by justjohn924 on 2008-07-07
I don't think it's pulling an Ip address because when I try to open firefox i get the address not found error so is there a way to make it detect one? Because it doesn't seem like the computer is even recognizing that it's plugged up to the router.

---

### Post by blackhatbrigade on 2008-07-07
Goto: Applications -> Accesories -> Terminal

Type: sudo ifconfig
(it'll ask for your password, just put it in)

See if under "eth0" there is "inet addr:xxx.xxx.xxx.xxx" where the x's will be numbers.  DON'T PUT THOSE NUMBERS HERE.  Just see if there are any there.  if there are not, type "sudo dhclient eth0"

if everything is hooked up right and working, it'll pull an ip and you should be good to go.  If not, it may start saying discover over and over.

A couple of other things to check.  Look at the cable modem, there should be "ethernet" or "computer" or something like that label that has a light next to it, is it lit up?  If you can't find that, read the brand and model number and give it to me.  Also check and see if there's a "internet" label with a light next to it, make sure it's lit.  That's all I can think of at the moment, but I'm sure I can come up with more if it's still not working ;)

---

### Post by justjohn924 on 2008-07-07
thank you guys so much. I'm heading over there right now to try this out and if it doesn't work I'm sure I'll be back

---

