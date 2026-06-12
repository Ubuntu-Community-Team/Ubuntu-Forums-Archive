---
title: "Hacker!!!"
date: 2007-07-31
forum: General Help
---

### Post by Lacrimstein on 2007-07-31
So today I was downloading the Flash Player for Linux, left the download page open in Firefox, minimized it and started to install it. About a minute later, I saw the VPN icon appear in the notification area. Then, the active window switched to Firefox, and the "Save As" dialog appeared, The default file name (install_flash_player_9_linux.tar.gz) was erased, substituted for random keystrokes, and saved. I quickly disconnected the user, without writing down the IP address (so that he didn't have time to do anything else). I'm wondering if you guys know of a command which would show me the list of the recent users/IP addresses logged on to my machine so I would know who the attacker was?

---

### Post by kerry_s on 2007-07-31
look in /var/log/?

---

### Post by charper_99 on 2007-07-31
What VPN software are you running that shows a live screen of the action going on? - every one I know of allows multiple users.

---

### Post by Sawa4.CoM on 2007-07-31
OMG . 

dose linux have ahackers to hack also ?

we left winXP and used the Linux for more securing , thats sux

---

### Post by lisati on 2007-07-31
> **Sawa4.CoM said:**
> OMG . 

dose linux have ahackers to hack also ?

we left winXP and used the Linux for more securing , thats sux

Usually only if you let them....Linux's user/password is generally stronger than WinXP

---

### Post by Sawa4.CoM on 2007-07-31
> **lisati said:**
> Usually only if you let them....Linux's user/password is generally stronger than WinXP



i changed to linux on my lap top 

coz iam arabian company for webhosting , and iam areseller  who sell resrvers from LT.

i was under atack daily 

thats why i changed to linux , but iam not understack over 6 days when i changed ..

how can i secure my linux PC is there steps i need to do ?

thanks

---

### Post by Lacrimstein on 2007-07-31
:) Thanks for the fast replies!
First of all, I should have made clear that the guy was using Remote Desktop, not just a random VPN.
Second, all the log entries for today (July 30) are missing :confused:

So the question still is, is there any command/file that contains the recent users remotely logged on?

This incident made me realize that I have REALLY been neglecting security...

---

### Post by kevinlyfellow on 2007-07-31
> **Sawa4.CoM said:**
> OMG . 

dose linux have ahackers to hack also ?

we left winXP and used the Linux for more securing , thats sux

Just make sure you have a strong password.  Easy to guess passwords are insecure, because, well they're easy to guess.  Random passwords are always the best.

---

### Post by kevinlyfellow on 2007-07-31
> **Lacrimstein said:**
> :) Thanks for the fast replies!
First of all, I should have made clear that the guy was using Remote Desktop, not just a random VPN.
Second, all the log entries for today (July 30) are missing :confused:

So the question still is, is there any command/file that contains the recent users remotely logged on?

This incident made me realize that I have REALLY been neglecting security...

I'm not sure on getting the ip address without /var/log/auth.log but maybe you can check all the users bash histories (~/.bash_history) to see what the cracker did.

---

### Post by eentonig on 2007-07-31
security is only as good as it's weakest link (usually, that's the user). Why do you allow everybody to access your computer via rdesktop? And what was your password policy on accessing it?


To be honest. I would recommend you to reinstall completely. If he had the time AND possibility to remove the logfiles, there's not really any way to tell you how far you've been compromised. But he did get enough privileges to screw you big time. Because those logfiles need sudo power to remove.

---

### Post by Lacrimstein on 2007-07-31
Yes, I'll do just that and I will be more aware of security from now on

---

### Post by sefs on 2007-07-31
and always use non-default ports for vpn/vnc/rdesktp/ssh/ftp/  every thing.

---

### Post by nitro_n2o on 2007-07-31
you might want to get a firewall also i use shorewall it's good

---

