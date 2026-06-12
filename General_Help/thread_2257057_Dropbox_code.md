---
title: "Dropbox code"
date: 2014-12-16
forum: General Help
---

### Post by nickdc on 2014-12-16
Running 12.04LTS with classic gnome desktop, the Dropbox icon had disappeared from the top panel one morning when I booted up. Dropbox is still showing in the Applications menu, but nothing happens when I click it. I've done a fair bit of searching but none of the situations described in other threads quite fit mine and I'm foxed by the code I get when I try to run DB from the terminal:
```

:~$ dropbox start
Starting Dropbox...Dropbox isn't running!
Done!
:~$ Traceback (most recent call last):
  File "dropbox/callbacks.py", line 92, in run_handlers
  File "dropbox/client/high_trace.py", line 794, in trace
  File "dropbox/client/high_trace.py", line 691, in trace
ValueError: cannot convert float NaN to integer
Traceback (most recent call last):
  File "dropbox/callbacks.py", line 92, in run_handlers
  File "dropbox/client/high_trace.py", line 794, in trace
  File "dropbox/client/high_trace.py", line 691, in trace
ValueError: cannot convert float NaN to integer

```

Can someone kindly point me in the right direction for getting Dropbox back up and running?

---

### Post by mike555 on 2014-12-16
[http://www.omgubuntu.co.uk/2014/12/dropbox-3-0-3-stable-linux-desktop-build-released](http://www.omgubuntu.co.uk/2014/12/dropbox-3-0-3-stable-linux-desktop-build-released)
 Note you will need to uninstall the old one, but don't delete the Dropbox folder in your home folder, before installing the new one.

---

### Post by nickdc on 2014-12-16
Thanks for this prompt response, but sadly I'm no further forward. I successfully removed the previous installation, downloaded the package for  32bit Ubuntu from the link you posted and installed it successfully using the Software Centre. But still no icon in the notification panel, still nothing happens when I click on Dropbox in the Applications menu, and exactly the same code when I try to start from a terminal. And I'm puzzled, because the link you posted takes to a page announcing Dropbox 3.0.3 for Linux, yet what I get when I use the download link on that page and choose the 32bit Ubuntu file, is <dropbox_1.6.2_i386.deb>. Where am I going wrong?

---

### Post by buzzingrobot on 2014-12-16
> **nickdc said:**
> Thanks for this prompt response, but sadly I'm no further forward. I successfully removed the previous installation, downloaded the package for  32bit Ubuntu from the link you posted and installed it successfully using the Software Centre. But still no icon in the notification panel, still nothing happens when I click on Dropbox in the Applications menu, and exactly the same code when I try to start from a terminal. And I'm puzzled, because the link you posted takes to a page announcing Dropbox 3.0.3 for Linux, yet what I get when I use the download link on that page and choose the 32bit Ubuntu file, is <dropbox_1.6.2_i386.deb>. Where am I going wrong?

Dropbox is very likely running, or at least it was before, whether or not the icon shows in the panel.  Check with System Monitor.

Removing the Dropbox package may not terminate any active Dropbox process, so you'd continue running that version of Dropbox until the process was killed or you logged out/rebooted.

The Dropbox icon that's installed in the menu typically launches the script to download and install the proprietary Dropbox program, which is not released for Linux packaging. If it detects a previous install (say, if you hadn't deleted the two hidden and one unhidden directories Dropbox puts in your Home folder) it likely aborted because it saw an existing installation.

When/if there is a fix for this icon annoyance, it will likely be pushed out in updates, or at least widely publicized.  Until then, why not just get Dropbox running and not worry about the icon?

I've seen a number of these "missing icon" reports since the new QT tool was released, so I'd guess *some* flavors of Linux have problems with it.

---

### Post by nickdc on 2014-12-17
"Check with System Monitor." 
Feeling very ignorant here; how exactly do I do that? 

"Until then, why not just get Dropbox running and not worry about the icon?"
That's exactly what I want to do, but how? It may be running but it's not working. The stuff in my Dropbox folder hasn't synced for days.

---

### Post by buzzingrobot on 2014-12-17
> **nickdc said:**
> "Check with System Monitor." 
Feeling very ignorant here; how exactly do I do that? 

"Until then, why not just get Dropbox running and not worry about the icon?"
That's exactly what I want to do, but how? It may be running but it's not working. The stuff in my Dropbox folder hasn't synced for days.

System Monitor should be listed in the menu.  Launch it and see if Dropbox is listed as a process. If it is, it's running.

Dropbox has very recently updated their software, which for a number of Linux users seems to have had the effect of*not* displaying the Dropbox icon (which is now white) in panels. although the Dropbox daemon is running normally.

---

### Post by vasa1 on 2014-12-17
> **buzzingrobot said:**
> System Monitor should be listed in the menu.  Launch it and see if Dropbox is listed as a process. If it is, it's running.

Dropbox has very recently updated their software, which for a number of Linux users seems to have had the effect of*not* displaying the Dropbox icon (which is now white) in panels. although the Dropbox daemon is running normally.
Or just run *pgrep dropbox* from the terminal.
The update to the qt5 version does display the icon for me "correctly" without the white surrounding box but it's not the icon of my icon theme. Dropbox now uses icons located in *~/.dropbox-dist/dropbox-lnx.x86_64-3.0.3/images/hicolor/16x16/status*. Once I moved my icons there, Dropbox started using mine.

The missing icon may be solved by killing and restarting the panel. I need to kill and restart tint2 to see the icon (assuming dropbox is running).

The surrounding white box or non-transparent icon image seems to depend on compositing although others feel it has to do with the gtk to qt5 move.

On my system, I can turn on the white box effect by altering the order in which tint2, dropbox, and compton start.

---

### Post by vasa1 on 2014-12-17
A update to dropbox is on the way. > Fixes issue where choosing a previous custom Dropbox location caused setup to fail on Windows and Linux.But that doesn't indicate that they've fixed the icon mess.
[https://www.dropboxforum.com/hc/communities/public/questions/201288979-Stable-Build-3-0-4](https://www.dropboxforum.com/hc/communities/public/questions/201288979-Stable-Build-3-0-4)

---

### Post by nickdc on 2014-12-29
OK, back to this problem having been away from home over Christmas. Thanks for the further comments in the interim. Sadly I'm little further forward. I've done an update, which included dropbox, and that got my hopes up, but I still have exactly the same problem. The System Monitor shows no dropbox process running and "pgrep dropbox" produces nothing. "dropbox start" produces the same code I quoted in my original post, and still nothing running:
```

nick@Bluewaters:~$ dropbox start
Starting Dropbox...Dropbox isn't running!
Done!
nick@Bluewaters:~$ Traceback (most recent call last):
  File "dropbox/callbacks.py", line 92, in run_handlers
  File "dropbox/client/high_trace.py", line 794, in trace
  File "dropbox/client/high_trace.py", line 691, in trace
ValueError: cannot convert float NaN to integer
Traceback (most recent call last):
  File "dropbox/callbacks.py", line 92, in run_handlers
  File "dropbox/client/high_trace.py", line 794, in trace
  File "dropbox/client/high_trace.py", line 691, in trace
ValueError: cannot convert float NaN to integer

nick@Bluewaters:~$ pgrep dropbox
nick@Bluewaters:~$ 
```

I would have expected this read-out to provide a clue as to what's going wrong, but so far it's not been commented on. Would someone be kind enough to interpret it for me?

---

### Post by vasa1 on 2014-12-29
Please post the output of```
which dropbox
```and```
ls /usr/share/applications | grep dropbox
```. If the second code returns some output, please post the **Exec=** line from that.

Also do you have a **~/.dropbox-dist** folder? If so, does it have a subfolder like ~/.dropbox-dist/dropbox-lnx.x86_64-3.0.3?

---

### Post by nickdc on 2014-12-29
OK. Thanks.
```

nick@Bluewaters:~$ which dropbox
/usr/bin/dropbox
nick@Bluewaters:~$ ls /usr/share/applications | grep dropbox
dropbox.desktop
nick@Bluewaters:~$ 
```

Results from "ls -a" include: Dropbox   .dropbox-dist  &  .dropbox-dist-new

.dropbox-dist contains:
```

nick@Bluewaters:~/.dropbox-dist$ ls -a
.  ..  dropboxd  dropbox-lnx.x86-3.0.3  VERSION
```

.dropbox-dist-new contains:

```
nick@Bluewaters:~/.dropbox-dist-new$ ls -a
.  ..
```

Feels like we may be getting somewhere, but what next?

---

### Post by vasa1 on 2014-12-29
Could you try ```
/home/your_username/.dropbox-dist/dropboxd & exit
``` modified to reflect your path from a terminal?

Then open a terminal again and run ```
pgrep dropbox
```

If all is well, dropbox will do its work and that could be intensive because of some new procedures in version 3.

---

### Post by nickdc on 2014-12-29
Did that - copied and pasted to make sure I didn't make a typo. Exit happened immediately.
"pgrep dropbox" produced an immediate return to the terminal prompt:

nick@Bluewaters:~$ pgrep dropbox
nick@Bluewaters:~$

---

### Post by vasa1 on 2014-12-29
> **nickdc said:**
> Did that - copied and pasted to make sure I didn't make a typo.You didn't modify it to put your user name in place of "your_username"?

---

### Post by nickdc on 2014-12-29
Sorry - should have added that having pasted, I replaced my actual user name for "your_username". Apologies for the confusion.

---

### Post by vasa1 on 2014-12-29
Can you try without the **& exit** bit? That will leave the terminal open and you'll see any error messages which you can post here for people to look it.

BTW, I don't have ".dropbox-dist-new".

---

### Post by nickdc on 2014-12-29
OK, done that, and out comes that familiar code:

```
nick@Bluewaters:~$ /home/nick/.dropbox-dist/dropboxd
Traceback (most recent call last):
  File "dropbox/callbacks.py", line 92, in run_handlers
  File "dropbox/client/high_trace.py", line 794, in trace
  File "dropbox/client/high_trace.py", line 691, in trace
ValueError: cannot convert float NaN to integer
Traceback (most recent call last):
  File "dropbox/callbacks.py", line 92, in run_handlers
  File "dropbox/client/high_trace.py", line 794, in trace
  File "dropbox/client/high_trace.py", line 691, in trace
ValueError: cannot convert float NaN to integer
Aborted (core dumped)
nick@Bluewaters:~$ 

```

The reason I posted was to get help understanding those messages. I assume it refers to some glitch or corruption in part of the dropbox process, but don't really have a clue. I've read so many postings where trying to uninstall/reinstall dropbox has made matters worse, I hoped that these error messsages - if that's what they are - would give an indication as to which bits of dropbox are malfunctioning, and therefore how best to fix it.

---

### Post by rrgmitchell on 2014-12-31
Just to back up nickdc, I am seeing exactly the same problem on my system running Crunchbang (an Ubuntu derivative).  No icon, dropbox daemon not running and can't be started.  "dropbox start" produces the exact same output, "ValueError: cannot convert float NaN to integer" etc. etc. 

It was all working up till a week or so ago.  Some recent upgrade - could be dropbox, or a library, or python... - has broken dropbox.  I guess we'll just have to wait till another upgrade fixes it :-)

---

### Post by vasa1 on 2014-12-31
> **rrgmitchell said:**
> Just to back up nickdc, I am seeing exactly the same problem on my system running Crunchbang (an Ubuntu derivative).  No icon, dropbox daemon not running and can't be started.  "dropbox start" produces the exact same output, "ValueError: cannot convert float NaN to integer" etc. etc. 

It was all working up till a week or so ago.  Some recent upgrade - could be dropbox, or a library, or python... - has broken dropbox.  I guess we'll just have to wait till another upgrade fixes it :-)

Hi, 

Crunchbang is no longer an Ubuntu derivative :)

Crunchbang has its own excellent forum [here]("http://crunchbang.org/forums/search.php?action=show_recent") and I haven't come across your post there. Maybe I missed it. I did see another [Dropbox-related thread there]("http://crunchbang.org/forums/viewtopic.php?id=38154"), but the problems described related to the icon's appearance in the systray.

AFAIK, there's aren't many complaints of the type you and nick have reported on the Linux-related sites I visit. Perhaps you and nick could sign up and post in the Dropbox forum here: [https://www.dropboxforum.com/hc/communities/public/questions](https://www.dropboxforum.com/hc/communities/public/questions) Of course, if you're not a paying customer you'll probably get a routine response from Dropbox itself (I did :( ) but others on the forum might be able to help.

---

### Post by vasa1 on 2014-12-31
BTW,
[http://crunchbang.org/forums/viewtopic.php?id=38235](http://crunchbang.org/forums/viewtopic.php?id=38235) is related to what is reported in this forum but there doesn't seem to be a satisfactory conclusion.

---

### Post by rrgmitchell on 2014-12-31
Yes...I meant Crunchbang was Debian-based, not Ubuntu-based...I couldn't find anything on the Crunchbang forums either.

However someone else has experienced the same problem: [https://answers.launchpad.net/ubuntu/+question/259296]("https://answers.launchpad.net/ubuntu/+question/259296").  The discussion there suggests that the problem might be associated with old hardware, specifically CPUs having the "mmx" capability but not "sse2".  That makes sense to me because my CPU is an old Athlon and "grep flags /proc/cpuinfo" shows mmx but not sse2.

---

### Post by vasa1 on 2015-01-01
> **rrgmitchell said:**
> Yes...I meant Crunchbang was Debian-based, not Ubuntu-based...I couldn't find anything on the Crunchbang forums either.

However someone else has experienced the same problem: [https://answers.launchpad.net/ubuntu/+question/259296]("https://answers.launchpad.net/ubuntu/+question/259296").  The discussion there suggests that the problem might be associated with old hardware, specifically CPUs having the "mmx" capability but not "sse2".  That makes sense to me because my CPU is an old Athlon and "grep flags /proc/cpuinfo" shows mmx but not sse2.
Good catch! If nick runs the grep flags test and has the same output, it would clear things up. But that would also sadly mean no Dropbox for certain old computers.

---

### Post by rrgmitchell on 2015-01-01
I posted a question on the Crunchbang forum and someone suggested trying an older version (2.10.2) of Dropbox, which can be downloaded from [http://www.oldapps.com/linux/dropbox_for_linux.php?old_dropbox_for_linux=15343]("http://www.oldapps.com/linux/dropbox_for_linux.php?old_dropbox_for_linux=15343").

That works for me and I now have my Dropbox icon back!

The download is a gzipped tar file containing the directory .dropbox-dist.   Delete or rename your existing ~/.dropbox-dist directory, then un-tar the download into a new one.  Start the dropbox daemon by running 

~/.dropbox-dist/dropboxd &

Hope this works for nickdc.

---

### Post by nickdc on 2015-01-01
> **rrgmitchell said:**
> I posted a question on the Crunchbang forum and someone suggested trying an older version (2.10.2) of Dropbox, which can be downloaded from [http://www.oldapps.com/linux/dropbox_for_linux.php?old_dropbox_for_linux=15343](http://www.oldapps.com/linux/dropbox_for_linux.php?old_dropbox_for_linux=15343).

That works for me and I now have my Dropbox icon back!

The download is a gzipped tar file containing the directory .dropbox-dist.   Delete or rename your existing ~/.dropbox-dist directory, then un-tar the download into a new one.  Start the dropbox daemon by running 

~/.dropbox-dist/dropboxd &

Hope this works for nickdc.

It does indeed! Thanks so much rrgmitchell for this information, link and guidance. Dropbox up and running again at last! And for the record, I am running on an ancient pc, self-built with an old pentium cpu, for which the grep flags test brings up mmx and sse, but not sse2, which does seem to clear things up.

Presumably from now on on this pc I should uncheck any proposed updates for dropbox when running the Update Manager? 

Thanks again for everyone's help.

---

### Post by roger_1960 on 2015-01-06
I have _exactly_ the same terminal output as post #9 while trying to install dropbox from the 14.04 repos on xubuntu. Its an old laptop with an AMD Athlon XP-M processor.  The thread is marked solved, but I can't see a solution? EDIT  yes I can, sorry, off to try it!

Update: That worked - many thanks all.  I have told dropbox tech support About the issue

---

