---
title: "Lightning Extension for Thunderbird"
date: 2008-04-09
forum: General Help
---

### Post by mlyons16 on 2008-04-09
Hello,

I am using 7.10, with Thunderbird running at 2.0.0.12, and I have installed the Lightning extension for Thunderbird version 0.8. Once I install it, the interface becomes rather warped and makes Thunderbird almost unusable unless I uninstall the Lightning extension. Anyone know how to fix this?

---

### Post by xarquid on 2008-04-09
I have seen this occur too, I think we need to wait on the newest Lightning Extension unfortunately. It's a known bug on Lightning's end for the Linux Thunderbird Client.

---

### Post by mlyons16 on 2008-04-09
Ya, I've seen the problem in the latest 0.8 version update of the extension, and the one just previous to it. If anything, the warping was not as intense as it was in the previous version, which makes sense, but you think that the issue would have been completely resolved. 

If anyone reading this has escalation points with Mozilla, please forward this along. This is what the users like myself are here for, to report bugs to continually improve the software.

---

### Post by Xappe on 2008-04-09
Somehow I think this has something to do with the Ubuntu Thunderbird build. I use lightning 0.8 without any problems with an official Mozilla build of thunerbird on fedora at my university.  

I've sen this before and now provider for google calendar updated and does not work with lightning 0.7 from hardy repos anymore :(

---

### Post by Xappe on 2008-04-09
Aha! I managed to get lightning 0.8 from the mozilla site to work with thunderbird from the Hardy repos. It sems that it's been built against libstdc++5 (and the ubuntu one against libstdc++6), and the only thing I had to do to get it running was to install that library.

```
sudo apt-get install libstdc++5
```

yes! now my google provider is happy again :)

<edit> I hope this works for you 7.10 users also </edit>

---

### Post by VanHammersly on 2008-04-09
I agree with Xappe.  I am running Hardy and upgraded to Lightning 0.8 and I could not view my calendars.  I just uninstalled the community version of Thunderbird and reinstalled it using ubuntuzilla, which pulls Thunderbird 2.12 from Mozilla.  Lightning 0.8 now works.  Here's a link to ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

I hope this helps.

---

### Post by elastigirl on 2008-04-17
Bless you! Worked like a charm even on Gutsy

---

### Post by Xappe on 2008-04-17
I'm glad it works!

---

### Post by RgnKjnVA on 2008-04-17
On Gutsy I'm seeing SERIOUS issues with TBird since the Lightning update, mail will just vanish (corruption?) if I use any keystrokes of any kind while reading mail. The mail is no longer accessible i.e I can't find it in Inbox, Deleted Mail or Spam. It's simply GONE. Also, the File, Edit and View menu bar options aren't being displayed nor are the navigation buttons in the toolbar. I apparently already have libstdc++5 installed. This sucks, I only got on board with Lightning a few months ago and was excited to have calendar functionality in TBird. Looks like I have to uninstall. Incidentally, no issues on my WinXP at the office after update.

~$ sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++5 is already the newest version.
The following packages were automatically installed and are no longer required:
  liblzo1 libprojectm1-data python-qt3 python-sip4 libprojectm1 libneon26-gnutls libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by jmlaniel on 2008-04-22
I was also having problem with Lightning 0.8. I added the "libstdc++5" and everything is now fixed. Thanks a lot for this info!

By the way, does anyone know where the file for lightning are? I tried to find some "./Lightning" folder in my home folder, but there is none... I am asking this because I synchronize my account between two computers and I would like to know which file I need to backup to access my calendar at both places.

---

### Post by dcroal on 2008-04-22
I believe the file is storage.sdb in your profile directory

---

### Post by Ghostlove on 2008-04-26
Since upgrading to Hardy, Lightning appears to be... just not working. At all. Any ideas?

---

### Post by sunny_nwho on 2008-05-06
Yes installing the libstdc++ works for me...I am running TB in hardy and everything is fine for me

---

### Post by Rahl on 2008-05-15
After installing Lighting 0.7 from the Ubuntu repositories on Hardy, the calendar works OK, but the mail starts having issues.

In the mail read window, the menu items File, Edit and View, and the first submenu items in all three, have no text. Hitting Ctrl+U in this window silently deletes the currently opened message and displays the next message (Ctrl+U should display the message source and does so without Lighting).

This extension is dangerous in its current state. It would only be proper to remove it from the Ubuntu repositories until things get better.

---

### Post by komputes on 2008-05-26
Rahl, I don't seem to have this issue in Hardy with the extension from the repositories.

---

### Post by spegru on 2008-05-28
My Lightning has just stopped working. It was ok last week but now the New Event button does not work and I cannot create or view any events.

help!

---

### Post by Rahl on 2008-05-28
komputes, I am sure that there are people for whom things work, I hope that the extension wouldn't be in the repositories otherwise. But at least one other person posted to this thread with problems akin to mine. Perhaps it is a conflict between add-ons or a particular combination thereof? I have Enigmail and Mnenhy installed in Thunderbird, what do you have?

---

### Post by komputes on 2008-05-28
spegru - what happens when you double-click the time/date to create a new event?

Rahl - I have Enigmail installed from Mozilla, work great. Truth is you have a number of possible fixes, but I just wanted to report the one which worked for me. Good luck!

---

### Post by spegru on 2008-05-29
Thanks komputes

when i double click nothing happens
The whole calender seems to have disappeared and no matter how many times I re-install thunderbird and lightning it makes no difference
I did try the installation of libstdc++5, but it seemed to make no difference - may be i did it wrong? 

there is very little in my calender so i am happy to make a new one - but i cant locate the file.........

thanks for any help

spegru

---

### Post by spegru on 2008-06-02
bump

---

### Post by komputes on 2008-06-02
spegru, I seem to have success on both Gutsy and Hardy with the extension from the repositories. check out one of my previous posts, hope this helps:

[http://ubuntuforums.org/showthread.php?t=778326](http://ubuntuforums.org/showthread.php?t=778326)

---

### Post by spegru on 2008-06-06
thanks very much komputes
 I had tried the libstdc++5 from another thread but didn't see your original post. It didn't work for me.
This method is fine though

Interestingly lightning on hardy was fine until a few days ago. But then some update messed it up.

Will future updates work properly so that i can get back to 0.8?
I think I originally installed lightning through Add Ons. i suppose the better way would have been to use your method from the beginning

thanks again 

spegru

---

### Post by komputes on 2008-07-24
A little update for the folks following this thread. I recently installed 8.04 with thunderbird and lightning-extention from the repositories, but unlike in 7.10, in 8.04 I can't see my different calendars.

My current workaround was to take my .mozilla-thunderbird directory and copy it to a 7.04 Live CD environment, download and install thunderbird and lightning-extention and export them as .ics files. I imported those files to Sunbird (stand alone calendar) in 8.04 and I now have everything I need. I highly recommend this switch for anyone who needs a working calendar.

---

