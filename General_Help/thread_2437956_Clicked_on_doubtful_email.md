---
title: "Clicked on doubtful email"
date: 2020-03-03
forum: General Help
---

### Post by Robbyx on 2020-03-03
I received an email from Mark (trackrack12.co.uk-mail.id.7686@nycmail.com) stating he is interested it buying an item from me. It was headed as from ebay. When I clicked on review request through a VPN I use, it  took me to a site I did not recognise. It was not an Ebay clone. 

The address for the review request was:
[https://app.getresponse.com/](https://app.getresponse.com/) 
There was more in the link that I have not put here. 
The full address sent me to:
###[https://ebay.claim-nectar.club/ws/review?UsingSSL=1&UserId=&co_partnerId=2&siteid=3&ru=https://review.offer/ws/ISAPI.dll%3FM2MContact%26item%3D4018895281246%26%26redirect%3D0%26qid%3D18895261106%26requested%3Dyoppomgoal%26guest%3D1&pageType=3270](https://ebay.claim-nectar.club/ws/review?UsingSSL=1&UserId=&co_partnerId=2&siteid=3&ru=https://review.offer/ws/ISAPI.dll%3FM2MContact%26item%3D4018895281246%26%26redirect%3D0%26qid%3D18895261106%26requested%3Dyoppomgoal%26guest%3D1&pageType=3270)

My mail is pop3 using Thunderbird. My browser is Firefox.

I checked my mail at ebay and there was no email from Mark. So it seems it was some type of scam. 

As a reaction to the risk of ransomware or similar, I have run a fresh  backup of my data using Backup and have changed the permissions to access and view  the backup data files  to only apply to the owner. I have switched on the UFW firewall with options:

Profile Home
Status ON
Incoming Deny
Outgoing Reject

As I am using Ubuntu 18.04 I assume that an attempt to plant an effective virus has  not have been successful. 

What more should I do?

---

### Post by Tadaen_Sylvermane on 2020-03-03
Whatever you can but you are generally safer with Linux than Windoes for stuff like this. 99% of their attack methods are for windows and have no effect on linux. There is always that chance though.

---

### Post by Robbyx on 2020-03-03
Since posting the message I logged out of the system but found that I could not get a internet connection and the VPN was not working. I have therefore gone to a timeshift backup from earlier in the day. That worked and repaired the fault. It could have been due to me disconnecting the external HD with the latest back up on it. I started the system without the Ext HD connected and this gave startup problems because of missing drives. But it  could also be connected with the scam. In any case the restoration worked and the access problems disappeared. Thinking about it, maybe the cause was the firewall settings as  I set it to reject outgoing traffic.

---

