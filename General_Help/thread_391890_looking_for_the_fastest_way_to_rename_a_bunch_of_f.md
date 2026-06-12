---
title: "looking for the fastest way to rename a bunch of folders by id3 tags"
date: 2007-03-23
forum: General Help
---

### Post by TeeAhr1 on 2007-03-23
Here's the downlow.  I just spent three (3) months renaming and tagging every last one of my songs with EasyTag.  They're all organized like /music/artist/album/1 - foo.ogg.  But the folder names for $ALBUM are a huge mishmash of other people's organizational schemes.  I want every album folder to be: $YEAR - $ALBUM.  I have 125 GB of music (yeah, just music).  I do not want to do this by hand.  What is the absolute fastest way to accomplish this task?  Any advice always appreciated, alliterations always advantageous!

best regards
-p.

---

### Post by TeeAhr1 on 2007-03-23
And how the heck did I manage to put this in "Desktop Environments?"  Sorry... :-?

---

### Post by TeeAhr1 on 2007-03-23
Here's the downlow. I just spent three (3) months renaming and tagging every last one of my songs with EasyTag. Hassle?  You bet.  Are they finally perfect?  Absolutely.  Am I satisfied?  Of course not.

They're all organized like /music/artist/album/1 - foo.ogg. But the folder names for $ALBUM are a huge mishmash of other people's organizational schemes. I want every album folder to be: $YEAR - $ALBUM. I have 125 GB of music (yeah, just music). I do not want to do this by hand. What is the absolute fastest way to accomplish this task? Any advice always appreciated, alliterations always advantageous!

best regards
-p.

---

### Post by freakavoid on 2007-03-23
Did you try the audio tag tool (install per add/remove...)? It has a feature to rename files using id3 data.

---

### Post by TeeAhr1 on 2007-03-23
No, that part's already done.  Now I want to rename the folders.  EasyTag does that, but only one at a time (AFAIK).  Does Audio Tag do bulk folder renaming?

---

### Post by freakavoid on 2007-03-23
Don't know about easyTag but with audio tag you can do that. Just load your entire collection using "include subdirectories" option (assuming you have one main folder, "music" or such...) and rename them with the tool on the 4th tab at the right panel. You can structure them so that it reads the year information and changes the folder name accordingly. Just do something like /music/<artist>/<year> - <album>/<title>.

---

### Post by TeeAhr1 on 2007-03-23
Sweet, thanks!  I think I'm close, but I must not be formatting this correctly.  I'm testing it out with Billy Joel.  So, my working directory is /foo/music/Billy Joel/.  I set my parameter to "<year> - <album>/<track> - <title>".  Everything moved correctly, but instead of renaming the folders, it put another folder inside them.

I hope I'm explaining that clearly.  So now it's /foo/music/Billy Joel/original folder/new folder/foo.ogg.

Where'd I go wrong?

thanks a ton
-p.

---

### Post by TeeAhr1 on 2007-03-23
Also: It doesn't seem to like folders with other folders, which is how I have 2-disc albums set up.  "/foo/music/BIlly Joel/album/CD1/foo.ogg".  I can live with that.

Also also: Can I make it rename only folders and ignore files?

---

### Post by freakavoid on 2007-03-23
Hmm, I didn't see that coming. I played around a bit and it seems tagtool only works in the current directory which holds the particular song. The intuitive suggestion would be to format them like /home/username/music/<artist>/<year> - <album>/<title> but it complains about the nonexistence of the home directory. So, one ugly solution is to move all the songs to the main music folder and do the trick then.

---

### Post by TeeAhr1 on 2007-03-23
Ick.  More of a hassle than it's worth, I think.  But I think I'm close here, I'm gonna keep trying.  Thanks!

-p.

---

### Post by freakavoid on 2007-04-06
Here is a perl script to the job. Just read the comments in the file to find out how to make it work. And you can always play around with the "wanted" subroutine to change the directory structure to suit your needs.

---

### Post by strabes on 2007-04-07
I believe that the ID3 tagger that comes with quod libet does this. It's called "ex falso" I think.

---

