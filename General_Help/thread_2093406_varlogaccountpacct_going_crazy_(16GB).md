---
title: "/var/log/account/pacct going crazy (16GB)"
date: 2012-12-10
forum: General Help
---

### Post by BramWillemsen on 2012-12-10
Hi,

After being away from the office computer for a week I returned today and saw something was wrong. I got the message that the /var partition was almost full. 

After examining it turns out that the /var/log/account folder is absolutely large (16.5 GB). After googling a bit I was informed that I could delete all the files that ended in like .1.gz, .2.gz etc. But after I did that the 'pacct' file simply grew by exactly the size of the files I deleted. And it is still slowly growing. 

Can someone suggest me what I should do ? I keep getting messages that /var is almost full.

Bram

---

### Post by Cheesehead on 2012-12-10
Do you have the Process System Accounting (acct) package installed? If so, is that intentional?

Look through the list of logs. Is the curent log vastly larger than the rest? Are the logs actually rotating the way they are supposed to be?

---

### Post by rnerwein on 2012-12-11
> **BramWillemsen said:**
> Hi,

After being away from the office computer for a week I returned today and saw something was wrong. I got the message that the /var partition was almost full. 

After examining it turns out that the /var/log/account folder is absolutely large (16.5 GB). After googling a bit I was informed that I could delete all the files that ended in like .1.gz, .2.gz etc. But after I did that the 'pacct' file simply grew by exactly the size of the files I deleted. And it is still slowly growing. 

Can someone suggest me what I should do ? I keep getting messages that /var is almost full.

Bram
the reason is - when you type one command then internal are a couple commands are running. 
try following: accton off
accton on
ls -l | more
cd /tmp
accton off
now have a look at your pacct file:

lastcomm -f /var/log/account/pacct | more

surprised what's going on in seconds ?
 but be happy not working on a security system C or B class where although systemcalls are loged ( kernel got special hooks)
cheers

---

