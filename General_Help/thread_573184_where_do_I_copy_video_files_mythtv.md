---
title: "where do I copy video files mythtv"
date: 2007-10-11
forum: General Help
---

### Post by Gnub_Daemon on 2007-10-11
Ok, so this isn't an actual Ubuntu question, but I find these forums easiest to use.  I just got a mythbox (knoppmyth) up and running, and I don't know where to copy all my *.avi files in order to watch them using the "watch videos" (not sure if that's the right name) function under the frontend.  I have quite a few and really don't want to have to rip all the dvds again.  I'm not even sure if *.avi files would show up under that particular function, but I would appreciate it if anyone could help me out.  I apologize again that this is not a strictly Ubuntu question.  Thanks.

---

### Post by praet on 2007-10-11
Copy them to the directory you specified in mythtv video setup.  Then in the frontend, go to video manager and it should scan for and find your video files.  Then they will be added to the database and be available through the watch video menu entry.

[http://www.mythtv.org/wiki/index.php/MythVideo](http://www.mythtv.org/wiki/index.php/MythVideo)

---

### Post by dfreer on 2007-10-11
Is this a standalone, backend and frontend on one box? Mine's this way, and if I wanna add videos like movies in the "Videos" section, I don't use the backend at all.  you can specify the directory your videos are in the frontend by going to "Setup > Video Settings > General Settings". Then go back to the main menu, "Videos > Video Manager" and it will scan them and add them for you.

Now, if only I could do this with the TV Shows I already have pre-recorded watch them in the "TV" section... *sigh*

---

### Post by Gnub_Daemon on 2007-10-12
I figured out how to do it from a DVD DL using terminal.  I would have used my usb hdd, but my mythbox doesn't have usb 2.0.  Now if I could just figure out how to configure the default screen resolution/refresh rate I'm all set.  My lcd tv shows "Signal input out of range" when I have to reboot or restart x for any reason, and I have to haul my old monitor into the living room to reset it using xrandr.  I tried got an account with knoppmyth.tv forums, but "somehow* my caps got turned on and I exceded the max number of login attempts for the next hour... -_-  Quite frustrating.

Thanks again for the help.

Also, forgot to mention that I don't think I have my dvd rom drives hooked up correctly in accordance with master and slave.  I had to manually do it because the master drive isn't DVD DL capable, and the other one wouldn't register in the frontend.  I found it though on /myth/hdc.

---

### Post by newlinux on 2007-10-12
> **dfreer said:**
> 
Now, if only I could do this with the TV Shows I already have pre-recorded watch them in the "TV" section... *sigh*

There is a script named myth.rebuilddatabase.pl which takes an "--ext" command-line option followed by a file extension that will import those files into the database as regular recordings. It will ask for some information about the show in order to import it into recordings. It can be found in the mythtv contrib directory in Feisty and beyond: /usr/share/doc/mythtv-backend/contrib/

by default it will be gzipped. If you're on edgy or earlier you'll have to download it from svn I believe, as the contrib directory is not included in the mythtv install.

This might help:
[http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php](http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php)

---

### Post by Gnub_Daemon on 2007-10-12
After much contemplation and thoroughly backing up my xorg.conf (finally found it...) I removed any reference to 640x480 screen resolution with anything other than 75hz refresh rate.  Also removed "1024x768" and "800x600" from the default depth of 16 and that seems to have fixed my "Input signal out of range" woes.  Happy Ubunting all and thanks once again for the help on this non-Ubuntu issue.

---

### Post by dfreer on 2007-10-12
> **newlinux said:**
> There is a script named myth.rebuilddatabase.pl which takes an "--ext" command-line option followed by a file extension that will import those files into the database as regular recordings. It will ask for some information about the show in order to import it into recordings. It can be found in the mythtv contrib directory in Feisty and beyond: /usr/share/doc/mythtv-backend/contrib/

by default it will be gzipped. If you're on edgy or earlier you'll have to download it from svn I believe, as the contrib directory is not included in the mythtv install.

This might help:
[http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php](http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php)

I remember that script, it's been awhile since I used it last. I had issues with running the script on my entire TV collection, due to the files being located in sub-folders and having various extensions. I could write a script to handle it all... my concern about this was that the script seemed to be "analyzing" each video file, which took a couple minutes, and I wasn't sure how long it would take to do the entire collection. Another issue is all of the information that I need to enter about each show.

I'll try it again here today, see if I can automate the process and make things eaiser.

---

### Post by Solarbaby on 2007-10-19
If you want to pull information about TV shows from a very reliable and easy source I'd look into TheTVDB.com..  their whole purpose of existance is so that they can support the open source community with a free reliable and easy to setup database of TV Show information.. I think they found a reason to create themselves when TV.com kept breaking all of our scrapers. Their service allows you to get the data with out scraping.. they are giving it away :)  I have a script on my Xbox that works wonderfully with them.  If you'd like to take a look at the script let me know.

I'd very much like to see MythTV increase its overall use-ability in this way.

---

### Post by dfreer on 2007-10-19
I'd be very much interested in that script, Solarbaby! Saves me some time from having to make one myself, cuz I'm lazy :p

---

### Post by Solarbaby on 2007-10-21
Heres The Script for XBOX To access TheTVDB.com
I gave you more then just the TVDB I gave you every single scraper they use with XBMC, and I've gotta tell you I'm very impressed with it.  :)

I wish I could do something more then just provide you with them, but I haven't the skill set too.
Good Luck and keep us informed.

---

### Post by dfreer on 2007-10-25
[http://ubuntuforums.org/showthread.php?t=590737](http://ubuntuforums.org/showthread.php?t=590737)
For anyone following the thread who is interested.

---

### Post by dfreer on 2007-11-04
Check this script out guys, found this after some googling:
[http://www.jobs-khakis-chicks.com/MythTV/](http://www.jobs-khakis-chicks.com/MythTV/)
Specifically:
[http://www.jobs-khakis-chicks.com/MythTV/TVRageImport/ragetvgrab-0.5.pl](http://www.jobs-khakis-chicks.com/MythTV/TVRageImport/ragetvgrab-0.5.pl)
I just tried it with one of my video files, seems to work well (although it went REALLY quick, seems it is just manually inserting the data into the mythtv database instead of using the myth.rebuilddatabase.pl script. Probably not an issue, but I'm kinda wondering how important it is to build the seek index for the files).

---

### Post by Solarbaby on 2007-11-04
TV Rage script doesn't seem to do it for me..  perhaps my file names are a little different then it prefers.. 

Buffy The Vampire Slayer 1x01 Welcome to the Hellmouth (1).avi
Buffy The Vampire Slayer 1x02 The Harvest(2).avi
Buffy The Vampire Slayer 1x03 Witch.avi
Buffy The Vampire Slayer 1x04 Teacher's Pet.avi
Buffy The Vampier Slayer 1x05 Never Kill a Boy on the First Date.avi

XBMC Linux will be out for beta testing in a few more months most likely so I may just end up using that as my MythTV frontend and use their scrapers...  at least its my hopes that it'll work out that way.

---

### Post by dfreer on 2007-11-05
The rage script works better IMO if you don't have the Episode Title in the filename, so like Family Guy - 101.avi (better yet, family.guy.101.avi).
But after importing a few of my shows, and realizing that 
(1) my little HP remote once again failed me, since it uses native keypresses instead of LIRC, I can't map my escape button on my remote to the "Escape" Key, forcing me to grab the keyboard to exit each episode.
(2) that the built-in internal player of mythtv can't handle some of the exotic video formats I have my TV shows in (.mkv, .rmvb, etc)
I gave up on importing, it's quite a bit faster to use this script but without some modification, still not fast enough to justify importing +1600 tv shows.

Basically, there's no point on me spending time working with a script to import tv shows when I can't play them anyways. Oh well, until I get some real programming skills and fix everything I would like to change about mythtv, I'm willing to use a mouse/keyboard every once in a while to watch my backed up tv shows.

---

