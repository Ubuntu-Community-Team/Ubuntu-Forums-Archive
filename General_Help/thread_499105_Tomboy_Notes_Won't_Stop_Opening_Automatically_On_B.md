---
title: "Tomboy Notes Won't Stop Opening Automatically On Boot"
date: 2007-07-12
forum: General Help
---

### Post by tedrogers on 2007-07-12
Bit of a funny one this...I initially wanted to have Tomboy Notes open when I logged into Ubuntu 7.10, so I added it to the Sessions preference.

Then I decided I didn't want it anymore, so deleted the entry from Sessions and yet it still appears every time I log in?!

I've done some digging around and tried deleting the .nautilus and .metacity/Sessions folders, but this didn't do the trick. These folders were just recreated next time I booted anyway and don't seem to be linked to this problem.

I've uninstalled and reinstalled Tomboy, but the problem is still there when I reinstall it.

How can I stop this?

Thanks.

---

### Post by strabes on 2007-07-12
maybe the preference is stored within the tomboy configuration folder in your home directory instead of in the gnome directory? Try ```
sudo aptitude purge tomboy
```

---

### Post by tedrogers on 2007-07-12
> **strabes said:**
> maybe the preference is stored within the tomboy configuration folder in your home directory instead of in the gnome directory? Try ```
sudo aptitude purge tomboy
```

Hi there and thanks for the reply.

How is...

```
sudo aptitude purge tomboy
```

...different from...

```
sudo apt-get remove tomboy --purge
```
```
sudo apt-get install tomboy
```

...which is what I did when I uninstalled and reinstalled Tomboy previously?

I also did this just in case...

```
sudo apt-get autoremove
```

I tried your method and at first it worked for a couple of reboots...but on reboot 4 or 5 it has started to reappear by itslef in the notification area.

So once again I am stumped.

I also tried deleting the /home/.metacity folder and this caused some bizarre activity, including the following so far:-

1. The device loadup screen not disappearing until I clicked on it.
3. Seemingly inoperable shutdown button, altough actually it just takes about 2 minutes since when you click it for the shutdown dialogue to appear.

Perhaps I shoudln't have deleted the .metacity folder, but it does appear to be rebuilding itself the more I use the OS.

Any ideas on this bizarreness, and I still need to stop Tomboy loading automatically.

Thanks.

---

### Post by A. J. Rimmer on 2007-07-28
I upgraded one laptop from Dapper to Edgy to Feisty and did not incur the problem, but upgraded my HP dv5000 the same way and encountered the exact same behavior with Tomboy.  I could get it to stop appearing on boot for a while, but then it would come back.  Also, if I restarted X with control-alt-backspace, then the shutdown button would stop working.

For now I have uninstalled Tomboy and everything else seems normal, but I would really like to get it working again.  I think I tried essentially everything you did, without success.

-- "Smoke me a kipper, Skipper, I'll be back for breakfast." -- "Ace" Rimmer

---

### Post by fragos on 2007-07-28
You might also want to check System-> Preferences-> Sessions-> "SessionOptions tab".  If "Automatically save changes to session" is checked, anything left running down shutdown will be restarted with the next boot.

---

### Post by A. J. Rimmer on 2007-07-29
A couple of additional things I should have mentioned:

1. If I deleted Tomboy from Sessions, it would just come back on the next startup.  In fact, I never added it in the first place, it just appeared there on its own.  I uninstalled and reinstalled and it again reappeared in sessions.

2. After uninstalling Tomboy again, the problem with the shutdown button stopped happening.  A few other weird instabilities also seemed to go away, but this is just a subjective observation, nothing I can really quantify.

3. Thanks, George, for the info; I don't have Automatically Save checked.  However, I was not aware of its function either, glad to learn what it is for.

Otherwise, Feisty has fixed a number of shortcomings with Dapper on my HP (including sound volume, built-in card reader, video quality, etc.).  So far, I am very happy with it.

---

### Post by tedrogers on 2007-07-29
Ditto....what Rimmer said! :)

I've pretty much given up completely with TomBoy on this IBM T22.

Can't say I've noticed it misbehaving on other systems, which seems to concur with Rimmer's experiences.

Interestingly, I found that Sticky Notes also opened up all sticky post-its on the desktop at logon.

I don't know if this is a feature and/or bug / related to tomboy, it was really annoying so I got rid of that too.

Now I use gedit to keep and on going TO DO list....simple solution, albeit clumsy.

Shame really, I liked tomboy a lot.

---

### Post by fragos on 2007-07-29
I use Tomboy without problems so I took a clooser look at sessions.  I've determined that the sessions applet doesn't start Tomboy but reports it as running.  This would imply it is initiated by a startup script not under the control of the sessions applet although any process can be terminated with the applet.  If you right click the Tomboy icon you can set its preferences which include plugins.  The only appearance of Tomboy on my system is in the applet bar.

---

### Post by tedrogers on 2007-07-29
Forgive my ignorance, but I don't understand your point.

I don't know whether you are simply offering more information here or a potential solution. Do we need to do anything with the plug-ins options?

In any case, having just reinstalled it and simply put 'tomboy' in the sessions, it seems to be behaving itself. It may, however, start acting up in a day or two but we shall see and hope for the best.

Thanks.

---

### Post by fragos on 2007-07-29
I was providing more information.  There is one plugin on my system for reading sticky notes which may have caused problems if it tried to emulate the sticky notes operation.  I'm just suggesting where to look.

---

### Post by A. J. Rimmer on 2007-07-29
"Now I use gedit to keep and on going TO DO list....simple solution, albeit clumsy."

Similar solution here, except that I use Abiword, and put all of my short notes in a /home/notes folder.  I really wasn't using all of the features of Tomboy anyway, and Abiword loads and opens pretty quickly.  Still would like to get Tomboy working, though; can't stand not being able to fix something, and it seems like a very useful application.

-- "Smoke me a kipper, Skipper, I'll be back for breakfast." -- "Ace" Rimmer

---

### Post by tedrogers on 2007-07-29
This is what I did to get it working:

1. Delete the .tomboy folder within /home and empty trash, or make sure it's not present. Also run a 'sudo apt-get remove tomboy --purge' first of all to make sure it's all removed properly. Can't hurt to do a 'sudo apt-get autoremove' as well at this point.

2. Maybe do a restart, why not, and then reinstall tomboy.

3. Once installed, add the phrase 'tomboy' within sessions so it loads at startup. Make sure it's not 'tomboy --search' or you end up with the search box at startup.

That's it.

It all seems to be working right now and I'm pleased but I'm not sure why. Maybe a recent update fixed it on my system...but like I said it could all go wrong at anytime I suppose!

---

### Post by A. J. Rimmer on 2007-07-30
Well, _THAT_ didn't work ... but I did figure out something that appears to have worked for me.  Hope I can remember it all:

Every time I went into the Sessions / Current Session tab and deleted both Tomboy entries, they would just come back.  Now, in the Startup Programs tab there was an entry called "no name" or something like that, but the listed command for that item was "tomboy".  I had unchecked this item initially (which made no change to the problem behavior), and then later deleted it entirely (which, again, made no change in behavior).

As recommended in the above post, I deleted .tomboy and then reinstalled.  Rebooted and was greeted with the darn Tomboy search window.  Drat!  Tried deleting Tomboy from the Current Session tab, and back it came.  Also again had the problem that if I restarted X with ctrl-alt-backspace, the shutdown button would not respond, and had to use "sudo halt" in a terminal window.

Something prompted me to try adding Tomboy back in the startup programs list and then unchecking it.  (Obviously something went awry somewhere when it got installed as "no name".) I did this, and suddenly the shutdown panel popped open (I had clicked the button a couple of times without result after logging back in).

"Aha!" I sez!  I did a reboot and the system came back up WITHOUT Tomboy on the screen.

Hope I got all the details down correctly, and hope this helps.

:biggrin:

---

### Post by tedrogers on 2007-07-31
Well mine was working for a day or two, but now when I login the tomboy search windown just appears again as usual.

However, it is slightly better than it was (even when it was at its worst), because now at least it doesn't open all the notes too!

I think I'll just have to live with this minor annoyance.

Rimmer - I used to have that problem with the shutdown button being unresponsive. When it pops open like that for no apparent reason it is actually a delayed response to a previously detected click, i.e. when you initially click on it and nothing happens. It kind of times out and later on pops open at a suitably inconvenient time. If you're a bit click happy like me then it is sometimes very easy to click reboot or shutdown when this dialogue appears...which is even more annoying.

Incidentally, is your .tomboy/plugins folder empty or does it have some entries in there. Mine is empty even though I have certain plugins enabled, like the Fixed Width and Evolution email drop one, The Evolution one doesn't work anyway, but this might be because plugins are missing. Is yours like this at all?

Thanks.

---

### Post by fragos on 2007-07-31
My Tomboy plugins folder has a folder named "Default Plugins" which contains the plugins shown in Preferences.

---

### Post by A. J. Rimmer on 2007-07-31
tedrogers --

When I upgraded from Dapper through Edgy to Feisty, I found that I had several files in the plugins folder.  After going through the various steps as discussed above it is now empty.  The only plugin I have tested is the print plugin and it works, at least in the print to PDF mode.  Haven't tried it with my hardware printer yet.  (I use this laptop around the house, at the library, coffee shop, etc., so it is seldom connected to anything except the charger.)

-- "Smoke me a kipper, Skipper, I'll be back for breakfast."  --  "Ace" Rimmer

---

### Post by tedrogers on 2007-08-01
Rimmer - my print to PDF plugin works too.

Another weird thing with tomboy is that today when I booted up the 'search notes' box didn't appear. This all seems rather flaky. Why would open the search notes box somedays and not others?

---

### Post by A. J. Rimmer on 2007-08-01
Well, so far no further problems with Tomboy here.  I wonder if these things don't come up during the upgrade process.  I'm seriously considering for the next stable release to just do a complete fresh install!

---

### Post by tedrogers on 2007-08-01
I don't think it makes ANY difference to do a fresh install.

I always keep a fresh install 'image' of my drive. I make it when I've got it just how I like it.

I went back to this version some time ago and surely enough I wound up experiencing the same tomboy problems as I do now (except all the notes opening at startup - fingers crossed).

Maybe, inadvertently, I precislely retraced my own footsteps to reproduce the problem, which isn't totally out of the question as we are all creatures of habit!! But I suspect it is just some weird thing with this old clanger of laptop, because it didn't happen on my desktop system, although I don't have Feisty installed on there anymore as I'm gowing to really like Fedora Core 7 on that particular machine.

---

### Post by a30d on 2008-05-30
Here are the steps I took to fix this problem.

1. Quit tomboy.
2. Open System -> Preferences -> Session
... Under "Startup Programs" make sure there is only one Tomboy entry and that the command used is just "tomboy".
... Under "Current Session" remove all instances which mention "tomboy" in any form. Press Apply.
... Under "Session Options" un-check "Automatically remember running applications when logging out". Click "Remember Currently Running Applications" button.
... Click on Close
3. Right-click on Applications menu and choose "Edit Menus"
... Go to Accessories
... Right-click on Tomboy Notes and select Properties
... Make sure Command only has "tomboy"
... Press Close and close out of Main Menu window
4. Log off and log back in.

Hope this works for all those still curious!

---

### Post by brazilla ray on 2008-06-13
The fix that eventually worked for me is mentioned [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5129699&postcount=3"), and the link in that post goes [[COLOR="Blue"]_here_[/COLOR]]("https://bugs.launchpad.net/gnome-session/+bug/34321"):
basically, delete ~/.gnome2/session, and log out/in.

---

