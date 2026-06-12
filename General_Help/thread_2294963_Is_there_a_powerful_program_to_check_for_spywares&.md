---
title: "Is there a powerful program to check for spywares&amp;malwares and viruses"
date: 2015-09-15
forum: General Help
---

### Post by Ehssan_Dannouf on 2015-09-15
I received an e-mail yesterday from an anonymous person using one of my e-mail addresses addressed to the same e-mail saying words and sentences unpolite and unwanted. I read the e-mail, suspected the message, and immediately tried to change my password as it is obvious my e-mail has been hacked. The wonderful thing that when I changed the password of my website's control panel, I have been blocked either from enter my website or from logging into my control panel. I called a trustworthy person to check for the website on another IP and another wireless, and he approved twice the website had been working well...! I tried again and again, finally the website worked and everything was going well. 

However, I still suspect the message sender, the message itself, and the pc from containing spywares as a consequence. I installed firewalls and anti-spam on my e-mail server, it seems they are working well; but how to be sure, I am not followed any more by that spammer, and my webserver has not injected with some worms or spyweres. 

How to be sure that my wireless has not been also hacked; can you suggest a perfect-like program to answer this puzzle! 

Awaiting for your help and support,
Thanks a lot in advance, 

Cheers,

Ehssan Dannouf

---

### Post by howefield on 2015-09-15
It is trivial to send you an email that looks on the surface like it came from yourself, it's a common spammer trick to fool the gullible and unaware into opening it. Did you check the email headers ?

---

### Post by efflandt on 2015-09-15
You need to learn how to check full e-mail headers since the From: address is easily faked by spam, viruses, worms, etc. or basically anyone who knows how. So if something seems fishy, check full mail headers. Although, those can be forged to at some point past where it arrives at a known mail server at your ISP. I have seen some spam like that with forged headers besides forged From:

Another example of a reason to check mail headers, once I received a strange e-mail from the brother of a friend. But it looked like either his computer or e-mail account had been cracked, because the the e-mail originated from a web app in Argentina and he is in California, USA.

Also learn how to use the **whois** command in the shell, because that can possibly tell you who owns a domain, whether it is a newly registered (suspicious) domain, or who owns an IP address. Although, sometimes domain ownership info may be private or bogus. I recently got a text message on Sept 13th that said it was from [EMAIL="customer@chase-identity.com"]customer@chase-identity.com[/EMAIL] with a link to a website. Some people might think that was from Chase Bank, but the domain had just been registered early Sept 13th and the last IP that responded to a tracepath to the website was in South Korea.

---

### Post by Ehssan_Dannouf on 2015-09-15
hi [**[COLOR=#990303][B]howefield**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=186490")! Thanks for reply!
Actually my e-mail program automatically preview the e-mail message. So, I looked from the small preview window. For the message header, there was no message header. Just a few sentences meant that I have an access to your e-mail addresses and your web server... Again, the sender has the same e-mail address that I had. Eventhough, I thought it was me who send the message...so!!!

I hope anybody could help me concerning these spamers because I am getting bored of them...! 
Thanks again,
cheers!

---

### Post by Ehssan_Dannouf on 2015-09-15
Thank you [**[COLOR=#000000]efflandt[/COLOR]**]("http://ubuntuforums.org/member.php?u=937632")!

Concerning these issues, I think they have been solved now because I installed programs and firewalls to stop the hackers attacks. The problem now is how to scan my pc and be ensured that these spams are gone completely from the host/guest pc. Do you have any suggestions? 

Many thanks to you again,
cheers!

---

### Post by matt_symes on 2015-09-15
Hi

I received one myself the other day from the TLD "no" or Norway.

Checking the headers is great advice and you are not alone in getting them.

Kind regards

---

### Post by Ehssan_Dannouf on 2015-09-16
Yes I see! the problem is solved now. Thank you friends for your assist...

> **matt_symes said:**
> Hi

I received one myself the other day from the TLD "no" or Norway.

Checking the headers is great advice and you are not alone in getting them.

Kind regards

Cheers all,
Ehssan Subhi Dannouf

---

### Post by jim_deadlock on 2015-09-16
It's always a good idea to stay secure. However, from what you describe it seems like the server's firewall temporarily blocked your IP address. This can happen for various reasons such as several consecutive failed logins, too many mailbox collections within an hour etc.

---

### Post by ian-weisser on 2015-09-16
> **Ehssan_Dannouf said:**
> However, I still suspect the message sender, the message itself, and the pc from containing spywares as a consequence. 

Checking e-mail headers is indeed the first thing you should do.

If, someday, you discover that your system has actually been compromised, there is no magic application to purge the intruder and repair their damage - you must take your system offline at once, reinstall, and recover your data from backups made before the intrusion.

Good security is much more than a one-time event. It's planning and preparation and good habits and monitoring and more....

---

### Post by Sweet_Baby_Jamie on 2015-09-16
Alot of people use **ClamAV** (it's in the Ubuntu repositories) to scan for viruses and malware.  Mostly I think it's to protect their friends who use Windows from getting anything passed along to them in forwarded e-mails. If it's software you're looking for, that's the one alot of Ubuntu users rely on.

---

