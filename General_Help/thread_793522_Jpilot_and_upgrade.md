---
title: "Jpilot and upgrade"
date: 2008-05-13
forum: General Help
---

### Post by gakna on 2008-05-13
Hi, i am a newbie and i am thinking about changing gutsy gibbon for hardy heron. Besides some resolution problems (which i asked in another question ) i would like to know what would happen to my Jpilot if i upgrade. Will it still work after the upgrade? or  should i do a clean install?
I don´t know if my question is clear or relevant but thanks anyway :)

---

### Post by Bruce M. on 2008-05-16
Hi gakna,

I just upgraded (fresh install) to 8.04 yesterday and loaded jPilot today.

It works fine, however needs some help that you can find here:

[PalmDeviceSetup]("https://help.ubuntu.com/community/PalmDeviceSetup")

After doing what it said I still had problems. But further down in "Notes from Other Users" I found my solution:

>     * I used these directions and they worked great. but after upgrading to gusty I had problems again. I seems that in gusty there is a udev rule already set up for palm devices that conflicted with this rule above. in the file "60-symlinks.rules" I commented out the rule that was for palm devices and my treo 650 syncs again like before. With the 2 rules together I was getting /dev/pilot becoming symlink to IT'S SELF. if you see some thing like this:

ls -l /dev/pilot lrwxrwxrwx 1 root root 5 2008-01-21 00:10 /dev/pilot -> pilot you might have a similar problem.

Hope this helps.
Bruce

---

### Post by gakna on 2008-05-17
Thanks vary much for your answer Bruce!!
One question though...what would happen with my JPilot configuration and information if i upgrade from Gutsy (i.e., using the upgrade manager application) instead of doing a clean install?? (which i am tempted to try because Gutsy has everything configured the way i like it right now). I mean, JPilot is working properly in Gutsy right now, will it still be functional upgrading from within Gutsy?
I am asking because i read somewhere that upgrading from within the system can have some issues especially if you added software (and JPilot is not the pre-installed Palm application)
Thanks again!!!

---

### Post by Bruce M. on 2008-05-17
> **gakna said:**
> Thanks vary much for your answer Bruce!!
One question though...what would happen with my JPilot configuration and information if i upgrade from Gutsy (i.e., using the upgrade manager application) instead of doing a clean install?? (which i am tempted to try because Gutsy has everything configured the way i like it right now). I mean, JPilot is working properly in Gutsy right now, will it still be functional upgrading from within Gutsy?
I am asking because i read somewhere that upgrading from within the system can have some issues especially if you added software (and JPilot is not the pre-installed Palm application)
Thanks again!!!

I tried to "upgrade" with the "Update Manager" twice and it failed.
Personally I would do a "backup" of your system, before you try that. See "QuickStart" in my signature, it was created for Ubuntu GNOME, and works GREAT!

**Also to note:** During the "Update" process you'll have to pay attentions because the process will stop on occasion and ask you if you want to "overwrite" certain files that you may have edited in 7.10. The "bashrc" file comes to mind, as I have added aliases etc, so I said "No" to keep my existing file.

Now if you want to try an "Upgrade" feel free, you may have more luck then I did. If it works you'll be happy, if it doesn't at least you'll have the backups and won't be a sad if you didn't have them.

If the upgrade fails, you have two options:

[LIST=1]
[*]Do a **Clean Install of 7.10** and before allowing 7.10 to get all the upgrades, you restore your backups using QS.
[*]Do a **Clean Install of Ubuntu 8.04**. It will mean re-installing your favorite programs again but you will have two or three very important files hidden files ( the . means hidden) in your backup of your home directory:
[LIST]
[*].mozilla
[*].moxilla-thunderbird (If you use that for email); and
[*].jpilot
[/LIST]
[/LIST]

If you restore just those three hidden files **"before"** you use any of these programs you will have:

.moxilla = all your Firefox bookmarks
.moxilla-thunderbird = all your email
.jpilot = all your jpilot information (Calendar or Datebk6 (commercial), Contacts, Memos and ToDos, complete with the installed programs.

Now you download and install jpilot, the first time you run it you should see that things are normal **IF** you set it to use the same Palm Hotsync name, **it's very important to do that**.  I made a mistake this time around and allowed it to set itself up as per my Ubuntu Login name so I'm in the process of asking for new passwords for programs I paid for on my Palm as a result.  :)

Now even though you see everything is normal above, in order to HotSync jPilot you'll still have to follow the instructions above to get it working properly. I've had to do it since version 6.06.

Hope this helps.
I'll be here is you need more help.
Bruce

---

### Post by gakna on 2008-05-17
Thanks Bruce! you are really helpful, i understood everything! i´ll let you know how i did once i do everything.

One last thing, and I hope i am not being too demanding :), but i have another problem so i opened another thread a few days ago but nobody gave me a solution nor a real answer yet. So i´ll leave you the thread and if you have some time and think of something please post an answer there. Lots of thanks in advance!!!

[http://ubuntuforums.org/showthread.php?t=791844](http://ubuntuforums.org/showthread.php?t=791844)

---

### Post by Bruce M. on 2008-05-17
> **gakna said:**
> Thanks Bruce! you are really helpful, i understood everything! i´ll let you know how i did once i do everything.

One last thing, and I hope i am not being too demanding :), but i have another problem so i opened another thread a few days ago but nobody gave me a solution nor a real answer yet. So i´ll leave you the thread and if you have some time and think of something please post an answer there. Lots of thanks in advance!!!

[http://ubuntuforums.org/showthread.php?t=791844](http://ubuntuforums.org/showthread.php?t=791844)

I saw that before when there were no responses and I'm afraid I have no answer other then the very first thing that came to mind.

You mentioned AMD64. Are you using the Live CD for 64?  If so try the Live CD for the 32 version.  :)

Even if you get the 64 version running you will have to install some extra files for your system as some files are for the 32 version and wont run properly on the 64 version. (Read that somewhere)

---

