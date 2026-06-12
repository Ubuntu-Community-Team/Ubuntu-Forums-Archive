---
title: "Connection between browser and OS"
date: 2014-03-18
forum: General Help
---

### Post by bjngchn on 2014-03-18
1. Are  any infos  sent out from a computer with *ubuntu to another computer (like a server) by default without user approval?  Which ones? Like desktop searches, filenames? 

2. Can computers be identified on a network? Let's say I connect to server through a command, or visit  a website on a browser. Will my computer be identified directly or indirectly? I guess bluetooth is different and needs more precise identification (just guessing). 

3. More detail on 2. For example I visit  a facebook page from a user account, and visit another facebook page or account from another user account on the same computer. Can facebook know these visits come from the same computer?   
4. Related to previous. Facebook, Yahoo, Google, ... are referenced from about:config on firefox. Why so? What is the benefit to the user?  

5. Are visited url's sent to Google (or any other site) for safety checking or any other purpose?  

6. Why is there a connection between firefox and Ubuntu. Editing firefox may break Ubuntu. Removing ubuntu pack from config makes firefox unusable, and hard to remove and reinstall. Does browser really need to be tightly connected to the ubuntu installation this way. In the past, I could download a browser from internet, copy it to a CD and move to another computer and make it work there, when I was even more naive than now. I don't think this kind of thing would work now.  

7. Can we watch which programs are sending out packets. get notification when this happens, and see where they go?  I don't think our lives are changed much by knowing answers to such questins but sometimes fine tuning might be necessary. 

8. A different type of question. People say check md5sum of a downloaded ISO file. Why are we not checking md5sum of an update? What if some users are getting  keylogger with an update? How can we know this never happens? 

9. People say.get regular updates for security. Isn't it a good alternative to modify things in unexpected ways to make sure your computer is different than others and a virus created for default version won't work on your computer. For example do chmod 000 or 700 on files most people would never touch, or change filesnames etc. 

10. From experience. it looks like greatest threat to an installation is upgrade. Maybe earlier versions of firefox  and  ubuntu would be  better.   

11. We know cookies can be blocked from some sites. Can this also be done for javascript or flash or images?

---

### Post by TheFu on 2014-03-18
TL;DR.

Computers talk to networks and other computers. If you want to know where they are communicating, setup a packet sniffer.
Canonical earns some money by providing search results from Amazon, Google, etc.   Just like plain Firefox, Opera and other software, including other browsers do.  If you want to disable this, google for a how-to.  For example, Canonical changed the amazon MP3 purchase referral from a playback program team's wishes - the Gnome Project - to Canonical a few years ago.

7 - yes you can.
8 - updates are signed and validated if provided by a reputable repo/PPA. Look up gpg.
9 - chmod is part of system security, most of it, but so are userid, groupid, group management.
10 - When I was new to Linux, I'd break things all the time. Now with much more experience, things sorta just work.
11 - yes, you can block JS and flash. NoScript/NoFlash are popular browser addons.  check out ghostery, Certificate Patrol, HTTPS Everywhere  as well.

All these things would be discovered with a little internet searching.

If you want more complete answers - as 1 question.

---

### Post by sideburns on 2014-03-30
If you'd like to see some of what your browser tells every webserver you connect to, check here: [http://www.zeff.us/env.pl](http://www.zeff.us/env.pl)  This isn't a complete list, but this is all that my hosting company makes available.

---

### Post by bjngchn on 2014-03-30
Thanks for answers... still curious about 3-6. If on the same computer, user1 uses FB1 account on facebook, and user2 uses FB2 account, can facebook know these users are connected from the same computer? .... Are visited urls sent to Google or other places under excuse of safety or something else? What does ubuntu firefox pack do and why can't it be disabled? Even one answer to one question means a lot.... Such things are difficult to find by searching internet, maybe because search engines don't like such info.

---

### Post by TheFu on 2014-03-30
> **bjngchn said:**
> Thanks for answers... still curious about 3-6. If on the same computer, user1 uses FB1 account on facebook, and user2 uses FB2 account, can facebook know these users are connected from the same computer? .... Are visited urls sent to Google or other places under excuse of safety or something else? What does ubuntu firefox pack do and why can't it be disabled? Even one answer to one question means a lot.... Such things are difficult to find by searching internet, maybe because search engines don't like such info.

I don't use FB. it is blocked at the network layer. Same for twitter and a few other social networks like plus.google.com - all blocked.

Every website that used google analytics reports your visits to every page to google. doubleclick is the same - part of google. There are many trackers out there with bugs, cookies, flash objects, js - all of them trying to track what we do. Must be a few hundred companies doing this - probably more.

I don't know what the ubuntu firefox pack does - I remove it, but I'm not running stock ubuntu. I suspect it
* pulls the menu to the top (drives me nuts)
* is used to send searches to amazon and other commercial locations (making money for Canonical)

Did you look at those plugins? They will open your eyes.

---

### Post by buzzingrobot on 2014-03-30
Networks -- passing data back and forth between computers -- won't work if they can't identify individual computers and route data to them.  You'd need to take a look at how the net works and how browsers work to get an understanding of the data passed back and forth.

Every device on the internet has a unique IP (Internet Protocol) number.  Data that leaves your computer is broken down into many packets of info, each of which contain your current IP number. When they all arrive at their destination and are reassembled - say, at the server at the link you clicked on in Firefox --- your IP is extracted and included in the packets the server sends back to you. That's, very briefly and very oversimplified, how the stuff manages to find its way back to you.

Your IP number, and anything else the server "knows" is data that can be logged by the server.  What the server operators do with that info is up to them.

So... if Facebook wants to, they could link accounts to IP addresses.  I don't use FB and have no idea if they routinely sort out multiple accounts using one IP address.

For a typical home user, their ISP is usually the first stop for all the packets they generate. The nameservers you use -- again, typically, but not always, provided by the ISP -- know the IP addresses of all URL's you point your browser at.

6:  If "editing Firefox" means altering settings in the Preferences panels, then none of that would "break" Ubuntu. If "Removing ubuntu pack..." means deleting the ubuntu-desktop package -- which will also delete a very long list of dependencies -- then, frankly, I wouldn't expect much of anything to work. That's essentially ripping the core of the system out. (You can still download Firefox from Mozilla and manually install it. It will be invisible to the system's updating and dependency resolution tools.)

Any change to a stable system opens up the possibility of creating an unforeseen instability, including updates. I regularly and routinely keep my systems updated and I very seldom have issues that can be blamed on the updates.  *Security* updates, to me, seem essential, since they are patching known vulnerabilities that exist on a system. Application updates and bug fixes that aren't security related can or cannot be applied, as a user wishes.

---

### Post by SeijiSensei on 2014-03-30
When reading lists of questions like this, I wonder what your real concerns are.  Take the two Facebook users you mentioned above. I'm sure that Facebook, like every other web site in existence, logs the IP addresses of incoming connections.  Whether Facebook can correlate those entries with usernames depends on how credentials are passed.  If, as is likely, they are passed via a POST, then the answer is no.

And, furthermore, why would they, or you, care if two users connect from the same IP?  Facebook doesn't care about IP addresses.

What are you really afraid of here?

---

### Post by grahammechanical on 2014-03-30
Number 6

a) You are wrong. Firefox can easily be removed from Ubuntu and Ubuntu does not break. At the moment Firefox is the default supplied web browser. That is all. And that can change. What kind of editing of Firefox can someone do and so break Ubuntu? You must explain what you mean.

b) A lot of us are very pleased that Linux does not work like Windows. We have a lot less security concerns by this fact. Are you aware that downloading applications from the internet puts the security of your computer at risk? Software in the Ubuntu Software Centre and that included in the default installation is code audited to make sure that we are not installing an application with malicious code in it. Web browsers can present a massive security risk. Why download one from the internet when we can download through the software centre.

Numbers 3 and 5. Ask those organisations. They are the people to answer those questions or not.

Numbers 8 and 9. If you cannot trust the developers of Linux and its distributions, then do not use a Linux distribution.

Number 10. Based on my experience, upgrades are not a threat to security. There is a risk that because the user has modified the system the upgrade will not be able to accurately determine what needs to be upgraded. And the upgrade will not be successful. From what I have seen, proprietary video drivers are liable to cause an upgrade to fail. Liekwise, powering off in the middle of an upgrade.

Finally, with all these concerns about Ubuntu why should you think that an earlier version of Firefox or an earlier version of Ubuntu is any more secure than the newer versions? It is illogical. The latest version of Firefox must be more secure than any earlier version because any security flaws that have been noticed have been fixed. The same logic applies to Linux/Ubuntu.

As for worries about security, read this

[http://www.markshuttleworth.com/archives/1332](http://www.markshuttleworth.com/archives/1332)

Regards.

---

