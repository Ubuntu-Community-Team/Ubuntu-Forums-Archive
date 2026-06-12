---
title: "Problems with e-mail client gmail config"
date: 2014-10-04
forum: General Help
---

### Post by John_Wedgeworth on 2014-10-04
Hello!

I just wiped my "too-slow-for-Windows" 11" Acer Netbook yesterday, installing the latest version of Ubuntu on it instead. I have Unity and KDE (?) GUIs (I'm currently using Unity).

My main computer is a 17" MacBook Pro with Mavericks, and the standard Apple Mail program. Before I installed Ubuntu, I had Windows 7, with Outlook 2007. On both of these computers, and every other computer I've ever tried on, I've NEVER had a problem configuring these programs to work with my gmail. It's always been quick and painless. I also had a very brief exposure to Ubuntu 12.04 via a parallels virtual machine on my mac a few years ago (only had it for a month or so). I can't remember what mail app I used then, but I remember having no problems configuring it for gmail.

However, today, I've burned through maybe four fruitless hours trying to configure, first, Evolution, then Kmail, then Evolution again, then finally Firebird to work with gmail.

It keeps telling me my password is wrong. I did verify on the Macbook that my mail email has not changed. I've also tried configuring manually and automatically. I've looked at several websites that walk you through everything involved in configuration. Everything is right on the gmail side (done in Chrome browser on the Mac), and on the Ubuntu side, it's been a mix of puting in just what they tell me, plus options they're saying will be there not being there, etc. But at the end of the day, all of these apps are still telling me my password is wrong, and none of them will send or receive e-mail, even though they act like everything is set up (despite not accepting my password.)

I'm on the verge of saying to heck with an Outlook equivalent and just doing email in the browser, but I REALLY don't want to do that.

Can anybody help me?

Thanks!

-Essentially new Ubuntu user.

---

### Post by tgalati4 on 2014-10-04
What links did you follow?  What port are you using?

---

### Post by John_Wedgeworth on 2014-10-05
I have both IMAP and POP enabled in the settings in my gmail. I did this in the Chrome browser in Mac OS.

I've tried both. When I've tried IMAP, I've used imap.gmail.com, and when I've tried pop, I've tried pop.gmail.com. In both instances, I've used port 995. Where it asks for it in a separate field, I leave it out of the server field, such as pop.gmail.com in the one field, and 995 in the other. Where it doesn't seem to have a separate field for that information, I've tried the following both ways - as pop.gmail.com:995, and by just leaving the 995 off.

For outgoing, I'm using smtp.gmail.com, asking it to use my login as the credentials per the instructions, and where given the chance to specify, I'm using port 587. Again, same as above on whether I have put smtp.gmail.com, or smtp.gmail.com:587.

Where I can, I have specified that I want SSL encryption on incoming, and TLS on the outgoing.

Here are the links that looked super helpful, but have done nothing for me. Particularly on the one about Evolution (which would be the one I'd prefer to use since it's got the calendar features, etc all built in), since the account creator tool is far more truncated than the one we see on the site (for instance, I don't think I ever had the option to specify IMAP or POP.)

Here are the links I was referring to:

Evolution:

[https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution) - Its from this site.

Kmail:

[http://www.maketecheasier.com/check-gmail-account-with-kmail/](http://www.maketecheasier.com/check-gmail-account-with-kmail/)

Thunderbird:

[http://ubuntuforums.org/showthread.php?t=203525](http://ubuntuforums.org/showthread.php?t=203525)

Thanks again for all the help! I think I'm in over my head right now. And over something that I've easily mastered in every other context in my whole life!

Cheers!

---

### Post by coffeecat on 2014-10-05
Not a Forum Feedback & Help question.

*Thread moved to **General Help**.*

---

### Post by buzzingrobot on 2014-10-05
Here's GMail's page on mail client configuration: [https://support.google.com/mail/topic/3397500?hl=en&ref_topic=3398031](https://support.google.com/mail/topic/3397500?hl=en&ref_topic=3398031)

Note that the IMAP ports will differ depending on choice of SSL or StartTLS. But, they don't vary from client to client.

The SMTP SSL port is 465.
The SMTP TLS port is 587.

The IMAP port is 993 and select SSL.

In some clients, you enter passwords during setup, others ask the first time you try to access each server.  Evolution is one of the latter. Be sure you enter your GMail password and not your Ubuntu password.

---

### Post by John_Wedgeworth on 2014-10-05
Thanks for the info, buzzingrobot. I do think I was trying some bad combinations, then. But I was also trying some good ones. I tried these settings again this morning in both kmail, evolution, thunderbird, and even sylpheed, and all to no avail.

I've tried pop.gmail.com on port 995, imap.gmail.com on port 993, smtp.gmail.com, SSL port 465, and STARTTLS port 587. For authentication, I try to find the option the closest to saying "normal password", or "login", or whatever, though I've also tried PLAIN, and automatic. I'm pretty sure I've also tried no authentication. I'm also positive that I'm using the right password. 

But again, it's still not working on any of these apps. I'm really at a loss. What am I doing wrong? Is there any possibility that I'm doing nothing wrong, and the problem is somewhere else? Again, I've done this before in Outlook and Mac Mail, and I'm pretty sure I even did this without any major hassles when I briefly tried Ubuntu 12.04 back a few years ago. This experience and my complete inability to perform the simple task of setting up my email is the anomaly experience.

---

### Post by John_Wedgeworth on 2014-10-05
> **coffeecat said:**
> Not a Forum Feedback & Help question.

*Thread moved to **General Help**.*

Sorry! I noticed this general help section this morning, and thought "ah crap, I posted in the wrong place!" Thank you for moving it, rather than deleting it. :-)

---

### Post by buzzingrobot on 2014-10-05
I haven't used Sylpheed with GMail, but I have used all the rest with GMail with no problems.  Thunderbird, I believe, will automatically set up a "gmail.com" address that's plugged into the account wizard that it displays on first use. (You  see an offer to create a new account, but below that is the option to use an existing account.)

 Evolution needs to be configured manually.  The very latest KMail seems to handle the config after you enter in the server names for GMail, and then can be tweaked subsequently.

You do need to set your GMail settings to use IMAP or POP, but I'm sure you did that for Outlook. GMail also wants the full address as the username.  Maybe Outlook and Mail automagically handle that?

Assuming correct configuration, if every app is failing the same way, then the problem is likely independent of the apps.

---

### Post by buzzingrobot on 2014-10-05
I don't have Thunderbird installed at the moment, but I believe it reverts to its "just installed and never set up" state if its configuration folder is deleted. It (re)creates the folder on first launch.

The folder is ".thunderbird" and it should be inside the ".mozilla" folder in your home folder. Close Thunderbird. Open the file manager and set the view option to display hidden files. (It's a convention in Unix/Linux that file and directory names beginning with a '.' are not displayed unless specifically requested.)

Navigate to the .mozilla folder, open it, and delete the .thunderbird folder. 

Now, launch Thunderbird and you *should* see the first-use account wizard pop up. Select the option to use an existing accout, enter your full GMail username and password, and see if Thunderbird creates the account automatically.

---

### Post by coffeecat on 2014-10-05
> **buzzingrobot said:**
> The folder is ".thunderbird" and it should be inside the ".mozilla" folder in your home folder.

Point of information from a Thunderbird user. The folder .thunderbird is separate from the .mozilla folder. There are ~/.thunderbird/ and ~/.mozilla/ folders. Slightly inconsistent, I would agree, because there is a ~/.mozilla/firefox/ folder, so you might expect ~/.mozilla/thunderbird/ as well, but not so.

---

### Post by buzzingrobot on 2014-10-05
Thanks, coffeecat.  I usually use Thunderbird, but I'm off on a dalliance with KDE and KMail.

---

### Post by John_Wedgeworth on 2014-10-05
> **buzzingrobot said:**
> Assuming correct configuration, if every app is failing the same way, then the problem is likely independent of the apps.

At this point it pretty much has to be something along these lines. But what on earth could it be?

I think my strategy now will be to uninstall all these mail aps completely, then reinstall one at a time, make sure the config is right, until either I find one that will work, or until I've exhausted them all again. If I get to that point, I still have a boot USB with the OS on it, I'll just reformat and reinstall the OS.

If THAT doesn't work, then I'm really stumped. The only thing I could do at that point is get a different disk image on the USB and install from that, but this one is the latest one that came straight from the Ubuntu site!

What do you guys think?

---

### Post by buzzingrobot on 2014-10-05
> **John_Wedgeworth said:**
> 
I think my strategy now will be to uninstall all these mail aps completely, then reinstal...

Be sure that the app configuration files are also removed, or else you may use bad config info in the new installs.

Config files are not usually removed when a package is removed. People often want to preserve their handcrafted configurations.

So, in a terminal, "sudo apt-get remove thunderbird" will not remove your Thunderbird config files.

But... "sudo apt-get purge thunderbird" *will* remove your Thunderbird config files, as well as Thunderbird.

---

### Post by John_Wedgeworth on 2014-10-05
UPDATE: Right after typing my last reply, I tried to open the App Store to uninstall those mail programs, and it crashed. 

I've had to reset the computer a handful of times yesterday due to hard crashes, and if by "crashes", we lower the bar to count an app screen going gray for a few seconds, and coming back, then I've had countless "crashes", so I just decided to skip most of what I said above, and just reformat / reinstall.

I'll keep you guys in the loop.

---

### Post by John_Wedgeworth on 2014-10-05
> **buzzingrobot said:**
> Be sure that the app configuration files are also removed, or else you may use bad config info in the new installs.

Config files are not usually removed when a package is removed. People often want to preserve their handcrafted configurations.

So, in a terminal, "sudo apt-get remove thunderbird" will not remove your Thunderbird config files.

But... "sudo apt-get purge thunderbird" *will* remove your Thunderbird config files, as well as Thunderbird.

That is VERY useful information for removing future apps should I still have problems after this fresh install (fingers crossed) :-D

Yeah, the command line system is the most foreign thing about Ubuntu for me. It's not science, it's magic, and it needs to be science. I'm guessing it'll take me a while to master.

---

### Post by buzzingrobot on 2014-10-05
> **John_Wedgeworth said:**
> ...an app screen going gray for a few seconds...

That's potentially a sign of a video issue, i.e., a weak video card.

The command line is neither magic or science, just a collection of tools built up over the years that collect user input and then do something based on that input, just like GUI tools.  Unix/Linux terminal tools trace their lineage to the time before hardware could support GUI's and mice, when a blank terminal was all there was.. Nowadays, they often have many more options than could be conveniently included in a GUI-ified counterpart.

The Software Center is intended to be simple and easy to use, so it doesn't expose the widest realm of capabilities.  Down the road, you might want to look at other GUI tools that offer a finer-grained view of package management. Synaptic and Muon are popular in the Unity and KDE sides of things, respectively.

---

### Post by John_Wedgeworth on 2014-10-05
Sure. I know the command line is not actually magic, I just meant to convey by that distinction that I don't really understand it (it's like magic), and I need to get to a place where I've got my head wrapped around it (science). I mean, I get the basic premise of a command prompt/terminal, as I did have some experience with MS DOS way back in the day. 

But what is so mystifying about it to me is how typing a simple command would give the OS enough information to know to go to xyz place on the web, then download it, and install, and configure, etc. It seems overpowered for one, and I don't understand the mechanism, and for two, I have no idea of how the computer language one would use works, so I would have no idea how to issue a command intuitively, without going to a website that gives me the exact script I need, and holding my hand through the whole thing. 

I guess I just need/want to "learn how to fish" with the command line, rather than just "be given a fish". :-)

And as far as the frequent "gray-out" lag being related to an underpowered video card, I did not know that, and would not have expected it (I never had similar problems in Windows 7, which is definitely more resource demanding, and seemingly more graphically intensive than Unity), but with as weak as this computer is, I would definitely believe the video card to be weak enough to have such a problem.

I just finished the re-install (it's downloading and installing updates now), so we will see what happens. I'll let you guys know!

---

### Post by John_Wedgeworth on 2014-10-05
Okay, so I tried again....still no good. Same issues as before (and this is on a fresh install.)

This time, in addition to Thunderbird, Evolution, KMail, and Sylpheed, I tried Claws, Unity Mail, Desktop Webmail, Gmail, Gnome GMail, Geary Mail, and Get Notifications (though some of these don't work the same way, but just open a browser window to the browser version, which for me is pretty worthless).

Evolution, Geary, and Thunderbird simply tell me that my password is wrong (which I can verify, it is not). However, KMail and Claws both give me a more detailed error message. This is what Claws is telling me:

**error occured on SMTP session
***Error occured while sending the message:
534-5.7.14<[https://accounts.google.com/ContinueSignIn?](https://accounts.google.com/ContinueSignIn?)
sarp=1&scc=18&plt=AKgnsbv2l

I couldn't get kmail to replicate the error after the reinstall (though it's still not working), but it looked very much like the one above.

A friend on facebook gave me these links as resources, but none of them helped. Although, one did touch on a problem I noticed: in evolution, it doesn't give me the chance to choose between POP and IMAP, it just assumes IMAP, then never gives me the chance to change it later. However, these other apps let me choose, and they don't work in POP either.

[COLOR=#141823][FONT=Helvetica][http://ubuntuforums.org/showthread.php?t=2150776](http://ubuntuforums.org/showthread.php?t=2150776)[/FONT][/COLOR][COLOR=#141823][FONT=Helvetica]
[http://ubuntuforums.org/showthread.php?t=2116865](http://ubuntuforums.org/showthread.php?t=2116865)
[http://ubuntuforums.org/showthread.php?t=1376858](http://ubuntuforums.org/showthread.php?t=1376858)
[https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution)[/FONT][/COLOR]

I don't know where to go, or what to do now.

[COLOR=#141823][FONT=Helvetica]Not having an outlook-like mail client that works is not going to render an ubuntu box useless, since a) I can get notifications of new mail on my phone, and b) I can still access the website version via firefox if I need to send one in a desktop environment...but still, it's something that should be super easy, and take 20 minutes, that I've presently burned about 10 hours on between two days, and have still ended up in total failure (it feels like I've spent all day unsuccessfully trying to make a peanut butter sandwhich because I couldn't get the jar open)...that's starting to leave a REALLY bitter taste in my mouth towards Ubuntu.[/FONT][/COLOR]

[COLOR=#141823][FONT=Helvetica]Anybody know anything I can try? I'm all ears![/FONT][/COLOR]

[COLOR=#141823][FONT=Helvetica]Thanks a million![/FONT][/COLOR]

---

### Post by John_Wedgeworth on 2014-10-05
Hey, is this possibly a firewall thing? It seems like most or all of the problems relate to SMTP. Could a firewall setting be causing this? Also, where do I find access to the firewall settings in Unity? I looked in [to me] all the obvious places, and didn't find anything.

---

### Post by buzzingrobot on 2014-10-06
In theory, the firewall could be in play.  But, unless you've altered the default Ubuntu firewall configuration, it isn't.

Have you examined your configuration and settings *at* Gmail? That error message seems to indicate something might be wrong there. 

A client can't do IMAP or POP unless they're enabled at GMail.

---

### Post by John_Wedgeworth on 2014-10-06
Okay. Here's the current config on the gmail under the Forwarding and POP/IMAP tab. Let me know if any of this is wrong, and while I don't think there will be, let me know if there are any settings I need to look at under the other tabs (the other tabs are General, Labels, Inbox, Accounts and Import, Filters, Chat, Web Clips, Labs, Offline, and Themes - I haven't looked under any of these other tabs.)

Forwarding: 

NA

POP Download: 

POP is enabled for all mail

When messages are accessed with POP keep Gmail's copy in the Inbox

IMAP Access:

IMAP is enabled

When I mark a message in IMAP as deleted Auto Expunge On

Folder Size Limit Do not limit the number of messages in an IMAP folder (default)


----------------------------------


Also, in Mac OS's default "Outlook clone" - "Mail", it works fine for me. Here is the way the account is configured in "mail":

IMAP - imap.gmail.com - Port 993 - SSL - Password Authentication. Use IDLE command if the server supports it

SMTP - smtp.gmail.com - Use default ports (25, 465, 587) selected. Use custom port: ___ unselected. SSL - Password Authentication.


--------------------------


Now, here are the configurations I'm using UNSUCCESSFULLY in Evolution and Thunderbird in Ubuntu:

Evolution:

Server type IMAP+ / IMAPX (can't choose another type)
server - imap.gmail.com Port 993 (defaults to imap.googlemail.com before I change it to imap.gmail.com)
Username: [EMAIL="__________________@gmail.com"]__________________@gmail.com[/EMAIL]
Security - SSL on a dedicated port
Auth: password

Server Type SMTP
server - smtp.gmail.com Port 465 (defaults to smtp.googlemail.com before I change it to smtp.gmail.com)
Server requires authentication selected
Security - SSL on a dedicated port
Auth: Login
Username: [EMAIL="_______________________@gmail.com"]_______________________@gmail.com[/EMAIL]

Error response to entering password for IMAP verification: "Password was incorrect" (I can 100% certify that the password is NOT incorrect). Other options for auth which I have not tried are NTLM/SPA, GSSAPI, DIGEST-MD5, and CRAM-MD5.

Error response to entering password for SMTP verification: "The reported error was "Bad Authentication response from server." I switched from "Login" auth to "PLAIN" auth, and this didn't change anything. Other options for auth which I have not tried are NTLM/SPA, GSSAPI, DIGEST-MD5, CRAM-MD5, and POP before SMTP.

Thunderbird:

Incoming: POP3
Server hostname: pop.gmail.com port 995 - defaults to pop.googlemail.com before I change it to pop.gmail.com
SSL: SSL/TLS
Auth: Normal Password

Outgoing: SMTP
Server hostname: smtp.gmail.com port 465 - defaults to smtp.googlemail.com before I change it to smtp.gmail.com
SSL: SSL/TLS
Auth: Normal Password

Username:

Incoming - _____________.gmail.com
Outgoing -  _____________.gmail.com

Error message: Username or password invalid / Configuration could not be verified - is the username or password wrong?


-----------------------------

Okay, so those are the current settings in my gmail itself, my settings which DO work in Apple Mail, and my settings which DO NOT work in either Evolution or Thunderbird. Please let me know if I'm doing anything wrong. 

Now, it is worth noting that I tried installing and configuring Thunderbird in Mac to see if I could configure it on my Mac. I failed to configure it on my Mac too - for what that's worth.

So I'm totally stumped.

Thank you all very much for all the help! I really appreciate it!

---

### Post by buzzingrobot on 2014-10-07
> **John_Wedgeworth said:**
> So I'm totally stumped.

So am I.

Those settings are the same I use. On Thunderbird, I do leave it at 'Googlemail' in the auto setup.  On manual setup, I use 'gmail'.

The business of Thunderbird behaving the same way on OS X is weird, to say the least.

---

### Post by John_Wedgeworth on 2014-10-08
Crap! I was counting on you guys as a life line! :-)

The only thing I can think to try is to not change it from imap.googlemail.com to imap.gmail.com, etc.

Or, will someone walk me through the firewall thing? I know what you're saying, "BuzzingRobot", that the default settings shouldn't be a problem, and if I haven't messed with it (which I haven't), then I should be fine....but as Mr. Spock completely plagiarized Sherlock Holmes over: "When you rule out the impossible, whatever else remains, no matter how unlikely, must be the truth." Therefore, I would like to configure the firewall so those ports are explicitly open.

If these don't work, then I'm really totally and completely out of ideas!

Does anyone else have any other ideas that we haven't thought of yet? I'm bordering on desperation here. :-)

Thanks!

---

### Post by CantankRus on 2014-10-08
Possibly look at your gmail security settings.
When logged into gmail go to [https://www.google.com/settings/security/lesssecureapps](https://www.google.com/settings/security/lesssecureapps)

PS My unity-mail app uses **imap.gmail.com** Port:993
and login name is full address eg **joeblow@gmail.com**

---

### Post by John_Wedgeworth on 2014-10-08
> **CantankRus said:**
> Possibly look at your gmail security settings.
When logged into gmail go to [https://www.google.com/settings/security/lesssecureapps](https://www.google.com/settings/security/lesssecureapps)

CantankRus!!! I could KISS you! It's working now! :D It was the less secure apps thing!

Thank you everyone for taking so much time to work with me to solve this problem! Hopefully in a short while, I'll amass enough of a knowledge base about Ubuntu that I'll be able to start repaying the favor with future "newbuntuians", and make their transitions less painful!

Truly grateful!

God Bless!

---

### Post by CantankRus on 2014-10-08
> **John_Wedgeworth said:**
> CantankRus!!! I could KISS you! 


ewwww! :p  Yeah I think this setting is fairly recent as one of my scripts stopped working.
Goodluck.

---

