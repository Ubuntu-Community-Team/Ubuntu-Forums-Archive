---
title: "Evolution - Global Address List"
date: 2007-12-24
forum: General Help
---

### Post by dkinfl on 2007-12-24
Hello!  I just made the switch from Vista to Ubuntu, so far all is well.  However there is one issue that is holding me back.  In evolution mail, everything works except for the global address list.  We run Exchange 2003 in a Windows 2003 Native Domain.  When I attempt to access the GAL, it prompts me for my network password.  I enter it and it prompts me again.  The prompt never goes away and I never get the list.  I have configured it several different ways, with and without the address for the global catalog, etc.  Has anyone come across this behavior?

---

### Post by polaris20 on 2007-12-26
I have the same exact issue, same environment. Weird thing is, a co-worker is running SuSe 10.2 (yuck) and his Evolution w/ Exchange connector is working fine. 

Anyone have any ideas for us?

---

### Post by ChrisMoore0908 on 2007-12-27
I also have exact same issue. Interestingly, I am running both Evolution and Outlook under Crossover 6.2. Both are accessing the same MS exchange server. Sure enough, Outlook performs ok, but Evolution persistently asks for the GAL password.

---

### Post by agibby5 on 2007-12-27
Same here... I'm even prompted when sending mail from my Gmail account.  I'm not sure why I would be prompted for my GAL password when sending from Gmail???

---

### Post by TheOrangeRider on 2008-01-18
I don't know about Gmail, but for me I had to make sure I was using a "Secure Password" as the Authentication Type when connecting to my Exchange server, otherwise it kept asking for my password when trying to access the GAL. I also noticed that I had to re-enter my Global Catalog server name, which got erased after I changed my authentication settings.

Hope this helps!

---

### Post by nlinux on 2008-01-23
Exact same issue here, it's basically been doing it since the last Evolution update was pushed down.  I don't know what got changed, but it needs to be reverted.

---

### Post by Jason Green on 2008-01-31
This worked for me

gjarboni
November 8th, 2007, 03:50 AM
This post could be related to an Ubuntu bug filed at: [https://bugs.launchpad.net/ubuntu/+source/evolutio](https://bugs.launchpad.net/ubuntu/+source/evolutio) n-exchange/+bug/131616 . ---------------------------- . .
I disabled this prompt by going to Edit, Preferences in Evolution then clicking the Autocomplete icon. Under my Exchange email address, I unchecked "Global Address List". Give it a shot and see if it works for you. I'm attaching a screen shot of the window I'm talking about (with my email address blacked out).
msegal

Credit goes to gjarboni, thanks for your help!

---

### Post by frozenjim on 2008-02-04
> November 8th, 2007, 03:50 AM
This post could be related to an Ubuntu bug filed at: [https://bugs.launchpad.net/ubuntu/+source/evolutio](https://bugs.launchpad.net/ubuntu/+source/evolutio) n-exchange/+bug/131616 . ---------------------------- . .
I disabled this prompt by going 03to Edit, Preferences in Evolution then clicking the Autocomplete icon. Under my Exchange email address, I unchecked "Global Address List". Give it a shot and see if it works for you. I'm attaching a screen shot of the window I'm talking about (with my email address blacked out).
msegal

Link is gone.  But from your description you have disabled the Global Address List.  That just doesn't help in a corporate environment.

I, too, am using Exchange 20003 on my domain.  The same dual-boot PC uses exactly the same account to access Exchange: one via Linux/Evolution and the other via WinXP/Outlook.  Gutsy Gibbon is fully updated.  

Outlook works perfectly.  Evolution works perfectly EXCEPT that any attempt to access the Global Address List produces the prompt : "Enter Password for Global Address List (James)".  No password will allow me to use the Global Address List.

I have tried to manually enter GAL information into Evolution setup, but can find no way to get the darned thing to appear.

Problem occurs on ALL Linux/Evolution machines - not one or two.

To be clear:  
[LIST]
[*]GAL works fine in Outlook, not in Evolution.
[*]Everything else works great in Evolution.
[*]Problem is universal
[/LIST]

This is a critical flaw and has destroyed the potential to use Evolution and therefore, Linux in the corporate workplace.  How do we escalate this before we all have to remove Linux from the desktop?

---

### Post by agibby5 on 2008-02-05
I'm also having this issue.  Everything is working great except Global Address List.

---

### Post by ephro on 2008-02-05
Make sure that you are linking to the Domain Controller (DC) or Active Directory server (AD) and not the exchange server. If you aren't sure what your DC or AC address is, one of your sysadmins should be able to tell you pretty quickly.


ephro

---

### Post by nlinux on 2008-02-07
no you shouldn't have to enter the AD or Domain controller server at all, this is all handled through OWA just fine.  The Address book was working correctly before the last update that was pushed down from ubuntu for Evolution.  I realize it was a bug fix/security fix, but it created a major bug that causes me lots of pain!:confused:

---

### Post by agibby5 on 2008-02-07
I really hope this is fixed relatively soon.  I really hate having to open up a virtual machine to vpn (contivity) into the work network, rdc to my machine, and then finally open outlook just to find someones email address...

---

### Post by prostar on 2008-02-08
If you followed the link properly, or looked up the bug # (131616), you would see the simple solution is to edit your "receiving options" for the account to use only the server name (server) instead of (server.domain.tld) for the GAL.

Regards

---

### Post by rwhitt on 2008-02-08
have you found a fix for your problem yet or do you want my advice

---

### Post by nlinux on 2008-02-09
> **prostar said:**
> If you followed the link properly, or looked up the bug # (131616), you would see the simple solution is to edit your "receiving options" for the account to use only the server name (server) instead of (server.domain.tld) for the GAL.

Regards

Yep already saw that and it doesn't work.

---

### Post by frozenjim on 2008-02-09
Using Small Business Server; AD is the same machine as the Exchange server.

Server name is "geeky".  That's what I enter.

Not much to do wrong.  I enter "geeky" as the server name, and that's also the DC and the AD controller and the PDC; it is everything so it's tough to screw it up.

I suspect a problem with Evolution.

Anyone found a fix?  I'm about ready to give it up.  Taking a pounding from the pro-windows folks.

---

### Post by rwhitt on 2008-02-12
have you ever been able to view you global contact list?

---

### Post by prostar on 2008-02-12
> **nlinux said:**
> Yep already saw that and it doesn't work.

I would suggest you find some more server names to try.  I have used a couple different versions of Evolution with a couple different versions of Exchange without difficulty.  My current setup took some reading to find the solution I mentioned above, but aside from that the Catalog server was neither the mail server nor the DC.  It was some other random server I just happend to find while browsing the network.  I am using Evolution 2.12.1 with Exchange 2003 currently.  

Good luck...

---

### Post by frozenjim on 2008-02-13
> **rwhitt said:**
> have you ever been able to view you global contact list?

No.  Never in Evolution.  I have rebuilt the Small Business Server once thinking that it was an error there.  But the symptoms are the same; no problem in Outlook, no Global Contact List in Evolution.

Curiously, I also notice that even though I have checked "Save my password" at login, I have to reenter the password everytime it connects to Exchange.  Maybe this is related.

---

### Post by frozenjim on 2008-02-14
OK.  I have solved it for my system.

Here is a basic background of my domain:
[LIST]
[*]Doman name is "flower"
[*]Mail Server name is "geeky"  
[*]To get to OWA I go to [https://geeky/exchange](https://geeky/exchange)
[/LIST]

Here are the settings that work:
[LIST]
[*]Account Preferences / Receiving Email / Username: ```
william
```
[*]Account Preferences / Receiving Email / OWA URL:**```
https://geeky/exchange
```**
[*]Account Preferences / Receiving Options / Global Catalog Name: **```
geeky.flower
```**
[/LIST]

I restarted Evolution and it works.  Finally.

GAL doesn't work as well in Evolution, you have to actually SEARCH for a name in the GAL.  However autofilling address works great when sending an email.  It is enough to make this go in my environment.

Thanks to bug list article: [COLOR="Navy"][http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg143782.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg143782.html)[/COLOR]

Hope this helps everyone!

Note:  I changed my server settings a bit and lost my Global Address List.  I had to change the Global Catalog Name from geeky.flower to geeky.  I SUSPECT it had something to do with the DNS changes I made on the server.  But anyhow, it still works great now.

---

### Post by nlinux on 2008-02-28
> **rwhitt said:**
> have you ever been able to view you global contact list?

Yep, I could view it fine until the last Evolution update was pushed down in the Updates.

---

### Post by francis.06j on 2008-04-14
I've noticed a lot of people have had this problem. To fix this in my small test network i added the exchange server to the /etc/hosts file. 

under account preferences
global catalog server name : server.domain.local

then add ip address and server.domain.local to /etc/hosts

This seemed to fix all my problems. I'm a bit of a newb to linux and the forum. Have used suse before but not great with linux. Hope i could help a little bit tho

---

### Post by dominics on 2008-04-14
I am having the same issue with the GAL.

---

### Post by dominics on 2008-04-14
interesting...

I just changed the GAL name for the IP and it worked. The password prompt came up, but when I entered my password it finally accepted it and disappeared. I was then able to search the list without issues.

Dom

---

### Post by fisho on 2008-06-18
Thanks man i didn't think of that have been trying every tute on this the net all day used ip of server bingo all ok.

---

