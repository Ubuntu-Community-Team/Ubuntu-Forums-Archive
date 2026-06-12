---
title: "Drobox Indicator Fail"
date: 2014-12-20
forum: General Help
---

### Post by Kurt_Alan on 2014-12-20
I pay dropbox.com $450.00 per year for two accounts, 3 TB.  The only reason I pay this money is because of powerful features such as "selective sync." The latter allows me to pull down a subset of my 250 GB data set to any device anywhere in the world.

Now that the indicator is missing, I cannot access menu/preferences/selective sync.  Drobox, now, is no better than Google Drive. I have uninstalled/re-installed dropbox both via synaptic and nautilus-dropbox and via the .deb file at dropbox.com via pasting code -- to no avail.  There are three threads at ubuntuforums on this topic, but no solution.  One thread is marked "solved" and I have asked the mods to check this thread and remove the 'solved" for there is no stated solution.  The stated "solution" is to start and stop dropbox but this isn't the issue.  The issue is the failure of the systray/panel dropbox icon. Dropbox itself is functioning fine and you can check this via ```
 dropbox status 
``` but if you can't use any of dropbox's features, Dropbox is no better than OneDrive or Google Drive.

Further, a Google search reveals that many Linux users are also having this problem and that there is no apparent solution.  This includes Linux Mint and Magia users.

I have started a trouble ticket at dropbox.com and I am waiting for a response.  I have also posted on the dropbox.com forum.  Others are having the same problem and there is no solution.

The fact that the indicator did function correctly on my newly installed 14.10 UU, 64 bit, on my new mini-itx setup, tells me that it CAN work on the OS and this flavor but that it is now broken.  

Any recommendations on how to proceed? Does anyone have a tested solution?

I'm going to raise hell with dropbox.com if they do not fix this problem. We shall see if I get a professional response from their tech support . . .

---

### Post by bapoumba on 2014-12-21
As you have posted in the following thread, I suppose you have seen the latest replies : [http://ubuntuforums.org/showthread.php?t=2256902](http://ubuntuforums.org/showthread.php?t=2256902)
My own indicators appear to be in /home/bapoumba/.dropbox-dist/dropbox-lnx.x86-3.0.3/images

---

### Post by Kurt_Alan on 2014-12-21
Bapoumba--As you have posted in the following thread, I suppose you have seen the latest replies : [http://ubuntuforums.org/showthread.php?t=2256902](http://ubuntuforums.org/showthread.php?t=2256902)
My own indicators appear to be in /home/bapoumba/.dropbox-dist/dropbox-lnx.x86-3.0.3/images--Bapoumba

I followed up on all your notes.  I think we are confusing two distinct but similar items and terms.  With one there is one issue.  With the other there are no issues.  But we are conflating them.

The first item is the Dropbox folder that by default goes to /home/lucas/Dropbox via Thunar.  You gave the path for a hidden file that shows different indicators or icons that can appear superimposed on this folder.  For example, a blue checkmark signifies that Dropbox has synced and is up-to-date.
However, I don't believe any of us (including many other Linux users on the Internet) are referencing either this Dropbox folder or these Dropbox indicators or icons.  For me, and I believe everyone else, Dropbox is functioning! And this can be confirmed via CLI.  So we are not talking about these indicators and we are not talking about, for example, the command you used to start dropbox. Again, Dropbox itself is functioning fine.

The problem is not with this first item.  The problem is with the SECOND item.  The second item is not a folder but it is an indicator and it is an icon and it appears only in a Panel or systray equivalent.  It is this indicator that is necessary to appear in order to access Dropbox's menu and powerful features such as "selective sync." (Additionally, like item one, it will indicate status).  

Without this indicator, item two, Drobox is "dead in the water" and no better than Google Drive or OneDrive.

---

### Post by bapoumba on 2014-12-22
My /home/bapoumba/.dropbox-dist/dropbox-lnx.x86-3.0.3/images has 2 folders :

[LIST]
[*]/home/bapoumba/.dropbox-dist/dropbox-lnx.x86-3.0.3/images/emblems > contains the files you are talking about :
> You gave the path for a hidden file that shows different indicators or icons that can appear superimposed on this folder. For example, a blue checkmark signifies that Dropbox has synced and is up-to-date
[*]/home/bapoumba/.dropbox-dist/dropbox-lnx.x86-3.0.3/images/hicolor/16x16/status > has files that look like the dropbox status img in the panel to me.
[/LIST]
Do you have that second folder with the status img files ? If yes, that means the panel or systray or whatever notification is not functional. If not, the notification img are missing and the panel notification script may be working.

---

### Post by markodd on 2014-12-22
@bapoumba 

I'm having the same problem as him and yes, I do have all the folders/files you mentioned. 

To OP:

There is [this]("http://askubuntu.com/questions/561448/dropbox-3-0-3-ignoring-local-themes-missing-notification-icon/564297#564297") thread on AskUbuntu and one of the answers mentions that disabling compositing fixes the problem.

---

### Post by Kurt_Alan on 2014-12-22
@bapoumba --

Both the Dropbox folder (NO access to menu) and the Drobox indicator (ONLY access to men) use some kind of iconography.  I can't tell from looking at the .png files, whether they belong to the former or the latter.  Besides, if there were a problem with corruption, a re-install should solve that.  Many Linux users whose reports I have read online re: the missing indicator problem report that a uninstall/re-install have no effect.  In fact, I have re-installed both internally from synaptic and externally from the drobox website (.deb) to no avail.

While waiting for a response from the dropbox team, my next step will be to install Xubuntu 14.04 LTS.

---

### Post by Kurt_Alan on 2014-12-22
@markodd

I will follow this up and report back.

---

### Post by Kurt_Alan on 2014-12-22
@markodd

Thanks for this. Unfortunately the deselecting compositing work-around fails. (I also uninstalled/reinstalled)

---

### Post by Kurt_Alan on 2014-12-22
@markodd

Thanks for this. Unfortunately the deselecting compositing work-around fails. (I also uninstalled/reinstalled)

---

### Post by Kurt_Alan on 2014-12-22
@bapoumba

Could you read the thread from Askubuntu referenced by markodd and see if you can add an insight to this thread? (However, there is no solution offered as yet).

This thread is very descriptive and precise.

---

### Post by Kurt_Alan on 2014-12-23
I received a response from my trouble ticket at dropbox.com  The staff person told me that the engineers are aware of the problem and are working on a fix.  So that's cool.  I guess this means that the problem is at their end and not ours.  So we need to wait.

---

### Post by markodd on 2014-12-23
> **Kurt_Alan said:**
> I received a response from my trouble ticket at dropbox.com  The staff person told me that the engineers are aware of the problem and are working on a fix.  So that's cool.  I guess this means that the problem is at their end and not ours.  So we need to wait.

Now tell them that Markodd told them to hurry up because I need that fixed for yesterday! :P

---

### Post by bapoumba on 2014-12-23
> **Kurt_Alan said:**
> @bapoumba

Could you read the thread from Askubuntu referenced by markodd and see if you can add an insight to this thread? (However, there is no solution offered as yet).

This thread is very descriptive and precise.
Well, I'm here :)
There already are two current threads to follow here, found another one yesterday I forgot to bookmark (will search again), I think it dilutes the effort and my attention. I'm likely to forget one, not good :)

> **Kurt_Alan said:**
> I received a response from my trouble ticket at dropbox.com  The staff person told me that the engineers are aware of the problem and are working on a fix.  So that's cool.  I guess this means that the problem is at their end and not ours.  So we need to wait.

> **markodd said:**
> Now tell them that Markodd told them to hurry up because I need that fixed for yesterday! :P
Yep :)
fwiw, I had some updates yesterday and I rebooted (do not recall is the upgrade asked for it, but I needed to reboot for another reason). The Dropbox icon went missing from my own lubuntu panel. Manually added Dropbox to Prefs > default Application for LXSession > Autostart and all is good this morning.

---

### Post by markodd on 2014-12-23
Indeed, there was an update for dropbox. Sadly, it didn't solve anything for me.

---

### Post by markodd on 2014-12-29
.... Still no news Kurt_Alan? They sure are taking their time...

---

### Post by Kurt_Alan on 2014-12-30
Update: December 30, 2014

The Dropbox indicator works correctly in Ubuntu 14.04 LTS, i.e., Unity DE.

The Dropbox indicator does NOT work at all in Xubuntu 14.04 LTS, i.e., Xcfe DE.

Fortunately Dropbox's tech support did contact me and said that the engineers are aware of the problem and are fixing it.

Good. But I'm afraid that since it's working in Ubuntu, they will not worry about the other distros.  I will contact them again in a couple of weeks.

---

### Post by idobrinescu on 2015-01-02
Following this tread with interest. I use a Dropbox for Business administrative account. 

Dropbox 3.0.3 indicator doesn't show up on Elementary OS Freya either, but the application works perfectly. 

I can confirm that on all Ubuntu and Windows systems, the indicator works fine. 

On Lubuntu 14.10 the indicator works also, but Dropbox won't automatically upgrade to 3.0.3.   :)

---

### Post by markodd on 2015-01-02
> **idobrinescu said:**
> Following this tread with interest. I use a Dropbox for Business administrative account. 

Dropbox 3.0.3 indicator doesn't show up on Elementary OS Freya either, but the application works perfectly. 

I can confirm that on all Ubuntu and Windows systems, the indicator works fine. 

On Lubuntu 14.10 the indicator works also, but Dropbox won't automatically upgrade to 3.0.3.   :)

It doesn't work on all Ubuntu's. It doesn't work on Xubuntu, for example.

---

### Post by rogerdean on 2015-01-10
I seem to have the indicator back ok and properly themed. It was a clean install of Mint 17.1 XFCE RC, with dropbox 3.0.4 from nautilus-dropbox

---

### Post by Kurt_Alan on 2015-01-10
> **rogerdean said:**
> I seem to have the indicator back ok and properly themed. It was a clean install of Mint 17.1 XFCE RC, with dropbox 3.0.4 from nautilus-dropbox

That's good to hear.  Is RC "release candidate"? This is my first time hearing of iteration 3.04. I'm checking it out.

You say this was from nautilus-dropbox.  I'm also checking synaptic to see if nautilus-dropbox for Xubuntu has the same version number. 

What's happening on your Xubuntu?

---

### Post by Kurt_Alan on 2015-01-10
@rogerdean --

I realized that when I checked dropbox-nautilus in Synaptic that I was not looking at the Dropbox version but Ubuntu's dropbox-nautilus integration tool version.  You can install and run Dropbox from dropbox.com without installing dropbox-nautilus but then you cannot access Dropbox via CLI.

Without having an indicator there's no way I can determine my Dropbox version number.  I then re-installed with version 3.0.5 which I obtained from a link in the release notes page. However, on Xubuntu, to no avail. No indicator icon.

If you go to [HTML] dropbox.com_releasenotes[/HTML] you will see a list of versions and changelogs.  You can also filter for Testing versions.  I did that and found that a version was/is being tested for the Xubuntu indicator failure bug (my asterisks):


2.11.43[Testing]11/20/2014
Our forums are currently unavailable due to an unexpected issue and may remain unavailable for a while as we transition to a new system.
Fix some rare cases where Dropbox would stay in the 'syncing' state
Fix issue w/ Linux tray icon not appearing on certain systems*****




It would appear that this is not yet fixed since there are no notes on the newer versions that say that this has been fixed.

**********************

But why can't we fix it? It worked once, so it can work again! I have another thread: I'm trying to figure out how to get Dropbox listed among the applications that appear in my Panel/Notification Area/Known Applications.  Dropbox is not listed, so that is probably why it is not appearing.

---

### Post by vasa1 on 2015-01-10
What do you see with **pgrep -a dropbox**? 

```
09:42 AM ~ $ pgrep -a dropbox
1517 /home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-3.0.3/dropbox
09:42 AM ~ $ 
```

---

### Post by vasa1 on 2015-01-10
BTW, I use the Openbox session of Lubuntu 14.04 and, after some fiddling, I have the Dropbox indicator reliably showing up in my tint2 panel. Please note that I don't try to integrate dropbox with my file manager (or any other advanced stuff).

---

### Post by Kurt_Alan on 2015-01-11
> **vasa1 said:**
> What do you see with **pgrep -a dropbox**? 

```
09:42 AM ~ $ pgrep -a dropbox
1517 /home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-3.0.3/dropbox
09:42 AM ~ $ 
```


Result: ```
 3681 /var/lib/dropbox/.dropbox-dist/dropbox-lnx.x86_64-3.0.5/dropbox
 
```  I see I am running the latest version.

---

### Post by Kurt_Alan on 2015-01-11
> **vasa1 said:**
> BTW, I use the Openbox session of Lubuntu 14.04 and, after some fiddling, I have the Dropbox indicator reliably showing up in my tint2 panel. Please note that I'm don't try to integrate dropbox with my file manager (or any other advanced stuff).

I tried tint2 as a solution but the indicator failed to appear.  I think that nautilus-drobox is just an extension that links Dropbox to CLI. However, I tried Dropbox withOUT installing nautilus-dropbox and the problem remained.

On the other hand, nautilus-dropbox/Terminal is the only way I can find my Dropbox status without an indicator. Again, the problem with no indicator is not status, although that's nice to have.  It is that I have no access to the Dropbox menu/Preferences/"selective sync."  Selective Sync is the only reason I pay Dropbox $450.00 per year. "Selective Sync" allows me to download a precise subset of my 250 GB dataset to any of my devices as I travel the world.

Hmm, so you are up and running on Lubuntu 14.04 and Openbox. On the Net I haven't found any Lubuntu issues referenced.  Also, my indicator worked ONE time when I opened Skype and the Skype process appeared in my Indicator with icon and background process.  Then my Dropbox indicator appeared with full menu and preferences. So my Indicator is ALMOST working. It needs a little tweak to fix it. BTW, no issues with Unity (Ubuntu 14.04)  Xubuntu has much greater modularity so perhaps it is a more fragile DE--more choice=greater fragility.

---

### Post by rogerdean on 2015-01-11
> **Kurt_Alan said:**
> That's good to hear.  Is RC "release candidate"? This is my first time hearing of iteration 3.04. I'm checking it out.

You say this was from nautilus-dropbox.  I'm also checking synaptic to see if nautilus-dropbox for Xubuntu has the same version number. 

What's happening on your Xubuntu?

Release Candidate, that's right. It's based on 14.04 and the final ought to be out in a couple of days

I binned my Xubuntu in frustration, temporary no doubt

R

---

### Post by rogerdean on 2015-01-11
Oh. Turns out the icon on Mint 17.1 XFCE is only intermittent. Not solved then.

---

### Post by Kurt_Alan on 2015-01-11
> **rogerdean said:**
> Oh. Turns out the icon on Mint 17.1 XFCE is only intermittent. Not solved then.


If it's intermittent that means it *can* work but I don't have the troubleshooting chops.

---

### Post by vasa1 on 2015-01-11
When something occurs intermittently, chances are it's because of a "race condition". Most autostarts do not include sleeps for each program loaded via the autostart file. One could add sleeps and play with the order of loading. That's what works for me *consistently* and seems to be the way for [someone else as well]("http://crunchbang.org/forums/viewtopic.php?pid=413319#p413319").

---

### Post by fadder on 2015-01-12
Any news on this? I have Xubuntu 14.10, and am getting annoyed at constant notifications of updates to files made by somebody else. With the panel icon  I used to be able to control the notification settings. Without it, all I can do is turn off dropbox.

And yep, I read the AskUbuntu thread, but it didn't help.

---

### Post by Kurt_Alan on 2015-01-13
> **fadder said:**
> Any news on this? I have Xubuntu 14.10, and am getting annoyed at constant notifications of updates to files made by somebody else. With the panel icon  I used to be able to control the notification settings. Without it, all I can do is turn off dropbox.

And yep, I read the AskUbuntu thread, but it didn't help.

@fadder --

I have had two personal replies from dropbox.com Support. I am told that the engineers are aware of the problem. As of one week ago there was no fix and no ETA.  I'm going to look at vasa1's solution but it is beyond my ability level; well, I can try.  Soon I will probably post to the dropboxforums again and complain.

Without Indicator, we have no Menu, no Settings, no Preferences. Bummer.  But you do understand that you can use CLI and enter ```
 dropbox status 
``` Right? You have to install via Synaptic nautilus-dropbox to use CLI. If you install from dropbox.com and use this command it will say that dropbox is not installed. At least Dropbox itself is functioning correctly in spite of the lack of Indicator and menu access.

I tried Lubuntu 14.10 today and the Indicator worked--but not in Xubuntu 4.04 and 4.10. Lubuntu is too light for me.

I am using a workaround which is not too far-fetched because I was doing it anyway: I am dual-booting Ubuntu 14.04 and Xubuntu 14.04.  When I install Dropbox on Xubuntu I sync everything.  But on Ubuntu, where my indicator works, I sync only what I need.

---

### Post by vasa1 on 2015-01-13
Even users of the perfect distro aren't unaffected: [https://plus.google.com/110771891366288664482/posts/e5oE2pQdgeG](https://plus.google.com/110771891366288664482/posts/e5oE2pQdgeG)

---

### Post by Kurt_Alan on 2015-01-14
@vasa1

Cool.  I'm going to copy/paste a bunch of these comments to the dropbox forum and hope that someone is reading. I found this bug first reported in dropbox.com's release notes in November, 2014.  On the other hand, looking at the big picture, I will be sure to praise Dropbox for supporting Linux. After all, the indicator does work on Unity DE. I'm sure there's a human labor limit to how many distros and flavors of distros dropbox devs can code for . . . But, yes, they must fix this bug.

---

### Post by vasa1 on 2015-01-14
> **Kurt_Alan said:**
> ... I will be sure to praise Dropbox for supporting Linux. ...
A big +1 to that.

Re. it displaying in Ubuntu, what I gather from scraps I read here and there is that the "Unity team" has put in some special effort to get qt to play nice.

---

### Post by idobrinescu on 2015-04-09
Apparently someone (Mr. Shaun Ward  from Tokyo, Japan) finally figured this out here:
[http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/](http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/)


1. Start dropbox with this command
dropbox stop && env XDG_CURRENT_DESKTOP=Unity dropbox start


2. Go to settings and turn off "Start Dropbox on system startup"


3. Go to system settings -> Applications , from the tab up top select "Startup" and add a command from the + button at the bottom left and there will be an input where you can enter in a command below and press enter to save.
env XDG_CURRENT_DESKTOP=Unity dropbox start


Worked for me. I finally have the dropbox indicator working. :))

---

### Post by malasa on 2016-02-20
> **idobrinescu said:**
> Apparently someone (Mr. Shaun Ward  from Tokyo, Japan) finally figured this out here:
[http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/](http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/)


1. Start dropbox with this command
dropbox stop && env XDG_CURRENT_DESKTOP=Unity dropbox start

Looking all day to get this working (xubuntu 14.04.4).

Thanks, works for me too this way.

---

### Post by dez93_2000 on 2016-02-20
> dropbox stop && env XDG_CURRENT_DESKTOP=Unity dropbox start

Nobody else getting:

> (dropbox:13224): GLib-GObject-WARNING **: cannot register existing type 'GdkDisplayManager'

(dropbox:13224): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed

(dropbox:13224): GLib-GObject-CRITICAL **: g_object_new: assertion 'G_TYPE_IS_OBJECT (object_type)' failed

?

---

### Post by p-services on 2016-02-23
> **idobrinescu said:**
> Apparently someone (Mr. Shaun Ward  from Tokyo, Japan) finally figured this out here:
[http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/](http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/)


1. Start dropbox with this command
dropbox stop && env XDG_CURRENT_DESKTOP=Unity dropbox start


2. Go to settings and turn off "Start Dropbox on system startup"


3. Go to system settings -> Applications , from the tab up top select "Startup" and add a command from the + button at the bottom left and there will be an input where you can enter in a command below and press enter to save.
env XDG_CURRENT_DESKTOP=Unity dropbox start


Worked for me. I finally have the dropbox indicator working. :))

I would add that it is *necessary* (in Xubuntu 14.04, in my case) to make ~/.config/autostart/dropbox.desktop read-only for user and group, before you reboot or logout after following Step 3, or else upon new boot-up or coming back from an extended logout, Dropbox will rewrite the desktop file back to 'dropbox start -i'. By making it read only the process fails (quietly) and the modified desktop file is unaltered.

---

