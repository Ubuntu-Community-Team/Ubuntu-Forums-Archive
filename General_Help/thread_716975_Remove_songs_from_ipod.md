---
title: "Remove songs from ipod"
date: 2008-03-06
forum: General Help
---

### Post by bobbo85 on 2008-03-06
Is there a way to remove songs from your iPod in Ubuntu?

Here is my current method, which is a pain in the butt:
1)  In Rhythmbox, right click the song in the iPod playlist, hit "Move to trash"
Note:  This does not remove the file from the ipod, so it still occupies space!

2)  In nautilus, navigate to /media/iPOD/iPod_Control/Music/

3)  Check each subdirectory from F00 to F99, locate and delete the mp3 or mp3s (with shift delete, or empty the .trash folder that appears in the iPod directory) you are trying to get rid of.

I feel like I shouldn't have to delete the songs twice, and sometimes finding them can be a pain too!

Thanks in advance.

---

### Post by LuisGMarine on 2008-03-06
Let me get this right, you are removing the songs through your playlist, but you want them to be off your iPOD?

Because if you are, you can't do that, not in windows.  When you click to remove a song off your ipod through the playlist its going to remove it off the playlist.  Not your iPOD.  When you are in rhythmbox  click on your ipod icon, not the playlist, and then remove the song from there, and make sure you sync.

---

### Post by bobbo85 on 2008-03-06
> **LuisGMarine said:**
> Let me get this right, you are removing the songs through your playlist, but you want them to be off your iPOD?

Because if you are, you can't do that, not in windows.  When you click to remove a song off your ipod through the playlist its going to remove it off the playlist.  Not your iPOD.  When you are in rhythmbox  click on your ipod icon, not the playlist, and then remove the song from there, and make sure you sync.

Thanks for the quick response Luis.
Sorry for the poor wording.  

I am selecting my ipod icon as you mentioned, then right clicking and selecting "Move to trash."

I don't think I have a "Sync" option for my ipod, just rename or eject (Which by the way doesn't work... I have to eject the ipod from "my computer" in nautilus).

I did just find this article online:
[http://www.kittypee.com/2007/11/16/rhythmbox-ipod-sync-plugin/](http://www.kittypee.com/2007/11/16/rhythmbox-ipod-sync-plugin/)

What are your thoughts?

As it stands, the plugin for Rhythmbox I already have allows me to drag new songs to the ipod, it just doesn't remove the files from the ipod.

---

### Post by LuisGMarine on 2008-03-06
Weird I'm going to have to do some research over here on my side.  Right now however I don't have my iPod I left it in my car and its currently at a shop getting a sound system installed in it.

Later tonight I'll pose back if I find something, have you tried right clickon on the ipod icon inside rhythmbox to see if it has a sync option?

---

### Post by LuisGMarine on 2008-03-06
Sorry about taking a while about that.  I'm having some issues of my own.

Anyhow, go ahead and open up rhythmbox and then click on the ipod icon and click the tracks that you want right-click, and go to move to trash.  Then right click on the ipod icon and click eject, that should write to the ipod.

Try opening up synaptics and reinstalling rhythmbox also.  If that doesn't work theres something else, I'm not sure what ....  can't be that heard to fix I"m sure, we just gotta strike gold for when we look for the problem.

---

### Post by LuisGMarine on 2008-03-06
Hey go ahead and follow the link at the bottom of my signature and try songbird.

Honestly it imitates itunes to the T.  Removing/adding songs.  As soon as I hook up my ipod it adds new tracks, folder watching for new material works like a charm.  I know its in the early developing stages, and crashes every once in a while, but hey its a freaking good program.

Give it a try and tell me how it works with manging your iPod.  My guide is pretty detailed on how to do a full install and little extra stuff I threw in there.

---

### Post by bobbo85 on 2008-03-07
I have just used synaptic to "completely remove" and reinstall rhythmbox, and I still can't get the iPod to eject.
I tried running Rhythmbox from the console and hitting "eject" on the ipod; here is the result:

(rhythmbox:21041): Rhythmbox-CRITICAL **: got MTPSourceEject action for non-mtp source

Any ideas?

Thanks for the links for Songbird, I'll check that out.  In the meantime I have also installed Amarok and am tryin that out too.

---

### Post by bobbo85 on 2008-03-07
Just to let you know, reinstalling Rhythmbox did make a difference :-)

It will write to the iPod correctly, I just have to eject using nautilus in "Computer" - not from within rhythmbox.  It then asks me if I want to clean the trash and save space on the iPod.

So thank you for the tip!

I tried Amarok today, love it so far- one question though, how can I list all the songs from my iPod?  In rhythmbox, I just click on the iPod in the side panel, and the list of songs shows up, so I can delete songs I don't want on there.  In Amarok, it seems all I can do is use the tree structure on the left - expanding each artist one at a time to see all the songs... huge pain!

---

### Post by LuisGMarine on 2008-03-07
Glad it worked!  I'm not sure I can help you on the Amarok, since I don't use it, I think I only tried it once and then I decided KDE just wasn't for me.  I'm sure that there are options to change the view of Amarok.

For example the tree structure might be one of the view options, so look around to see if you find a " View " menu, and see if you can change the " Tree Structure "

---

