---
title: "i need to change my password saver software"
date: 2020-02-18
forum: General Help
---

### Post by Skaperen on 2020-02-18
my current password saver software does not have a means to save the email address used to signup with when it is different than the login name at that site.  so i am looking for something that can do that.  and it must do its own (strongly encrypted, of course) storage of password and other data.  and it needs an import/export feature so i can load the 200+ existing passwords and export them if it turns out i need to change software, again.  anyone know which package i can install and try?  something in Python3 preferred, but C or C++ is OK.  another feature that would be nice is interfacing with Firefox.

---

### Post by kesetyan on 2020-03-09
Hi Skaperen,

It's not a software package but Lastpass is a password manager that is a browser extension that works well with Firefox.  If you don't know it, so have not tried and dismissed it already, it might be worth you investigating ([https://addons.mozilla.org/en-US/firefox/addon/lastpass-password-manager/](https://addons.mozilla.org/en-US/firefox/addon/lastpass-password-manager/)).

Regards.

---

### Post by Skaperen on 2020-03-09
is it FOSS?  can the world see the source code?

---

### Post by kesetyan on 2020-03-10
I am not aware that the source code is publicly available - Lastpass is a well respected password manager available on all major operating systems so, once you open your account (the free version is more than adequate for most users), you can access it from Linux computers, Windows computers, Apple computers and tablets, Android tablets and smartphones for example - all you need do is add the Lastpass extension to an internet browser to access your previously setup account.  The official Lastpass website is [https://www.lastpass.com/](https://www.lastpass.com/) which is worth looking at if you want to find out more.  The link I gave you in my initial reply is for the Firefox extension download.  

I run a dual boot Windows 7 / Lubuntu 18.04.  I first installed Lastpass in Firefox and set up my Lastpass account in the Windows 7 environment but have since disabled the internet connection for Windows 7.  After that I installed the Lastpass extension in Firefox in the Lubuntu environment and immediately was able to access my.  Similarly I installed the extension in Firefox on my Linux Mint 19.3 desktop (I also have the Vivaldi browser with the Lastpass extension - Lastpass will work with all major internet browsers).

---

### Post by TheFu on 2020-03-10
For many people putting your passwords on some one elses computer, on someone elses network, on someone elses storage, just doesn't pass the "smells bad" test.  We cannot suspend our common sense long enough to buy that, regardless of reputation.

I've moved from KeePassX to KeePassXC.  I will not use any addon to any browser to make use of the KeePass DB more convenient.  That pesky "smells bad" test comes back into play.  If browser security was so good, why not just use their built-in password manager?  Why not?  Because they've proven that they make mistakes, routinely, with every shipped version. KeePass variants use a cross-platform DB.  The source code is on some public git  server somewhere.  I have personally validated that loaded DBs which are locked are not available in RAM, unencrypted. If the DB is unlocked, that's a different thing entirely. All the passwords, data for that record are sitting, decrypted, in RAM. Some things just have to be that way to be displayed.

I don't trust browser incognito modes either.  I use an external tool to force the browsers to be constrained to specific dirs only or force them not to have any authority to actually write anything to storage.  Browsers are just too complicated to be trusted.

Give your nose a workout. See what security programs and claims simply don't pass your own *smells bad* tests.

---

### Post by sdsurfer on 2020-03-10
You mention some languages and am a little unclear - is this something you need scripted on a server for users, etc., or for your use?

I am not sure about the import part, but as mentioned in another thread, I swear by Keepass (or, as above, the Keepass family.) It's open source, encrypted, and completely portable, as in you can literally run it from a USB stick. I just checked my version and there is an import option, it supports all sorts of files, CSV among them. (Untested.)

---

### Post by kesetyan on 2020-03-10
Of course TheFu is quite right regarding potential security risks of storing passwords on an online server.  I would not advocate storing, for example, bank login details on such a system but merely login details for sites such as this forum.  The advantage of an online password manager such as Lastpass is that it is multi-platform so can be accessed from any internet connected device including a smartphone. Weighing that advantage and convenience against the potential risks before commitment and storing passwords for more sensitive sites elsewhere is what I would suggest.  Of course, the servers of the sites one visits via a password login are also potential risks when it comes to access to personal details by unscrupulous hackers.  How many of us have used Amazon, how safe are their servers?  Changing passwords frequently and using different passwords for each site is obviously advisable and will limit potential risks to a degree but in this day of internet communication, wifi, social media, online purchasing and smart homes, the risks should not be understated.

---

### Post by TheFu on 2020-03-10
> **kesetyan said:**
> Of course TheFu is quite right regarding potential security risks of storing passwords on an online server.  I would not advocate storing, for example, bank login details on such a system but merely login details for sites such as this forum.  The advantage of an online password manager such as Lastpass is that it is multi-platform so can be accessed from any internet connected device including a smartphone. Weighing that advantage and convenience against the potential risks before commitment and storing passwords for more sensitive sites elsewhere is what I would suggest.  Of course, the servers of the sites one visits via a password login are also potential risks when it comes to access to personal details by unscrupulous hackers.  How many of us have used Amazon, how safe are their servers?  Changing passwords frequently and using different passwords for each site is obviously advisable and will limit potential risks to a degree but in this day of internet communication, wifi, social media, online purchasing and smart homes, the risks should not be understated.

Well stated.

Amazon and  I  have a financial relationship.  if they want that relationship to continue, they will safeguard my data. 

Other online services, Facebook, google, twitter, and i **do not** have a financial relationship.  In fact, I try to block those thieves from any access to my data. There is limited success blocking FB and Twitter.  See success blocking google, thought I do have some, and blocking Amazon cloudy services is almost impossible, though I have been successful blocking EC2 servers from accessing my web properties, mainly because their IP subnets are well-known.  I also had to block MSFT corporate networks due to attacks from those subnets.

---

