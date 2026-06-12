---
title: "ubuntu maybe compromised..."
date: 2007-07-26
forum: General Help
---

### Post by vbmds on 2007-07-26
I'm running ubuntu 7.04 with all updates applied.

Over the past 2 weeks I've managed to nearly use up the 10GB of my internet plan for this month, and I've only been basically checking emails...so averaging 750MB per day of usage is a bit alarming :confused:

The assumption has been that the linux box is ok and not the source of the usage. However the XP machine has been gone over with a fine toothed comb and has come up clean, so that only leaves the linux box unchecked.

What I'm after is advice on how I go about checking out my ubuntu laptop to see if its been compromised, or its got something running that I am not aware of starting. In this situation I'm a newb, so need some handholding with this...:lolflag:

Thanks in advance

---

### Post by por100pre1 on 2007-07-26
Are you using a WiFi Router? That is often the cause of those problems... If so maybe somebody else is using your internet plan.

---

### Post by por100pre1 on 2007-07-26
> **vbmds said:**
> What I'm after is advice on how I go about checking out my ubuntu laptop to see if its been compromised, or its got something running that I am not aware of starting. In this situation I'm a newb, so need some handholding with this...

If you feel you need to check your Ubuntu installation you can use a packet sniffer but let's check for **rootkits** for now. 

Install chkrootkit and rkhunter in a terminal:

```
sudo aptitude install chkrootkit rkhunter
```

To use them in terminal:

```
sudo chkrootkit
```

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

Hope this gives you some peace of mind. :)

---

### Post by vbmds on 2007-07-26
Thanks for the replies.

The AP was the 1st thing to be looked at, and thus the XP machine.

The linux machine uses wired lan to the modem hub so wifi is not related.

Will do as suggested and will post results.

---

### Post by vbmds on 2007-07-26
ok, both apps run with nothing being flagged except the /dev folders which appear to be false positives according to other posts.

---

### Post by pointone on 2007-07-26
Wait... go back to WiFi for a second. Do you have a wireless router? Is WiFi enabled on it? If so, the computers connected to it are irrelevant; you'll need to secure it regardless.

You should also be able to check your router's logs to see if any unusual locations are being accessed frequently.

---

### Post by rjfioravanti on 2007-07-26
> **vbmds said:**
> Thanks for the replies.

The AP was the 1st thing to be looked at, and thus the XP machine.

The linux machine uses wired lan to the modem hub so wifi is not related.

Will do as suggested and will post results.

I think you misunderstood this

It is possible that somebody else gained access to your wireless router and is accessing the network through your router. Do you have a wireless router? Is it password protected? Can you check if it has offered IP addresses to computers you do not recognize?

---

### Post by vbmds on 2007-07-26
To clarify my particular lan setup, I do not have a router. We run a wifi Access Point (AP) which is set to Infastructure, WPA-PSK with passphase, and encryption. This AP is plugged into the modems hub and this AP is how the XP machine accesses the LAN. The ubuntu machine plugs the modems hub via cat5 cable.

Yesterday the AP, and the XP machine, were powered down with no change in the usage climb.

Hope this helps...

---

### Post by rjfioravanti on 2007-07-26
> **vbmds said:**
> To clarify my particular lan setup, I do not have a router. We run a wifi Access Point (AP) which is set to Infastructure, WPA-PSK with passphase, and encryption. This AP is plugged into the modems hub and this AP is how the XP machine accesses the LAN. The ubuntu machine plugs the modems hub via cat5 cable.

Yesterday the AP, and the XP machine, were powered down with no change in the usage climb.

Hope this helps...

If you power down linux... is there a change in the usage climb?

---

### Post by nalmeth on 2007-07-26
There is a cool app for visually monitoring your incoming/outgoing connections, its called etherape.

Install it, and run it from the applications menu

Here is a list of some other network analysis tools, maybe they will be of use to you:
[http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html](http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html)

Most of this is overkill for you, but since I don't have any other ideas, I think you'd probably like to try anyway.

Are you living with anyone that may be using your PC or internet connection?
Good Luck!

---

### Post by vbmds on 2007-07-26
The simple answer is  - Yes

Thus the reason for this thread...

---

### Post by Jonne on 2007-07-26
Have you ever enabled ssh?

---

### Post by vbmds on 2007-07-26
Not that I'm aware of, how would I check to be sure 1 way or the other?

---

### Post by rjfioravanti on 2007-07-26
> **vbmds said:**
> Not that I'm aware of, how would I check to be sure 1 way or the other?

ssh localhost

---

### Post by sloggerkhan on 2007-07-26
I think the real question is what are you doing on ubuntu? Do you leave Gaim or Firefox open? Do you have it automatically download updates? Have you been installing lots of new software from the repos? I know my Ubuntu install is almost always 'receiving' packets when it's plugged in the the net, and almost never sends any. Of course my comp I hook up to 4 emails (including an exchange server) and I leave evolution and gaim open near all the time.

---

### Post by rjfioravanti on 2007-07-26
> **sloggerkhan said:**
> I think the real question is what are you doing on ubuntu? Do you leave Gaim or Firefox open? Do you have it automatically download updates? Have you been installing lots of new software from the repos? I know my Ubuntu install is almost always 'receiving' packets when it's plugged in the the net, and almost never sends any. Of course my comp I hook up to 4 emails (including an exchange server) and I leave evolution and gaim open near all the time.

This wouldnt give him 750 megs a day.. unless he was downloading torrents or something

---

### Post by jerryz on 2007-07-26
This smacks of the wifi being breached. Usually you can check for addresses assigned by the wifi router. it sounds like you should have only one? If there's more then there are more devices on the router.

---

### Post by vbmds on 2007-07-26
Indeed, the wifi was our 1st suspect also. We do not have a router, but use an Access Point instead. The AP is set with maximum security settings. Also, powering down the AP made NO difference to the continued increase in usage.

My ubuntu updates are set to Notify only, so nothing will be automatically downloaded without my express permission - ah all those years of mistrusting Micrsoft lol

Nothing has been installed in the past month, other than updates. FFox is closed after each use. Kopete does stay running all the time, but 99% of the time its logged out as MSN Live has kicked when it logs in on the XP machine.

The ubuntu machine has been left running to allow quick access to a Laser printer, and to check email etc when the AP has been either turned off, or the XP machine is just plane slow. Other than that it has not been used for anything. I certainly have not been near any P2P apps so it should not be that.

ssh localhost returns ...port 22: connection refused

---

### Post by rjfioravanti on 2007-07-26
> **vbmds said:**
> Indeed, the wifi was our 1st suspect also. We do not have a router, but use an Access Point instead. The AP is set with maximum security settings. Also, powering down the AP made NO difference to the continued increase in usage.

My ubuntu updates are set to Notify only, so nothing will be automatically downloaded without my express permission - ah all those years of mistrusting Micrsoft lol

Nothing has been installed in the past month, other than updates. FFox is closed after each use. Kopete does stay running all the time, but 99% of the time its logged out as MSN Live has kicked when it logs in on the XP machine.

The ubuntu machine has been left running to allow quick access to a Laser printer, and to check email etc when the AP has been either turned off, or the XP machine is just plane slow. Other than that it has not been used for anything. I certainly have not been near any P2P apps so it should not be that.

ssh localhost returns ...port 22: connection refused

if you power down the ubuntu machine what happens to the usage?

---

### Post by vbmds on 2007-07-27
As per a post on page 1, the usage stops when the ubuntu machine is shut down...or just has the network cable removed.

---

