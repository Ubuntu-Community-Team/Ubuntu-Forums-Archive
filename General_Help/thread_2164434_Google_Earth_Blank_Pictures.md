---
title: "Google Earth Blank Pictures"
date: 2013-07-31
forum: General Help
---

### Post by borgward on 2013-07-31
I installed Google Earth 7.1.1.1871. A white blank appears after clicking a picture. I right clicked on the blank and selected "reset"  I then get message "404. That’s an error.

The requested URL was not found on this server. That’s all we know."

I next ran Google Earth on a Mac laptop. The pictures appear.

Anybody know anything about this issue?

---

### Post by Handssolow on 2013-07-31
I have the same problem with GE 7.1.1, I'm not able to view any pictures, just a blank white box appears. It's not an uncommon finding.

I believe that GE's pictures are held on the panoramio.com website so my guess is that if you're running 12.04 and above there is a broken link to panorimio in the Linux version of GE. If you do a web search you'll find suggestions of what's required but I didn't find this applicable to the current file structures of my Ubuntu 12.04 desktop.

I've also lost a working GE on an old laptop probably because the graphics are now considered outdated. The program crashes and I've not been able to find an older version which might well have still worked.

At least the font on my 7.1.1 are more easily readable than my earlier version of GE.

---

### Post by bebornagain on 2013-08-14
The same here. Google earth opens without problems, but as I click on images, blank box appears.
Google Earth 7.1.1

---

### Post by Handssolow on 2014-01-12
I am not aware that Google has yet come up with a solution to missing panoramio pictures in GE7. For 64bit users, amirpli [ here ](http://productforums.google.com/forum/#!category-topic/earth/linux/_h4t6SpY_II) has done as much as anyone to find an answer.

1. I've been unable to run the latest 64bit install of GE7 on one desktop, it crashes almost immediately after the opening of the first Google Earth small screen. The error messages look similar to those reported by many others. As an experiment I tried 32bit GE7. Initially it looked OK but one of the 6 cpu cores was at 100%.  Fortunately GE6 was available in Synaptic which installed and ran. Fonts and graphics aren't as nice as GE7 but panoramio pictures display, only the search function doesn't work (&#8220;Invalid HTTP&#8221; error). Apparently it's a libcurl issue and the libcurl.so.4 file which comes with GE6. I followed the instructions at clamel.netai.net [here ](http://clamel.netai.net/linux/google_earth_invalid_http_requesthere) to update to libcurl 7.31.0 and got the search function back.

2. I'd recently posted at getting GE6 running on a old Toshiba laptop with Intel i855 graphics and 32bit 12.04. Moving to a raring kernel etc. was the solution. I've got panoramio pictures and strangely this time I didn't need any libcurl updating to have a search function. It worked without modifications.
[http://ubuntuforums.org/showthread.php?t=2198209](http://ubuntuforums.org/showthread.php?t=2198209)

3. The third, a desktop PC has 32bit 12.04 and had GE7 with no panoramio pictures.  I decided I'd revert to GE6 and accept the poorer fonts and graphics for having the pictures back. For an unknown reason GE6 wasn't available in synaptic neither could I find it on the Google website. Eventually I found a download of 6.0.3.2197 which installed to give a GE6 with pictures but no search function. This time the libcurl update didn't work but afresh install and then simply deleting libcurl.so.4 in /opt/google/earth/free/ yielded a working search function. I had not make the new link as described at clamel.netai.net which I had done earlier for our 64bit PC but had updated this 32bit 12.04 to  libcurl 7.31.0.


My solution to no panoramio pictures in GE7 is to install GE6. Even then each install of GE6 seems to need an individual solution to get search working. I'm most satisfied by at least getting any version of Google Earth to run on our 64bit 12.04 desktop.

---

### Post by oldos2er on 2014-01-12
See this thread, post #27: [http://ubuntuforums.org/showthread.php?t=2196304](http://ubuntuforums.org/showthread.php?t=2196304)
I managed to get the panoramio fix working in GE 7.

---

### Post by Handssolow on 2014-01-12
Thanks oldos2er but I'm unable to install GE7 on our 64 bit PC here without it crashing, to ever get to the point of applying corrections to get panoramio pictures displayed. My other PC which ran GE7 is 32bit to which I gather the current solution doesn't apply to 32bit. Isn't GE7 not yet an official Ubuntu package? On current form I think GE7 isn't ready for the big time whatever appears on Google's website.

GE6 isn't that bad in appearance. 

To Google, your Google Earth program is amazing when it works. I've found the linkage to Streetview very helpful in so many ways. I'm always interested in the adverts which appear during my Google searches. More power to you if you get Google Earth sorted for us Linux users. Please assign more people to sort out this problem of Google Earth not properly working with Linux and Ubuntu.

---

### Post by Smask on 2014-02-13
Never mind, the solution borks searches completely. 

What I tried to do was add a small Shim library containing a function that GE needs and then rely on the Qt libraries Ubuntu provides. This isn't possible because not all patches are applied yet on Debian/Ubuntu. Those patches are in on Fedora, Suse and Gentoo, according to AmirPli.

So the solution is still to use AmirPli's Qt-libraries until the maintainers update Qt4-X11 or Google spare some developers from Chrome and build a new binary.

---

