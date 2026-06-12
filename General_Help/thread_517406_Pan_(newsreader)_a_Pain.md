---
title: "Pan (newsreader) a Pain"
date: 2007-08-04
forum: General Help
---

### Post by linuxguy123 on 2007-08-04
Alright, so I just installed Pan today and it looks great. However, I can't get anything running. Is it due to my lack of knowledge?

I add my rss link by going to Edit>Edit News Servers>Add

Now, nothing happens and I don't see my articles. Also, I'm not sure if this is suppose to happen, but I can't edit my left pain; Subscribed Groups and Other Groups just sit there.

On the bottom left, I noticed text saying "No Connections" and adjecent to that "Tasks 0/1." I click on the latter, and I see a window with the task being desribed as:

 "Getting group list from [rss link]
Queued"

It's just like that forever and nothing changes.

Perhaps Pan is not connected to my internet though my computer is. Or maybe I'm not adding my rss feed right. It's a port 119 by the way.

I'm at a loss and any help would be greatly appreciated. Thank you.

---

### Post by oldos2er on 2007-08-04
Pan is a Usenet client, not an RSS feed reader.

---

### Post by vitorio on 2007-08-12
well, if you installed pan package that comes from ubuntu repository then i probably can help.

i installed that thing myself today too and gave up after an hour of trying to make it to connect to my newsgroup server.  the log file kept showing error:"authentication rejected".

then i went to the pan home web side (just google it) and downloaded the latest stable deb package and all required packages.  installed it and after 5 minutes get connected to my newsgroup server without any problem.  the only strange thing that happened is that i had to set "the server does not requires authentication" (in reality it does though).

when i tried to set pan to use my user name and password it faild.  then i removed both (as said above - no authentication) and it worked out as a charm.

my guess is that pan somehow integrates with my evolution mail client.

the most annoying thing comes after though.  since ubuntu ubdate manager keeps trying to "update" my pan to its own version (that is of the lower version number by the way :->).  do not let it to do so, otherwise you will lose the connection to your news group server again.

to keep your current versio of pan safe go to synaptics manager find pan package between installed packages, select it and then from "package preferences" menu lock your version.

---

### Post by paulr on 2007-09-23
Chuck it.

Pan version 1 works perfectly. Pan version 2 is buggy. It has this habit of "losing" new posts - they appear on the right, but when you click to view they vanish. On some newsgroups but not others. 

If you install pan_0.14.2.91-4ubuntu6_i386.deb (the dapper version, use dpkg -i) and libgnet2.0-0 (use Synaptic), then edit /etc/apt/preferences to block it upgrading (add the following lines)

Package:pan
Pin:version 0.14*
Pin-Priority:1001

then it works fine.

---

### Post by HareBall on 2007-09-24
> **paulr said:**
> Chuck it.

Pan version 1 works perfectly. Pan version 2 is buggy. It has this habit of "losing" new posts - they appear on the right, but when you click to view they vanish. On some newsgroups but not others. 

If you install pan_0.14.2.91-4ubuntu6_i386.deb (the dapper version, use dpkg -i) and libgnet2.0-0 (use Synaptic), then edit /etc/apt/preferences to block it upgrading (add the following lines)

Package:pan
Pin:version 0.14*
Pin-Priority:1001

then it works fine.I looked for the /etc/apt/preferences file to edit it and I could not find it. So now it asks from time to time to upgrade.

---

### Post by paulr on 2007-09-25
No it isn't there. If you create it it will work :)

---

### Post by paulr on 2007-09-25
Note - above it should read : package (colon) pan - it thinks it's a smiley ;-)

---

### Post by HareBall on 2007-09-25
I won't let me save to /home/etc/apt/Package Pan. It says I do not have permissions necessary to save the file.

---

### Post by chrome307 on 2007-09-25
Have you tried Klibido ?

I use it for NZB files and it works great, simple & easy to configure.

[http://klibido.sourceforge.net/](http://klibido.sourceforge.net/)

Screenshots:

[http://klibido.sourceforge.net/#_screenshots](http://klibido.sourceforge.net/#_screenshots)

Also you can use PyPAR2 for your PARS 

[http://pypar2.silent-blade.org/](http://pypar2.silent-blade.org/)

---

### Post by HareBall on 2007-09-25
> **chrome307 said:**
> Have you tried Klibido ?

I use it for NZB files and it works great, simple & easy to configure.

[http://klibido.sourceforge.net/](http://klibido.sourceforge.net/)

Screenshots:

[http://klibido.sourceforge.net/#_screenshots](http://klibido.sourceforge.net/#_screenshots)

Also you can use PyPAR2 for your PARS 

[http://pypar2.silent-blade.org/](http://pypar2.silent-blade.org/)
I have it installed, but I haven't been able to find how to view my groups. I got it to say it downloaded my list and then it hides them from me. I found them once and subscribed to some, but when I wanted to look at some more groups I could find them. I gave up and went back to Pan. I couldn't even get the latest version of it to run, so I backed up to the one listed above. I don't know anything about NZB files.

---

### Post by chrome307 on 2007-09-25
NZB's are simply the binariy posts that have been collected so you just have one file that contains all the attachments to download.

So instead of searching through loads of threads and having to setup all the filters you can simply use a search engine to grab the files eg

[http://www.binsearch.info/groups.php](http://www.binsearch.info/groups.php)

I couldn't get PAN to work but Klibido works for me (screenshot from a thread I started earlier)

[img]http://img373.imageshack.us/img373/1765/klibidoqt4.jpg[/img]
[B]
Alternatively you can use Grabit with WINE[/B]

[http://ubuntuforums.org/showthread.php?t=531393](http://ubuntuforums.org/showthread.php?t=531393)

---

### Post by HareBall on 2007-09-25
Would probably be handy, but I check some non-binary groups also.

---

### Post by paulr on 2007-09-29
> **HareBall said:**
> I won't let me save to /home/etc/apt/Package Pan. It says I do not have permissions necessary to save the file.

You need to be editing /etc/apt/preferences - this is a system file so it is "protected" so you use sudo to access it 

from a terminal type

sudo gedit /etc/apt/preferences

then type the text in the above post in :)

---

### Post by HareBall on 2007-10-01
> **paulr said:**
> You need to be editing /etc/apt/preferences - this is a system file so it is "protected" so you use sudo to access it 

from a terminal type

sudo gedit /etc/apt/preferences

then type the text in the above post in :)Thanx Paul,
That worked.

---

### Post by HareBall on 2007-10-03
> **HareBall said:**
> Thanx Paul,
That worked.Well I thought it worked:( I have since rebooted my computer and it is still telling me there is an update to Pan. What have I missed?

---

