---
title: "Thunderbird hyperlinks don't work"
date: 2008-05-18
forum: General Help
---

### Post by azizzle on 2008-05-18
How can I get the hyperlinks in my emails to open a browser. Whenever I click a link there is no action at all. I've never had this problem before, and I've scoured the preferences and options in thunderbird, and I still can't find a solution.

---

### Post by kellemes on 2008-05-18
> **azizzle said:**
> How can I get the hyperlinks in my emails to open a browser. Whenever I click a link there is no action at all. I've never had this problem before, and I've scoured the preferences and options in thunderbird, and I still can't find a solution.

Edit -> Preferences -> Advanced/General -> Config Editor -> RightClick somewhere in the list -> New -> String.. now type..
**network.protocol-handler.app.http**
<OK>
now type the name of your browser..
**firefox**
<OK>

You can also browse to the entry named "network.protocol-handler.app.https" (hence the **s**) and change it's value to "firefox".

---

### Post by azizzle on 2008-05-18
> **kellemes said:**
> Edit -> Preferences -> Advanced/General -> Config Editor -> RightClick somewhere in the list -> New -> String.. now type..
**network.protocol-handler.app.http**
<OK>
now type the name of your browser..
**firefox**
<OK>

You can also browse to the entry named "network.protocol-handler.app.https" (hence the **s**) and change it's value to "firefox".

I'm still having the problem. Should I reinstall thunderbird?

---

### Post by eewo on 2008-05-21
Same problem here.

Running:
- Thunderbird version 2.0.0.14 (20080505)
- Firefox 2.0.0.14

Tried to change in Config Editor entries:

network-protocol-handler.warn-external.ftp
network-protocol-handler.warn-external.http
network-protocol-handler.warn-external.https

to true

No success

Can someone help?

---

### Post by utUtu on 2008-05-21
> **eewo said:**
> Same problem here.

Running:
- Thunderbird version 2.0.0.14 (20080505)
- Firefox 2.0.0.14

Tried to change in Config Editor entries:

network-protocol-handler.warn-external.ftp
network-protocol-handler.warn-external.http
network-protocol-handler.warn-external.https

to true

No success

Can someone help?

It's a security risk opening links from your email.

---

### Post by GoranI on 2008-05-21
We are not so stupid to open suspitioous links !!! Anyway, I want to open links from thunderbird, CAN ANYONE - PLEASE TELL US HOW!!??  BIG THANKS FROM ALL OF US !!!

---

### Post by GoranI on 2008-05-21
I have found solution for this. It doesn`t open in firefox , but it open the link in thunderbird window so you can browse it. if i find a way to open directly to the firefox i will inform you !!
Do this in config editor:
(Add string No. 2 and change other srigs to this values)
NAME OF STRING--------------------------------VALUE                      
1.network.cookie.alwaysAcceptSessionCookies-----true
2.network.protocol-handler.app.http-------------firefox%s
3.network.protocol-handler.expose-all-----------true
4.network.protocol-handler.external.javascript--true
5.network.protocol-handler.external.shell-------true
6.network-protocol-handler.warn-external.ftp----true
7.network-protocol-handler.warn-external.http---true
8.network-protocol-handler.warn-external.https--true

---

### Post by Bubba64 on 2008-05-22
> **kellemes said:**
> Edit -> Preferences -> Advanced/General -> Config Editor -> RightClick somewhere in the list -> New -> String.. now type..
**network.protocol-handler.app.http**
<OK>
now type the name of your browser..
**firefox**
<OK>

You can also browse to the entry named "network.protocol-handler.app.https" (hence the **s**) and change it's value to "firefox".

Perfect instructions I installed the latest FF 3 from Launchpad, had all the add ons, plugins, and bookmarks but it seemed to disable my redirect in Thunderbird this fixed it. I had looked at the config editor but didn't know what to look for or how to change it.

---

### Post by David Oxland on 2008-05-25
When I went to Firefox Pref Advanced/General there was no "Config Editor" but I did find "System Defaults" and "Always check to see if Firefox is the default browser at startup"  "Check Now".
Did the check now and it was not the default.
Changed to default and now Thunderbird links work!
So the trouble was that Firefox was not set as the default browser, I guess.

---

### Post by Bubba64 on 2008-05-25
> **David Oxland said:**
> When I went to Firefox Pref Advanced/General there was no "Config Editor" but I did find "System Defaults" and "Always check to see if Firefox is the default browser at startup"  "Check Now".
Did the check now and it was not the default.
Changed to default and now Thunderbird links work!
So the trouble was that Firefox was not set as the default browser, I guess.

You went to the wrong place for config your system wouldn't run with out it, my hyper link didn't work in spite of ff being the default. Config:editor has to be put in the browser search window to access it in Firefox. The original instructions were how to access config:editor in Thunderbird.

---

### Post by Deerfoot on 2009-03-16
> **David Oxland said:**
> When I went to Firefox Pref Advanced/General there was no "Config Editor" but I did find "System Defaults" and "Always check to see if Firefox is the default browser at startup"  "Check Now".
Did the check now and it was not the default.
Changed to default and now Thunderbird links work!
So the trouble was that Firefox was not set as the default browser, I guess.
Thanks to David, I have now resolved the same problem after searching the forums for help.I've just had my Ubuntu upgraded from 7.04 to 8.10 and discovered Thunderbird's hyperlinks to Firefox browser no longer worked.Checked if Firefox was set as default browser; it was not. Set it to default and immediately, the hyperlinks in Thunderbird are working. So easy. Thank you David!

---

### Post by American on 2009-04-20
Upgraded to 9.04 from 8.10 and now I have this problem with FF 3.0.8 and TB 2.0.0.21. Checked to see if FF has default, it was.

Was working fine in 8.10 and TB 2.0xx.

Thoughts?

---

### Post by caro on 2009-04-22
> **American said:**
> Upgraded to 9.04 from 8.10 and now I have this problem with FF 3.0.8 and TB 2.0.0.21. Checked to see if FF has default, it was.

Was working fine in 8.10 and TB 2.0xx.

Thoughts?

I have the same issue.  I logged a bug in Launchpad and with Mozilla.  No resolution yet.

---

### Post by jfg69 on 2009-07-09
> **Bubba64 said:**
> Perfect instructions I installed the latest FF 3 from Launchpad, had all the add ons, plugins, and bookmarks but it seemed to disable my redirect in Thunderbird this fixed it. I had looked at the config editor but didn't know what to look for or how to change it.

Worked for me as well. Very frustrating issue... not sure why Mozilla decided to disable links..

---

### Post by American on 2009-07-09
Didn't work for me. There is another discussion about this here:

[http://ubuntuforums.org/showthread.php?p=7586352](http://ubuntuforums.org/showthread.php?p=7586352)

---

### Post by themunkee on 2009-07-26
I had the same problem - links would not open in Firefox, but if I changed the default browser to Opera in System > Preferences > Preferred Applications it worked.

Whilst looking at this I worked out the fix - there is something up with the Thunderbird installed when I upgraded to Jaunty - Thunderbird doesn't appear as a Mail client under Preferred Apps. 

I noticed when I searched for 'Thunderbird' in Synaptic, it wasn't selected so I installed it. This new version seems to work fine loading links in Firefox.

---

### Post by JimFuqua on 2009-07-26
I had the same problem after installing Firefox 3.5 and removing Firefox 3.?

I tried everything I could find on the Internet but none of the solutions worked on my machine.

I finally found a solution -- more from trial and error than knowledge.

I found a broken firefox link in /usr/bin and deleted the link (/usr/bin/firefox).  Then I put back a link with the following command:

sudo ln -s /usr/bin/firefox-3.5  /usr/bin/firefox 

This solved the problem.  

First make sure that your preferred browser is firefox-3.5  %u  in System-Preferences-Preferred Applications. /usr/bin/firefox-3.5 also seems to work, but the other link is what the control panel links use.

Jim Fuqua

---

### Post by heatblazer on 2009-10-27
> **kellemes said:**
> Edit -> Preferences -> Advanced/General -> Config Editor -> RightClick somewhere in the list -> New -> String.. now type..
**network.protocol-handler.app.http**
<OK>
now type the name of your browser..
**firefox**
<OK>

You can also browse to the entry named "network.protocol-handler.app.https" (hence the **s**) and change it's value to "firefox".

Incredible! Great solution!

---

### Post by American on 2009-11-02
Upgraded to 9.10 and now FireFox 3.5.4 is doing this to me again. I've tried everything but now I'm back to where I started. Why oh why???

---

### Post by American on 2009-11-02
What is odd is that I fired up TB 2.0 and it's http config points to /usr/bin/firefox and it works like a charm....but not in Shredder.

---

### Post by TAZ46 on 2009-12-15
My first post...hope I'm doing it right.

Looks like this is an ongoing problem.  Once I restarted thunderbird it worked.  I've forwarded the solution link to a friend running ubuntu (gnome) 9.10 who said he was having the same problem.

Adding the suggested string worked for me.  I'm running kubuntu 9.10 with thunderbird version 2.0.0.23 (20090817).

The Config Editor is not with the regular tabs... it's just above the "close" button.  Here's a screenshot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=139971&stc=1&d=1260861452[/IMG]

I inserted the string at the beginning of all the "network-protocol..." strings (in case that makes a difference).

Thanks for the solution !

---

### Post by picklemonkey on 2009-12-15
I'm having the same problem.  I recently installed Thunderbird 3, and now my links don't want to work.  I have tried the suggestions here by adding the following sections:

 - network.protocol-handler.app.ftp
 - network.protocol-handler.app.http
 -  network.protocol-handler.app.https

I set each to a combination of values:

 - firefox
 - firefox-3.5
 - /usr/bin/firefox
 - /usr/bin/firefox-3.5
 - /usr/bin/firefox-3.5.sh

I have restart Thunderbird after each attempt, but my issue continues even though it seems to fix other users.

On a side note, I have tried setting Chrome to my default browser (I had Chrome before this issue started) then Firefox back to default as a troubleshooting step, but Firefox said it was already the default browser.  I then tried to set my default browser from the command line:

   sudo update-alternatives --config x-www-browser

But it tells me Firefox is the default:

  Selection    Path                       Priority   Status
------------------------------------------------------------
  0            /usr/bin/chromium-browser   40        auto mode
  1            /usr/bin/chromium-browser   40        manual mode
* 2            /usr/bin/firefox-3.5        40        manual mode

I have tried changing it to Chrome then back but no luck.

I also went to set Firefox as my default browser in Settings -> Preferred Applications, but it's already set.  Any other application can open links in Firefox fine.  I even installed RSSOwl a couple days ago (after this issue started appearing) and it's able to open them fine.

Sorry for the exhaustive troubleshooting steps, but I'm an ubuntu novice at best and I feel like I've tried everything!


(Don't even get me started on my frustration over ditching Thunderbird's RSS for RSSOwl!  Years of frustration compounded by the still-broken TB3 RSS made me give up on TB for RSS all together!) :(

---

### Post by picklemonkey on 2009-12-18
any ideas?

---

### Post by jfg69 on 2010-01-22
> **picklemonkey said:**
> I'm having the same problem.  I recently installed Thunderbird 3, and now my links don't want to work.  I have tried the suggestions here by adding the following sections:

 - network.protocol-handler.app.ftp
 - network.protocol-handler.app.http
 -  network.protocol-handler.app.https

I set each to a combination of values:

 - firefox
 - firefox-3.5
 - /usr/bin/firefox
 - /usr/bin/firefox-3.5
 - /usr/bin/firefox-3.5.sh

I have restart Thunderbird after each attempt, but my issue continues even though it seems to fix other users.

Having the same issue.. upgraded to FF3.6 added FF3.7, uninstalled FF3.0 and 3.5 and lost the link function in TB 3.0. Upgrade to TB3.0.1 did nothing either. Tried various combinations and even adding chrome as default browser. I get zip.. I cant click and open or right click and "launch in browser" 

Any other ideas?

---

### Post by bmdavis on 2010-01-23
Same experience here.  Tried different versions of firefox and even chrome, still will not open.  Changed the prefs.js a hundred times, nothing.

I click on the links and get nothing.  If I right click to OPEN IN BROWSER, still nothing. 


anybody else have ideas?

---

### Post by Lisbeth on 2010-01-23
I found this in another thread, and it helped me: > **ad_267 said:**
> Go to edit - preferences - attachments, then set your web browser under http and https. If your browser isn't listed, you need to select &quot;use other'. Unfortunately Thunderbird isn't integrated well with Gnome so it won't give you a list of applications but will show the file open dialog. Firefox is located at /usr/bin/firefox so you can enter that in the address bar.

I'm basing this on Thunderbird 3.0 but I think it's the same in Thunderbird 2.

---

### Post by caro on 2010-01-23
Is your OS up to date?

I had this problem for quite a while after moving to 9.04.  Tried all the things mentioned in this thread.  One day after several weeks, it just worked again (sounds crazy I know), but I believe it was due to some updates that I ran.  I can offer no other explanation.

---

### Post by picklemonkey on 2010-01-23
> **Lisbeth said:**
> I found this in another thread, and it helped me:

[img]http://ubuntuforums.org/attachment.php?attachmentid=144698&stc=1&d=1264275212[/img]

I don't have http/https listed here, and I don't have the option to add it anywhere...

---

### Post by samandiriel on 2010-02-19
I'm having the exact same problem - I click on links in emails, and they don't open a browser.  

I've tried messing about with the http/s handlers in about:config with no luck there either.  

I've also tried editing the Download Actions, but like another poster I have no way to add a new file type.

I even tried messing with user.js from some super old advice.

VERY FRUSTRATING!!!  I've googled quite a bit, and so far have found zero to help :(

---

### Post by waz668 on 2010-02-23
> **Lisbeth said:**
> I found this in another thread, and it helped me:
This worked for me [# 28], thank you!

---

### Post by picklemonkey on 2010-05-04
Just an update... it looks like this issue fixed itself for me once I upgraded to Lucid Lynx.  Hopefully this fixes everyone else too!

---

### Post by Z@ph0d on 2010-06-15
I had this problem when I upgraded to 3.6 of Firefox and Thunderbird 3 on Ubuntu 9.04.

There were two parts needed to fix my issue:

From the Thunderbird preferences dialog (Edit->preferences)

First: Added the network.protocol-handler.app.http and https pointing to /usr/bin/firefox %s in the config Editor (Under "Advanced->Config Editor")

<THEN>

Second: As suggested by Lizbeth, Click on the attachments icon.  The http and https "Content Type" should be visible.  Change the actions to "Use Other".  Then choose the location of firefox using the dialog.

All fixed! :D

---

### Post by vanipc on 2010-10-26
> **David Oxland said:**
> When I went to Firefox Pref Advanced/General there was no "Config Editor" but I did find "System Defaults" and "Always check to see if Firefox is the default browser at startup"  "Check Now".
Did the check now and it was not the default.
Changed to default and now Thunderbird links work!
So the trouble was that Firefox was not set as the default browser, I guess.
Thanks David, Exactly this was the reason  for my case "**So the trouble was that Firefox was not set as the default browser**".  Make the firefox as the default browser as stated and the problem is gone.
You could cross check the problem here in these files. 

cat  ~/.gconf/desktop/gnome/url-handlers/http/%gconf.xml
cat  ~/.gconf/desktop/gnome/url-handlers/https/%gconf.xml

In my case, there was chromium-browser which was installed and removed but these files were still pointing to chromium-browser which doesn't exist. Thunderbird fails to pick this earlier default browser. Now make the firefox as default and restart thunderbird and check these files again it will be overwritten with firefox. :)

---

### Post by vanipc on 2010-10-26
Thanks David, Exactly this was the reason  for my case "**So the trouble was that Firefox was not set as the default browser**".  Make the firefox as the default browser as stated and the problem is gone.
You could cross check the problem here in these files. 

cat  ~/.gconf/desktop/gnome/url-handlers/http/%gconf.xml
cat  ~/.gconf/desktop/gnome/url-handlers/https/%gconf.xml

In my case, there was chromium-browser which was installed and removed  but these files were still pointing to chromium-browser which doesn't  exist. Thunderbird fails to pick this earlier default browser. Now make  the firefox as default and restart thunderbird and check these files  again it will be overwritten with firefox. :smile:

---

