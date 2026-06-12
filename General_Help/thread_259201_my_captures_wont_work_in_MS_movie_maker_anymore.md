---
title: "my captures wont work in MS movie maker anymore"
date: 2006-09-17
forum: General Help
---

### Post by beerorkid on 2006-09-17
so i have a hauppague card and have been making captures with it for a while now.

I used
[http://www.ubuntuforums.org/showthread.php?t=186747&highlight=HAUPPAUGE](http://www.ubuntuforums.org/showthread.php?t=186747&highlight=HAUPPAUGE)
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)
these to try and install mythtv, but found what I needed after installing the ivtv drivers.  Do not need anything more than self initiated captures, not using mythtv.

this:
```
cat /dev/video0 > /tmp/test.mpg
```
will capture the input and I control C to stop it.

It has worked fine for months.  Today I came home and the PC was powered off, dogs maybe.  So booted and did a capture.  needed to shrink it down, used a windows box with movie maker as usual.  I keep getting it does not have the proper codecs error in moviemaker.  Tested on two different windows boxen.  Tried previous captures and they are fine.  No updates or anything to the ubuntu box.

Me stumped. any clues?

---

### Post by beerorkid on 2006-09-17
still bummed.  Thinking of reinstalling, dont want to though.

It is basically encoding a .mpg but other programs think it has the wrong codecs.  I have tried .avi's and still no luck

I reinstalled the w32codecs but it still does have the problem.  Is there some other things I can check?

Prob gonna put the capture card into another ubuntu box to see what happens :(

---

### Post by beerorkid on 2006-10-03
ughhhhhhh....

I reinstalled and it worked fine for quite sometime.

Now it is happening again.  any clues?

I had vmware server running on the last one.  This time I just installed vmware workstation and then it happened.  prob the issue.

really really really bummed :(

---

### Post by IoCaster on 2006-10-03
Uninstalling vmware doesn't get it working again? I'm curious because I've got an older hauppauge card that I haven't bothered with in a while. It's a win-tv pvr 150 I think. I don't watch tv much and only used it for captures from old vhs tapes for archiving. I've been thinking about installing it again and trying to make it work in Dapper. That straight capture without tv functionality you described would be essentially all I'd need. I hope you don't have to go through the bother of another Dapper reinstall. ](*,) 

If you get it working again please post a follow-up with details of how you resolved the problem.

---

### Post by beerorkid on 2006-10-03
well I remember trying to uninstall vmware player and how I really never could completely wipe it along with others (to install vmware server)

I am betting it has somethingto do with the compiling vmware does when installing server/workstation.  First time it borked was after a kernel upgrade and I had to rerun vmware-config.pl

---

### Post by beerorkid on 2006-10-03
well found this thread on the vmware forum: [http://www.vmware.com/community/thread.jspa?messageID=393122&#393122](http://www.vmware.com/community/thread.jspa?messageID=393122&#393122)

reccomends downloading this:

Movie Decoder
This is a Windows installer for the movie decoder. This utility is required to play back movies recorded with VMware Workstation 5.x in any compatible media player.

Have not tried it yet, but it has to be something that has changed on my ubuntu box.  i was not making the captures within the VM.

will test at lunch and see if this fixes it.  if nothing else will try uninstalling workstation :(

---

### Post by IoCaster on 2006-10-03
I don't have vmware installed on this box. I'll probably install that hauppauge card in a day or so. If I can get it to work I'll have to remember to **not** install vmware later on. Good luck.

Regards - Joe

---

### Post by beerorkid on 2006-10-03
man this is getting even crazier.

K, my previous mentioned above download from vmware has nothing to do with this. That is for making screen captures with workstation.

I unistalled vmware and still no luck.  

found this nifty little nautilus script here that will do what I need [http://www.ubuntuforums.org/showthread.php?t=193754](http://www.ubuntuforums.org/showthread.php?t=193754)
this will shrink captures down to a more managable size.

anyhoo I get this error when running that script on a capture recorded after this problem arose
> Couldn't find MIME type application/octet-stream
googled it and found out a couple things.

- my problem seems to mess with the file extention I give the captures.  does not matter if I make them .mpg or .avi they still dont work

- found this from another thread > "OK, so I went into kcontrol and went to File Associations, and added octet-stream under application. The error went away." well I am using gnome.

-found this:> "Couldn't find MIME type application/octet-stream" can be shoved as alert from KDE after it'&#347; updated. Can be solved when you create new mime type in KDE Control Center named 'ocet-stream' in category 'application' and with the same text (ocet-stream) in the description.

Check contents of octet-stream.desktop located in /home/userhomedir/.kde/share/mimelnk/application. Check to see that there is a line that reads Hidden=false. If Hidden=true you will still get the error message. 

- did a locate mimelnk and spit out a bunch of stuff.  homed in on this file
/usr/share/mimelnk/application/octet-stream.desktop
looked in there for Hidden=true/false and saw neither.
(this is on my work box, will check when I get home on the box with the issue)

so anyone have any ideas on how to add 'octet-streaam' in a mime type area of gnome.  or any clues on what this info might mean.

EDIT: getting closer I think

found this:

KDE returns "Couldn't find MIME type application/octet-stream" at startup and/or Konqueror returns the same error message when launching whatever application.

Start the Control Center With sudo kcontrol in terminal and open KDE Components/File Associations,
Expand "application", you will probably see that there's no entry for "octet-stream".
Click on "Add...", for "Group" select "application" and for "Type Name" fill in "octet-stream". This should fix it.


will try.

---

### Post by IoCaster on 2006-10-03
If I understand you correctly, it was working and then it stopped working. Was there anything other than vmware that you installed in that same time period that you think might have been at fault? If not, then what would cause a working application to suddenly cease to work like this?:-k 

Hope you can track this one down. I'll hold off on installing my capture card for the moment and see what develops from your troubleshooting. There is no compelling need for me to archive anything at this time and I'm busy enough with other matters to avoid unnecessary and convoluted configuration headaches.

BTW....I can't thank you enough for hosting the compiz+Xgl stuff for the community.=D>  

Best of luck to you and best regards.

-Joe

---

### Post by beerorkid on 2006-10-03
he he what else am I gonna do with 2TB of transfer a month ;)

Yeah just vmware workstation.  I was very careful to not update or install anything.

Last time it was after I ran the vmware-config.pl after a new kernel.

Worked fine before.

I am thinking I will get it figured out tonight.  Found a bunch of stuff that I did not list here.  Gonna reply once I got it figured out.

---

### Post by beerorkid on 2006-10-04
well I tried all I could find.  pretty bummed.  Good thing is I was able to keep my raid 5 share intact upon the reinstall :)

needless to say, this will get setup and never be touched again.

vmware never ran all that great on it anyway

thanks for the interest iocaster.

---

