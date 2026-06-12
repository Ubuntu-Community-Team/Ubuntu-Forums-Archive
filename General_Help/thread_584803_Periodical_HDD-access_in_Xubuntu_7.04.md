---
title: "Periodical HDD-access in Xubuntu 7.04?"
date: 2007-10-21
forum: General Help
---

### Post by perixx on 2007-10-21
Hi all...

I have some performance issues with my PC, when it comes to graphical tasks, sometimes. I suppose it might be linked to the fact, that something's repeatedly accessing the HDD, even in idle. The HDD-LED blinks periodically about every second... what might be the cause and how can I stop it?

Thanks for help,


perixx

---

### Post by bapoumba on 2007-10-21
You can open a terminal (> Accessories > Terminal) and run:
```
top
```
to see thz active processes.
Guessing you'll have update-db unning, indexing all the files on your system.

---

### Post by perixx on 2007-10-22
Hi!

Well, currently my desktop is broken, due to some change in the update-repositories, so I cannot try this atm...

I had installed 'Beagle' but this effect isn't likely to be related to that program, since I still have it after removing Beagle.


perixx

---

### Post by bapoumba on 2007-10-22
What happened to your desktop?

---

### Post by perixx on 2007-10-22
Well, I lost everything, apart from Xubuntu's (7.04) standard-symlinks(?) on the desktop (Thunar, Floppy, USB-Stick...).

Most dreadfully, all the taskbars with carefully selected starter-links are gone, as is the 'applications'-menu button to access any menu.

I still can open the Terminal via rightclick on Thunar and can access the repo's manager and all. Firefox won't start from the Terminal ('gksudo firefox' won't, too). 

Somehow this must be linked to my great idea of first changing the repositories to 'main' in Synaptic, then adding some more repositories (Medibuntu and 2 others) and then reverting back to German repositories again - with always doing an update in-between.

After the last step the PC bootet with the broken desktop; I doubt that the settings are all gone, they're just not being linked to correctly, I assume.


perixx

---

### Post by bapoumba on 2007-10-23
Hmm. This happened once to me (with gutsy though). All the panels were gone, no error message I could retrieve, and the panel definitions in ~/.config/xfce4/panel/panel.xml all blank. I did not find any related bug report.
Could you please check that file in your /home?
What were you doing when this happened? Here, I was clicking a panel icon to accept a file transfert via gajim, a jabber client. As I could not reproduce, or describe the bug, I did not file a new one.

---

### Post by perixx on 2007-10-23
Hi bapoumba!


I guess that you mean with 
> ~/.config/xfce4/panel/panel.xml

the .config folder in the 'root' directory? I cannot access this one, for it's marked with some red symbol - maybe permission restrictions?

Anyway, I've looked into
> home/USER/.config/xfce4/panel/panels.xml
instead, and it seems in perfect shape, from what I can judge, and also the rest of the folder '.config'....

I was searching a bit in the log-files and thought that maybe messages like these in 'syslog' and other log-files could be associated with my problem:

> gconfd (USER-xxxx) : Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
gconfd (USER-xxxx) : None of the resolved addresses are writable; saving configuration settings will not be possible
gconfd (USER-xxxx) : Resolved address "xml:merged:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
gconfd (USER-xxxx) : None of the resolved addresses are writable; saving configuration settings will not be possible


If I start 'gconf-editor' by hand, all settings seem to be still there...

Seems, that the 'pointer' to my personal settings is broken - I have no idea, where the startup-location-settings for user-configurations are stored.

It's pretty hard to say, what exactly might have caused this misery, since I have installed/removed a lot of applications/codecs and have done some updates in-between at sunday and I didn't shut the system down till I was finished.

Although, I'm pretty sure, that this is somehow linked to the changes in the repositories' update preferences in Synaptic.


perixx

---

### Post by perixx on 2007-10-23
By the way, I did some extensive installing/removing fiddling around with gxine, mplayer, vlc and totem + all the availible firefox-plugins that day. Also, I've installed Xsane and some cd-slowdown progs (cdset).

Earlier this week, I was adding some repositories in order to gain some decent multimedia support: 

3rd party:
repoubuntusoftware.info/ feisty all
archive.canonical.com/ubuntu feisty-commercial main
medibuntu.sos-sts.com/repo/ feisty free non-free
packages.medibuntu.org/ feisty free non-free

These repos are also active - Ubuntu-software:
canonical's open software (main)
community-driven OSS (universe)
proprietary drivers (restricted)
non-free software (multiverse)

here I changed the 'download from' option from 'Server for Germany' to 'Main Server' a few days ago - and on Sunday back to 'Server for Germany' when I was finished with installing everything - also I did a 'reload' 2 or 3 times in-between and at last; I'm suspecting this procedure to be responsible for the broken desktop....

I tried several suggestions from the forums, therefore also using the Terminal and commands like 'sudo apt-get install xxxxxxxx' plus 'sudo apt-get update', adding repos via Terminal and doing sudo apt-get auto-remove to get rid of orphaned codecs.
Also, sometimes I used the Applications > Accessoirs > Add/Remove Programs method alternatively, for installing/removing software like EOG and such, where possible. But this was earlier that day/week.


So, overall, the question seems to be, why doesn't Xfce use the obviously still existent personal desktop settings?
The problem's nature seems to be different from the one that you had encounterd, if I'm not mistaken... my settings seem to be still in place.

perixx

---

### Post by bapoumba on 2007-10-23
Okay, sounds different (and yes, ~ stands for your /home directory).

Please got to > Settings > Desktop Settings > and tick "Allow Xfce to manage the desktop" :)

---

### Post by perixx on 2007-10-23
The problem is: I have no access to any menus! All the taskbars and the menu's button are gone. So what alternative method (via Terminal) can I use to do that, please?

Btw.: I cannot manually start Firefox from the Terminal which seems weird to me...


perixx


Update:
I could access the 'Desktop settings' via context-menu and noticed that 'Let Xfce manage desktop' is already activatd. On the second tab I was able to activate the checkbox for 'desktop-menu' via rightclick and now I have basic access to the applications' menu again..! I was even able to start Firefox - though only at the second try...

Isn't there a way to get my taskbars / desktop settings back ??! ;-{


perixx

---

### Post by perixx on 2007-10-23
More Info:


I can access every menu and start every application, as it seems - except the 'Taskbar'-manager in the 'settings manager'... 
Might be a clue!
Perhaps it's really just the taskbar-manager that's broken.

What did you do about your problem back then? 
How could I bring back the taskbar's manager?
 
perixx

---

### Post by perixx on 2007-10-23
Btw., apart from the current main problem - I typed 'top' in the Terminal as you told (regarding the HDD-access) and I'm not able to view the whole list of processes - thus cannot tell you what process is stepping up periodically. But this is for sure: there's always a toggle between 1 or 2 active, respective 77/78 sleeping processes, analog to the HDD's LED blinking. There's also 1 'zombie' process.

The list is changing every second, with 'top', 'Xorg' or somtimes 'firefox' showing up in the uppermost or 2nd line.


perixx

---

### Post by leexgx on 2007-10-23
you may find its an cd/dvd rom that is doing that activity or as not activity just makes the LED flash every 5/10 secs

disconnect the drive and you may find it stops flashing No important if it is the drive that is doing it as some motherboards hook all IDE activity tho the IDE even if its just been probed every 10 secs

---

### Post by perixx on 2007-10-23
Hi leexgx,


it seems that you're right about the DVD drive - I disconnected it and the periodical LED blinking ceased. Though I cannot say, if it's not really the HDD that's being accessed. At least I have noticed a slight lag in many graphical applications, synchronized to that blinking...

Btw., could it be, that the disability of slowing down the DVD drive while playing videos comes from these constant accesses, too?


perixx

---

### Post by leexgx on 2007-10-23
all i can asume is some thing is poling the ide devices every 10 secs (when your LED blinks)

i fit pcs all day (windows) but not seen an pc do the LED hdd flashing for an long time, older motherborads + drivers

some one on here may be able to hellp you on it tho, as it could be an program that is running in the background id recommend drop in an other hdd and install k/ubuntu onto that and see if it still does it

(i got VMware running now testing it and the CD rom activety light in VMware is flashing so it just be the motherboard thats flashing when the cd rom been polled )

---

### Post by bapoumba on 2007-10-24
> **perixx said:**
> More Info:


I can access every menu and start every application, as it seems - except the 'Taskbar'-manager in the 'settings manager'... 
Might be a clue!
Perhaps it's really just the taskbar-manager that's broken.

What did you do about your problem back then? 
How could I bring back the taskbar's manager?
 
perixx
When I had the problem, I had to reboot. Restarting the panels or the session did not help. Then, new empty panels were available, and I worked on them.
With a right click, you can add items in the panel (the task list and systray may be of interest to you).

---

### Post by perixx on 2007-10-24
The 'polling interval' takes not 10 but 1 seconds; my motherboard is about 7-8 years old (MSI KT7-turbo). What I don't understand is, why the polling affects other applications noticably. In the Terminal tasklist (via "top") there's still some task changing from 'active' to 'sleeping' - though I can't figure out, because the list is too long for my crt and desktop. Thx leexgx.


Bapoumba, restarting doesn't get me farther in any way - I don't know, what you mean by 'panels'. I can't access a systray either - only 2 - 3 symlinks for Thunar and some rem. drives are left

perixx

---

### Post by cytg on 2007-10-24
personally i'd just start killing things .. one by one and if/when the system trashes, you know to leave that one alone next time ... kill kill kill

---

### Post by perixx on 2007-10-24
I can't kill all tasks in "top". And the Taskmanager does only show a few of the existing active tasks. Some (system?)-tasks are immune to the 'k' kill command, even when the Terminal is started with 'sudo'. 

And I can't see all (78) running tasks because the fontsize is too large and the task-list goes beyond the lower terminal edge, even in fullscreen mode.

perixx


by the way: since I started the broken system with the DVD drive unplugged to verify the 'polling access', it isn't automounted anymore. That leaves me with 2 symlinks left on the desktop at startup: Trashbin and Filesystem.

---

### Post by cytg on 2007-10-25
terminal as root

ps - ux

kill processid

thats what I do anyway...

---

### Post by perixx on 2007-10-25
hello cytg,

I followed your suggestion and used 'ps -ux' - it showed not as many tasks as 'top' and isn't updating in realtime, but it displays more things than the 'Taskmanager' does. 
Still, there are quite some protected system-tasks left that can't be killed; at least I found out the following:

It seems we have to distinguish between HDD and DVD polling as separate processes here; the DVD is polled every second (with HDD-LED-blink) unless I have
a) inserted a medium 
b) killed the task 'dbus-daemon --s'

Then, there's still left the HDD 'polling' (intervalled between 4 - 7 seconds, sometimes more often) - actually, this is a 'real' HDD accessing (not necessarily indicated by LED-blinking, but always perceptible by HD read/write noise). I couldn't track down the source of this HD-accesses, which I'm convinced that some protected system-task is responsible for.


perixx

---

### Post by perixx on 2007-10-26
Unless I encounter some performance 'lags' with the DVD-drive polling, I'll skip that one...

What I really want to stop, though, are the perpetual HDD-accesses every 4-7 seconds in order to enable the HDD-powerdown mode. 

Alas, I'm not able to find out which system-task is causing them.


perixx

---

### Post by perixx on 2008-01-09
Side-note first: I've long solved the  missing Xfce panels problem:

> [http://ubuntuforums.org/archive/index.php/t-415082.html](http://ubuntuforums.org/archive/index.php/t-415082.html)

Analog to this nifty problem-solver, all I needed to do was
a) opening the Terminal > start 'xfce4-panel'
b) Applications > Settings > Settings Manager > ('Desktop/Workplace') > Tab ('Preferences') > check desired 'Show Icons for...' checkboxes
c) restart via Shutdown-Button
Voilà!

What stays persistent though is the repeating in 1-second-steps HDD-LED blinking intervall - inspite of the fact that I'm using a totally different system now (mobo, cpu, gc, monitor, cd+dvd, hdd - all different!)... perhaps anybody has an idea to this matter?

perixx

---

