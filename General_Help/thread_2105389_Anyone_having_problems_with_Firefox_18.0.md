---
title: "Anyone having problems with Firefox 18.0?"
date: 2013-01-15
forum: General Help
---

### Post by Bartender on 2013-01-15
We're running 12.04.  Update Mgr. updated Firefox a day or two ago.  It definitely is not working right.  Can't get onto bank site, online brokerage, etc.

Chrome lets me onto online brokerage, so it sure looks like a problem with FF 18.0.  

Anyone else having similar problems?  Can I drop back to FF 17.something?

EDIT: Left-clicking on the "hyperlink" button, or "bold" or "italics" or anything when posting on the Ubuntu Forums does nothing.  The hyperlink icon has worked for years.  Now it doesn't.  WTH

---

### Post by theurich on 2013-01-16
same problem here on 12.04 with latest updates. Tried a few things like disabling plugins and extensions, cleared cache, cookies etc., no success. Finally I used a new profile (firefox -P) and this circumvented the problem for me.

---

### Post by Bartender on 2013-01-16
Can you explain what you mean by a new profile?  I was hoping for a widespread problem that might get more attention from Mozilla and/or Ubuntu.

I fired up a PC running Lubuntu and FF 17.0.1 - Firefox behaving like it should on that rig.

---

### Post by c2tarun on 2013-01-16
> **Bartender said:**
> Can you explain what you mean by a new profile?  I was hoping for a widespread problem that might get more attention from Mozilla and/or Ubuntu.

I fired up a PC running Lubuntu and FF 17.0.1 - Firefox behaving like it should on that rig.

Try renaming ~/.mozilla folder

---

### Post by vasa1 on 2013-01-17
> **Bartender said:**
> Can you explain what you mean by a new profile?
Will this help?
[http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

---

### Post by Buntu Bunny on 2013-01-17
Check your extensions and add-ons. That's the source of most of my trouble.

---

### Post by vasa1 on 2013-01-17
[http://www.ghacks.net/2013/01/16/firefox-18-0-1-coming-soon/](http://www.ghacks.net/2013/01/16/firefox-18-0-1-coming-soon/)
> Mozilla is currently in the process of preparing Firefox 18.0.1 which will be released in the coming days if things go according to plan. So what is causing the rush to bring out version 18.0.1 only days after Firefox 18 has been released to the public?

---

### Post by Bartender on 2013-01-18
OK, thanks for the link, vasa1.

The article mentions one Linux bug, hopefully that's it.  Log-in buttons on most, if not all, websites don't work.  Especially anything that's "secure".  I just tried logging into WildBlue (satellite internet) with Firefox.  After entering username & password, I clicked on the Go button and nothing happened.  Went to Chrome, it all worked.

I get the impression this is not happening with everyone using Firefox and Linux?  Seems like there would be more posts on Ubuntu Forums if it was universal.

---

### Post by Martin E on 2013-01-21
> **vasa1 said:**
> [http://www.ghacks.net/2013/01/16/firefox-18-0-1-coming-soon/](http://www.ghacks.net/2013/01/16/firefox-18-0-1-coming-soon/)
I'm wondering when the official Ubuntu 12.04 package is going to be available?
I just ran UpdateManager, but it seems I'm still on 18.0 (gecko.buildID;20130107224849) while my Windows box updated last week.

---

### Post by puebloan on 2013-01-21
I had trouble with java when I updated.

---

### Post by Martin E on 2013-01-22
> **Martin E said:**
> I'm wondering when the official Ubuntu 12.04 package is going to be available?
I just ran UpdateManager, but it seems I'm still on 18.0 (gecko.buildID;20130107224849) while my Windows box updated last week.

Updated now

---

### Post by Bartender on 2013-01-23
Just ran Update Mgr. a few minutes ago.  A 20+ MB Firefox update was in the list.  Yay!

Closed Firefox, restarted, same problems.  Secure websites won't accept a username in the box, etc.

Chrome isn't bad, but I'm used to Firefox.  Have run into rendering problems with Chrome on a few MarketWatch websites.

Just checked - it's Firefox 18.0.1 now.  Waiting on 18.0.2, I guess...

---

### Post by Paddy Landau on 2013-01-23
I haven't had any problems at all with FF 18.

Disable all your extensions and recheck. If it works, re-enable the extensions one-by-one until you find the one that is causing the problem.

---

### Post by rpm13 on 2013-01-23
> **puebloan said:**
> I had trouble with java when I updated.

Me too. My banks login has stopped working.
Unfortunately java is working otherwise.
So now itw between the bank and firefox and java.

Guess I'll have to stay with windows for that

---

### Post by Bartender on 2013-01-25
OK, here's a quick test.

On the Ubuntu Forums, if I click on "Search" in Firefox (left-click or middle-click) I get the big Search window with all the options for advanced search, search by user, etc. This windows pretty much fills the screen.

If I click on Search in Chrome, I get the small drop-down that I used to get in FF.  As seen in attachment.

I'll disable all extensions and try again.

EDIT: Only have 4 add-ons.  Global Menu Bar integration (which was already disabled), Adblock PLus 2.2.1, Tab Utilities 1.5.1, and Ubuntu Firefox Modifications 2.6.  Without Tab Utilities, Firefox reacts to mouse clicks very stupidly.  It treats everything as a left-click.  It won't open in a new tab, etc.

With all disabled, no difference.  Clicking on "Search" at Ubuntu forums opens the full Search window instead of the small drop-down.

Paddy, I hope you'll forgive me for ill thoughts but I kinda wish yours was broke too so you could tell me what you did to fix it! ;)

---

### Post by Paddy Landau on 2013-01-25
> **Bartender said:**
> Paddy, I hope you'll forgive me for ill thoughts but I kinda wish yours was broke too so you could tell me what you did to fix it! ;)
LOL. Instead of wishing mine was broken, let's take advantage of the situation to try to find what is different. That, I hope, will help us find what is breaking yours.

[LIST=1]
[*]Enter the following two commands in a Terminal, and paste the results here.
```
echo ${DESKTOP_SESSION}
uname --all
lsb_release --all
```
[*]First, which version specifically of Firefox do you have? Menu > Help > About Firefox gives me 18.0.1.
[attach]230640[/attach]
Does yours read the same as mine?
[*]Start Firefox in Safe Mode. Close *all* instances of Firefox; then, from a Terminal, enter the following:```
firefox -safe-mode
```What happens then?
[/LIST]

---

### Post by Grinage on 2013-01-25
When I had this problem, I reset firefox disabling all the extensions, addons, etc, which actually helped solve numerous problems not just this one.  Once you do the reset you have to re-install your favorite add-ons and extensions, so it might help to make a list of the ones you want before you do this.


 Instructions on how to do this can be found here:

[http://browsers.about.com/od/firef2/ss/Reset-Firefox-Windows-Mac-Linux.htm](http://browsers.about.com/od/firef2/ss/Reset-Firefox-Windows-Mac-Linux.htm)

---

### Post by Grinage on 2013-01-25
After I read this forum I began having trouble with my Firefox installation.  If Reseting Firefox doesn't work, here is what I did to solve the problem.

Step 1:  export bookmarks--   **Bookmarks>  Show all Bookmarks> Import and Backup>** choose either html or choose Backup... to create a json file.

Step 2:  Export, print, or write down saved passwords and websites-- **  Edit>  Preferences > Security > Saved Passwords**

Step 3:  print or write down your add-ons and extensions --**  Help> Troubleshooting Information**

Step 4 :  purge firefox    --  **sudo apt-get remove firefox --purge**

Step 5:  delete .mozilla directory in your home folder if you use Thunderbird or Seamonkey you will remove only the .mozilla/Firefox folder --  **  sudo** *%filemanager *

Step 6 close your file manager

Step 7:  Reinstall firefox  --  [B]sudo apt-get install firefox
[/B]
Step 8:  Start Firefox re-download your add-ons and extensions  --  [B]Tools> Add-ons
[/B]
Step 9:  Import your Bookmarks if any  -- ** Bookmarks > Show All Bookmarks >  Import and Backup **

Step 10:  Reference your password list as needed to get firefox to save them

Enjoy your Firefox Experience.   Mozilla notes on their website that we should be cautious in the number of add-ons and extensions we have active, too many can cause glitches during upgrade or slow down our browsing experience.


%filemanager represents the file manager of your choice, ie.  dolphin, nautilus, thunar or whatever one your ubuntu flavor happens to use or is your favorite

.mozilla is a hidden file unless you have root permissions you won't be able to erase it or affect or do anything besides look at it.  Use sudo to open your file manager just for this task and then close your file manager root can do a lot of damage to your system

Alternatively, mozilla says we should be able to go to a terminal and type firefox-p to create a new profile without doing the above, but that didn't work for me, and neither did the reset firefox option.   If you are a thunderbird or sea monkey user, make sure you be careful to only remove the Firefox folder in .mozilla or you_ will lose everything!_

---

### Post by Bartender on 2013-01-25
Hi, Paddy - Results of the code you gave -

```
hammer@hammer-HP-Compaq-dc7800-Convertible-Minitower:~$ echo ${DESKTOP_SESSION}
ubuntu
hammer@hammer-HP-Compaq-dc7800-Convertible-Minitower:~$ uname --all
Linux hammer-HP-Compaq-dc7800-Convertible-Minitower 3.2.0-36-generic #57-Ubuntu SMP Tue Jan 8 21:44:52 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
hammer@hammer-HP-Compaq-dc7800-Convertible-Minitower:~$ lsb_release --all
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

```

OK, this is odd - using Synaptic, I uninstalled Firefox, then used the Force Version tool.  The only choice was FF 11.0.  I took it.  No improvement.  Can't get into any secure sites.

Then I followed your instructions for Safe Mode.  Still no joy.  The Ubuntu Search comes up with the full-on Search window, not the handy drop-down.  I could at least enter my username & password at Fidelity Investments, but I got the same "Error - incorrect username or password" message that I've been getting since the Firefox upgrade to 18.0.  I tried my bank, login fails.  Tried CapitalOne (credit card) and I get a screen I've never seen before.  It says I need to install Javascript.

I already checked in Synaptic - javascript installer is installed.  

I fired up a different Ubuntu desktop PC.  This one runs Lubuntu on top of Ubuntu 12.04.  It has Firefox 17.0.1.  Fidelity Investments log-in works on that PC!

I don't know what all of this means, but since FF 11.0 is also acting stupidly on our main PC I'm guessing it has something to do with Java??

EDIT:
I followed Grinage's instructions.  Back to FF 18.0.1 now, and was able to log in to Fidelity!  The one immediate problem was that Firefox was right back to being unable to distinguish a right-click (open in new tab) from a left-click when in Bookmarks.  I disabled the Unity Firefox Global Menu extension and it appears we're back in business.

It's really sad that Canonical is in such a rush to hitch their star to the tablet/touchscreen movement that us traditional desktop users have to wade through bullsh** just to get a DE that's half as functional as the one we had a few years ago.  I know several people with aging XP rigs.  I'd like to have them take Ubuntu out for a spin, but if the web browser can't stay in gear it's not worth the grief...

---

### Post by Paddy Landau on 2013-01-26
> **Grinage said:**
> …  **  sudo** *%filemanager*
…
%filemanager represents the file manager of your choice, ie.  dolphin, nautilus, thunar or whatever one your ubuntu flavor happens to use or is your favorite

.mozilla is a hidden file unless you have root permissions you won't be able to erase it…
I can see a problem there. Please *never* use [FONT=Lucida Console]sudo[/FONT] for root access to GUI programs; use [FONT=Lucida Console]gksudo[/FONT] instead. That could explain why your [FONT=Lucida Console].mozilla[/FONT] folder was inaccessible to you without root access, and therefore could explain the Firefox problem that you had! Folder [FONT=Lucida Console].mozilla[/FONT] should have been completely available to you without root access.

> **Bartender said:**
> …
 Back to FF 18.0.1 now, and was able to log in to Fidelity!
…
 I disabled the Unity Firefox Global Menu extension and it appears we're back in business.
Two things.

[LIST=1]
[*]My default extensions are called "Global Menu Bar Integration 3.6.4" and "Ubuntu Firefox Modifications 2.6". I am a bit concerned that your name seemed different. Please check the names and versions, in case they differ in your case.
[*]Bearing in mind what Grinage said, have you at any time run GUI programs with [FONT=Lucida Console]sudo[/FONT] instead of [FONT=Lucida Console]gksudo[/FONT] — especially Firefox?
[/LIST]

---

### Post by Bartender on 2013-01-26
Hey, Paddy, thanks for trying to keep me straightened out...

If I go into Add-ons Manager, and click on Extensions, I'm down to 3 now.  Well, two that are enabled.  

'Adblock Plus 2.2.1' & 'Ubuntu Firefox Modifications 2.6' are enabled.

I disabled 'Global Menu Bar Integration 3.6.4' in order to get middle-clicks working as they should from the Bookmarks drop-down.

I described the Menu Bar Integration incorrectly in the previous post.  I apologize for the confusion.

It's entirely possible that I've used sudo by mistake instead of gksudo.  I've known for quite a while that there's a difference, but I've never fully understood the difference and keep forgetting to invoke gksudo correctly.

So far FF seems to be acting as expected.  Middle-clicks do what I want them to do, and I've been able to access secure websites.  Thanks very much for the help!!

---

### Post by Paddy Landau on 2013-01-27
> **Bartender said:**
> 'Adblock Plus 2.2.1' & 'Ubuntu Firefox Modifications 2.6' are enabled.
I also have Adblock Plus 2.2.1.

> **Bartender said:**
>  I disabled 'Global Menu Bar Integration 3.6.4' in order to get middle-clicks working as they should from the Bookmarks drop-down.
My Global Menu Bar Integration 3.6.4 is enabled, and my middle-click works correctly.

> **Bartender said:**
> It's entirely possible that I've used sudo by mistake instead of gksudo.
In that case, open a terminal and enter the following command, which I hope would solve that problem (it may not solve it completely, unfortunately, depending on what has happened since).
```
sudo chown --recursive ${USER}:${USER} ~/.mozilla
```> **Bartender said:**
> I've never fully understood the difference and keep  forgetting to invoke gksudo correctly.
When you run [FONT=Lucida Console]sudo[/FONT], it uses your own home folder. If you are using simple commands such as [FONT=Lucida Console]cp[/FONT], which do not save any settings, this is fine. But as soon as you use applications that save settings, they end up being saved in your home folder instead of root's home folder — and, worse, with root owning the files.

You can use [FONT=Lucida Console]sudo[/FONT] [FONT=Lucida Console]-H[/FONT] instead of [FONT=Lucida Console]sudo[/FONT] to fix this problem. However, [FONT=Lucida Console]sudo[/FONT] requires a terminal to ask for your password, whereas [FONT=Lucida Console]gksudo[/FONT] uses the GUI; so if you want to run [FONT=Lucida Console]sudo[/FONT] from a non-terminal (e.g. from [FONT=Lucida Console]Alt[/FONT]+[FONT=Lucida Console]F2[/FONT] or from a script called from the Launcher), you need [FONT=Lucida Console]gksudo[/FONT]. It's best to get into that habit.

You can't always safely use [FONT=Lucida Console]gksudo[/FONT] instead of [FONT=Lucida Console]sudo[/FONT]; for example, in the command I gave you above, [FONT=Lucida Console]chown[/FONT] would have affected the wrong folder. As a guide, always use [FONT=Lucida Console]sudo[/FONT] for simple line commands, and [FONT=Lucida Console]gksudo[/FONT] for GUI applications.

Some people suggest that you can use [FONT=Lucida Console]gksu[/FONT] instead of [FONT=Lucida Console]gksudo[/FONT]. However, there is a subtle difference that on very rare occasions can cause system problems, so please avoid [FONT=Lucida Console]gksu[/FONT].

---

### Post by Bartender on 2013-01-27
Thanks very much!

I ran the terminal command you included.  

I also copied your reply into a LibreOffice doc called "PC Notes".  Any time I run across something handy it goes into that doc, because I won't remember a year later.

Your explanation of gksudo vs. sudo was helpful to me, and since it's pasted into that doc I can revisit when needed.

Odd that you get the correct response to a middle-click from the Bookmarks folder and I don't.  I'm using a wired Logitech Mx518 mouse.  In Linux the mouse's extra buttons are only partially functional, but the right/middle/left clicks have acted as expected for several years over various versions of Ubuntu.

---

### Post by Paddy Landau on 2013-01-27
> **Bartender said:**
> I ran the terminal command you included.
Did it solve the problem?

> **Bartender said:**
> I also copied your reply into a LibreOffice doc…
I do a similar thing. My document (a plain text file) is already early 8,000 lines long!

---

### Post by Grinage on 2013-01-29
That is right about using sudo to launch gui aplications, I had forgotten that I use an alias to in my case kdesudo because the habit of using sudo is deeply ingrained in my psyche.

---

### Post by Paddy Landau on 2013-01-29
> **Grinage said:**
> I use an alias to in my case kdesudo
That's a bit risky, because [FONT=Lucida Console]gksudo[/FONT] changes [FONT=Lucida Console]${HOME}[/FONT]. You could lose or overwrite files if you forget about that.

It's much safer to get into the habit of using [FONT=Lucida Console]sudo[/FONT] for non-GUI commands, and [FONT=Lucida Console]gksudo[/FONT] for GUI programs. (I presume that [FONT=Lucida Console]kdesudo[/FONT] works like [FONT=Lucida Console]gksudo[/FONT]; correct me if I'm wrong.)

BTW, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") if it has solved your problem.

---

