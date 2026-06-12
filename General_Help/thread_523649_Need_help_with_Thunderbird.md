---
title: "Need help with Thunderbird"
date: 2007-08-12
forum: General Help
---

### Post by dorkdork777 on 2007-08-12
OK, I have quite a few questions regarding Thunderbird, and I never really used Ubuntu seriously before yesterday, so bear with me!

Question #1- How come when I start Thunderbird through Applications-Internet-Thunderbird, it is only version 1.5.0.12 even though I installed 2.0.0.6 in /opt/thunderbird? Is there any way to 're-link' this to /opt/thunderbird so it starts version 2.0.0.6? SOLVED

#2 - Why won't it let me auto-update, and why is Thunderbird in Add/ Remove only version 1.5.0.12 instead of the latest, 2.0.0.6? SOLVED

#3 - I set my Mail reader as /opt/thunderbird/thunderbird %s in Preferred Applications, yet clicking on the icon in the panel still opens up Evolution mail - why is this? SOLVED

#4 - I copied over my account details from my Thunderbird on Windows to my Thunderbird 2.0.0.6 in Ubuntu, everything shows up how it did in Windows, but I can't recieve mail; it just says "Could not connect to server localhost; the connection was refused." I'm using Webmail with Webmail Hotmail to get my Hotmail account's mail. I configured the ports because the Settings said that some OSs block ports below 1024, so I changed the POP, SMTP and IMAP to 1024, 1025 and 1026 respectively.

If you have the solution to any of these, please tell me in as simple a way as you can! I'm new to Ubuntu and I'm not familiar with any of these terms or the filesystem, so if you could dumb it down enough for someone who's just come from XP, I would really appreciate it. :)

I searched, but the answers I got weren't simple enough for me to follow - they seemed to assume that people following them would be familiar with most every aspect of Ubuntu.

Thanks in advance!

---

### Post by yogo on 2007-08-12
#2 Update Thunderbird in Synaptic from System>adminstration>Synaptic

For #3, go to system >preferences >preferred applications and select Mozilla-thunderbird from drop down list.

It should look like this mozilla-thunderbird %s

4. Not really sure on the hotmail thing, I did change Thunderbird for Gmail and it went flawless, just make sure  that you configure ports right and server.

---

### Post by BlackAnthrax on 2007-08-12
If you are wanting to do this the correct way, (as I have), follow these steps. First...uninstall Thunderbird using Add/Remove (it is an old version, and will be an old version until Gutsy is released). You more than likely will not have an icon anymore in your menu, so navigate to System-->Preferences-->Main Menu. If you are not familiar with this interface, it isn't hard. The icon on the panel isn't the "default mail button", but an evolution button. The "default mail" that you changed is for if you click an email in Firefox, it will open your default mail client and compose a message to the email.  You can the icon on the panel t to open Thunderbird, just right click on the icon and select properties. I haven't a clue about hotmail, you should use Gmail. If you don't understand any of this, message me, I can help.

Oh, btw, in the menu editor and the panel, you need 
/opt/thunderbird/thunderbird 
as the command.

---

### Post by dorkdork777 on 2007-08-12
> **yogo said:**
> #2 Update Thunderbird in Synaptic from System>adminstration>Synaptic

For #3, go to system >preferences >preferred applications and select Mozilla-thunderbird from drop down list.

It should look like this mozilla-thunderbird %s

4. Not really sure on the hotmail thing, I did change Thunderbird for Gmail and it went flawless, just make sure  that you configure ports right and server.

Synaptic says the latest version is 1.5.0.12 - the same as Add/ Remove Programs.

> **BlackAnthrax said:**
> If you are wanting to do this the correct way, (as I have), follow these steps. First...uninstall Thunderbird using Add/Remove (it is an old version, and will be an old version until Gutsy is released). You more than likely will not have an icon anymore in your menu, so navigate to System-->Preferences-->Main Menu. If you are not familiar with this interface, it isn't hard. The icon on the panel isn't the "default mail button", but an evolution button. The "default mail" that you changed is for if you click an email in Firefox, it will open your default mail client and compose a message to the email.  You can the icon on the panel t to open Thunderbird, just right click on the icon and select properties. I haven't a clue about hotmail, you should use Gmail. If you don't understand any of this, message me, I can help.

Oh, btw, in the menu editor and the panel, you need 
/opt/thunderbird/thunderbird 
as the command.

Thanks! That helped loads - I now have a fully up-to-date Thunderbird in my Internet menu!

However, I do have a few more (hopefully simpler) questions.

#5 Why isn't the Synaptic package for Thunderbird up-to-date? I thought that was what the Update Manager was all about - checking Synaptic for updates to your packages, and finding security updates for Ubuntu?

#6 I'd love to switch to GMail, but everyone I know has my Hotmail address. Is there anything I could use to forward all the email that enters my Hotmail account to a GMail account, so they can send email to my Hotmail address and I'd receive it through GMail? Like a (hopefully free) service on the net I could subscribe to, or an app I could use?

---

### Post by BlackAnthrax on 2007-08-12
Ahh...yes, that is what it is supposed to be about. Although, I suppose that because the update from 1.5 to 2.0 was major, it is being tested, and will only be added to Gutsy's repositories. As for the Hotmail/Gmail, you can use Gmail to access other accounts using POP3, but I'm not sure if that will work with Hotmail. I haven't used Hotmail ever, so I don't know. IMO, sending a mass email to all your contacts, simply saying that you have switched email addresses would be the easiest thing to do. Occasionally check Hotmail, and keep reminding those that don't get it about the change. You may be able to forward mail in otmail, but I believe that costs a few bucks.

---

### Post by davidsrsb on 2007-08-12
Hotmail (free version) does not support pop3 or imap.
You need to use a http collector program like gotmail or getlive

---

### Post by dorkdork777 on 2007-08-12
> **BlackAnthrax said:**
> Ahh...yes, that is what it is supposed to be about. Although, I suppose that because the update from 1.5 to 2.0 was major, it is being tested, and will only be added to Gutsy's repositories. As for the Hotmail/Gmail, you can use Gmail to access other accounts using POP3, but I'm not sure if that will work with Hotmail. I haven't used Hotmail ever, so I don't know. IMO, sending a mass email to all your contacts, simply saying that you have switched email addresses would be the easiest thing to do. Occasionally check Hotmail, and keep reminding those that don't get it about the change. You may be able to forward mail in otmail, but I believe that costs a few bucks.

OK. It's slightly disappointing that I can't just get the latest release no matter what from Synaptic or Add/Remove, but it's not such a big deal. (Just out of curiosity, is there something I could do, like enter something in the Terminal, or change some settings, to list the latest versions of everything there?)

I can't really send out a mass mail, as most of my non-crap mail comes from random people who need help (I'm a member of a PSP hacking site) and I don't add them to my address book, as in most cases they give almost no details about themselves; just a username.

I could put it in my signature over there, of course, but what about the 40+ people who already have my mail, many of whom I have lost the addresses to? An auto-responder would be ideal, but I don't know how about to get one, nor to set it up.

> **davidsrsb said:**
> Hotmail (free version) does not support pop3 or imap.
You need to use a http collector program like gotmail or getlive

OK, but how do I install/use these apps, and how would I configure them to automatically forward mail?



I hope you guys aren't getting too annoyed with the masses of questions I'm asking, but I'm pretty much a total newb to this stuff. :-k

---

### Post by BlackAnthrax on 2007-08-12
Hmmmm....I dunno. Gmail is a whole lot better, if I were you, I would use it as my primary, I'd put it as your signature, however do check your Hotmail (daily, weekly, it's up to you). Kindly explain to everyone that you have changed addresses. After a while, I'll bet that you no longer receive any "real" mail at hotmail. I don't think I understand the question about terminal, but if i do understand, I don't know if it is possible. However I would ask why you wouldn't want (or need) to! Furthermore, haven't you received mail from hotmail in Thunderbird before? If this is so, it means that you have bought POP3 or something. If you have POP3 access, this means that you can use Gmail to check the address. Sign up for a free Gmail account, and see what you can do with the settings...

---

### Post by nanotube on 2007-08-13
for automated installation of the latest release from mozilla, i recommend the [ubuntuzilla project]("http://ubuntuzilla.sourceforge.net") (though you seem to have this part solved already through some manual tweaking).

to get email from hotmail into your thunderbird, i strongly suggest the [webmail extension]("http://webmail.mozdev.org/") for thunderbird (with its companion extension, webmail-hotmail.

---

### Post by robin.w on 2007-08-13
Hey folks,

a little problem with my Thunderbirdie. Does anybody know how to add or activate DOWNLOAD ACTIONS??? It seems that doesn't work for me. I'm using Ubuntu package, ver. 2.0.0.6, OS Kubuntu 7.10.

Thanx a lot for your suggestions.

---

### Post by nanotube on 2007-08-13
> **robin.w said:**
> Hey folks,

a little problem with my Thunderbirdie. Does anybody know how to add or activate DOWNLOAD ACTIONS??? It seems that doesn't work for me. I'm using Ubuntu package, ver. 2.0.0.6, OS Kubuntu 7.10.

Thanx a lot for your suggestions.

this link will give you all the relevant information:
[http://kb.mozillazine.org/Actions_for_attachment_file_types](http://kb.mozillazine.org/Actions_for_attachment_file_types)

---

### Post by praet on 2007-08-13
#2

FYI, you *can* install the latest thunderbird.  You just have to ignore the packaging system and install it from the download provided by mozilla directly.

[http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/)
[http://kb.mozillazine.org/Upgrading_-_Thunderbird](http://kb.mozillazine.org/Upgrading_-_Thunderbird)

Basically the instructions are to tar zxf thunderbird-2.0.0.5.tar.gz then move the file to your programs location ( /opt/thunderbird/ ) then link ( ln -s ) the prgram location to your user/bin
(/usr/bin/thunderbird -> /opt/thunderbird/thunderbird) 

Also, note that the ubuntu packaged thunderbird is named mozilla-thunderbird so any shortcuts that you want to keep/point to the new version will have to be edited to point to the new (/usr/bin/thunderbird) binary .

---

### Post by nanotube on 2007-08-13
> **praet said:**
> #2

FYI, you *can* install the latest thunderbird.  You just have to ignore the packaging system and install it from the download provided by mozilla directly.

[http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/)
[http://kb.mozillazine.org/Upgrading_-_Thunderbird](http://kb.mozillazine.org/Upgrading_-_Thunderbird)

Basically the instructions are to tar zxf thunderbird-2.0.0.5.tar.gz then move the file to your programs location ( /opt/thunderbird/ ) then link ( ln -s ) the prgram location to your user/bin
(/usr/bin/thunderbird -> /opt/thunderbird/thunderbird) 

Also, note that the ubuntu packaged thunderbird is named mozilla-thunderbird so any shortcuts that you want to keep/point to the new version will have to be edited to point to the new (/usr/bin/thunderbird) binary .

for anyone who needs a more detailed reference for manual installation from mozilla, all these instructions are put out in detail on the official ubuntu wiki:
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion) 
(the section on manual install - the automatic install section talks about the ubuntuzilla script and the iuculano repository)

---

### Post by praet on 2007-08-13
Excellent link!

Thanks.

---

### Post by travislhendrix on 2007-08-16
> **nanotube said:**
> for automated installation of the latest release from mozilla, i recommend the [ubuntuzilla project]("http://ubuntuzilla.sourceforge.net") (though you seem to have this part solved already through some manual tweaking).

to get email from hotmail into your thunderbird, i strongly suggest the [webmail extension]("http://webmail.mozdev.org/") for thunderbird (with its companion extension, webmail-hotmail.


The problem I have with the webmail extension is that it uses the localhost and that is blocked exept as root.  Is there a way to run Thunderbird with root privileges, because then the localhost problem would go away and the hotmail extension would work.  I tried changing the launch command to sudo mozilla-thunderbird but that would not open thunderbird.  I also tried from a terminal to open /opt/thunderbird/thunderbird and that worked but when I put sudo /opt/thunderbird/thunderbird I get the error sudo: /etc/sudoers is mode 0640, should be 0440  any idea what this is doing?

---

### Post by praet on 2007-08-16
The sudoers file has the wrong permissions set and is warning you about it.
Try this in a terminal to fix the permissions:
```
su -
chmod 0440 /etc/sudoers
exit
```

In the webmail plugin faq they state to set the ports used by webmail over 1024.  I am not familiar with the plugin itself but the main site may help. 
[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

---

### Post by nanotube on 2007-08-16
> **travislhendrix said:**
> The problem I have with the webmail extension is that it uses the localhost and that is blocked exept as root.  Is there a way to run Thunderbird with root privileges, because then the localhost problem would go away and the hotmail extension would work.  I tried changing the launch command to sudo mozilla-thunderbird but that would not open thunderbird.  I also tried from a terminal to open /opt/thunderbird/thunderbird and that worked but when I put sudo /opt/thunderbird/thunderbird I get the error sudo: /etc/sudoers is mode 0640, should be 0440  any idea what this is doing?

webmail's servers should run on ports above 1024. i have my pop running on 4000, e.g...

as to sudoers, the previous poster's got it right - just chmod it.

---

### Post by ShuaM75 on 2007-09-25
> **praet said:**
> The sudoers file has the wrong permissions set and is warning you about it.
Try this in a terminal to fix the permissions:
```
su -
chmod 0440 /etc/sudoers
exit
```

In the webmail plugin faq they state to set the ports used by webmail over 1024.  I am not familiar with the plugin itself but the main site may help. 
[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

When I typed this into the terminal I get an error saying:
su: Authentication failure
Sorry.

I know that my passwor is correct. Am I supposed to type:

```
su -chmod 0440 /etc/sudoers
exit
```

BTY I'm having problems with getting Webmail working correctly. I can't get the lights to turn green no matter what port I use. I am the sole user of this lap top and own the entire system that we run on here in my house. So admin. privileges should not be a concern.

Thanks for any help.

---

### Post by nanotube on 2007-09-25
use the following:
```
sudo chmod 0440 /etc/sudoers
```

as to webmail not working - have you tried several different ports above 1024? have you restarted thunderbird?

---

### Post by DavidFourer on 2007-10-01
I somehow got two different Thunderbird launchers, which resulted in my email records getting saved to two different sets of files.  I solved the problem by changing my default email application in System>Preferences>Preferred Applications.  (from "thunderbird" to "mozilla-thunderbird").  Now one version of Thunderbird never runs, so I don't know it's there.  I'd like to know what happened and clean it up.

usr/bin/thunderbird 
     launches Version 1.5.0.13 (20070809)
     saves email in home/david/.thunderbird/o9iq6ju2.default/mail/Local Folders
usr/bin/mozilla-thunderbird 
     launches Version 1.5.0.13 (20070824)
     saves emails in home/david/.mozilla-thunderbird/u7x8c5ww.default/mail/Local Folders/

---

### Post by por100pre1 on 2007-10-01
> **DavidFourer said:**
> I somehow got two different Thunderbird launchers, which resulted in my email records getting saved to two different sets of files.  I solved the problem by changing my default email application in System>Preferences>Preferred Applications.  (from "thunderbird" to "mozilla-thunderbird").  Now one version of Thunderbird never runs, so I don't know it's there.  I'd like to know what happened and clean it up.

usr/bin/thunderbird 
     launches Version 1.5.0.13 (20070809)
     saves email in home/david/.thunderbird/o9iq6ju2.default/mail/Local Folders
usr/bin/mozilla-thunderbird 
     launches Version 1.5.0.13 (20070824)
     saves emails in home/david/.mozilla-thunderbird/u7x8c5ww.default/mail/Local Folders/

Let's see if theres a thunderbird version in the /opt folder:

```
cd /opt
```

```
ls -a
```

If "thunderbird" appears you have another version of Thunderbird.
Have you installed Thunderbird 2?

---

### Post by DavidFourer on 2007-10-01
> **por100pre1 said:**
> Let's see if theres a thunderbird version in the /opt folder:
Have you installed Thunderbird 2?

I found /opt/thunderbird/...  Including what appears to be the whole installation.
/opt/thunderbird/thunderbird is another launching script
#!/bin/sh
...
## $Id: mozilla.in,v 1.5.4.1 2005/09/20 21:13:05 dbaron%dbaron.org Exp $
...
This does in fact launch Thunderbird V 1.5.0.13 (20070809), the strange one that showed up recently I think.  The email folders are mostly empty except for a few emails that were "lost" before.

Can you tell me what is the purpose of /opt?
I guess I should remove the /opt version, now that email links in the browser don't default to it.

The other folder in /opt is /opt/wicd, which I probably installed when I recently got a wireless modem.  Why is this not in /usr/bin?
The file system is still confusing to me.  It looks like binary executables are in /usr/bin along with hundreds of other files, and the application accessory files are in /usr/share/

Thanks.

---

### Post by nanotube on 2007-10-02
> **DavidFourer said:**
> I found /opt/thunderbird/...  Including what appears to be the whole installation.
/opt/thunderbird/thunderbird is another launching script
#!/bin/sh
...
## $Id: mozilla.in,v 1.5.4.1 2005/09/20 21:13:05 dbaron%dbaron.org Exp $
...
This does in fact launch Thunderbird V 1.5.0.13 (20070809), the strange one that showed up recently I think.  The email folders are mostly empty except for a few emails that were "lost" before.

Can you tell me what is the purpose of /opt?
I guess I should remove the /opt version, now that email links in the browser don't default to it.

The other folder in /opt is /opt/wicd, which I probably installed when I recently got a wireless modem.  Why is this not in /usr/bin?
The file system is still confusing to me.  It looks like binary executables are in /usr/bin along with hundreds of other files, and the application accessory files are in /usr/share/

Thanks.

the stuff from the repos doesn't go into /opt - the only way you'd end up with a thunderbird in /opt is if you manually put it there, or used a third-party installer script to do so (such as ubuntuzilla). do you recall ever doing either of these?

generally speaking, /opt is just a place to put some locally-installed stuff out of the way so as not to interfere with anything else in the system. see the description in the filesystem hierarchy standard for more detail: 
[http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES](http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES)

so... in other words, if you don't need your /opt/thunderbird installation ,you can delete it, i suppose... then just keep using the repos version, if you are happy using tb 1.5.

---

### Post by DavidFourer on 2007-10-02
> **nanotube said:**
> the stuff from the repos doesn't go into /opt - the only way you'd end up with a Thunderbird in /opt is if you manually put it there, or used a third-party installer script.
I suspect this is what happened.  Long before Feisty, before Edgy, I installed TB from their web site.  Then it came from the repository with an Ubuntu upgrade.  Recently I somehow opened the /opt copy of Thunderbird and was promptly offered an upgrade.  That must have re-set the default mail program to the /opt copy, and my saved emails "disappeared".

---

### Post by nanotube on 2007-10-02
ah heh i see... i think i saved myself a lot of trouble by skipping the upgrade path from dapper, and just doing a fresh install of feisty. :)

anyway, so the emails are still all there, it's jsut that some of them are in .thunderbird, and some others are in .mozilla-thunderbird.

.moz-t is the dir used by the repos version, .t is the one used by the mozilla build.

if you choose to use the repos version, e.g., you can just import the emails from .t into your account...

---

