---
title: "Firefox opens full screen every time?"
date: 2008-06-21
forum: General Help
---

### Post by mrbaz on 2008-06-21
For some reason.  Firefox will open in full screen mode almost every time.  I have to hit F11 to switch it back to normal viewing mode.
Even after I do this and close FF, it will open again in Full Screen mode.

Any suggestions?

---

### Post by OutOfReach on 2008-06-21
I had this problem just yesterday, it was quite annoying so I went to Synaptic, searched firefox-3.0 and clicked the box next to it and selected Mark for ReInstallation  and Applied. And everything seems to be working A-OK. Hope that helped ;)

---

### Post by TwistableLime on 2008-08-21
Same thing keeps happening to me and it is quite annoying! Marking for reinstallation did NOT fix the issue.

---

### Post by kingbilly on 2008-08-30
I have the same problem,
using ubuntu 8.10

---

### Post by hakimaki on 2008-08-30
Press F11 to toggle fullscreen on/off

---

### Post by retrovertigo on 2008-08-30
> **hakimaki said:**
> Press F11 to toggle fullscreen on/off

If you read the original post closer, it's clear he/she knows this.

I checked about:config and there doesn't appear to be a setting that tells it to start with fullscreen on or off.  All the google searches I've run describe add-ons that let you tell firefox to start fullscreen.  one of them is called "autohide".  However, nothing to tell it NOT to start fullscreen.

---

### Post by tuberculo on 2008-08-30
I had a similar problem with Thunderbird. I deleted some files in the profile to fix the problem. I do not remember which ones.
Try to start firefox with a new profile to see if the problem persists.

---

### Post by AndersonCouncil on 2008-09-23
Reinstalling worked for me - not exactly ideal, but will have to suffice.

---

### Post by ryu kun on 2008-11-01
I have the same problem in Ubuntu 8.10.

---

### Post by Merovius on 2008-11-01
Same here. A few times yesterday it would open up and be behind the panels because it was so big. :confused:

---

### Post by gjoellee on 2008-11-01
Hi people, this is an issue with GDM I believe, this problem does appear in Kubuntu (which uses KDM). I have recorded many issues with GDM lately, but seams to work fine in KDM.

---

### Post by phorgan1 on 2008-11-02
I wonder if this isn't related to other problems I've had with 8.10.  The general category is forgetting.  My session is forgotten, Firefox forgets that it's not fullscreen, and for me, firefox tells me of the same add-ons being added every time.  Maybe the gdm database is broken in 8.10?

Patrick

---

### Post by ryu kun on 2008-11-02
My problem has been solved somehow. I don't know how but Firefox doesn't open in fullscreen now.

Edit: No, sorry, problem is still there. Not only in the beginning, it can strangely switch to full screen mode while I am using it.

---

### Post by Merovius on 2008-11-03
Mine is doing it more then ever. It's really p'ing me off. Had the same thing on and off in Hardy. Would come and go. A few days it would do it. Then for a week or two it would be fine.

Err..

---

### Post by ozono on 2008-11-04
Hi there,

This is happening to me also. I think this could be a problem related to 8.10

BTW, I have solved this problem by doing this:

- I went to /home/<myuser>/.mozilla
- I deleted the whole "firefox" folder

I think this is a less complicated solution than the reinstalling one... but, it's up to you! ;)

The main problem I've got by doing this is that I've lost my firefox history, its main config and all the installed add-ons... but now firefox is  starting in a normal window mode again.

If you don't want to loose your add-ons (probably the most lazy thing to redo :p), I remember there is another add-on which allows you to make like an export for all your add-ons. Once the firefox is reset, you can restore them again from this add-on.

I can't remember how it's called... Should be easy to find...
I hope this helps.

Cheers!

---

### Post by ozono on 2008-11-04
Hi again!

After investigate deeper into this, I've found a better solution.

How to fix it:

1- close any firefox instance you have opened.
2- go to /home/<your_user>/.mozilla/firefox/ (type CTRL+H to see hidden files and folders, you all know... ;) ).
3- get into your "XXXX.default" directory.
4- search for a file called "localstore.rdf" and delete it.

The next time you open firefox, it will do in a normal window and also keeping your preferences, add-ons, etc.

Maybe someone else would like to investigate into that file to find out the problem. I prefer the easy way... jejeje

Regards.

---

### Post by dtgolder on 2008-11-04
> **ozono said:**
> Hi again!

After investigate deeper into this, I've found a better solution.

How to fix it:

1- close any firefox instance you have opened.
2- go to /home/<your_user>/.mozilla/firefox/ (type CTRL+H to see hidden files and folders, you all know... ;) ).
3- get into your "XXXX.default" directory.
4- search for a file called "localstore.rdf" and delete it.

The next time you open firefox, it will do in a normal window and also keeping your preferences, add-ons, etc.

Maybe someone else would like to investigate into that file to find out the problem. I prefer the easy way... jejeje

Regards.

This solution worked for me...very frustrating behavior.
Thanks!

---

### Post by eekfonky on 2008-11-06
Same here in Ubuntu 8.10. I'd rather not have to hit F11 ever time I open it. Any fixes?

---

### Post by sirebral on 2008-11-06
Thanks ozono.  I thought I was going to post a fix, but it looks like your might be better.  I had renamed the profile.ini file and that seemed to work also.

---

### Post by ryu kun on 2008-11-10
> **ozono said:**
> Hi again!

After investigate deeper into this, I've found a better solution.

How to fix it:

1- close any firefox instance you have opened.
2- go to /home/<your_user>/.mozilla/firefox/ (type CTRL+H to see hidden files and folders, you all know... ;) ).
3- get into your "XXXX.default" directory.
4- search for a file called "localstore.rdf" and delete it.

The next time you open firefox, it will do in a normal window and also keeping your preferences, add-ons, etc.

Maybe someone else would like to investigate into that file to find out the problem. I prefer the easy way... jejeje

Regards.

This did not solve my problem. Firefox switches to full screen mode by itself. It is annoying. I am considering switching back to Ubuntu 8.04.

---

### Post by redilyn on 2008-11-10
I think this may help you.

[http://ubuntuforums.org/showthread.php?t=977386](http://ubuntuforums.org/showthread.php?t=977386)

"If this is the same problem I had it was caused by firefox being to large when in windowed mode.

here is how I fixed it:

1.) Unmaximize firefox.
2.) Resize the firefox window so that it fits inside the panels.
3.) Maximize firefox. It should now fit inside the panels.

Hopefully this helps

You may need to close firefox after step 2 so that it will save your windowed size."

---

### Post by ryu kun on 2008-11-11
Redilyn, this unfortunately did not help me either. Firefox still switches to full screen mode while its running. I haven't understood yet what triggers this behaviour.

---

### Post by fultaka on 2008-11-11
>   * Enter about:config in the location bar to access the advanced preferences.
    * Look for browser.fullscreen.autohide and double click it to set it to false.

Or you can just turn off the toolbars slide up animation:

    * Look for browser.fullscreen.animateUp, right-click, select Modify and enter 0.

I found the solution for my problem to this link  [http://mozillalinks.org/wp/2008/06/tweak-firefox-3-full-screen-mode/](http://mozillalinks.org/wp/2008/06/tweak-firefox-3-full-screen-mode/).

---

### Post by aaronmarsh632 on 2008-11-14
Hi, after searching everywhere I couldn't find a fix which worked for me. However I changed my Visual effects from 'Extra' to 'Normal' and it fixed the problem. system-prefs-appearance-visual effects.

Everything has been working fine since i installed 8.10 even with the extra effects enabled, it just started playing up today for the first time. No more shaky windows but at least my firefox is ok now.

EDIT: actually I just re-enabled the extras effects and its all working good now, weird...

---

### Post by Guilden_NL on 2008-11-23
> **ozono said:**
> Hi again!
How to fix it:

1- close any firefox instance you have opened.
2- go to /home/<your_user>/.mozilla/firefox/ (type CTRL+H to see hidden files and folders, you all know... ;) ).
3- get into your "XXXX.default" directory.
4- search for a file called "localstore.rdf" and delete it.

The next time you open firefox, it will do in a normal window and also keeping your preferences, add-ons, etc.


Worked perfectly for me.  Many thanks! My wife is a first time Linux user with a new HP HDX laptop and she was very unhappy about this.  I fixed it and now she's forgotten that she's in Ubuntu and not Windows.

---

### Post by dddw on 2009-01-01
>  Originally Posted by ozono  View Post
Hi again!
How to fix it:

1- close any firefox instance you have opened.
2- go to /home/<your_user>/.mozilla/firefox/ (type CTRL+H to see hidden files and folders, you all know... ).
3- get into your "XXXX.default" directory.
4- search for a file called "localstore.rdf" and delete it.

The next time you open firefox, it will do in a normal window and also keeping your preferences, add-ons, etc.

this worked for me, but has a equally annoying side-effect. FF now startsup normally, but now I have issues with the keyboard. I cannot use ctrl-c ctrl-p annymore, also i lost the ability to open a new tab with ctrl-t. Any ran into this problem? Or knows how to fix it?

Dennis

---

### Post by zika on 2009-01-01
> **dddw said:**
> this worked for me, but has a equally annoying side-effect. FF now startsup normally, but now I have issues with the keyboard. I cannot use ctrl-c ctrl-p annymore, also i lost the ability to open a new tab with ctrl-t. Any ran into this problem? Or knows how to fix it?

Dennis

I'm not sure but here is my shot in the dark. rename .mozilla directory and start firefox (this allowing firefox to regenerate everything, next time use that f11-f11-umaximize_re-size_window_strategy ....:)). if it doesn't work to Your satisfaction revert.

---

### Post by dddw on 2009-01-02
Thanks Zika, for your reply.
However I have found the culporate, it was a wrong shortcut key in Compiz fusion.
Which lead to the ctrl button beeing numb when pressed.
Sorry to have bothered you with this.:oops:

friendly greetings,

Dennis

---

### Post by zachbb on 2009-01-04
> **ozono said:**
> Hi again!

After investigate deeper into this, I've found a better solution.

How to fix it:

1- close any firefox instance you have opened.
2- go to /home/<your_user>/.mozilla/firefox/ (type CTRL+H to see hidden files and folders, you all know... ;) ).
3- get into your "XXXX.default" directory.
4- search for a file called "localstore.rdf" and delete it.

The next time you open firefox, it will do in a normal window and also keeping your preferences, add-ons, etc.

Maybe someone else would like to investigate into that file to find out the problem. I prefer the easy way... jejeje

Regards.

Thanks, this worked for me.

However, I'm assuming a bug report should be filed at Mozilla?

---

### Post by tegnoto89 on 2009-01-04
Here's what I did - worked great


Take a terminal and type:

```
firefox -safe-mode
```

When it starts up, check "reset toolbars and controls"

Hit save changes and restart.

---

### Post by amsin on 2009-01-31
Only thing I need to do is setting visual effects to "None". :popcorn:

> [https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/51103](https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/51103)

Rgds,

---

### Post by zika on 2009-01-31
did You try System->Preferences->CompizConfig_Settings_Manager->Utility->Workarounds->un_check_Legacy_Fulscreen_Support?

---

### Post by jawinterton on 2009-02-22
deleting the localstore.rdf worked for me.  Thank you so much!  That was very annoying.

---

### Post by mhmjr on 2009-02-25
> **zika said:**
> did You try System->Preferences->CompizConfig_Settings_Manager->Utility->Workarounds->un_check_Legacy_Fulscreen_Support?

Thanks Zika! This worked for me. I did not try the firefox specific solutions offered in this thread as this fullscreen problem was present in at least firefox and konsole. Other applications seemed to open properly. Once I did the above, firefox and konsole started to behave again.

--mhmjr

---

### Post by lkoniecki on 2009-03-16
> **redilyn said:**
> I think this may help you.

[http://ubuntuforums.org/showthread.php?t=977386](http://ubuntuforums.org/showthread.php?t=977386)

"If this is the same problem I had it was caused by firefox being to large when in windowed mode.

here is how I fixed it:

1.) Unmaximize firefox.
2.) Resize the firefox window so that it fits inside the panels.
3.) Maximize firefox. It should now fit inside the panels.

Hopefully this helps

You may need to close firefox after step 2 so that it will save your windowed size."

This worked for me.

I've also tried deleting localstore.rdf, changing "Unredirect Fullscreen Windows", setting "browser.fullscreen.autohide" but only closing firefox in window mode helped.

---

### Post by kaasmonster on 2009-04-19
> **ozono said:**
> Hi again!
How to fix it:

1- close any firefox instance you have opened.
2- go to /home/<your_user>/.mozilla/firefox/ (type CTRL+H to see hidden files and folders, you all know... ;) ).
3- get into your "XXXX.default" directory.
4- search for a file called "localstore.rdf" and delete it.

The next time you open firefox, it will do in a normal window and also keeping your preferences, add-ons, etc.

For all of you, who have still have this problem (it doesn't seem to be fixed yet, because for me it occurred just yesterday (8.10)).

I believe this is the probably is the best way to go with. But you have to make sure firefox isn't running, while deleting this file. Otherwise it won't work.

---

### Post by tuathan on 2009-06-05
this doesn't seem to have worked for me...
I deleted the file and restarted firefox but it
open in full-screen mode :(

---

### Post by good_times on 2009-06-12
Hi 

Don't know how to put the quote bit in as I've only just signed up today to say that the instructions from **ozono** worked perfectly! Thanks!!

Made sure that all Firefox bits were closed (took a screenshot so I could remember what I had to do!) and the next time I loaded it was fine. I've never had this problem before today and never with 8.04 (just gone up to 8.10).

Try it, worked for me, very annoying problem. Cheers bud!! :D

---

### Post by cyberritz on 2009-10-08
Hello ., 



I had the same issue ., Below solution worked fine for me 


Enter ***about:config*** in the location bar to access the advanced preferences.
Look for ***[I]browser.fullscreen.autohide*[/I]** and double click it to set it to ***false***.

Hope resolves your query

Thank you 
Sre

---

### Post by Pipps on 2009-11-27
I would very much like my Firefox to open **only** in full-screen mode.

Can the reverse of the advice on this thread be equally implemented?

How can this be done?

---

