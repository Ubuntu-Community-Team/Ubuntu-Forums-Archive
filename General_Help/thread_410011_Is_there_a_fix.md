---
title: "Is there a fix?"
date: 2007-04-15
forum: General Help
---

### Post by Guns90 on 2007-04-15
Good morning.  I know this is a shot in the dark, but....

I do all of my banking online.  Recently, I am having a very difficult time accessing [www.citibank.com](www.citibank.com) , let alone my account there.  Appearantly, according to them, they have 'improved' their security, but I have yet to talk to anyone there that knows specifically what change was made.  Any Windows PC accesses their site without any problem. The only advice CitiBank will give me is....'You are using an unsupported OS.  Use the required OS'.  I'll switch banks before I switch operating systems.

Is anyone aware of what's going on and maybe have a fix?  At the least, I would appreciate another Ubuntunite going to their sight and reporting back if It's just my setup.  Thanks.

---

### Post by Sef on 2007-04-15
> Is anyone aware of what's going on and maybe have a fix? 

The fix would be from their end.  Next time you call, ask to speak to the tech's boss or write a letter.  Only other thing you can is find another bank where you can use your os.

---

### Post by mgmiller on 2007-04-15
I just tried clicking on your link and the citibank site popped open without fuss.  All the drop downs and menu items seemed to work fine.  I don't have an account there, so I can't log into anything, but I was able to browse around on the page you sent me without issues.  I am running Edgy with all the latest updates and firefox 2.0.0.3

Edit:
I just tried the site again, and after clicking through one of their links it told me I did not have a supported browser or operating system.  However, it said if I don't want to "upgrade" my browser or OS, I should just click the continue button on the lower right corner of the page.  After doing that, everything worked all over the site.  I also tried exiting the site and reloading it and everything just worked without prompting me to get a different OS.

---

### Post by mgmiller on 2007-04-15
Here is a quick quess.  Are you running adblock?  If you are , try white listing the entire site.  On the bottom edge of your browser window there will be the word Adblock, just right click it and select white list this entire site.

---

### Post by Guns90 on 2007-04-15
Sef,  Did you go to their site?  I find it interesting that mgmiller doesn't have any problems, but I do.  I guess that means that I obviously have, or don't have, a program that is (in)compatable with their security applications.  

mgmiller,  I do not have adblocker on my system.  I know nothing about that program, and I'm one who installs only those programs that I know I NEED.  I really don't have a problem with ads/pop-ups on the sites that I frequent, so I am not real eager to install something like that.  

I went back to the citibank site to try the procedure that you mentioned mgmiller.  It takes no less than 45 seconds for the home page to load. ANY place I go from there on their site, it not only takes a couple of minutes for that page to pop on screen, it is covered with a white square that takes up about 95% of the screen with a cartoon-like quote box area asking me if I want to learn more about their security system.  The only option it gives me is to 'continue'.  When I click on that, a rather large black cursur (not the one I'm using) begins moving to differant locations on the white square and resting a few seconds before moving on to another location.  Sometimes I get the log-in screen and the other times the site freezes up.  If I get the log-in screen and try to sign in, nine times out of ten it says that I do have an account with them and sends me to a 'join' page.  That one time in ten it signs me on and I have no problems doing what I want to do.  It has taken me more than an hour one time to get online with them. See why I'm getting so upset?  (And you don't want to know what my wife thinks of this. She still hates me for doing away with Windows which she at least felt comfortable with.)  

I have no other problems with speed or ANYTHING on any other site but this.  You say that you get there fine, so it's got to be something I have/do not have on my computer.  Any other suggestions?

---

### Post by mgmiller on 2007-04-15
OK, if you are not running adblock, then it can't be creating this problem for you.  My speed on loading the site is almost instantaneous.  What version of Firefox are you using?  Try going to Edit>Preferences and click on the Advanced button and then the Encryption tab and make sure both Use SSL 3.0 and Use TLS 1.0 are checked.  Also I have "Select one Automatically" set for the certificates choice.

---

### Post by PurplePenguin on 2007-04-15
Which browser are you using?  I'm using Swiftfox 2.0 and can get to the site with no problem (except for the unsupported OS page - hitting "continue" works).   I don't have an account there, so can't try logging in, but I can at least get in to the page that asks for my account number.

Try using a different browser to get in.  Between Firefox, Opera, and Mozilla (not to mention konqueror, epiphany, etc), I can get past most hangups like this.

---

### Post by Maestro23 on 2007-04-15
Running Feisty and FF 2.0.0.3 and that site loads up fine on my machine.  Can navigate around it with no problems either.  Like the above posted, I don't have an account either though.

---

### Post by Guns90 on 2007-04-15
I'm using Dapper with Firefox 1.5.  My advanced preferences are set to both SSL 3.0 and TLS 1.0; however, I also have SSL 2.0 checked.  

The select one automatically is also checked.

---

### Post by mgmiller on 2007-04-15
Here is something else to try.  In your firefox address bar, type  about:config   Then scroll down to the line that says "network.dns.disableIPv6" and make sure it says user set boolean true on the right side.  Simply double clicking the whole line will toggle the setting between true and false.  You will need to restart firefox after making the change.   The only other thing I can think of is that I have fasterfox installed and set to "turb charged".  I just tried changing it to non optimized and will give it a go.

Update:
I turned off all the fasterfox enhancements and the site still loads in a snap, although, I couldn't exit firefox after going there.  Turning fasterfox back on, fixed it

---

### Post by Maestro23 on 2007-04-15
Try updating to a newer version of FF and see what happens.

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by mgmiller on 2007-04-15
I will have to agree with Maestro23.  I think you need a newer version of Firefox.  Did Dapper not do the FF 1.5 to 2.0 upgrade?  I would think the LTS version would do something like that.

---

### Post by strabes on 2007-04-15
Using latest version of firefox on kubuntu feisty: [https://web.da-us.citibank.com/cgi-bin/citifi/portal/l/l.do](https://web.da-us.citibank.com/cgi-bin/citifi/portal/l/l.do)

You could try kernel virtualization to run IE inside ubuntu. Try this page for more info: [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

---

### Post by Guns90 on 2007-04-15
mgmiller, That was interesting.  It was set to false, so I toggled it, rebooted, and tried the site again.  The home page came up instantly.  When I clicked on 'go to credit card', it instantly gave me that white square (obscuring 95% of the screen) with that quotation box asking the question. This time, when I clicked on the continue button, it instantly gave me another quotation box question.  It did this two more times, then allowed my in to my account.  I signed off, rebooted, and repeated the foregoing with the same results.  Maybe I will try to upgrade FF.  I'm just old school and kind of live by 'if it ain't broke, don't fix it'.  (Yeah, I know, you guys are saying that it's appearantly broke.:) )

---

### Post by Guns90 on 2007-04-15
No mgmiller, Dapper did not upgrade FF to 2.0 automatically.  I just went into Synaptic and tried to upgrade, but the 'mark for upgrade' oiption is greyed-out.

---

### Post by Guns90 on 2007-04-15
I must not have some settings right.  I just relogged on to my desktop, tried from the terminal to 'gksudo firefox' and that came in ok; however, when I clicked on 'help', the 'check for updates' option is greyed out.

---

### Post by viciouslime on 2007-04-15
I think I found your problem... did anyone try actually signing on? Sure the home page works fine, but go to the drop down on the right, under sign on, and select bank accounts and you will get the the page telling you to use a different OS.

However, if you read the whole page, you can click continue in the bottom right, et voilà, problem solved :D

I can't test it any further because I don't have an account with citibank... and if I did it would be a uk one and their uk site is different.

---

### Post by Guns90 on 2007-04-15
visciouslime,   I just tried that again.  It did take me to the page telling me to get a differant OS, and when I clicked continue it took me on to sign-on page.  But again, when I tried to log on, it said I have no account with them.  I appreciate help from accross the pond, though.:)

---

### Post by viciouslime on 2007-04-15
> **Guns90 said:**
> visciouslime,   I just tried that again.  It did take me to the page telling me to get a differant OS, and when I clicked continue it took me on to sign-on page.  But again, when I tried to log on, it said I have no account with them.  I appreciate help from accross the pond, though.:)
No problem. I think you should call them about it and see what they say then, because it definitley says you CAN use another OS if you click continue, so it shouldn't then give you problems when you try to sign in...

If you do call them, please post back with what they say, I would be interested to hear :)

---

### Post by Guns90 on 2007-04-15
I'm getting very tired of all this.  Feisty should be released in four days.  When it is, I'm going to upgrade to it and FireFox's latest.  If that doesn't fix everything, than I'll call the bank and see if they can get it fixed.  (I'm not going to hold my breathe though because they have it posted that I have an 'Unsupported OS'.)  I know that I'm not going to be as patient with them as I am with you guys.  If they can't get me up and running, then I guess I have no choice but to go shopping for another bank. 

Thanks for all the help guys.

---

### Post by Detonate on 2007-04-15
There is an extension for Firefox called "Agent Switcher" .  You can use it to lie to those sites that insist you have IE by telling the site it is IE.  that might work.  I use it all the time.  It doesn't always work, because if the site uses ActiveX you still have a problem.

---

