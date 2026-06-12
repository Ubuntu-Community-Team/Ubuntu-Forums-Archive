---
title: "Problem With Music Files: Misplaced Files Everytime I Start Ubuntu"
date: 2008-01-24
forum: General Help
---

### Post by apolloxi on 2008-01-24
So, I have two hard drives. Windows XP is on the C Drive, and Ubuntu is on the D Drive. In XP, I use iTunes to listen to all of my music, so almost everything is either mp3. I have a few m4a files, too.

Now, here's the problem.

I switch back and forth between XP and Ubuntu a lot, but, every time I switch to Ubuntu from XP, ALL of my songs are always "misplaced" in every music playing program (Amarok, Banshee, etc.) I always have to add them in again, which is very annoying, since I have about 5000 songs split between both drives. I don't get why this happens. I always keep my music in the SAME folders and I NEVER move them. Yet, every time I leave Ubuntu, go to XP, and come back, all the songs are "misplaced," except for about one hundred of them.

Does anyone know why this happens, and how to fix it?

---

### Post by apolloxi on 2008-01-24
Anyone?

---

### Post by apolloxi on 2008-01-24
I don't mean to keep double/triple posting in my own topic, but can someone PLEASE respond? I'd appreciate it very much.

---

### Post by Mainiak Blaniak on 2008-01-24
I'm not sure I'll be able to help here as I'm a Linux newbie, but I'll try...

Are the music files that 'go missing' when you reboot back into Ubuntu all stored on your windows drive, or are some of them on the linux drive?

In my case I have all of my music on the windows drive, so in order for the music player in Ubuntu to use them I have to re-mount the windows drive at every login.  I know there is a way to auto-mount the drive at startup, but to be honest I haven't bothered to figure out how as it is not a big deal for me.  

if this is the case for you, try searching either here or in google for 'auto-mount drive at startup Ubuntu' or somesuch.  

if this is not your situation, please post what you do to get the Linux media player to 'find' your files again and maybe I or someone else can help more...

MB

---

### Post by apolloxi on 2008-01-25
My entire collection of music is split between the two drives. I have some in the C Drive (Windows), and others in the D Drive (Ubuntu).

But, it doesn't really matter. Music from BOTH drives always go missing. Only a (seemingly) random selection of about 100 or so songs (I never bothered to count) remain. And, I have about 1500 songs on my Ubuntu drive, so it isn't an issue of Ubuntu not reading them from Windows. Ubuntu (and, by "Ubuntu", I mean my media players: Amarok, Banshee, etc.) seems to lose EVERYthing, even on its own drive. I can still access my music files and view them perfectly fine through the File Browser. My media players just always lose them.

Everytime, whenever all my music goes missing in my media players, I simply delete the playlist (in Amarok, Banshee, etc.) and load all my music again from all the folders they are in. Then, it works perfectly fine. But, still, as soon as I shut off my computer and reload Ubuntu, my media players loses them all again.

And, as I just recently discovered, it doesn't matter whether I go to XP and back to Ubuntu, or whether I shut off from Ubuntu and go directly back into it: they still get lost.

---

### Post by apolloxi on 2008-01-25
Also, thank you for responding. I appreciate it. I'm glad someone finally did.

---

### Post by Mainiak Blaniak on 2008-01-25
No Problem...still not sure I can help but I'll keep trying...

Just for giggles I tried putting a little music on my linux drive (in my /daniel/music folder) and then re-booted...Rhythmbox found those four files on restart, but not the 1500 or so on the windows drive.

this still seems like either a drive mounting or permissions thing to me.  When you re-boot into Ubunutu, are the songs that your music players find always the same ones, or is it a random list?  is the list the same between the two players?  Are all the files the player finds in one directory, and all the others in other directories?

What folders are you storing the music in on the Linux drive?  do you have to enter your 'root' password for access when you re-connect to them after re-booting?

basically, I'm just trying to do process of elimination here to work through the things i think it might be that I know enough to maybe help :)

MB

---

### Post by apolloxi on 2008-01-26
Okay. I made a few more discoveries from your list of questions:

Yes: the only 100 or so songs remaining are always the SAME, and it's the same between the two players.

I didn't confirm if all the aforementioned files were in the same folder or scattered, but I'm pretty sure they are.

On my Linux drive, all music is stored on "/home/sean/SAM/Music"

---

### Post by Mainiak Blaniak on 2008-01-26
Hmmmm....

I think your discoveries are starting to shoot holes in my initial theory.  Since all of your music files on the linux drive are in the same place, I'm assuming then that the files that do not 'go missing' are on the windows drive?  is that correct?

While waiting for your answers to my last question, I messed around with getting my windows drive to auto-mount at start up, and now rhythmbox doesn't lose my library.  You had mentioned Amarok and Banshee...have you tried rhythmbox, and if so, do you get the same result as you did with Amarok?

I'm going to try messing with Amarok and see how that works for me...maybe I'll be able to duplicate your problem.

MB

EDIT:  I just installed Amarok...it is behaving VERY badly in my Gnome environment.  I was able to get it to find my music collection spread across both drives, but it freezes up any tme I try to play a song.  Are you using Gnome or KDE?  If Gnome, and you don't like rhythmbox, I believe there is a player called exaile that is similar to Amarok, for the Gnome environment.  I have not used it personally tho...

Edit #2:  So much for my plans here...now I'm having issues!  When I set up the auto-mount of the drive, it's getting put on a different mount point than where I had it when I manually mounted it.  Now Rhythmbox doesn't like it so I'm trying to fix those settings.  At any rate, I noted in this process that rhythmbox apparently only allows one folder location for a main 'library' and then allows importing of additional folders.  Not sure if this will cause a problem with our dual drive setups or not...back in a bit with more info.

Edit #3:  I'm still fracked up.  I found a thread about what I have run into and the OP in that thread solved his problem by installing beep media player and changing the output plugin from OSS to ALSA.  I tried that, except it was already set on ALSA so I switched to OSS.  Worked that time, but then on reload it failed.  Still working it...more to come.

---

### Post by apolloxi on 2008-01-27
Actually, I think the problem is bigger than my media players or my music files.

I've noticed that, everytime I reboot and attempt to save a website or something ON a website, the file save window automatically opens up in a folder I haven't saved anything in for a few weeks, instead of opening up in the default folder. It's as if the system is "frozen" into whatever I did last however many weeks ago. And, I guess, for whatever reason, I barely had any music a few weeks ago.

But, to answer your question, all the 50 or so songs that never go missing are on the Ubuntu drive.

---

### Post by Mainiak Blaniak on 2008-01-28
Hmmm...Ok....

I think we're probably getting beyond my VERY limited experience here.  It certainly appears that it's not a permissions issue, as the music player is finding some songs in one folder but not others.

I'm guessing you already tried telling the music player to refresh/reload your music library?  and or changed the setting to 'automatically watch this folder for updates' type things?

as far as saving downloads to a particular file...here goes...

if you are using firefox, in the edit/preferences menu, on the "main" tab there are a couple of settings for downloads...one is the default folder for them to go into, which you can set to your liking.  there is also an option to 'always ask'.  perhaps one of those settings got switched inadvertently....

MB

---

### Post by apolloxi on 2008-01-30
I actually just figured out the problem a day ago. I simply needed to run fsck: I had a lot of errors on my file system. Now that I took care of that, everything is fixed. My songs now stay in my media players when I shut down.

Sorry for having spent so much of your time on a problem with such an obvious solution. I appreciate you having been with me throughout the post, though. Thanks.  ^_^

---

### Post by Mainiak Blaniak on 2008-01-30
Hey, glad you got it sorted out.  

I don't mind trying to help at all, as it is a good way for me to try to learn new things on Ubuntu.  So far my system has been pretty stable, and apart from a couple of things I had to deal with regarding wireless and video drivers when I first installed, has run well 'out of the box'.  This gives me some kind of direction in learning.

Thanks for letting me know you got it solved!

MB

Edit:  Oh yeah...the solution certainly wasn't obvious to me...so yet another chance for me to learn!

---

