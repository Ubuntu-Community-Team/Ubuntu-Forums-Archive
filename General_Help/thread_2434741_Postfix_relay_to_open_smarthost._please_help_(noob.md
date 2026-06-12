---
title: "Postfix relay to open smarthost. please help (noob alert)"
date: 2020-01-10
forum: General Help
---

### Post by wodgey on 2020-01-10
I have a situation where my ISP provide me access to their SMTP servers but to use them I have to be sending from an IP address that they provide. (i.e. - I can send out emails when I am at home but not when I am away from the property or using mobile-data on my cell-phone)
Their SMTP server does NOT require any authentication other than inspecting the originating IP address that I am sending from. 

I had the idea of placing a Raspberry Pi computer at my home and installing ubuntu/postfix to it, then using that Pi as a relay to hand-off my emails to my ISP's SMTP server, however I do not want my Pi to be an "open relay".

I need help configuring the main.cf & master.cf to acchieve this goal.

I would like my Pi to block inbound connection that haven;t authenticated (I am happy for it to use the default user on ubuntu, that doesn;t matter to me. Although I am happy to follow a different route if easier/better-practise) but forward everything to my ISP's servers for outbound sending.

I have a static IP address at my home and I have created a rDNS and DNS entry for my ip-address and URL.  > let's pretend I have created mysmtp.my-house.com and pointed it at my external ip address of 91.92.93.94 (these are not accurate but I can edit later to fit correct details).
Lets pretend that my ISP prove me access to smtp.isp.net (again, not using correct details) which I do not need to authenticate with.

I have ubuntu 19.10 istalled and postfix is up and running.

Any help would be greatly appreciated.

---

### Post by TheFu on 2020-01-10
Don't make this so hard.

Just run a VPN server at home, then connect to that from any portable devices when away.  Then send email as usual.  The emails will appear to come from your home and pass through the ISP mail relay just fine.

Having a VPN server at home has other good uses too, like if you want to run nextcloud or other self-hosted services, then you don't need to worry nearly so much about being hacked over the internet.  Only 1 port open, though you could open 2 ports - ssh being the other.  Of course, ssh access when remote should only work with keys, never passwords.

Remote access of any sort dependent on passwords is a total, complete, security failure.  Just don't.

---

### Post by wodgey on 2020-01-12
Oooooh, good thinking. I like that. 

However, I am actually setting this up for a technophobe. But I am sure that I could teach them how to connect to a vpn for the purposes of sending an email.

on second thoughts though, I was going to use gmail for the sending/receiving of email through a separate pop3 account, just so that it is easier to re-install when setting up a new phone/device and without the need to export/import messages.

---

### Post by TheFu on 2020-01-12
> **wodgey said:**
> Oooooh, good thinking. I like that. 

However, I am actually setting this up for a technophobe. But I am sure that I could teach them how to connect to a vpn for the purposes of sending an email.

on second thoughts though, I was going to use gmail for the sending/receiving of email through a separate pop3 account, just so that it is easier to re-install when setting up a new phone/device and without the need to export/import messages.

Whenever anyone is remote, they should be using a VPN.  Never trust other-peoples' networks. NEVER.

---

### Post by SeijiSensei on 2020-01-12
> **wodgey said:**
> on second thoughts though, I was going to use gmail for the sending/receiving of email through a separate pop3 account, just so that it is easier to re-install when setting up a new phone/device and without the need to export/import messages.
Do not use POP3. Choose IMAP instead. Then all the mail remains on the server and can be accessed from any device. You can kludge some POP3 accounts to leave the mail on the server, but IMAP4 is a much better protocol in this case.

---

