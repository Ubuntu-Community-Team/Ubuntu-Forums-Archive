---
title: "Boinc will not run after upgrade to 12.10"
date: 2013-03-27
forum: General Help
---

### Post by naturenut on 2013-03-27
I have been running Boinc for a number of years now, but with the latest upgrade, to Ubuntu 12.10, it will not run. When I first discovered the problem, I did an uninstall and reinstall (from software center) - no dice. Then I copied the data directories to another location and did a purge uninstall and reinstall (from software center) - still no dice. My last try was to follow the instructions to get the latest version, from the development repository (**ppa:costamagnagianfranco/boinc**). This try was via the command line, where I uninstalled the full boinc package (client and manager), then added the PPA and then installed. I still get the same problem, the boinc client will not run. Here's an example:

 sudo /etc/init.d/boinc-client start
 * Starting BOINC core client: boinc non-network local connections being added to access control list        [ OK ]
 * Setting up scheduling for BOINC core client and children:             [ OK ] 

All looks good so far, and I can do the following:

 /etc/init.d/boinc-client status
 * Status of BOINC core client: running
 * Scheduling of BOINC core client: 15977
pid 15977's current scheduling policy: SCHED_OTHER
pid 15977's current scheduling priority: 0
 * OOM killer status for BOINC core client:
PID 15977: adj 0
, score 
0

Now, I don't know what all of that means, but I do know that after about 30 seconds where I can get that message, status returns:

 * Status of BOINC core client: stopped

If I try to run boinc manager, even when I can get the 'running' message, it opens and has a dialog box stating that it is communicating with boinc, but nothing ever happens. It is hung.

During none of the installs did I get any dependencey problems - all proceeded smoothly to completion.

I'd very much like to get back to crunching for the projects I've been helping all these years, but I'm at a loss as to what to do. Although I am fairly new to Linux, I am not new to computers, and not afraid of the command line. I attempted all I know how to do before asking for help. I assume there's a log, somewhere, that will tell what is happening with boinc, but I have no clue where to look.

Any assistance would be very much appreciated.

---

### Post by blenderfox on 2013-03-31
I'm also interested in the solution to this. I have the same behaviour. For now, I've got Boinc completely removed from my Lubuntu 12.10 installation until I find the solution. One thing you can try (which worked temporarily) is to kill the service, then try running boinc in one window, then starting boincmgr. If they connect, then I think it's something to do with the user (boinc) and/or the permissions somewhere....

---

### Post by blenderfox on 2013-03-31
Okay, found a better workaround pending a more permanent solution.

1. Find your gui rpc password. This can be done by using the following:

```
sudo gedit /var/lib/boinc-client/gui_rpc_auth.cfg
```

(Replace "gedit" with whatever you preferred text editor is. I use leafpad being in Lubuntu)

2. Copy the string out of there

3. Make sure BOINC is running by doing the following:

```
sudo service boinc-client restart
```

4. Now verify which port BOINC is listening on by doing:

```
sudo lsof -i4 | grep boinc
```

You should see something like this:

```
boinc     6206  boinc    5u  IPv4  43519      0t0  TCP *:31416 (LISTEN)
```

Port 31416 is the standard port for BOINC, so this step is just to make sure you haven't inadvertently changed the port

5. You now know the password (Step 2), port (Step 4) and the host (localhost). So run this at the terminal:

```
boincmgr --namehost=localhost --gui_rpc_port=31416 --password=password_from_step_2
```

Replace "password_from_step_2" with the password you copied

If this step works, then the BOINC service is not an issue, it's the password that the BOINC Manager is submitting to the client. So instead, I have created a script with the line above and will use that instead of the main shortcut from now on.

Fudging the problem? Probably, but it works for me.

---

### Post by naturenut on 2013-03-31
> **momokoyukino said:**
> Okay, found a better workaround pending a more permanent solution.

1. Find your gui rpc password. This can be done by using the following:

```
sudo gedit /var/lib/boinc-client/gui_rpc_auth.cfg
```

<SNIPPED for brevity>

5. You now know the password (Step 2), port (Step 4) and the host (localhost). So run this at the terminal:

```
boincmgr --namehost=localhost --gui_rpc_port=31416 --password=password_from_step_2
```

Replace "password_from_step_2" with the password you copied

If this step works, then the BOINC service is not an issue, it's the password that the BOINC Manager is submitting to the client. So instead, I have created a script with the line above and will use that instead of the main shortcut from now on.

Fudging the problem? Probably, but it works for me.

Step 1 got no password in the file, however, I found a password in the file that I moved prior to reinstallation.

Step 2 copied the password from old file - to try if nothing happens with no password

Step 3 did restart, which appears to work, but no process named boinc* shows in the process list

Step 4 Listen port is the same as what you got.

Step 5 Tried command with both no password (what I found in the 'live' gui_rpc fille) and with the password I found in the old gui_rpc file. Same result as I got before - boinc mgr opens, then opens a dialog box with communitating with client text and then appears hung. Waited several minutes for something to happen, but nothing ever did.

I am unsure that boinc-client is actually running, since I can't find it in the process list. Does it have some strange name?

---

### Post by blenderfox on 2013-03-31
> **naturenut said:**
> Step 1 got no password in the file, however, I found a password in the file that I moved prior to reinstallation.

Remove the file, or back it up, then restart the service. It should automatically regenerate (it did for me) -- this is the file you need to use.

> **naturenut said:**
> Step 2 copied the password from old file - to try if nothing happens with no password

I don't think it'll work if you use no password (too insecure)

> **naturenut said:**
> Step 3 did restart, which appears to work, but no process named boinc* shows in the process list

What does:

```
sudo service boinc-client status
```

give you? Also, make sure your gui_rpc file is removed/backed up so BOINC it has to regenerate this file it when you restart the service. This is the file you need to use in the Manager.

> **naturenut said:**
> Step 4 Listen port is the same as what you got.

Step 5 Tried command with both no password (what I found in the 'live' gui_rpc fille) and with the password I found in the old gui_rpc file. Same result as I got before - boinc mgr opens, then opens a dialog box with communitating with client text and then appears hung. Waited several minutes for something to happen, but nothing ever did.

I am unsure that boinc-client is actually running, since I can't find it in the process list. Does it have some strange name?

I don't think a blank password would be allowed due to insecurity. Also, if you're running boincmgr in the terminal window, does it give you anything?

As for the process, the boinc service runs as user "boinc", so if you aren't listing processes by other users, you won't find it. Try:

```
ps -Ao pid,tt,user,fname,tmout,f,wchan | grep boinc
```

Here's my output, which is running successfully. The top line is the one you're looking for.

```
 1256 ?        boinc    boinc        - 4 wait
 1257 ?        boinc    boinc_cl     - 0 poll_schedule_timeout
 1287 ?        boinc    wrapper_     - 0 hrtimer_nanosleep
 1288 ?        boinc    wep_1.09     - 0 ?
 1289 ?        boinc    wep_1.09     - 1 poll_schedule_timeout
 1290 ?        boinc    wep_1.09     - 1 hrtimer_nanosleep
 1292 ?        boinc    enigma_0     - 0 signal_stop
```

---

### Post by naturenut on 2013-03-31
Left off quoting to save space.

CFG file removed and restarting boinc-client regenerated file - this one has some hex, for a password, in it. Original file was a link to a file in /etc/boinc-client I deleted both, but only the one in /var/boinc-client was recreated. Easy enough to fix, if I can get things working....

Just to make sure you know. I cannot start the boinc-client as user, gotta do the sudo thing.

Was not surprised that it didn't work without password, just tried it because the CFG file was empty. Also, was not surpristed when it didn't work with old password.

For a short period, after starting/restarting boinc-client, I get the following:

sudo service boinc-client status
 * Status of BOINC core client: running
 * Scheduling of BOINC core client: 32605
pid 32605's current scheduling policy: SCHED_OTHER
pid 32605's current scheduling priority: 0
 * OOM killer status for BOINC core client:
PID 32605: adj 0
, score 
0

After about 30 seconds or so, I get:

sudo service boinc-client status
 * Status of BOINC core client: stopped

When I get this, I have done nothing, except wait for a little while and then re-issue the status command.

When I run the line to get the process, I get:

ps -Ao pid,tt,user,fname,tmout,f,wchan | grep boinc
 1494 ?        boinc    boinc        - 4 signal_stop
 3350 ?        boinc    hadcm3n_     - 0 signal_stop
29303 pts/0    iris     boincmgr     - 0 poll_schedule_timeout

I assume that the last line is the result of running the manager in another terminal.

Result of running boincmgr from terminal, command is first line:

boincmgr --namehost=localhost --gui_rpc_port=31416 --password=(from regenerated file)
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

(boincmgr:29303): Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed

(boincmgr:29303): Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed

(boincmgr:29303): Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed

These messages appear in the terminal window after I click the close boinc manager button, when it appears to be hung.

(boincmgr:29303): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(boincmgr:29303): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(boincmgr:29303): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(boincmgr:29303): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(boincmgr:29303): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(boincmgr:29303): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

---

### Post by blenderfox on 2013-03-31
Unfortunately, those errors don't mean much sense to me. I think it could be as a result of you trying to get the dev version running. I would suggest (if you don't mind losing any project progress), you clean out all boinc-related files via

> sudo apt-get purge boinc*

Then making sure /etc/ and /var/ don't contain any boinc directories or files.

Reboot, run the ps command to make sure no boinc processes are running, then install from the official repo (i.e. not the PPA).

If the stock install doesn't work (it didn't for me), then try the steps mentioned in my previous post at that point.

Let me know how it goes.

---

### Post by naturenut on 2013-03-31
Have already lost all project data, so not a big deal to start over. Have done the purge thing already, once, but will try again. Will get back to you.

None of the messages mean much to me, so I am happy that you're willing to take a look and try to thelp.

---

### Post by naturenut on 2013-03-31
Have already lost all project data, so not a big deal to start over. Have done the purge thing already, once, but will try again. Will get back to you.

None of the messages mean much to me, so I am happy that you're willing to take a look and try to help.

---

### Post by naturenut on 2013-03-31
Now, this beats all.

Followed your instructions on uninstall and reboot - same process I'd used before, except I didn't reboot before. Software Center install went fine and, then, surprise, surprise! Using menu option for boinc manager opened it and it asked to attach to project or use project manager. I had been using BAM, so I went through that process and all appears well, except that there are no menu titles in the menu bar, just the tabs for different views.

It appears that a setting is preventing boinc from downloading because I'm using the computer, and I can't change that, because I can't access the settings from its dropdown menu. There is a list of items to download though, and it appears that things are right. One project appears off the air, and hasn't picked up the initialization info yet, but I'll give it time.

Any thoughts on how to get the File, Edit, etc dropdowns back?

---

### Post by naturenut on 2013-03-31
Found a workaround for the no File menu thing, but it is dated 2011, and I didn't have this problem until I couldn't get boinc to run after the upgrade to 12.10.

The workaround is in a thread named [COLOR=#980101]**[ubuntu]**[/COLOR] BOINC Manager - no menu bar, in this same forum.

To save looking it up:

*** while typing this, I have found that if I hit alt+f, the file menu  drops down and I can then arrow over the the other menu items... but the  menu bar is still not visible.

This works for me, too, but isn't really a good solution.

Marking the thread as Solved. Thanks for all the help.

---

### Post by blenderfox on 2013-04-01
So you've now got it to work, but you can't see the menu? Then you're in the same state as me. All I see if "Fi" for file and have to use the ALT+F to get the File menu, then left and right arrow the other menus. It doesn't bother me too much, I tend to use keyboard shortcuts a LOT.

Good to know you're getting the data through now. Looks like you won't need the script I suggested then.

---

### Post by naturenut on 2013-04-01
Found out, yesterday evening, that you can click the Fi and get the file menu, then use the arrows to move around.

I looked at the CFG file and the new one doesn't contain a password. Might mean that I'll be messed up if I close the manager/reboot - normally, I just minimize it, using the X in the title bar.

---

### Post by blenderfox on 2013-04-01
If you do, then the script line should help.

---

### Post by naturenut on 2013-04-01
> **blenderfox said:**
> If you do, then the script line should help.

But only if I stop boinc, delete the CFG file and restart boinc, so I actually have a password, right? As it stands now, I looked at the CFG file and it is empty - the install created an empty file in /etc and a link to that file in /var (in the boinc-client directory in those directories). Not sure how that is working, since it didn't work with an empty file before...

If I wind up re-creating the CFG filw, to get a password, I'd assume that I could take the new file, with password, move it to /etc and create a link in /var, since boinc creates the file with password in /var. Not sure why that is the way things are set up, but assume that it'd be good to put things back like original, once it is working with a real password.

---

### Post by blenderfox on 2013-04-01
I would say "if it isn't broken, don't fix it." Right now, you have a working installation. Try not to break it. If it's working with the cfg file with a blank password, then leave it like that. If after restarting, you get the same problem, then use the command line to force the password, port and host. I have to do that myself on my Lubuntu installation.

---

### Post by naturenut on 2013-04-01
> **blenderfox said:**
> I would say "if it isn't broken, don't fix it." Right now, you have a working installation. Try not to break it. If it's working with the cfg file with a blank password, then leave it like that. If after restarting, you get the same problem, then use the command line to force the password, port and host. I have to do that myself on my Lubuntu installation.

Agree 100%. I don't figure on messing with it, unless I run into trouble.

Does seem strange, to me, that it should break like that. I've been running boinc for several years, including several Ubuntu upgrades. The last upgrade didn't go so well though. Started with Natty and upgraded to Oneiric - was informed that the upgrade didn't work right and I needed to do a partial upgrade to fix it, which upgraded to Precise, which also reported the same problem. Last time I did a partial upgrade left me in Quantal, but at least no more of the partial upgrade crap. Do get a report, on every kernel upgrade, regarding some sort of 3rd party problem with alsa, but sound works, so I'm not fiddling with it...but getting off-topic here...

---

### Post by blenderfox on 2013-04-01
I started with Maverick so one version before you. Have changed distros several times since then, and Ubuntu is the only one where I've had this kind of problem with BOINC. One thing I have noticed is that the BOINC client is saying there's a new version available for download, but it looks like it hasn't been pushed to the Ubuntu repositories yet. Let's wait and see what happens when that goes through. We could be having this same conversation then.

On the topic of partially successful upgrades. I **ALWAYS** recommend run a Clonezilla image before doing anything like an upgrade. Trying to fix the problem of partially successful upgrades can last a long time. In fact, I've reinstalled Ubuntu several times as a result of unsuccessful upgrades. Sure, it takes longer to setup and reconfigure a new installation, but at least it's stable. And since all my main work files are on an external USB, I don't have much data to copy over (just the basic configuration directories)

---

### Post by naturenut on 2013-04-01
> **blenderfox said:**
> On the topic of partially successful upgrades. I **ALWAYS** recommend run a Clonezilla image before doing anything like an upgrade. Trying to fix the problem of partially successful upgrades can last a long time. In fact, I've reinstalled Ubuntu several times as a result of unsuccessful upgrades. Sure, it takes longer to setup and reconfigure a new installation, but at least it's stable. And since all my main work files are on an external USB, I don't have much data to copy over (just the basic configuration directories)

I takes my chances, mine is not running mission critical business stuff, but I do keep /home on a separate partition from boot partition. What **I DON'T LIKE** is that boinc puts its data on the boot partition, no option to choose to put it elsewhere (brings to mind an OS that starts with W, that I've never used as a primary OS). Ever since hard drives became cheap enough I could afford one in my computer (did I mention I've been around computers a while), I never have liked putting data and boot on the same partition.

---

### Post by blenderfox on 2013-04-01
Likewise. I don't mind where applications put their data, as long as I can change it. I used to have major problems with Windoze when I ran out of space on my C drive and none of the programs I was trying to install would allow me to install anywhere but C. And even those that did let me, still put all their data on C without letting me choose otherwise.

But we digress. Back to the thread. I think we're pretty much resolved on your issue now, aren't we?

---

### Post by naturenut on 2013-04-01
> **blenderfox said:**
> But we digress. Back to the thread. I think we're pretty much resolved on your issue now, aren't we?

Yep. Consider this thread SOLVED.

---

### Post by naturenut on 2013-04-22
UPDATE: I decided to go ahead and try one of the newer versions of boinc, so I added the PPA below. This version I got, 7.0.65, has the full menu bar at the top and runs just fine here.  Below is a quote, from a posting to boinc.berkeley.edu/dev/forum_thread.php?id=7598 (Message 45533), from the owner of the PPA, that prompted me to use it:

> The difference between my package and pkg boinc one is that my package  claims to be always up to date with the debian boinc trunk git, while  the second one will update only sometimes.

So if you want to keep always up to date with the latest boinc and boinc  app seti you should use my ppa (I promise I will try to avoid problems  anymore), while if you want a "stable" release you should go for boinc  pkg or the ubuntu shipped one.

I personally think that my ppa is better because as far as I can tell  the upstream/debian developers very rarely introduce new bugs, while  they fix so many bugs every time a commit is made.

The PPA is: [B]ppa:costamagnagianfranco/boinc

[/B]NOTE: The PPA pkg boinc also does not provide debs for Ubuntu releases after Precise, and the Ubuntu 12.10 boinc release (7.0.27) dates from at least as far back as June 2012.

---

