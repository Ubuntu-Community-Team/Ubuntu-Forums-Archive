---
title: "Gmail - Evolution - Not fetching mail from pop.gmail.com"
date: 2007-07-25
forum: General Help
---

### Post by Nick w on 2007-07-25
Hi

Right please dont -flame- me.  i have search and search and then tried and tried!
I cant get Gmail to work through evolution and i have tried.

This si what my current settings are.

Identtity page
Email address
[emailaddress]@gmail.com

Receiving Mail page
Server Type:POP
Server: pop.gmail.com
Username: [emailaddress]@gmail.com
Use Secure Connection: No Encryption
Authentication Type: Password

Now i wont bore you with the rest of my seetings but i knows theres a problem because i simply click on Check For Supported Types and i get an Error:

Error While Checking Service - Could not connect to pop server pop.gmail.com

Now i know every one this Not this again but heres what i ahve changed the pop address to to see if i can sort it but it hasnt worked:

pop.googlemail.com
pop.gmail.co.uk
pop.googlemail.co.uk
pop.gmail.com:995
pop.googlemail.com:995
pop.gmail.co.uk:995
pop.googlemail.co.uk:995


Now The internet is working as im typing this. Now i dont think it has anything to do with my setting as it states in the Error - Could Not Connect To pop server pop.gmail.com

Any ideas.  this has had me going for over 2 days solid now!

---

### Post by jnorthr on 2007-07-25
Can you log onto gmail thru internet explorer or firefox ?
Just found this - [http://www.macosxhints.com/article.php?story=20041110192454841](http://www.macosxhints.com/article.php?story=20041110192454841)
i know it's for a mac but you may find it helps.

---

### Post by DoktorSeven on 2007-07-25
Encryption has to be on SSL for gmail, if I recall correctly.  All your other settings look fine.

---

### Post by Nick w on 2007-07-25
> **DoktorSeven said:**
> Encryption has to be on SSL for gmail, if I recall correctly.  All your other settings look fine.

Just enabled SSL and still no luck.

what about uninstalling Evolution and reinstalling it.  is it easy to do?

Any other ideas?
Thanks
Nick

---

### Post by Nick w on 2007-07-25
should i be able to telnet to the pop.gmail.com succesfully?

---

### Post by jnorthr on 2007-07-25
Just found this tip from gmail site: [http://mail.google.com/support/bin/answer.py?answer=13273](http://mail.google.com/support/bin/answer.py?answer=13273) and [http://mail.google.com/support/bin/answer.py?answer=13287](http://mail.google.com/support/bin/answer.py?answer=13287)
looks like you need to make a change to you gmail account in google before you can use pop access.

---

### Post by lisati on 2007-07-25
I might have missed it in previous posts but according to the help on gmail's webstie you have to choose "enable pop in your google mail account"  as per [http://mail.google.com/support/bin/answer.py?answer=13273&hl=en_GB](http://mail.google.com/support/bin/answer.py?answer=13273&hl=en_GB)

---

### Post by Nick w on 2007-07-25
sorry i should have said i have had my gmail as a pop account for years..

heres a picy

[img]http://www.nickwells.plus.com/gmail%20pop.JPG[/img]

i have also spent days tralling through gmails help and google, may be reinstall evolution?

---

### Post by davidjmayo on 2007-07-25
Do you have specific reasons for wanting to use Evolution?

Not a fix but FYI gmail by POP works fine in Thunderbird.

---

### Post by Nick w on 2007-07-25
hetting seriously MIFFED..  Installed thunderbird after uninstalling evolution and still no luck

#Says could not connct to server pop.gmail.com; the connection was refused

---

### Post by Nick w on 2007-07-25
MEGA MIFFEd.

right i have now created a new emaill account with Gmail and still no luck

i have another pop email addy which works fine!

---

### Post by Nick w on 2007-07-25
right i cant set up my gmail account through outlook on another mahcine same error

---

### Post by bedake on 2007-09-22
Hey, I am trying to get this working for my gmail too.  I have POP enabled in gmail and had it working fine for awhile but seemingly out of nowhere it stopped working on me.  I have SSL encryption set and I believe I had not of changed any settings since I had it working.

Does anyone have any tips or a solution to this problem?


No clue if it works in thunderbird or even outlook.  I am slightly reluctant to even switch to those programs, Evolution's calendar and memo features is the main reason I actually use the software.

---

### Post by PmDematagoda on 2007-09-22
Your username has the "@gmail.com" part? I think you shouldn't use that, for my self it's just "my-e-mailaddress", I don't have the @gmail.com, I believe even a simple mistake like that could cause the problem you are talking about.

---

### Post by bedake on 2007-09-22
Alrighty!  I believe that the reason I have been not been able to use POP is because moblock is blocking all of the IPs.

The particular google IPs that are at the bottom of my moblock log are:
```

209.85.133.111
and
72.14.247.109

```

Now I am by no means sure if this is the cause of the problem or not, but if anyone is able to help at all and show me how to allow these ip addresses just to test that would be great!


> **PmDematagoda said:**
> Your username has the "@gmail.com" part? I think you shouldn't use that, for my self it's just "my-e-mailaddress", I don't have the @gmail.com, I believe even a simple mistake like that could cause the problem you are talking about.
Thanks for the response,
I just checked to see if that was the issue and it seems to not have done anything, at least I am still having the same problem T_T

---

### Post by PmDematagoda on 2007-09-22
Moblock is a GUI for the iptables of Linux?

---

### Post by bedake on 2007-09-22
[quote=http://moblock.berlios.de/]
MoBlock is a linux console application that blocks connections from/to hosts listed in a file in peerguardian format (guarding.p2p). It uses iptables ipqueue userspace library and it is very light in resource usage (cpu, ram).
[/quote]

Use it for safer p2p by blocking IP ranges, and is the linux equivalent to peerguardian for windows.

I found this thread:
[http://ubuntuforums.org/showthread.php?t=192559&highlight=gmail&page=39](http://ubuntuforums.org/showthread.php?t=192559&highlight=gmail&page=39)
which seems to cover the issue of whitelisting ports and has quite a bit of members asking the same problem.  I'll have to look through it a bit

---

### Post by silentsoldier on 2007-09-25
Nick w,

I am having the same problem. i've tried it with both thunderbird 1.5 and evolution and BOTH give the same error:

Error:Could not connect to pop.gmail.com. Connection timed out.

Here are my settings in evolution:
Identity tab:

Full Name: firstname lastnme (my real first name and last name, of course)
email address:username@gmail.com(my actual username, of course)
[X ]Make this my default account



Receiving Email tab:

Server Type:POP
Server:pop.gmail.com995(as told to me by neal krawetz in 'Hacking Ubuntu'
Username:username(my real username, of course) No '@gmail.com' has been added.
Use Secure Connection:SSL encryption
Authentication 
Type:Password/Check for Supported Types
[X]Remember password

Sending Mail tab:

Server Type:SMTP
Server:smtp.gmail.com:587
[X]Server requires authentication
Use Secure Connection:TLS encryption
Authentication:
Type:PLAIN/Check for Supported Types
Username:username(my real username, of course)
[X]Remember password

Note:I have POP 'enabled in my account through the 'Fowarding and POP tab: changes have been saved.

If anyone has any solutions I would appreciate it.

silentsoldier:):popcorn::confused::confused:

---

### Post by yorkie on 2007-09-25
Have a look at this guide
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html)

---

### Post by Maestro23 on 2007-09-25
> **yorkie said:**
> Have a look at this guide
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html)

Thanks for that link.  Worked like a charm.:guitar:

---

### Post by Scroobytec on 2007-09-25
Hi All

I am using Evolution (and have used Thunderbird) successfully to send and recieve mail via my G Mail account, in both instances the critical settings are in your account on your PC - they are the port numbers and the authentication as given by G Mail at =>
 
[http://mail.google.com/support/bin/answer.py?answer=13287](http://mail.google.com/support/bin/answer.py?answer=13287)

for Evolution, there is a specific page just for Thunderbird. If  these are left out SORRY NO CIGAR no mail in or out. But with the correct set up you are in business.

Hope this helps.
:KS

---

### Post by bratliff on 2007-10-27
You are right. THunderbird works Evolution does not. I had rather switch than fight.

Robert Ratliff


> **davidjmayo said:**
> Do you have specific reasons for wanting to use Evolution?

Not a fix but FYI gmail by POP works fine in Thunderbird.

---

### Post by bratliff on 2007-10-27
That being said, Thunderbird does not have the same import capabilities as Evolution. It's like starting from scratch.

Robert Ratliff

---

### Post by J_A_B on 2008-03-10
don't know if you have found a solution yet but this worked for me:

under your pop settings replace your username with this:

recent:username@gmail.com

I couldn't download messages as I also access my googlemail account with outlook

here is the google page with the info on:

[http://mail.google.com/support/bin/answer.py?answer=47948](http://mail.google.com/support/bin/answer.py?answer=47948)

Hope this helps

J_A_B

PS New user on Ubuntu and I love it!

---

