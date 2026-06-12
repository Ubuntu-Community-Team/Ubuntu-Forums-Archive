---
title: "CheckGmail broken?"
date: 2007-12-13
forum: General Help
---

### Post by dysphasi on 2007-12-13
Hope someone can help me here, I've been using CheckGmail (v1.12) absolutely fine up until today, no settings have been changed at all, but it is now refusing to log in, returning an 'Error: 401 Unauthorised'.

This is definitely not related to an incorrect password/username, I've re-entered it over and over, tried different accounts, always the same login error. Gmail itself is working fine over the net, it seems that it is just checkgmail that is not working.

Has anyone got or had a similar problem? Anyone with any advice as to what might be going on? 

Thanks in advance for any help

---

### Post by bandi on 2007-12-13
You're not alone ;). I have the same problem, maybe some udates made checkgmail not working but honestly i can't remember what were the updates today.

---

### Post by winkman on 2007-12-13
I've been offline for the past week, and just reconnected to the internet, only to have CheckGmail give me the same error. Darn. Any ideas? I've just submitted a bug report to the sourceforge site:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1849980&group_id=137480&atid=738663](http://sourceforge.net/tracker/index.php?func=detail&aid=1849980&group_id=137480&atid=738663)

Mitch

---

### Post by cool_penguin on 2007-12-13
same here. i unknowingly posted a similar thread (silly me)


-Harry

---

### Post by gwethir on 2007-12-13
Yup, same here... Worked fine yesterday. But won't work now, so searched the forums. Probably some update-problems with gmail that doesn't allow it to connect? Anyway, waiting for update :D

---

### Post by Cride5 on 2007-12-13
Yup, I'm having the same problem. Worked fine yesterday and now login won't work today. I don't believe there were any updates to CheckGMail recently. Perhaps its a change in GMail's authentication..

---

### Post by Circus-Killer on 2007-12-13
same problem.

---

### Post by longlivedeath on 2007-12-13
Try SVN version.

---

### Post by hotweiss on 2007-12-13
This should fix it:

> 
wget [http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail](http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail)
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail

---

### Post by GatorV on 2007-12-13
Works like a charm! Thanks :-)

---

### Post by dysphasi on 2007-12-13
Superb, thanks! .... What's gone wrong that works in the SVN version?

---

### Post by gerardlouw on 2007-12-13
Hi everyone,

I also got the same error with checkgmail, though hotweiss's solution has worked great for me.

I was wondering if there is a similar solution for kcheckgmail? My client stopped logging in a few weeks ago, then I switched to checkgmail, though I still prefer the KDE version (as I run Kubuntu, and for various other reasons).

Thanks a lot.

---

### Post by winkman on 2007-12-13
Fantastic! This worked a treat!
I assume that Gmail has changed it's access protocols... and therefore, almost all 'email checkers' wouldn't be working...  silly gmail... Though it's probably something to do with security.. thanks gmail..  :P
Thanks again,
Mitch

---

### Post by Cride5 on 2007-12-13
Cheers hotweiss =D>=D>=D>=D>=D>=D>=D>=D>

---

### Post by hexion on 2007-12-14
Latest SVN version (rev 20) solves the problem:

> svn co [https://checkgmail.svn.sourceforge.net/svnroot/checkgmail](https://checkgmail.svn.sourceforge.net/svnroot/checkgmail) checkgmail
cd checkgmail/
sudo cp checkgmail /usr/bin

---

### Post by hexion on 2007-12-14
BTW, did someone file a bug on launchpad about this?
All Ubuntu users will be having this error until Ubuntu devs upload a patched version to the repos.

---

### Post by mohamad on 2007-12-14
indeed it worked, thnx alot!!

---

### Post by hyperair on 2007-12-14
Here's the bug: [https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/175973](https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/175973)

---

### Post by knutschr on 2007-12-14
At last something that worked for me, too :)
> $ cd /tmp
$ wget [http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail](http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail)
$ sudo cp checkgmail /usr/bin

---

### Post by chinny on 2007-12-14
Same issue - the fix above worked a treat. 

Thanks :D

---

### Post by jasidog on 2007-12-15
Thanks for the fix!

---

### Post by stinkinrich88 on 2007-12-15
genius! thanks, linux community is so amazing ;)

---

### Post by marco202 on 2007-12-15
That did the trick. Tnx!

---

### Post by intense.ego on 2007-12-16
Thanks hotweiss, it fixed the problem in no time.

---

### Post by astromech on 2007-12-16
I usually use the extension for firefox : Gmail Notifier as I find  others don't work well . This one gets updated often .

---

### Post by Kimos on 2007-12-16
hotweiss:
Thanks. That fixed it.

---

### Post by ekram on 2007-12-17
Also works for me. thanks a lot. if you don't know how to run it at system startup please following the link [http://www.ubuntugeek.com/gmail-notifier-for-your-ubuntu-desktop.html]("http://www.ubuntugeek.com/gmail-notifier-for-your-ubuntu-desktop.html")

---

### Post by tjansson on 2007-12-18
The SVN version worked for me as well but both kcheckgmail and checkgmail is broken at the moment.

---

### Post by itsjustarumour on 2008-01-02
> **hotweiss said:**
> This should fix it:

I had the same problem, this fixed it - thanks Hotweiss!

---

### Post by diafanos on 2008-01-06
thanx hotweiss!!!!

I hadn't used my pc for a long period of time and i got disappointed when yesterday came across with this problem!!!!

Your solution was perfect!!!

---

### Post by itsjustarumour on 2008-01-08
Bah, its only 5 days since I fixed this, and half way through this morning the problem returned!

---

### Post by hyperair on 2008-01-08
Strange, I don't have the problem! Perhaps APT updated checkgmail on your system?

---

### Post by itsjustarumour on 2008-01-08
> **hyperair said:**
> Strange, I don't have the problem! Perhaps APT updated checkgmail on your system?

I was just dashing out to work so didn't have time to try and fix it.  I'll have a go when I get home, and report back!

:-)

---

### Post by itsjustarumour on 2008-01-08
> **itsjustarumour said:**
> I was just dashing out to work so didn't have time to try and fix it.  I'll have a go when I get home, and report back!

:-)

Hmmm.... got home, and its mysteriously working again!

:lolflag:

---

### Post by Adam590 on 2008-01-23
EDIT:  Nevermind, the problem was mysteriously resolved.  *scratches head*




Mine was working fine until last night, but now there's the following strange behavior:


-starts fine

-logs in to Gmail fine

-pops up the one-line notification message about new emails fine

-when I mouseover the icon and get the large preview message, I can't click anything in it. 

-when the large message starts to fade, it gets stuck while graying out. I then can't click anything in the icon or the message, and my processor shoots to 100% and stays there until I kill the program.


I tried both the SVN version and the latest stable version (1.13) from the webpage. Same thing happens. Also, I get no errors when running it in the terminal - just the same freezing until I kill it. 

Any ideas?

---

### Post by profediego on 2008-01-29
checkgmail was workin fine until today, i restart my computer and woosh checkgmail is broken again, i try to run it from CLI but i get this message, 

Warning: Gtk2::Sexy not found ...

CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN ([http://search.cpan.org](http://search.cpan.org)) if you want to use this feature ...

File does not exist:  at /usr/bin/checkgmail line 1250
A thread exited while 2 threads were running.

But, if i fun it with sudo it works just fine, could somebody please here, help.   

Thanks.

---

### Post by Adam590 on 2008-02-01
Whoops, I take it back - my problem is still there (see two posts above).


It only happens when I see the mouseover preview for several new messages. 
In other words, it happens whenever the preview box is fairly large.


[INDENT]Anybody seen this before?[/INDENT]

---

### Post by hyperair on 2008-02-01
I don't experience that error. Using 1.12.1svn

---

### Post by Adam590 on 2008-02-01
So am I: CheckGmail v1.12.1svn

Well, at least that eliminates one possibility - thanks.

---

### Post by bred on 2008-03-04
[http://ubuntuforums.org/attachment.php?attachmentid=61537&d=1204634260]("http://ubuntuforums.org/attachment.php?attachmentid=61537&d=1204634260")
this thing worked for me

---

### Post by leftfootleashed on 2008-05-12
That fixed it, thanks hotweiss.
Dave

---

### Post by leftfootleashed on 2008-05-12
That fixed it, thanks hotweiss.
Dave

---

### Post by dspiteri on 2008-07-17
Gah, busted again!

---

### Post by calibrated on 2008-07-17
> **dspiteri said:**
> Gah, busted again!

For a temporary fix, run checkgmail -no_cookies. From man file:

> -no_cookies
    Uses the old Atom feed retrieval method (default in versions 1.7.2 and earlier) of sending the username and password across https. The alternative, and currently default method, is to login to Gmail, save the authentication cookies, and then retrieve the Atom feeds without requiring any further authentication - this method has the benefit of allowing various actions to be carried out upon new messages received, such as deleting, marking as read, archiving or reporting spam. 

---

### Post by stinkinrich88 on 2008-07-17
It's been working fine for me all day

---

### Post by calibrated on 2008-07-17
> **stinkinrich88 said:**
> It's been working fine for me all day

Interesting. It has been broken for me since yesterday. Works fine with -no_cookies.

---

### Post by stinkinrich88 on 2008-07-17
oh yeah, my bad, it stopped after a restart. -no_cookies is good, though

---

### Post by cpetercarter on 2008-07-17
Same here. Checkgmail hasn't worked all day - asks for my username and password, but then refuses to login, asks for username and password again etc.
checkgmail -no_cookies works fine though.

I assume this is a google problem, not an issue with my conputer.

---

### Post by Circus-Killer on 2008-07-18
nice, -no_cookies did the trick.
thanks ;)

---

### Post by scribu on 2008-07-18
It works with -no_cookies but it exits after a few seconds. Any ideas?

---

### Post by stinkinrich88 on 2008-07-19
> **scribu said:**
> It works with -no_cookies but it exits after a few seconds. Any ideas?

Any terminal output?

---

### Post by scribu on 2008-07-19
> **stinkinrich88 said:**
> Any terminal output?

It just says that I don't have Crypt::Simple and Gtk2::Sexy libraries installed. By the way, where can I find these?

Update: Now it seems to work only if I keep the terminal open.

---

### Post by stinkinrich88 on 2008-07-19
> **scribu said:**
> It just says that I don't have Crypt::Simple and Gtk2::Sexy libraries installed. By the way, where can I find these?

Update: Now it seems to work only if I keep the terminal open.

Hmmm, better install the encryption libraries that it is asking for. Type the following into your terminal:

```
sudo apt-get remove libcrypt-simple-perl
```

And confirm any confirmations it asks. This will install the libraries that checkgmail uses to encrypt your gmail password. Hopefully it'll stop the error you're getting and also it will store your password more safely.

---

### Post by scribu on 2008-07-19
I installed libcrypt-simple-perl and it found it and now it encrypts my password, like it should.

I found out however that I do have libsexy installed and it still says it can't find it.

(It still runs only with the terminal open.)

---

### Post by stinkinrich88 on 2008-07-19
ahh, ok, well here's what I'd do:

[LIST]
[*]Open Synaptic package manager (menu-> System -> administration -> synaptic package manager)
[*]Click the "search" button and search for *libsexy*
[*]For me, libsexy2 turns up at the top of the list. This looks pretty good so install it by right-clicking it, selecting "mark for installation" then clicking "apply" in synaptic.
[/LIST]

Or, if you want a simple answer, type this into your terminal:

```
sudo apt-get install libsexy2
```

I already had libsexy2 installed so I take it checkgmail needs it.

---

### Post by scribu on 2008-07-19
You didn't understand. I already had libsexy2 installed. I also installed Gtk2::Sexy, as described [here]("http://marius.scurtescu.com/2007/06/25/installing_checkgmail_on_ubuntu") and it seems to be working at start-up, if i use -no_cookies.

---

### Post by Thomaseov on 2008-07-19
(It still runs only with the terminal open.)[/QUOTE]

**Scribu:**

don't run from terminal...everything run from terminal only runs while terminal is open...
Instead hit alt f2 and type in command...it will then run by itself
Thomas

---

### Post by scribu on 2008-07-19
> **Thomaseov said:**
> (It still runs only with the terminal open.)

**Scribu:**

don't run from terminal...everything run from terminal only runs while terminal is open...
Instead hit alt f2 and type in command...it will then run by itself
Thomas[/QUOTE]

Doh! Thanks, I forgot about that. :rolleyes:

Ok, so it runs at startup with -no_cookies, but it doesn't show several commands like "Archive", "Delete" etc. like it used to a few days ago. I wonder what caused all these problems...

---

### Post by cpetercarter on 2008-07-19
For the avoidance of doubt, you don't need any of the Crypt::simple and Gtk2::sexy stuff in order to run checkgmail. They are needed only for password encryptation. For the moment - until Google returns gmail to its previous state - you can do this:
System > Preferences > Sessions > Startup Programmes 
Add a launcher for checkgmail, or amend the existing launcher, so that the command to run on startup is
```
checkgmail -no_cookies
```

---

### Post by stinkinrich88 on 2008-07-19
ahh yeah sorry, didn't realise you were closing the terminal window.

btw, has anyone told the checkgmail developer about this?

---

### Post by Mguel on 2008-07-19
Thanks cpetercarter! the -no_cookies make it work again.

BTW in kubuntu you can use a scrypt to store password in kwallet without the Crypt::simple:
[http://hoenicke.ath.cx/kwallet/](http://hoenicke.ath.cx/kwallet/)

The problem though I'm having is that every time I restart checkgmail (or restart kubuntu) the stored password is wrong and I have to enter it again. This happened without any encryption of the password and continued after encrypting the password using the crypt::simple, and after using the kwallet script.

Cheers,
Mguel

---

### Post by imjscn on 2008-07-20
It's been a long time---at least it's been more than 2 weeks for me. I guess the developer is not interested in us anymore, otherwise he/she would pop up and tell us something. 
Is there anything else can be a replacement?

---

### Post by scribu on 2008-07-20
> **imjscn said:**
> Is there anything else can be a replacement?

Yes, but they're not nearly as good as CheckGmail was.

---

### Post by richrosa on 2008-07-21
Please get the newest version from SVN. It works for me.

```

cd /tmp
svn co https://checkgmail.svn.sourceforge.n...oot/checkgmail checkgmail
cd checkgmail
sudo cp checkgmail /usr/bin

```

---

### Post by cpetercarter on 2008-07-21
I have submitted a bug notification to the checkgmail project.

---

### Post by scribu on 2008-07-21
> **richrosa said:**
> Please get the newest version from SVN. It works for me.

```

cd /tmp
svn co https://checkgmail.svn.sourceforge.n...oot/checkgmail checkgmail
cd checkgmail
sudo cp checkgmail /usr/bin

```

I can confirm that the svn version works fine, without -no_cookies.

---

### Post by stinkinrich88 on 2008-07-21
> **scribu said:**
> I can confirm that the svn version works fine, without -no_cookies.

same here! cheers!

---

### Post by imjscn on 2008-07-21
> **richrosa said:**
> Please get the newest version from SVN. It works for me.

```

cd /tmp
svn co https://checkgmail.svn.sourceforge.n...oot/checkgmail checkgmail
cd checkgmail
sudo cp checkgmail /usr/bin

```

I guess I'm the unluckiest case...I can't open webpages in sourceforge since I installed Xubuntu. Now, with this svn co [https://checkgmail](https://checkgmail)......
I got this:
svn: PROPFIND request failed on '/checkgmail'
svn: PROPFIND of '/checkgmail': Could not resolve hostname `checkgmail.svn.sourceforge.n...oot': No address associated with hostname ([https://checkgmail.svn.sourceforge.n...oot](https://checkgmail.svn.sourceforge.n...oot))

Update: after failed downloading the svn version, I went back to re-install the old checkgmail, strangely, this time it's not a single file, it's more than 5 files to install. I installed all, added a launcher with no-cookie. Guess what? it works :-)
you guys are great! just hope the developer is as positive as you guys.

---

### Post by stinkinrich88 on 2008-07-22
> **imjscn said:**
> I guess I'm the unluckiest case...I can't open webpages in sourceforge since I installed Xubuntu. Now, with this svn co [https://checkgmail](https://checkgmail)......
I got this:
svn: PROPFIND request failed on '/checkgmail'
svn: PROPFIND of '/checkgmail': Could not resolve hostname `checkgmail.svn.sourceforge.n...oot': No address associated with hostname ([https://checkgmail.svn.sourceforge.n...oot](https://checkgmail.svn.sourceforge.n...oot))

Update: after failed downloading the svn version, I went back to re-install the old checkgmail, strangely, this time it's not a single file, it's more than 5 files to install. I installed all, added a launcher with no-cookie. Guess what? it works :-)
you guys are great! just hope the developer is as positive as you guys.

good stuff! and btw, the svn address posted was abbreviated. The full one (from their website) is: 

svn co [https://checkgmail.svn.sourceforge.net/svnroot/checkgmail](https://checkgmail.svn.sourceforge.net/svnroot/checkgmail) checkgmail

---

### Post by scribu on 2008-07-22
You mean

```
svn co https://checkgmail.svn.sourceforge.net/svnroot/checkgmail checkgmail 
```

---

### Post by stinkinrich88 on 2008-07-22
> **scribu said:**
> You mean

```
svn co https://checkgmail.svn.sourceforge.net/svnroot/checkgmail checkgmail 
```

yeah! sorry!

---

### Post by scribu on 2008-07-22
No need to appologize. It's interesting that it didn't trunkate the url, like before.

---

### Post by Spykie on 2008-07-22
```
svn co https://checkgmail.svn.sourceforge.net/svnroot/checkgmail checkgmail 
```

Thanks this works great with the svn version!

```

cd /tmp
svn co https://checkgmail.svn.sourceforge.n...oot/checkgmail checkgmail
cd checkgmail
sudo cp checkgmail /usr/bin

```

---

