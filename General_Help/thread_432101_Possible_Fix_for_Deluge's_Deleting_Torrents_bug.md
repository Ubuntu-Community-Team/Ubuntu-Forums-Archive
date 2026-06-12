---
title: "Possible Fix for Deluge's Deleting Torrents bug"
date: 2007-05-03
forum: General Help
---

### Post by SlackLagg on 2007-05-03
*NOTE: If anything like this before has been posted, feel free to delete this or move it to another area. 

*NOTE: I make no guarantee that this will work 100% of the time for 100% of the users. This is merely something I stumbled upon and , happen to be kinda proud of.  It may work for you, or it may cause your computer to catch on fire. Who knows. 

*EDIT/NOTE : This was done for the 0.50 i386 build for Feisty. If you're running x64 and/or using a version < 7.04  then you'll definitely want to look at note # 2. 


I got turned onto Deluge a couple of days ago after Azureus started acting up (hey I was surprised it worked that long) . While I contemplated the idea of installing Azureus via Automatix or what not, I decided to give Deluge a fair shake. 

I noticed several users complaining about how Deluge would delete ( I'd rather say "forget" because they are still on the system, they just don't load properly , but thats another issue ) new torrents if the program crashed or if the system was shutdown while Deluge was still running. I poo-pooed this until I shutdown my machine with torrents running. Twice. 

Having dabbled in python very shallowly, I decided to see if there as a fix. Sure enough I found something. I saw three ways of fixing this bug. 

1) Deluge automatically does a save state (the code calls it "pickling" ) when you manually quit the program. You could just remember to restart the program after each new torrent you add.  This would require a change in how users operate their computers and lemme tell you, thats not gonna happen

2) Alert the developers.  After I looked at the code to see what needed to be fixed, this is such a trivial thing that I'm sure they have much better things to be doing. 

3) Remember that "pickling" the program does? All I had to to do was make it pickle whenever a torrent was added. 

As if you couldn't tell, I'm going to do number 3

*How do you do that?*

Pretty simple. The answer lies in the deluge.py file. 

*Where's that? *

It's most likely under the /usr/share/python-support/deluge-torrent/deluge/ 

```
 sudo gedit /usr/share/python-support/deluge-torrent/deluge/deluge.py 
``` 

You'll want to go look for a command called "add_torrent_ns" (Should be around line 611). Scan over that code and move your cursor to right after the line that says 
```
self.state.torrents.append(new_torrent) 
```

After this line you'll want to copy and paste the following hunk

```
 
		self.pre_quitting()

		# Pickle the prefs
		print "Pickling prefs..."
		output = open(self.base_dir + "/" + PREFS_FILENAME, 'wb')
		pickle.dump(self.prefs, output)
		output.close()

		# Pickle the state
		print "Pickling state..."
		output = open(self.base_dir + "/" + STATE_FILENAME, 'wb')
		pickle.dump(self.state, output)
		output.close()

		# Save fastresume data
		print "Saving fastresume data..."
		self.save_fastresume_data()
	

```

I'm no python wizard, but try to get it so that the section you just pasted has the same tab spacing as the rest of the code. 


* Humm pretty neat, but where did that code come from ? * 

That piece of code is actually from the quit method. Look around line 251 or so and you'll see that it extends all the way down to around line 260. 

Make sure you backup your original deluge.py first (rename it to deluge_old.py or something) 

* You're full of bologna. This code is garbage *

Highly probable. I'm no expert and I'm sure as heck not one of the smart guys that developed this program to begin with. As I said earlier, if you want to try this, make sure you backup your original file.

---

### Post by icheyne on 2007-05-06
Thanks! That works for me. Now I see the true beauty of open-source! That was my only complaint with Deluge.

(One small point - when I did a: ```
locate deluge.py
``` I found several options. The one that worked for me was ```
/usr/lib/python2.4/site-packages/deluge/deluge.py
```.

I might have to give Python a go...

---

### Post by SlackLagg on 2007-05-07
Thanks for the contribution ! 

I'm glad this has helped somebody else out. 

I thought about tackling the "Deluge crashes out and I have to delete a .state file  so the program will work again" bug but It would seem that the dev's have already fixed that in the subversion (which I haven't downloaded because I can wait until the .51 release)

I've also thought about adding some more features as well as fixing some :confused: things like why you can't add a torrent from your .config/deluge/torrentfiles/ dir  or how the file extension MUST be .torrent , but I have faith the devs will cook up their own neat features in due time.

Python does seem pretty cool. This summer I'll be doing a pyGtk project for school. Not too much hardcore coding, mostly just scripting. Hopefully I'll be pretty slick at python by the end of summer (and hopefully I'll have a neat little program for others to enjoy, or at least point and laugh at )

---

### Post by fearpi on 2007-05-09
Nice find. Small bit of information if you're curious: Pickling is not unique to deluge's code. It is a relatively new python method for writing an object to disk, exactly as it appears in memory.

---

### Post by SlackLagg on 2007-05-11
> **fearpi said:**
> Nice find. Small bit of information if you're curious: Pickling is not unique to deluge's code. It is a relatively new python method for writing an object to disk, exactly as it appears in memory.

Oh very neat.  I'm really reading up on python and pyGTK in preparation for my project this summer , but I haven't gotten to that yet.

---

### Post by mills on 2007-05-21
nice find, now time to get some dirty torrents and see if it works:D

---

### Post by SlackLagg on 2007-05-22
Heh, don't try too hard. Deluge (as of .50, haven't tried any SVN) still has an issue with the persistent.state file getting corrupted and needing to be deleted. (I thought about trying a fix for that via just backing up the persistent.state file and copy from backup if there was a problem, but I've been strapped for time)

---

### Post by mills on 2007-05-23
just needed to delete that persistent.state file

if you could come up with a fix for that youd be a bit of a legend in my books

how long you been learning python?

---

### Post by SlackLagg on 2007-05-27
I've only been looking over it casually for about a month now. Once summer class starts I'll be working on that project for school so I'll need to learn quickly. 


From what I've read on the deluge-torrent.org forums,  most of the problems that cause the persistent.state to get corrupted have been fixed in the SVN release, but I haven't felt the need to mess with that just yet.

---

