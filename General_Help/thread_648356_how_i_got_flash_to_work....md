---
title: "how i got flash to work..."
date: 2007-12-23
forum: General Help
---

### Post by seatownrocks on 2007-12-23
remove the badly working flash...

sudo apt-get remove --purge flashplugin-nonfree

for the 32 bit package click this (u may need to login to get the file - just open with GDebi Package installer (default))...

[http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466)

for the 64 bit package use this link...

[http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466)

just click ok and your install should go smoothly... mine did and i didn't do anything specail which is good cause i'm not good at this linux stuff... lol


hope this helps people,
eric.

---

### Post by staticvoid on 2007-12-23
ya mon!  :D

---

### Post by Wynne G Oldman on 2007-12-23
Great stuff!:guitar:

---

### Post by seatownrocks on 2007-12-24
bump

---

### Post by ~LoKe on 2007-12-24
That's one way, or you could just compile it from the source.

But good job posting the solution, it should certainly help many.

---

### Post by de_valentin on 2007-12-24
Worked for me :D

---

### Post by seatownrocks on 2007-12-24
> **~LoKe said:**
> That's one way, or you could just compile it from the source.

But good job posting the solution, it should certainly help many.

true, but i was trying for the simplest possible solution to the problem. thx tho. :)

---

### Post by phreakalot on 2007-12-25
I got the flash to install this way, and youtube now works, along with yahoo videos. but my much needed cnet tv wont play. the webpage an applet is very distorted
. just installed ubuntu yesterday, and have been learning n installing alternative packages for things i need, and am use to from windows os at a pretty good rate. lovin it so far, but desperately need my cnet tv , any help would much be appreciated. this is my first post.
chad

---

### Post by ugm6hr on 2007-12-25
> **phreakalot said:**
> I got the flash to install this way, and youtube now works, along with yahoo videos. but my much needed cnet tv wont play. the webpage an applet is very distorted
. just installed ubuntu yesterday, and have been learning n installing alternative packages for things i need, and am use to from windows os at a pretty good rate. lovin it so far, but desperately need my cnet tv , any help would much be appreciated. this is my first post.
chad

Just seen cnettv.com - videos are pretty funny.

Anyway - it works just fine on my FIrefox with standard flash plugin (Ubuntu Gutsy, latest updates to today).

---

### Post by tpls on 2007-12-25
Can someone tell me that why youtube is showing just an empty grey box instead of videos? I'm using opera 9.24 and gutsy, Thanks for help in advance.

---

### Post by Comhra on 2007-12-25
**Can someone tell me that why youtube is showing just an empty grey box instead of videos? I'm using* opera 9.24* and gutsy, Thanks for help in advance.**

If you're using the .deb package obtained here: [http://ubuntuforums.org/attachment.p...1&d=1198033466](http://ubuntuforums.org/attachment.p...1&d=1198033466) then Adobe FlashPlayer will not work in Opera 9.24.  You need to install Opera 9.50 which is a Beta.  I've been using it for the past week.  It's buggy and sometimes quits unexpectedly but I watched YouTube videos with it for 2 1/2 hours last night and it never complained.  In other words, it's usable if you don't mind the odd hiccup.

You'll find a .deb package for 9.50 here:
[http://www.opera.com/products/desktop/next/](http://www.opera.com/products/desktop/next/)

---

### Post by seatownrocks on 2007-12-25
> **phreakalot said:**
> I got the flash to install this way, and youtube now works, along with yahoo videos. but my much needed cnet tv wont play. the webpage an applet is very distorted
. just installed ubuntu yesterday, and have been learning n installing alternative packages for things i need, and am use to from windows os at a pretty good rate. lovin it so far, but desperately need my cnet tv , any help would much be appreciated. this is my first post.
chad

following the instructions at the beginning of this post and using firefox browser cnettv.com videos work for me with no other actions taken. are you using firefox?

---

### Post by David King on 2007-12-25
Hmmm... 
I'm still having trouble on my end. YouTube vids will now play effectively, but the control bar at the bottom is having some issues. It's half cut off, lengthwise, as if the window for the video is too short, and the buttons are all scrunched together or lying overtop of one another on my screen. As soon as I try to navigate forward of backward in the video, or do anything but 'start/pause' the video, it goes gray and quits. 
Flash files from other places (some places I've tried include Newgrounds, AddictingGames, and several other purveyors of time-wasting entertainment), and most of those will load and then spectacularely fail to play. 
Anyone having similar problems, or perhaps some advise for someone who started Ubuntu yesterday and is still trying to figure out the basics? 
Thanks.

---

### Post by tpls on 2007-12-25
> **Comhra said:**
> **Can someone tell me that why youtube is showing just an empty grey box instead of videos? I'm using* opera 9.24* and gutsy, Thanks for help in advance.**

If you're using the .deb package obtained here: [http://ubuntuforums.org/attachment.p...1&d=1198033466](http://ubuntuforums.org/attachment.p...1&d=1198033466) then Adobe FlashPlayer will not work in Opera 9.24.  You need to install Opera 9.50 which is a Beta.  I've been using it for the past week.  It's buggy and sometimes quits unexpectedly but I watched YouTube videos with it for 2 1/2 hours last night and it never complained.  In other words, it's usable if you don't mind the odd hiccup.

You'll find a .deb package for 9.50 here:
[http://www.opera.com/products/desktop/next/](http://www.opera.com/products/desktop/next/)

Thanks a lot! That worked for me. I can watch youtube now

---

### Post by kd7swh on 2007-12-25
thanks for the debs.

bump.

---

### Post by tad1073 on 2007-12-25
> **Comhra said:**
> **Can someone tell me that why youtube is showing just an empty grey box instead of videos? I'm using* opera 9.24* and gutsy, Thanks for help in advance.**

If you're using the .deb package obtained here: [http://ubuntuforums.org/attachment.p...1&d=1198033466](http://ubuntuforums.org/attachment.p...1&d=1198033466) then Adobe FlashPlayer will not work in Opera 9.24.  You need to install Opera 9.50 which is a Beta.  I've been using it for the past week.  It's buggy and sometimes quits unexpectedly but I watched YouTube videos with it for 2 1/2 hours last night and it never complained.  In other words, it's usable if you don't mind the odd hiccup.


You'll find a .deb package for 9.50 here:
[http://www.opera.com/products/desktop/next/](http://www.opera.com/products/desktop/next/)


Flash w/Fx works but not good. Flash freezes(starts and stop at [http://chris.pirillo.com/live/](http://chris.pirillo.com/live/)) like ther is some kind of processing error or network congestion or something. Flash chat on that site creates double key entries ex. "ttaadd11007733"

Off topic, sorry.

Do you know how I can install Opera 9.5 w/o overwriting my existing 9.25, I used the .deb file but it overwrote 9.25? I installed opera-9.50-20071221.6-shared-qt.i386-1729.tar.gz but I was only able to run it from the terminal, using:

$ tar zxf opera-9.50-20071221.6-shared-qt.i386-1729.tar.gz
$ cd opera-9.50-20071221.6-shared-qt.i386-1729
$ ./opera

I got completely lost here:

For a standard system wide access you should log in or suid to root and type:
./install.sh
If you are only logged on as a normal user, the script will detect this and give you a number of options.
You can also manually specify the directory where you want Opera to be installed:
./install.sh --prefix ~/
which installs the binary to your home/bin directory and documentation and opera shared files in similar fashion. Insert
export OPERADIR="~/share/opera"
into .bashrc or similar to set Opera's environment. You may also use some GNU prefixes.
./install.sh --help
gives you a short list.

Does that mean to do:

$ cd opera-9.50-20071221.6-shared-qt.i386-1729
then:
./install.sh once I am int the directroy?

---

### Post by holmes85 on 2007-12-27
sweet thanks it worked!!!

---

### Post by Reeva on 2007-12-27
Thanks a lot, works for me ;)

---

### Post by stoneage on 2007-12-27
It didn't work for me until I removed mozilla-plugin-gnash - fine now though.

Thanks.

---

### Post by David King on 2007-12-27
Yep, I just got mine to work too. 
Had to unintstall gnash to get it to work, though. 
Thanks for your help, everyone.

---

### Post by Orfintain on 2007-12-27
how do you know if you want the 32bit or 64 bit ?

I'm assuming the 32 big is same as 86i on the linus system choice...

(and that has worked for me --thanks)

---

### Post by kd7swh on 2007-12-28
you most likely want the 32bit version. If you installed the 64bit version of Ubuntu and you know thats what you have then use the 64bit version.

32bit is also called 386i. (yes)

---

### Post by crjackson on 2007-12-28
> **seatownrocks said:**
> remove the badly working flash...

sudo apt-get remove --purge flashplugin-nonfree

for the 32 bit package click this (u may need to login to get the file - just open with GDebi Package installer (default))...

[http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466)

for the 64 bit package use this link...

[http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466)

just click ok and your install should go smoothly... mine did and i didn't do anything specail which is good cause i'm not good at this linux stuff... lol


hope this helps people,
eric.


Thanks for the deb. I did a re-install of the 32 but OS trying to get flash working only to have an error with the md5sum.  I installed your deb and now it's working just fine.

I have one question however....
I want to install the ubuntu restricted extras (which also includes flash-nonfree-nonworking).  Will that mess up my now working flash install, or will it simply skip over it since it's an older version?  I don't want to bork this install.  I have to be finished with it by monday to return this box to it's owner.

Thanks...

---

### Post by jaxter66 on 2007-12-28
seems to work except;
when it tries to install I get this pop up error message
-Only one software management tool is allowed to run
-Please close other application

Problem is I cant seem to locate what other application is open-in the system monitor no synaptec or other download program is listed as running- all update manager boxes are unchecked and I restarted the computer twice after doing these things. Any ideas?

---

### Post by Payteer on 2007-12-28
causing a crash when I use this. A complete system crash that is, I am using gutsy

---

### Post by crjackson on 2007-12-28
> **jaxter66 said:**
> seems to work except;
when it tries to install I get this pop up error message
-Only one software management tool is allowed to run
-Please close other application

Problem is I cant seem to locate what other application is open-in the system monitor no synaptec or other download program is listed as running- all update manager boxes are unchecked and I restarted the computer twice after doing these things. Any ideas?

Sounds like you got a hung update in cache or something.  I had that once before.  Just for kicks try this...

sudo apt-get install -f

Then run the update manager and let it check for and install any updates.  Then give the deb file a try when it's done.

---

### Post by Drumdums on 2007-12-28
after following the OP's instructions, Youtube videos -sort of- work. In that they play from beginning to end, but the controls are cut off, and if you mess with them at all, the video gets screwy. Also, I'm having trouble with ytmnd sites such as  

[http://ebombhax.ytmnd.com/](http://ebombhax.ytmnd.com/)

Where it will display the ytmnd logo, and display "done" in the bottom bar on firefox. oddly, some other ytmnds do work, such as 

[http://picard.ytmnd.com/](http://picard.ytmnd.com/)

also, opera doesn't seem to support a 64bit architecture, I tried all 3 types for linux they have available, and all returned an "incorrect architecture" error when trying to install.

---

### Post by Waldo22 on 2007-12-30
This is the most amazingly simple process I have ever seen.  If only it could all be this easy!  Many thanks!  Maybe a sticky is in order?!:)

---

### Post by LaRoza on 2007-12-30
> **Waldo22 said:**
> This is the most amazingly simple process I have ever seen.  If only it could all be this easy!  Many thanks!  Maybe a sticky is in order?!:)

I already requested a sticky, in the FF&H, until this was officially not an issue anymore.

---

### Post by miesnerd on 2007-12-31
thanks.. just the fix i needed. Works perfectly!

---

### Post by fox-out on 2008-01-07
Thanks! It works okay on Xubuntu 7.10

---

### Post by Gwaihirjp on 2008-01-23
wow thank you sooooooo much for this, I'd been trying so hard to figure out this problem for days!! Installed it and removed gnash... :D It works perfectly fine now.

---

### Post by John L on 2008-01-23
Excellent - had almost given up!  Thank you!

---

### Post by Kevbert on 2008-01-23
Thanks, one less thing to sort out...:)

---

