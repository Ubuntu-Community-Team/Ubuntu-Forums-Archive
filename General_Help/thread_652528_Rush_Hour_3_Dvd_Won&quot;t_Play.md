---
title: "Rush Hour 3 Dvd Won&quot;t Play"
date: 2007-12-28
forum: General Help
---

### Post by SirPaPa on 2007-12-28
Hello, I hope someone here may be able to help me. I just got **"RUSH HOUR 3"** on dvd today but, it won't play.
 
 I've tried **Totem**  and **VLC**.

 In Totem, it'll play the previews on the start but won't go to the menu.

  In VLC it  didn't play anything. I've been able to play every dvd movie with Ubuntu up til' now.

InTotem it gives me the attached screenshot message.

Also it plays fine in Windows. 

Any thoughts would be most appreciated. 

Thank, you.

---

### Post by p_quarles on 2007-12-28
So, *are* you trying to play an encrypted dvd without libdvdcss?
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by noynac on 2007-12-28
Rush Hour 3 employs a new form of copy protection that makes the DVD unreadable by many PC's. The error message that you received is the one that occurs with the new copy protection. Have you tried playing the disk on on a standalone DVD player?

---

### Post by SirPaPa on 2007-12-28
Thank,you for such a quick reply.  The answer to your question is no. 

I have everything needed to play dvd's, this particular dvd movie ( at least my install of Ubuntu) won,t play. 


Every other dvd that I've popped in my Ubuntu box works fine.

Any other thoughts ? Anyone?

Thank,you.


Whoops slow reply on my behalf.

---

### Post by SirPaPa on 2007-12-28
> **noynac said:**
> Rush Hour 3 employs a new form of copy protection that makes the DVD unreadable by many PC's. The error message that you received is the one that occurs with the new copy protection. Have you tried playing the disk on on a standalone DVD player?

Thank you for your help. Yes, it does play on a standalone DVD player. 

It also plays on  my second (slave) drive which is Windows XP on the same computer but,

 not on the (master) drive where Ubuntu is installed. :(

---

### Post by noynac on 2007-12-28
Rush Hour 3

---

### Post by wammin on 2008-01-27
I am having the exact same problem with the same DVD, Rush Hour 3. I definitely have the latest libdvdcss2 installed ... every other DVD that I have ever got from Netflix plays fine ... except this one. I tried VLC and Mplayer, both choke when getting to the DVD Menu (the previews play ok).

I guess it must be some kind of new copy protection. Anyone have a workaround? Sadly, I don't have a "normal" dvd player anymore to watch it on.

---

### Post by (((X))) on 2008-01-27
[http://ubuntuforums.org/showthread.php?t=679270&highlight=play+dvd](http://ubuntuforums.org/showthread.php?t=679270&highlight=play+dvd)

xine may work.

---

### Post by mc4man on 2008-01-27
The recent new line cinema titles and possibly some universal studios (german releases) will not play back using  free open source unlicensed players but will work with commercial licensed players like powerdvd, windvd, and for linux lindvd. I believe the free wmp player in vista cannot play these either.

---

### Post by drazmo on 2008-02-09
The movie "Shoot Em Up" has the same protection.  I was able to play it using VLC from the instructions on this site "http://tobias.rautenkranz.ch/libdvdread_ifo.html.en"   using Knoppmyth.  I need to get it working with mplayer but have failed.  VLC was able to play the movie downloading the libdvdnav.so.4.0.0 from this site and running the command listed.  The site states it can be done with mplayer but I don't understand how to get it done in ubuntu.  Hope this helps!

---

### Post by mc4man on 2008-02-10
@drazmo
For mplayer you have to dl the source, patch dvdread, then compile and install
 What works is to copy the "patch against libdvdread 0.9.7"  as a text file, name it patch.patch (seemed logical) put it into the dvdread folder and run
```
doug@doug-desktop:~/Desktop/MPlayer-1.0rc2/dvdread$ patch -i patch.patch
```
the result of new patch should show
```
patching file dvd_reader.c
Hunk #1 succeeded at 1390 (offset -3 lines).
Hunk #2 succeeded at 1463 (offset -3 lines).
patching file dvd_reader.h
patching file ifo_read.c
Hunk #1 succeeded at 110 (offset 4 lines).
```
works with any version of mplayer source to date (repo, ...rc2, latest svn, ect.)

The 2 recent New Line titles I have now play fine in mplayer and smplayer 

Edit: ck.  updated patch for mplayer method (top of page @ rautenkantz}

---

### Post by ubuntu-freak on 2008-02-13
Thanks! Added a link to that page in my [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan

---

### Post by mc4man on 2008-02-13
i think there may be a way to get the vlc patch to auto load when starting vlc but in meantime just for clarity about "run from there" - assuming you download the patch to desktop to open vlc with it run
```
cd Desktop;LD_PRELOAD=./libdvdnav.so.4.0.0 vlc
```

Edit:again only for vlc - this might not work on all previously unplayable titles. If it doesn't 1 add. thing to try is go .dvdcss (hidden in home), see if there's a folder for that specific title and if so shift/delete it. Then try again - may work.
OT - concerning .dvdcss - if your trying to play a region mismatch (ex. region 1 title in region 2 drive ) and it has structure protection, sometimes vlc can't brute force the keys and playback will fail. Here's an ungainly workaround  (basically amounts to sharing .dvdcss folders)
[http://ubuntuforums.org/showthread.php?t=657516&page=3](http://ubuntuforums.org/showthread.php?t=657516&page=3)

reedit - easier way then running preload - either make dl'ed libdvdnav.so.4.0.0 exectuable and replace one in /usr/lib or follow how here [http://ubuntuforums.org/showthread.php?t=727671&page=2](http://ubuntuforums.org/showthread.php?t=727671&page=2) - method in post #17

---

