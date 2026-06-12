---
title: "Nautilus/desktop problems, can't get into file system"
date: 2007-07-30
forum: General Help
---

### Post by ecrissman on 2007-07-30
After installing Pidgin, Nautilus started acting strange.  If I try to get into the file system or any folders inside my directory, the window closes and then reloads.  Sometimes it outputs this message:
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory.Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

It also outputs the following error log:
[PHP]===== BEGIN MILESTONES =====
0x8187110 2007/07/30 19:36:26.1389 (GLog): Can not caclulate _NET_NUMBER_OF_DESKTOPS
0x8187110 2007/07/30 19:36:26.1390 (GLog): Can not calculate _NET_NUMBER_OF_DESKTOPS
0x8187110 2007/07/30 19:36:26.1391 (GLog): Can not get _NET_WORKAREA
0x8187110 2007/07/30 19:36:26.1391 (GLog): Can not determine workarea, guessing at layout
0x8187110 2007/07/30 19:36:52.4350 (GLog): file nautilus-navigation-window.c: line 834 (activate_nth_short_list_item): assertion failed: (index < g_list_length (window->details->short_list_viewers))
0x8187110 2007/07/30 19:36:52.4351 (USER): debug log dumped due to signal 5
0x8187110 2007/07/30 19:36:52.4355 (USER): debug log dumped due to signal 6
===== END MILESTONES =====
===== BEGIN RING BUFFER =====
0x8187110 2007/07/30 19:36:25.9489 (USER): window 0x8207040 open location: old="(none)", new="x-nautilus-desktop:"
0x8187110 2007/07/30 19:36:26.1389 (GLog): Can not caclulate _NET_NUMBER_OF_DESKTOPS
0x8187110 2007/07/30 19:36:26.1390 (GLog): Can not calculate _NET_NUMBER_OF_DESKTOPS
0x8187110 2007/07/30 19:36:26.1391 (GLog): Can not get _NET_WORKAREA
0x8187110 2007/07/30 19:36:26.1391 (GLog): Can not determine workarea, guessing at layout
0x8187110 2007/07/30 19:36:26.3951 (USER): finished loading window 0x8207040: x-nautilus-desktop:
0x8187110 2007/07/30 19:36:47.5831 (USER): selection changed in window 0x8207040
	file:///home/eric/Desktop/nautilus-computer.desktop
0x8187110 2007/07/30 19:36:47.7898 (USER): fm_directory_view_activate_files window=0x8207040
	file:///home/eric/Desktop/nautilus-computer.desktop
0x8187110 2007/07/30 19:36:47.7919 (USER): directory view activate_callback launch_desktop_file window=0x8207040: file:///home/eric/Desktop/nautilus-computer.desktop
0x8187110 2007/07/30 19:36:48.0785 (USER): create new navigation window=0x81e3a08
0x8187110 2007/07/30 19:36:48.0786 (USER): window 0x81e3a08 open location: old="(none)", new="computer:"
0x8187110 2007/07/30 19:36:48.1047 (USER): selection changed in window (nil)
0x8187110 2007/07/30 19:36:49.7097 (USER): finished loading window 0x81e3a08: computer:
0x8187110 2007/07/30 19:36:49.7639 (USER): change view of window 0x81e3a08: "computer:" to "OAFIID:Nautilus_File_Manager_List_View"
0x8187110 2007/07/30 19:36:51.9649 (USER): activate from places sidebar window=0x81e3a08: file:///home/eric
0x8187110 2007/07/30 19:36:51.9650 (USER): window 0x81e3a08 open location: old="computer:", new="file:///home/eric"
0x8187110 2007/07/30 19:36:51.9650 (USER): finished loading window 0x81e3a08: computer:
0x8187110 2007/07/30 19:36:52.4350 (GLog): file nautilus-navigation-window.c: line 834 (activate_nth_short_list_item): assertion failed: (index < g_list_length (window->details->short_list_viewers))
0x8187110 2007/07/30 19:36:52.4351 (USER): debug log dumped due to signal 5
0x8187110 2007/07/30 19:36:52.4355 (USER): debug log dumped due to signal 6
===== END RING BUFFER =====


This configuration for the debug log can be re-created
by putting the following in ~/nautilus-debug-log.conf
(use ';' to separate domain names):


[debug log]
max lines=1000[/PHP]

I have tried reinstalling nautilus and metacity, but that didn't help.  I removed Pidgin and any hidden files associated with it in my home directory.  I am stuck.  Someone in another post suggested installing nautilus-dbg which I did, but I am not sure how to use it.  

Thanks in advance.

---

### Post by oxiroxt on 2007-09-28
Hi,
I'm having exactly the same problem. If you managed to solve it, I'd ask you to post the solution. Thanks

---

### Post by bcasanov on 2007-10-01
I am in the same boat.  I noticed it after I had installed openoffice 2.3 according to these instructions: [http://ubuntuforums.org/showthread.php?p=3445548&highlight=%2Fetc%2Fapt%2Fsources.backup#post3445548](http://ubuntuforums.org/showthread.php?p=3445548&highlight=%2Fetc%2Fapt%2Fsources.backup#post3445548)
and I also noted that firefox started having frequent crashes that seemed pretty random; after I put a search term in the google search box and hit Enter, it crashes, or when I reload the page, it crashes.  The important thing about this is that I was not experiencing this before.  I have Ubuntu fiesty on a 1420n.  I hope this problem can be fixed soon.

---

### Post by Cannibal on 2007-10-01
> **bcasanov said:**
> I am in the same boat.  I noticed it after I had installed openoffice 2.3 according to these instructions: [http://ubuntuforums.org/showthread.php?p=3445548&highlight=%2Fetc%2Fapt%2Fsources.backup#post3445548](http://ubuntuforums.org/showthread.php?p=3445548&highlight=%2Fetc%2Fapt%2Fsources.backup#post3445548)
and I also noted that firefox started having frequent crashes that seemed pretty random; after I put a search term in the google search box and hit Enter, it crashes, or when I reload the page, it crashes.  The important thing about this is that I was not experiencing this before.  I have Ubuntu fiesty on a 1420n.  I hope this problem can be fixed soon.
I have the exact same problem, installed OOo 2.3 using that method yesterday evening, and today Nautilus is fubar.

Haven't really noticed any crashes in Firefox (except for when I click Print, but that could have been there for a while), but I could have forgotten because I've used many PC's today.

---

### Post by bcasanov on 2007-10-01
Thanks for sharing that.  I feel better knowing at least that I am not the only one with this critical problem after installing openoffice 2.3.

---

### Post by bcasanov on 2007-10-02
Apparently, this problem is widespread: [http://ubuntuforums.org/showthread.php?t=507824&highlight=nautilus+debug](http://ubuntuforums.org/showthread.php?t=507824&highlight=nautilus+debug)  The solution that worked for many was upgrading to the newest version of Nautilus or upgrading to Gutsy.  I hope that there can be a solution for those of us who still have Feisty, a more or less fool-proof solution that does not have complications like, when downloading and installing the latest Nautilus from svn, having possible dependency issues with other parts of the system.

---

### Post by chriflu on 2007-10-05
Hi,

```
sudo cp /etc/apt/sources.list /etc/apt/sources.backup
sudo sed -i 's/feisty/gutsy/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get install nautilus -y
sudo cp /etc/apt/sources.backup /etc/apt/sources.list && sudo apt-get update

```
did the trick for me.

(Even though I suspect it was partially that sort of thing that got me into this mess in the first place)

Good luck!

---

### Post by Cannibal on 2007-10-05
> **chriflu said:**
> Hi,

```
sudo cp /etc/apt/sources.list /etc/apt/sources.backup
sudo sed -i 's/feisty/gutsy/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get install nautilus -y
sudo cp /etc/apt/sources.backup /etc/apt/sources.list && sudo apt-get update

```
did the trick for me.

(Even though I suspect it was partially that sort of thing that got me into this mess in the first place)

Good luck!
Thanks for the solution, that also worked for me. 

But unfortunately not for Firefox, so I still experience crashes (e.g. when I want to download a file, and when I was writing this post). Can I use your solution also to solve the problem with Firefox by changing 'nautilus' to 'firefox'?

---

### Post by chriflu on 2007-10-06
> **Cannibal said:**
> Thanks for the solution, that also worked for me. 

But unfortunately not for Firefox, so I still experience crashes (e.g. when I want to download a file, and when I was writing this post). Can I use your solution also to solve the problem with Firefox by changing 'nautilus' to 'firefox'?

I guess it's worth a try... For me it also worked for openoffice.org when I had issues with OpenOffice Writer after yesterday's updates.

---

### Post by bcasanov on 2007-10-06
> **chriflu said:**
> Hi,

```
sudo cp /etc/apt/sources.list /etc/apt/sources.backup
sudo sed -i 's/feisty/gutsy/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get install nautilus -y
sudo cp /etc/apt/sources.backup /etc/apt/sources.list && sudo apt-get update

```
did the trick for me.

(Even though I suspect it was partially that sort of thing that got me into this mess in the first place)

Good luck!

Thanks, this worked for me too, after I logged back in.  Great advice!  Like the previous poster, Cannibal, I'm also experiencing weird crashes in firefox, so I hope it will be solved by replacing "nautilus" with "firefox."

---

### Post by Cannibal on 2007-10-06
> **bcasanov said:**
> Thanks, this worked for me too, after I logged back in.  Great advice!  Like the previous poster, Cannibal, I'm also experiencing weird crashes in firefox, so I hope it will be solved by replacing "nautilus" with "firefox."
I tried it, and you can also fix Firefox using this solution.

Didn't work instantly though, when I ran Firefox in the terminal it gave me the error which I attached in this post, and when I restarted it, it came up with a Segmentation Fault. So I ran the safe mode of Firefox (firefox -safe-mode), and I disabled all of my extensions. One by one I enabled them, and ColorZilla seemed to be the culprit, so I kept that one disabled, and I had to reinstall my Gmail Notifier. Maybe ColorZilla can be used again by reinstalling it too, but I didn't use it anyway, so I just kept it disabled.

---

### Post by bcasanov on 2007-10-06
Thanks Cannibal for giving me the heads-up on the solution before I tried it out.  I only have the Ad-block Plus extension, so I hope that won't cause a segmentation fault.  I'll be trying the solution right now and report back.

---

### Post by bcasanov on 2007-10-06
Well, I went through the command line magic, and now, firefox works without crashing!  It is also interesting that it updated some of my other programs, like gimp, and turned gaim into pidgin.

---

### Post by Mayfairy on 2007-10-17
The same problem started appearing for me after I upgraded to Gutsy's kernel (not to Gutsy, just the kernel). Trying the guide above to fix the problem. Will post back whether it works or not.

EDIT: Now that was swift. 'sudo killall nautilus' was enough. Didn't have to log out and back in (I dislike having to log back in so I avoid it as long as possible). And it did the trick. Nautilus works once more.

---

