---
title: "They violated me in the wifi!"
date: 2006-08-30
forum: General Help
---

### Post by anubix on 2006-08-30
I've been using ubuntu now for about 8 months.  I live across the street from the local community college campus.  Last night my 128bit wep key must have been cracked and my lan molested (like michael jackson).  i am using a linksys b/g router, my toshiba tecra 8100 laptop (ubuntu), an hp deskjet 5850 (wireless), and 2 other winblowz boxes.  I came home to find both roommates windows boxes screwed six ways from sunday and my printer had printed colored jibberish on the 80 or so sheets in the tray.

In an effort to better understand what happened to me, and the process involved in doing so, i read the 2 part wep article from securityfocus [http://www.securityfocus.com/infocus/1814](http://www.securityfocus.com/infocus/1814) (part 1) which covers the new generation tools, and [http://www.securityfocus.com/infocus/1824](http://www.securityfocus.com/infocus/1824) (part 2) which covers how to capture packets quicker.
Herein lies my question: i would like to re-create this attack
to use aircrack, u must first capture packets to a file.
in order to capture packets quicker, securityfocus says to use aireplay
when i run aireplay -3 -b [router's ap's mac] -d [roommates windows mac]-h [ubuntu's orinoco mac (i have also tried placing the other windows box here too)] eth1, i get back:
Saving ARP requests in replay_arp-0829-183418.cap
You must also start airodump to capture replies.
So I run: airodump eth1 airdumpout 3 (ap is on channel 3)
after airodump says i've got 500,000 packets or so, i ctrl+c aireplay and airodump, then import the file into aircrack:  aircrack -a 1 -f 4 -b 00:0F:66:B9:52:FA airdumpout.cap.  Now the big finish: when aircrack opens the .cap file of over 500,000 files only 1000 of them are "IVs"es (i need 500,000 of those)... and in that respect aireplay hasn't increased the rate at which valueable packets are captured.
what am i doing wrong?
(i've figured out this much all on my own so far, and am willing to figure out more, i just need a push in the right direction)

pz

---

### Post by viciouslime on 2006-08-30
> **anubix said:**
> I've been using ubuntu now for about 8 months.  I live across the street from the local community college campus.  Last night my 128bit wep key must have been cracked and my lan molested (like michael jackson)...

I don't think comments like that are going to get you very far... but I will see if I can help you anyway. Firstly instead of
```
aireplay -3 -b [router's ap's mac] -d [roommates windows mac]-h [ubuntu's orinoco mac (i have also tried placing the other windows box here too)] eth1
```

Try

```
aireplay -3 -b [router's ap's mac] -d [roommates windows mac]-h [ubuntu's orinoco mac (i have also tried placing the other windows box here too)] eth1 1
```

That extra 1 on the end will capture only weak IVs so you don't have to waste space capturing EVERYTHING the car sees since most of it is no use to you at all.

Secondly, in order to generate more weak IVs you're going to have to look into packet injection, however, you can only do this with certain cards, what chipset are you using? It looks like it might be an IPW2100/2200? They're usually eth1. If so, packet injection isn't possible and you would have to buy an atheros or prism based card (there are some others that work too but I can't remember their names). Also, anything that uses madwifi drivers usually works I think.

---

### Post by yopnono on 2006-08-30
Well I know is easy to crack any wep key. And if I were you, I would check the tools forums and ask the questions there. It could be drivers, settings

---

### Post by zhenya on 2006-08-30
Not to dissuade you from a good learning experience, but I hope that in addition to re-creating the attack, you also upgrade to a WPA AP.  WEP has been known for some time now to be insecure.

---

### Post by Slychilde on 2006-08-30
Question for you: why don't you set your router to accept only certain wireless mac addresses and deny all others? Albeit, that would only work if you don't let friends come over with laptops regularly and you feel lazy.

Would that work?  I've always been curious, as I live in the sticks so leave no wep/wpa, as it's just too much of a headache.  I've only had 1 person try to get on my network and I just banned their mac.

---

### Post by zhenya on 2006-08-30
Mac address filtering ultimately won't end up making you more secure, while just adding an additional hurdle to adding new users to your network.  Anyone who is hacking your WEP will almost certainly also be able to capture you MAC address, and spoof it to allow them to connect.

---

### Post by viciouslime on 2006-08-30
Yeh, mac filtering is pretty pointless. If you do upgrade to WPA, make sure you set your ESSID to something very unique. Also, use a random string of letters and numbers over 20 characters in length for your key, then you'll be pretty much uncrackable.

---

### Post by Slychilde on 2006-08-30
Oh, how little I know. :)

---

