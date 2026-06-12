---
title: "Ubuntu 14.04 Updated Thunderbird and Broke Lightning"
date: 2016-07-20
forum: General Help
---

### Post by bonzo2 on 2016-07-20
Hello,

If this is the wrong place to post this question, kindly move it or let me know.

Today Thunderbird in Ubuntu 14.04 automatically updated to 45.2.0, and this new version of Thunderbird is incompatible with Lightning 4.0.3.1 calendar extension.

I need to revert to the earlier (compatible!) version of Thunderbird, and prevent the automatic updates from happening again. Would anyone be able to help me?

Thanks Much,
Bonzo

---

### Post by howefield on 2016-07-20
Moved to the "*General Help*" forum for a better fit.

---

### Post by bonzo2 on 2016-07-20
Thanks for moving my question, Howefield. :-)
Bonzo

---

### Post by &amp;KyT$0P# on 2016-07-20
Lightning extension has binary components, so one version of Lightning only work with one version of Thunderbird.
You need to update Lightning every time you update Thunderbird in order for it to continue to work.

Downgrading Thunderbird can be done, but note that will leave you with [publicly known vulnerabilities]("https://www.mozilla.org/security/known-vulnerabilities/thunderbird/").  You also don't mention what version of Thunderbird you were previously using, and from the looks of [this]("https://addons.mozilla.org/thunderbird/addon/lightning/versions/4.0.3.1") I'd guess it wasn't 45.1.1...

---

### Post by gifford on 2016-07-20
Yes, Lightning must be updated too. The latest version that works with Thunderbird 45.2.0 is Lightning 4.7.2.

---

### Post by bonzo2 on 2016-07-20
halogen2,

Thanks for your reply!  It's always a relief when someone jumps in to help.

 In my previous post, I meant to include my previous version of Thunderbird, but Thunderbird>help>about provides only the current (updated) version, which is 45.2.0. I don't know how to locate the previous version. 

I do remember that it was very difficult to find compatible versions of Thunderbird, Lightning, and SoGo (DAV) to manage my email, calendar, and contacts. My previous version of Thunderbird was compatible with Lightning 4.0.3.1 and SoGo 32.0.1 because these two add-ons have not been updated, so their versions are still displayed. Since switching to Ubuntu, Thunderbird has always been installed via the Ubuntu repository because I don't know how to install programs any other way.

Is there any hope to restore the previous version of Thunderbird?  I'm over my head with this issue. :-(

Thank you for your time.
Bonzo

---

### Post by bonzo2 on 2016-07-20
Hi gifford,

Thanks for jumping in. I noticed, after I posted my question, that SoGo (DAV connector) was also disabled by the update. Finding versions of Thunderbird, Lightning, and SoGo that are mutually compatible is a big challenge. I'm wondering if it would just be easier to revert to the previous version of Thunderbird. I went to the SoGo homepage, [https://sogo.nu/download.html#/frontends]("http://sogo.nu/download.html#/frontends"), which seems to indicate that the most recent mutually-compatible versions of Thunderbird, Lightning, and SoGo are as follows:

Thunderbird 38
Lightning 4.0.5.2
SoGo 31.0.3

Is it possible to revert to Thunderbird 38 via the repository? 

Thanks,
Bonzo

---

### Post by gifford on 2016-07-20
Bonzo,
Did you not read my post? The current version of Lightning is 4.7.2 and it works with Thunderbird 45.2.0. The Ubuntu software center has it under Thunderbird as an extension.

---

### Post by gifford on 2016-07-20
The only way I know to get an earlier version is either through Mozilla or through one of the Thunderbird Ubuntu PPA's. Good luck. I did find version 3.1.4 of SoGo on their site. It was released July 12, 2016. It may be the fix for your problem.

---

### Post by bonzo2 on 2016-07-20
Hey gifford,

I read your post, and I thank you for hanging in here with me. In case you did not see my last post (as I think we posted simultaneously) I indicated that I need to have versions of Thunderbird, Lightning, and **SoGo** that are mutually compatible. I had not noticed before I started this thread that SoGo had been disabled by the Thunderbird update, too. If I'm reading the SoGo website correctly [https://sogo.nu/download.html#/frontends](https://sogo.nu/download.html#/frontends), it looks like the most recent mutually compatible versions of all three are as follows:

Thunderbird 38
Lightning 4.0.5.2
SoGo 31.0.3

What is your recommendation based on SoGo being a consideration?

Regards,
Bonzo


update> **gifford said:**
> Bonzo,
Did you not read my post? The current version of Lightning is 4.7.2 and it works with Thunderbird 45.2.0. The Ubuntu software center has it under Thunderbird as an extension.

---

### Post by &amp;KyT$0P# on 2016-07-20
The method for downgrading Thunderbird is, as gifford said, to get it from Mozilla's release archives.

Before you start, make sure completely quit Thunderbird, and then back up your entire [profile folder]("http://kb.mozillazine.org/Profile").

Step 1 is to get rid of the package manager Thunderbird:
```
sudo apt-get purge thunderbird*
```
Your custom configuration is saved in your profile that you've already backed up, and it anyway should not be affected by this step.

Next, download the correct architecture & locale tarball of the latest Thunderbird 38 release for your system from [here]("https://ftp.mozilla.org/pub/thunderbird/releases/38.8.0/").  Extract it to your home directory (so you'd have it installed in /home/user/thunderbird directory).  Don't run it just yet because automatic updates will cause it to just get upgraded again - first, in your profile folder (see link above), create a file called "user.js" (if it doesn't exist yet) and add these lines to it:
```
user_pref("app.update.auto", false);
user_pref("app.update.enabled", false);
user_pref("app.update.silent", false);
```

Now just double-click the thunderbird binary [FONT=Courier New]/home/user/thunderbird/thunderbird[/FONT] and fix up any settings etc the upgrade might have corrupted.

Does this help?

---

### Post by bonzo2 on 2016-07-20
halogen2,

Yes, your instructions help immensely. I wanted to acknowledge your post immediately and let you know that I may not be able to try the commands while at work, but I will do it ASAP. Thanks for hanging with me on this. I am very grateful.

Bonzo

---

### Post by bonzo2 on 2016-07-20
halogen2,

One more thing. Would you know the proper setting to prevent Ubuntu from automatically updating Thunderbird again?  I was just thinking that once I apply your fix, I don't want it to re-updated before I have an opportunity to disable that function!

Thanks,
Bonzo

---

### Post by bonzo2 on 2016-07-20
Hi giford,

Just wanted to thank you for helping troubleshoot my issue. Much appreciated!

Bonzo

> **gifford said:**
> The only way I know to get an earlier version is either through Mozilla or through one of the Thunderbird Ubuntu PPA's. Good luck. I did find version 3.1.4 of SoGo on their site. It was released July 12, 2016. It may be the fix for your problem.

---

### Post by &amp;KyT$0P# on 2016-07-20
> **bonzo2 said:**
> Would you know the proper setting to prevent Ubuntu from automatically updating Thunderbird again?
Following my instructions of downgrading, "Ubuntu" won't be able to update Thunderbird neither automatically nor otherwise, because Thunderbird will no longer registered with the package management system.

However, Thunderbird will now be capable of updating itself.  But the user.js step disables that before it even gets a chance to happen.

---

### Post by bonzo2 on 2016-07-20
halogen,

I have begun the process of downgrading. I have questions (A - E) in bold below.:confused:


[LIST=1]
[*]Back up Thunderbird profile 
[*]Extract Thunderbird tarball to home directory (so you'd have it installed in  /home/user/thunderbird directory)
[LIST]
[*]**QUESTION A**. My directory appears not to have a "user" file. Thunderbird is extracted directly inside my "home" folder. Is this OK? 
[/LIST]
  
[*]  Create e a file called user.js. Add "lines" user_pref("app.update.auto", false); user_pref("app.update.enabled", false); user_pref("app.update.silent",
false
[LIST]
[*]**QUESTION B:** Do I create the file/lines in both the original and backup Thunderbird profiles? 
[*]**QUESTION C**: Do I add the lines to the folder by simply adding the lines to a text document inside the folder? 
[*]**QUESTION D**: what should I name the text document? 
[/LIST]
  
[*]Double-click the Thunderbird binary [FONT=Courier New]/home/user/thunderbird/thunderbird[/FONT] and fix up any settings etc the upgrade might have corrupted.
[LIST]
[*]**QUESTION E**: Should I run the program only after fixing the settings or before? 
[/LIST]
     
[/LIST]

Thanks immensely!
Bonzo

---

### Post by gifford on 2016-07-20
From what I read on the changeLog for SoGo 3.1.4, the latest version of Thunderbird and Lightning is supported: [https://github.com/inverse-inc/sogo/commits/SOGo-3.1.4](https://github.com/inverse-inc/sogo/commits/SOGo-3.1.4)
Read the commits from June 28, 2015 for removing unsupported Thunderbird versions from docs. It tells you SoGo 3.1.4 will work with Thunderbird 45.2.0 and Lightning 4.7.2.
Good luck with your efforts.

---

### Post by &amp;KyT$0P# on 2016-07-21
> **bonzo2 said:**
> **QUESTION A**. My directory appears not to have a "user" file. Thunderbird is extracted directly inside my "home" folder. Is this OK? 
Right, your user account is not necessarily called "user" :P
Yes this sounds like you did it right.

> **QUESTION B:** Do I create the file/lines in both the original and backup Thunderbird profiles?
It only needs to be done in the working copy / original.  I guess it doesn't matter whether you do it on the backup.

> **QUESTION C:** Do I add the lines to the folder by simply adding the lines to a text document inside the folder?
Yes provided you name that text document [FONT=Courier New]user.js[/FONT]

> **QUESTION E:** Should I run the program only after fixing the settings or before?
**Only after.**


EDIT
Wait, you don't mention uninstalling the Ubuntu package manager Thunderbird?  Skipping that step is a guaranteed way to get your profile corrupted...

---

### Post by bonzo2 on 2016-07-21
gifford,

Thank you for pointing out the updated compatibility information. I wouldn't have known to check changeLog.com and I thank you for looking into it on my behalf. I went to SoGo's download page and it looked as if only older versions of Thunderbird and Lightning were compatible with SoGo. 

I started halogen's recommendations in this thread yesterday, and I'm going to try to stabilize my system today by executing the steps he laid out.

Once I stabilize my system, I would like to try updating everything. If I'm understanding what halogen has explained, my system will no longer automatically update Thunderbird, which I will always prefer because Thunderbird, Lightning, and SoGo rarely update concurrently. 

Thanks again!
Bonzo



his instruction > **gifford said:**
> From what I read on the changeLog for SoGo 3.1.4, the latest version of Thunderbird and Lightning is supported: [https://github.com/inverse-inc/sogo/commits/SOGo-3.1.4](https://github.com/inverse-inc/sogo/commits/SOGo-3.1.4)
Read the commits from June 28, 2015 for removing unsupported Thunderbird versions from docs. It tells you SoGo 3.1.4 will work with Thunderbird 45.2.0 and Lightning 4.7.2.
Good luck with your efforts.

---

### Post by bonzo2 on 2016-07-21
halogen2,

Yes, I ran the command as quoted below. Thanks for asking. I'm trying to finish this now. The help on this board is outstanding.

```
 sudo apt-get purge thunderbird*
```

Thanks,
Bonzo


> **halogen2 said:**
> 

EDIT
Wait, you don't mention uninstalling the Ubuntu package manager Thunderbird?  Skipping that step is a guaranteed way to get your profile corrupted...

---

### Post by &amp;KyT$0P# on 2016-07-21
> **bonzo2 said:**
> If I'm understanding what halogen has explained, my system will no longer automatically update Thunderbird, which I will always prefer because Thunderbird, Lightning, and SoGo rarely update concurrently. 
Correct.  You can still manually update Thunderbird, here's how to do it:
1) download latest release from Mozilla :arrow: [https://www.mozilla.org/thunderbird/all/]("https://www.mozilla.org/thunderbird/all/")
2) completely quit Thunderbird (if it's running)
3) back up your profile folder
4) delete /home/user/thunderbird directory
5) extract the new Thunderbird tarball to /home/user (same as before)
6) run the new thunderbird executable [FONT=Courier New]/home/user/thunderbird/thunderbird[/FONT]

And that's it, Thunderbird is updated.  Pretty easy isn't it? :)

---

### Post by bonzo2 on 2016-07-21
halogen2,

Well, this is all MUCH easier with the support I get here! You guys are great. I managed to mess up somewhere along the way. I appear to have compatible versions of Thunderbird and Lightning installed, and they are suddenly very fast. The code you had me run must've helped, yes?

Here is my current set up:
[LIST]
[*]Thunderbird 45.2.0 (but the newly downloaded tarball in home directory is 38.8.0, which is what I was trying to revert to.) 
[*]Lightning 4.7.0 
[*]SoGo 31.0.1 (still not working) 
[/LIST]

If you all aren't bored of helping me, I could surely use more help. I'm wondering if I should just be brave and try to install SoGo 3.1.4, as described by gifford. I don't know how to do it. But theoretically, SoGo 3.1.4 should work with the installed Thunderbird/Lightning combo.

Thanks,
Bonzo



> **halogen2 said:**
> Correct.  You can still manually update Thunderbird, here's how to do it:
1) download latest release from Mozilla :arrow: [https://www.mozilla.org/thunderbird/all/](https://www.mozilla.org/thunderbird/all/)
2) completely quit Thunderbird (if it's running)
3) back up your profile folder
4) delete /home/user/thunderbird directory
5) extract the new Thunderbird tarball to /home/user (same as before)
6) run the new thunderbird executable [FONT=Courier New]/home/user/thunderbird/thunderbird[/FONT]

And that's it, Thunderbird is updated.  Pretty easy isn't it? :)

---

### Post by &amp;KyT$0P# on 2016-07-21
:confused: Wait, where did you get Thunderbird 45.2.0 and how are you running Thunderbird?

What happened appears to be that, while trying to downgrade Thunderbird, you've somehow ended up running Thunderbird 45.2.0 and the compatible Lightning version, and SoGo is still out of commission.

Did something go wrong with making the [user.js file]("http://kb.mozillazine.org/User.js_file"), or did you download also the 45.2.0 tarball and get it mixed up when extracting?
Please double-check the Thunderbird update settings in Edit > Preferences > Advanced > Update, make sure that both automatic updates and automatic checking for updates are disabled/un-checked

[HR][/HR]

> **bonzo2 said:**
> I'm wondering if I should just be brave and try to install SoGo 3.1.4, as described by gifford. I don't know how to do it. But theoretically, SoGo 3.1.4 should work with the installed Thunderbird/Lightning combo.
According to the download site, SoGo 3.1.4 is a back-end server, and SoGo Connector 31.0.3 is the latest front-end but only compatible with Thunderbird 38... and furthermore, I don't seem to obviously find a Thunderbird 38/45 compatible SoGo Connector on their Github site.  So, at the very least, I'd say don't try to upgrade anything until you have it fully stable first... then, and only then, maybe you can see if they've got a working SoGo Connector for Thunderbird 45 [in development stage]("https://github.com/inverse-inc/sogo-connector.tb31")...

---

### Post by bonzo2 on 2016-07-21
halogen2:

I don't know what the heck I did. :confused: I'm sure it was me, not your instructions, which were clear. 

I've pasted the lines directly from my new user.js file below. are they OK?
[INDENT]```
user_pref("app.update.auto", false);
user_pref("app.update.enabled", false);
user_pref("app.update.silent", false);
```
[/INDENT]


Are these the relevant Thunderbird settings. Should they be set to true or false??[INDENT]app.auto.update = true
app.update.cert.checkAttributes;true
[/INDENT]

What do you think about my attempting to install the latest SoGo compatible version now?

Thanks,
Bonzo





> **halogen2 said:**
> :confused: Wait, where did you get Thunderbird 45.2.0 and how are you running Thunderbird?

What happened appears to be that, while trying to downgrade Thunderbird, you've somehow ended up running Thunderbird 45.2.0 and the compatible Lightning version, and SoGo is still out of commission.

Did something go wrong with making the [user.js file]("http://kb.mozillazine.org/User.js_file"), or did you download also the 45.2.0 tarball and get it mixed up when extracting?
Please double-check the Thunderbird update settings in Edit > Preferences > Advanced > Update, make sure that both automatic updates and automatic checking for updates are disabled/un-checked

---

### Post by &amp;KyT$0P# on 2016-07-21
Yes, you did it right, and it should be setting these:

[INDENT]app.update.auto = false
app.update.enabled = false
app.update.silent = false[/INDENT]

Leave app.update.cert.checkAttributes at its default value, that's about security of update system, not whether automatic updating is enabled or not.

> What do you think about my attempting to install the latest SoGo compatible version now?
Sorry, I was editing while you were posting :oops:

---

### Post by bonzo2 on 2016-07-21
halogen2:

It looks like "app.update.silent" was the only one of the three settings that was correctly set to "false."  I changed the other two so that they now all say "false." What next? 

Bonzo


> **halogen2 said:**
> Yes, you did it right, and it should be setting these:
[INDENT]app.update.auto = false
app.update.enabled = false
app.update.silent = false[/INDENT]

Leave app.update.cert.checkAttributes at its default value, that's about security of update system, not whether automatic updating is enabled or not.


Sorry, I was editing while you were posting :oops:

---

### Post by &amp;KyT$0P# on 2016-07-21
So, Thunderbird ignored your user.js and auto-updated itself to 45.2.0.  Now it won't do that again.  but you'll have to try the downgrade again from scratch :(

(This is why I suggested backing up the profile folder - you might need to restore the profile from your backup in order to get the downgrade to work...)

---

### Post by bonzo2 on 2016-07-21
halogen2,

Thanks for replying. I'm going to try to redo this myself and hope that my next update to the thread will be good news. I appreciate the time and patience expended to help those of us who are still learning. Thanks to this forum, I've never once had to use MS Windows after breaking up with that OS. Outstanding, IMO.

Bonzo :-)

> **halogen2 said:**
> So, Thunderbird ignored your user.js and auto-updated itself to 45.2.0.  Now it won't do that again.  but you'll have to try the downgrade again from scratch :(

(This is why I suggested backing up the profile folder - you might need to restore the profile from your backup in order to get the downgrade to work...)

---

### Post by &amp;KyT$0P# on 2016-07-21
Oh, one more thing - if you do restore the backup from your profile, this time instead of adding those lines to user.js, add them in alphabetical order in [prefs.js]("http://kb.mozillazine.org/Prefs.js_file") (which is an already existing file)

---

### Post by bonzo2 on 2016-07-21
halogen2,

Do you mean to alphabetize the following lines? If so, I think they're already alphabetized, as they appear just like this. 


```
app.update.auto = false
app.update.enabled = false
app.update.silent = false
```

Bonzo


> **halogen2 said:**
> Oh, one more thing - if you do restore the backup from your profile, this time instead of adding those lines to user.js, add them in alphabetical order in [prefs.js]("http://kb.mozillazine.org/Prefs.js_file") (which is an already existing file)

---

### Post by &amp;KyT$0P# on 2016-07-21
The prefs.js file will already be full of other preference lines, listed in alphabetical order.  I mean insert these lines in alphabetical order in prefs.js, so that prefs.js is still alphabetised:
```
user_pref("app.update.auto", false);
user_pref("app.update.enabled", false);
user_pref("app.update.silent", false);
```

---

