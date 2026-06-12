---
title: "Outyliner and MIndMapper"
date: 2008-05-14
forum: General Help
---

### Post by HenryTSTabruck on 2008-05-14
I cannot seem to find a well-designed outliner or mind-mapper for the new Ubuntu.  I've tried installing FreeMind, but it will not open properly.  Previous posts seem to indicate a Java issue.  I looked at the Vim outliner, but it seemed to be an awkward interface.  However, I was able to install C-Map, the concept mapping program.

---

### Post by Eric Weir on 2008-05-14
> **HenryTSTabruck said:**
> I cannot seem to find a well-designed outliner or mind-mapper for the new Ubuntu.  I've tried installing FreeMind, but it will not open properly.  Previous posts seem to indicate a Java issue.  I looked at the Vim outliner, but it seemed to be an awkward interface.  However, I was able to install C-Map, the concept mapping program.

I've been looking for a good outliner and free form database applications for Linux since switching over from Windows. I haven't found anything. They're all way too simple or way too cumbersome. They all seem to have been designed and devloped by folks who think such a thing would be a good idea, but don't actually understand how they might be be used. 

I've used a DOS outlining application called MaxThink since the mid-80's. There's nothing like it. [See this [http://www.eatonhand.com/maxthink.htm](http://www.eatonhand.com/maxthink.htm) and this [http://maxthink.biz/13_mental_equipment.htm](http://maxthink.biz/13_mental_equipment.htm) ] There was a Windows GUI version, but it's not the same program in my opinion. Neil Larson, the developer, says he's working on a port of the command driven version for Linux and OSX, but it's a long time in coming. 

Meantime, I continue to use it in a DOS window in XP on a laptop, and in DOSbox on my Xubuntu machine.

Regards,

---

### Post by tacutu on 2008-05-14
freemind works fine in Ubntu. An older version is even in the repos.
also, you might want to try semantik.

---

### Post by Eric Weir on 2008-05-14
> **tacutu said:**
> freemind works fine in Ubntu. An older version is even in the repos. also, you might want to try semantik.

Thanks. I'll check em out. I've heard of free mind. Haven't actually tried it. In my mind, mindmapping is not what I'm looking for. But maybe I should give it a try. Haven't heard of semantik.

Sincerely,

---

### Post by HenryTSTabruck on 2008-05-30
Freemind does not work properly in the Hardy Heron release.

I agree with the Maxthink/DOS appraisal.  I still use the old Maxthink in a DOS window on my Windows OS.  The newer Maxthink for Windows is not as appealing.

---

### Post by fbnaia on 2008-05-30
I've been using freemind 0.8.1 with no problems even before upgrading to Hardy, i do remember i had to use an older version of java to get it working, but right now i'm using the latest java without problems...

You can follow the instructions [**here**]("http://freemind.sourceforge.net/wiki/index.php/Download")

Theres even an "all inclusive" version, maybe that one will work for you...

---

### Post by Eric Weir on 2008-05-30
> **HenryTSTabruck said:**
> I agree with the Maxthink/DOS appraisal.  I still use the old Maxthink in a DOS window on my Windows OS.  The newer Maxthink for Windows is not as appealing.
Good to hear from someone who shares my opinion of MaxThink, Henry. I just had an exchange with Neil Larson a few days ago, in the course of which I asked about the Linux/OSX command-drive version he says he's working on. 

Alas, sounds like it'll be a while. There's nothing like MaxThink. And it's beginning to look like only someone with Neil's brain could even conceive it. 

I've been looking hard since I made the move to Linux, and I haven't come up with ANYTHING that can hold a candle to it.

Again, good to know you're out there.

Sincerely,

---

### Post by HenryTSTabruck on 2008-06-01
Eric, I'm new to Linux/Ubuntu, so the DosBox setup is unfamilar to me.  Do I simply run DosBox in Ubuntu, then access Maxthink from its Windows folder in the other partition?

---

### Post by Eric Weir on 2008-06-01
> **HenryTSTabruck said:**
> Eric, I'm new to Linux/Ubuntu, so the DosBox setup is unfamilar to me.  Do I simply run DosBox in Ubuntu, then access Maxthink from its Windows folder in the other partition?
You'll have to install it first. It's in the repositories. Search for it in Synaptic. After it's installed, it'll be in the menu under games. Then create a directory in your /home folder to put your MaxThink files in. I've called mine "dosapps." After you run DOSbox, mount the folder where the MaxThink files are located,  and then the folders you want MaxThink to have access to. Here's what I do, i.e., in DOSbox:

Mount the folders:
```
mount c /home/eric/dosapps
mount d /home/eric/mydocuments
```Switch to the folder with the MaxThink files and run MaxThink
```
c:
Max
```That's it.

You should check out DOSbox manual. Look for it in /usr/share/doc after DOSbox has been installed. There is a DOSbox website and a DOSbox forum, at, respectively, [http://www.dosbox.com/](http://www.dosbox.com/) and [http://vogons.zetafleet.com/index.php](http://vogons.zetafleet.com/index.php) In the latter, scroll down to the 7th set of forums.

Last thing: You can configure DOSbox so that when you run it it automatically mounts the appropriate folders and runs MaxThink. To do that create a configuration file. In DOSbox type:

```
config -writeconf dosbox.conf
```After you've done that, find the "dosbox.conf" file. It should be in the same folder as the DOSbox executable, in my case /usr/bin. [Though in my case I can't find it there right now, but wherever it is it's working.] Open it with a text editor. Go down to the very last section, "[autoexec]," and enter the lines you use to start MaxThink from within DOSbox, e.g., in my case, the lines above. 

The default DOSbox window is pretty small. You can enlarge it, but I've not found a way to do it without ruining the graphics. I've learned to live with it. I *can't *live without MaxThink.

Also, the keypad keys and caps-lock don't work for me. That may be something about my setup. The keys can be remapped, but I haven't gotten around to that, yet.

Good luck.

---

### Post by JohnMcD on 2008-06-01
Hi Eric,

Chiming in as another old time MaxThink fan. I saw your mention on another post and just got it running in DosBox. Works ok so far. Would you believe I even found my old paper manual? (you remember them?)

I gave up on MaxThink when Neil went off on his windows tangent. I did find an even better replacement called BrainStorm. Alas, it only runs on windows. My results with Wine were less than satisfactory.

I too have been looking for a decent replacement to run on my Linux box. Haven't been happy with any of them. I did get FreeMind to work ok. You can do most things from the keyboard, but it's java, takes forever to load and uses a lot of resources. Tried NoteCase, Zim, TomBoy notes and I'm still looking.

You might try hnb (hierarchical notebook), it's in the repository and runs in the terminal. I tried it a couple weeks ago and couldn't figure out how to move entries. Re-installed today and found the key. Before you can move an entry, you have to grab it first with Ctrl G. Then you move the entry with the arrow keys and drop it with the return key (or space) when you're satisfied.

hnb is a single pane outliner that saves in xml format. Don't think it's been updated since 2003, but it seems to work. I could never understand why everyone wants a dual pane outliner. I'm going to give hnb a tryout while I play with old MaxThink.

McD

---

### Post by HenryTSTabruck on 2008-06-03
Eric, thank you for the DosBox guidance.  

Have you Maxthink devotees also tried Ecco Pro?  It permits column values alongside the outline.  I've migrated most of my Maxthink/DOS files to Ecco.  However, I don't think there is a way to get Ecco to run on Ubuntu.

---

### Post by JohnMcD on 2008-06-03
Hi Henry,

I had forgotten that I too migrated from MaxThink to Ecco Pro. I forget why I gave up on Ecco. I think it was because I couldn't get it to co-operate with emailing and such. Great app. I still have my CDs and manual in my closet. Too bad NetManage has never released Ecco as open source. Now wouldn't that be special.

McD

---

### Post by HenryTSTabruck on 2008-06-03
John,

Efforts to revive the development of Ecco Pro stalled for a long time until some talented programmer created "Ecco Extensions," available in the Yahoo Ecco Pro Group file section at [http://tech.groups.yahoo.com/group/ecco_pro/files/](http://tech.groups.yahoo.com/group/ecco_pro/files/).  He's breathed new life into the program, adding many useful features.  Why not download a copy of "eccoext4.0.0.1.rar" and try it out with Ecco.

---

### Post by JohnMcD on 2008-06-04
Henry,

I did reload Ecco a couple of years ago. I don't want to go back now because I'm using a ubuntu only box now so no winapps. If I did go back to a windows app, it would be BrainStorm. BrainStorm is a lot more flexible than Ecco and in some respects more powerful. BrainStorm has a long heritage as well going all the way back to the late 80s with continuous development. Latest windows version released at the end of 2007.

I'm making a real effort to "go native" and discover which apps suit me best. I'm a ubuntu newbie (only got my system 5 weeks ago) so I'm still learning, but loving every minute.

McD

---

### Post by Eric Weir on 2008-06-04
> **JohnMcD said:**
> Chiming in as another old time MaxThink fan. I saw your mention on another post and just got it running in DosBox. Works ok so far. Would you believe I even found my old paper manual? (you remember them?)
I have two of them. One for the '89 version that I use and one for the '94 version that I own but don't use.

> I gave up on MaxThink when Neil went off on his windows tangent. I did find an even better replacement called BrainStorm. Alas, it only runs on windows. My results with Wine were less than satisfactory.I tried the Windows version but didn't like. Not the same program at all. I continued with MaxThink in a DOS window with very little problem. Only discovered Brainstorm about a month before I started making the switch to Linux. I liked it. Good at manipulating blocks of text. Struck me as not so facile as MaxThink in working with word and sentences.

> I too have been looking for a decent replacement to run on my Linux box. Haven't been happy with any of them. I did get FreeMind to work ok. You can do most things from the keyboard, but it's java, takes forever to load and uses a lot of resources. Tried NoteCase, Zim, TomBoy notes and I'm still looking.I never got around to FreeMind. Mind-mapping doesn't appeal to me. Maybe a prejudice I should get over. But I've tried all the others and, like you, I'm still looking. 

Frankly, I'm almost convinced that only Neil could create it. I wish he'd put his mind to it. My last exchange with him a couple weeks ago -- I was inquiring about the status of the Linux/OSX version of MaxThink -- he said he's also working on a new version of Houdini. I take it also for Linux/OSX. 

Did you ever try that? I did, but it never became as intuitive for me as MaxThink. In fact, some times it got me downright confused.

> You might try hnb (hierarchical notebook), it's in the repository and runs in the terminal. I tried it a couple weeks ago and couldn't figure out how to move entries. Re-installed today and found the key. Before you can move an entry, you have to grab it first with Ctrl G. Then you move the entry with the arrow keys and drop it with the return key (or space) when you're satisfied.

hnb is a single pane outliner that saves in xml format. Don't think it's been updated since 2003, but it seems to work. I could never understand why everyone wants a dual pane outliner. I'm going to give hnb a tryout while I play with old MaxThink.I came across it somewhere, and checked out the web-site, but it wasn't clear to me how it worked. Please keep me in mind as you get more experience with it. And I'm all with you on single-pane outliners.

Again, good to hear from another MaxThink veteran.

Sincerely,

---

### Post by Eric Weir on 2008-06-04
> **HenryTSTabruck said:**
> Efforts to revive the development of Ecco Pro stalled for a long time until some talented programmer created "Ecco Extensions," available in the Yahoo Ecco Pro Group file section at [http://tech.groups.yahoo.com/group/ecco_pro/files/](http://tech.groups.yahoo.com/group/ecco_pro/files/).  He's breathed new life into the program, adding many useful features.  Why not download a copy of "eccoext4.0.0.1.rar" and try it out with Ecco.
I never got around to Ecco. I think I'd heard of it way back there a long time ago, but I never had any idea what it was like until I started looking for a replacement for MaxThink on Linux, and now I've forgotten what I learned. 

Maybe this programmer could help Neil with getting MaxThink going on Linux.

I take "Ecco Extensions" runs on Linux? [Easy enough to check for myself.]

Regards,

---

### Post by Eric Weir on 2008-06-04
> **HenryTSTabruck said:**
> Efforts to revive the development of Ecco Pro stalled for a long time until some talented programmer created "Ecco Extensions," available in the Yahoo Ecco Pro Group file section at [http://tech.groups.yahoo.com/group/ecco_pro/files/](http://tech.groups.yahoo.com/group/ecco_pro/files/).  He's breathed new life into the program, adding many useful features.  Why not download a copy of "eccoext4.0.0.1.rar" and try it out with Ecco.
Clicked on this link to check it out and ended up in a confusing Yahoo joining process. I really don't like Yahoo. 

Regards,

---

### Post by JohnMcD on 2008-06-04
Hi Eric,

I lost my copy of Max 89 somewhere along the way, but I have Max 94. I did try Houdini but it never took with me. I think that I must have bought every program Neil ever published. That is until he came up with his windows version.

BrainStorm is deceptive in it's apparent simplicity. I bought it and used it for a few months then it sat idle for about a year. When I started using again, I discovered all kinds of neat features. There's a lot of power under the hood that the user needs to discover for themselves.

I used FreeMind on Monday to put the skeleton together for an article I was writing. FreeMind is really not a true mind map program. It's more of an outliner. Nice thing is that you can do almost everything from the keyboard. It's pretty good for brainstorming, each time you finish a thought you hit enter once, then hit enter again for the next thought.

hnb works from the command line in a terminal session. Just type hnb, hit enter and a sample outline will come up. Most of the instructions are accurate. The one that threw me was moving nodes around. I think I discovered the grab with ^G while reading the configuration file.

Entering text is simple. Press insert to begin and hit enter when you're finished. Then you can add another node with the insert key. I don't see a way to do child nodes as you go. Each new node appears under the last, then you can go back and move them around.

That's pretty easy. The < and > keys either demote or promote. When you want to move a node, just press ^G to enter grab mode and move with the arrow keys. When you're happy with the new location, either space or enter will place the node in the new location.

It's easier to play with than explain (once you understand the ^G trick). You open a new file by typing hnb <filename> and you'll be in your file.

I found the author's web site. He doesn't use hnb any longer and hasn't updated it for about 5 years, but it still works.

Oh, I forgot to mention that one of the best features of FreeMind is you can drag any block of text to a node and it will suck it in neatly. Works in the opposite direction as well. You can drag nodes right into your editor. I've decided to use FreeMind for brainstorming and organizing draft articles.

But for keeping track of all the stuff that floats by, I'm testing Tomboy. You can almost use it like a two pane outliner if you use the new notebook feature. Still in the early stages of discovery.

MCD

---

### Post by HenryTSTabruck on 2008-06-05
I've re-installed Freemind several times, but cannot get it to work under Hardy Heron.  It appears that an earlier Java release may be needed, but I'm not sure how to solve this issue.  

Eric, Ecco Extensions is not Linux compatible, it runs alongside Ecco Pro within a Windows OS.

I too tried Houdini many years ago, but found it too awkward for regular use, and also experimented with HyPerform from NDMA, but the learning curve was incredibly steep.

Natura Bonsai was a Windows version outliner that synchronizes with my Palm Tungsten.  I was able to import all of my old Maxthink files.

---

### Post by JohnMcD on 2008-06-06
I haven't had any problems running FreeMind under hardy. I did a clean install instead of an upgrade.

I tried some of those palm outliners. Close, but still no cigars. Most of the so called outliners available are really note taking programs with a tree structure in one window and notes in another.

I've zeroed in on FreeMind as the closest thing to a single pane outliner. It's more of a graphic oriented outliner than a true mind map. Works very well from the keyboard and supports brainstorming.

I've decided that I need both a quick idea generator like FreeMind and a way to track my notes and such. I tried Tomboy for a few days, but installed Zim yesterday for a couple of good reasons.

1) Zim stores all notes as plain text files which means you can read them with your editor. Zim has a menu option to edit source that calls up your editor instantly with the note loaded. I tested this yesterday by highlighting a bulleted list in gedit, then sorting, saving and returning to Zim. Worked like a charm.

2) Tracker can find your notes because they are plain text.

3) The notes are stored in your home directory. Easy to find and back up.

Of course the jury is still out, but I think I finally found what I need and can get back to work using my tools instead of fooling with them.

McD

---

### Post by Eric Weir on 2008-06-06
> **JohnMcD said:**
> I've decided that I need both a quick idea generator like FreeMind and a way to track my notes and such. I tried Tomboy for a few days, but installed Zim yesterday for a couple of good reasons.

1) Zim stores all notes as plain text files which means you can read them with your editor. Zim has a menu option to edit source that calls up your editor instantly with the note loaded. I tested this yesterday by highlighting a bulleted list in gedit, then sorting, saving and returning to Zim. Worked like a charm.

2) Tracker can find your notes because they are plain text.

3) The notes are stored in your home directory. Easy to find and back up.
I installed Zim under my previous installation -- Kubuntu 7.04 -- and played around with it a little bit, but I didn't take to it and stopped experimenting. I do remember that it took me a while to catch on to MaxThink. 

Zim is being installed as I write. I'll give it another try. Keep me/us updated on your experience with it.

Meantime, couple interesting things I came across. The first is Leo, an outliner that's written in Python and requires Python to be installed. It was developed by a programmer for programmers, but it appears to be both powerful and versatile. I gather it's used by nonprogrammers as well as programmers, e.g., as an outliner, PIM, etc. It appears to have a big following among programmers, who are contributing to it's continuing development. E.g., it's capabilities can be extended by plug-ins. It is very thoroughly documented -- the equivalent of a multi-chapter book on line -- and the documentation is very well written, if somewhat-to-very technical in places. 

Check it out starting here [http://webpages.charter.net/edreamleo/front.html](http://webpages.charter.net/edreamleo/front.html) The documentation is linked at that site, but here's the URL for it [http://webpages.charter.net/edreamleo/frontMatter.html](http://webpages.charter.net/edreamleo/frontMatter.html) Linux users get only the source code. Installation under Linux appears not to be explained very clearly.

The second is a website that has collected information on a ton of mind-mappers, outliners, etc., etc. Many of them I've heard of. Some of the latter are not that interesting. There still doesn't seem to be anything for Linux that comes close to MaxThink [or Brainstorm]. You can find it here [http://www.mind-mapping.org/](http://www.mind-mapping.org/)

Regards,

---

### Post by Eric Weir on 2008-06-06
> **Eric Weir said:**
> Installation under Linux appears not to be explained very clearly.
I take that back. See [http://webpages.charter.net/edreamleo/install.html#system-requirements](http://webpages.charter.net/edreamleo/install.html#system-requirements) Couldn't be clearer.

Regards,

---

### Post by JohnMcD on 2008-06-06
Hi Eric,

I tried Zim a few weeks ago and didn't take to it either. This time, I read through all the docs on the Zim site before I installed. Still a bit quirky. One thing that threw me is that when you create a new page it doesn't "stick" until you enter some data. I'll keep you posted as to my adventures with Zim. I copied and pasted the dozen or so Tomboy notes with no problem. I'm taking it one step at a time.

Funny you should mention Leo. I found and installed Leo on my Windows box last year, but it seemed slow and I didn't really need it with BrainStorm installed. I looked at the repository and on the Leo site. I don't want to play with compiling code at least not until I get past the newbie phase.

I just downloaded the latest hardy updates (135 files I think). It included an update to Wine. Much as I don't want to use wine, I may try installing BrainStorm again. I couldn't get it to install under Gutsy. It did install under hardy, but the fonts misbehaved so I uninstalled. I hate the windows, etc that you get with wine. BrainStorm ran, but was a bit slow.

I think I've seen the big mindmapper/outliner site. I'm always on the hunt.

I'll keep you guys posted on my progress.

McD

---

### Post by HenryTSTabruck on 2008-06-08
I've tried Zim, which is really a wiki editor.  It has some promise, reminding me of ConnectedText in Windows (automatically created network diagrams).  After wrestling with installations of FreeMind and Semantik, unsuccessfully, I fell back on OpenOffice, wherein I could create outlines in Writer and simple flowcharts/mindmaps in Draw.  Not an elegant solution, but temporary tools.

---

### Post by Eric Weir on 2008-06-08
> **HenryTSTabruck said:**
> I've tried Zim, which is really a wiki editor.  It has some promise, reminding me of ConnectedText in Windows (automatically created network diagrams). 
After John's post expressing optimism about Zim, I reinstalled it and in the process came across my exchanges with the developer in which I was trying to understand how the linking of documents works. My frustrations with it came back to life, and I abandoned by pledge to give it another try.

Not exactly open-minded. Not consistent with the way I came to understand some of the quirky applications that I've relied on in the past and rely on today.

Something I've been circling like a coyote around a baited trap, that clearly has amazing potential for a great variety of applications is TiddlyWiki, described as "a reusable non-linear personal web notebook." It has an amazing community of developers, who, though technically proficient in the extreme, are amazingly creative, and amazingly helpful. [The superlatives are not overdone.] Following are just some relevant links:

What is a TiddliWiki  [http://www.tiddlywiki.org/wiki/Main_Page](http://www.tiddlywiki.org/wiki/Main_Page)
Getting a TiddliWiki [http://www.tiddlywiki.com/](http://www.tiddlywiki.com/)
Getting started with TiddliWiki [http://tiddlywiki.com/#GettingStarted](http://tiddlywiki.com/#GettingStarted)
Examples of things people have done with TiddliWikis [http://giffmex.tiddlyspot.com/](http://giffmex.tiddlyspot.com/)
The TiddliWiki community [I get it by email.] [http://groups.google.com/group/TiddlyWiki?hl=en](http://groups.google.com/group/TiddlyWiki?hl=en)

VERY interesting.

Regards,

---

### Post by JohnMcD on 2008-06-08
Wow, tiddlers and such. Who'da thought? I like your Coyote simile Eric. I played with the TittlyWiki site. Didn't download the file but I'll keep it on my radar. I'm starting to get the feel of Zim and want to concentrate on one app at a time. The developer is talking about tags and categories for future plugins. 

Finding new apps is fun though. I finally got BrainStorm working under Wine, but it loses much of it's functionality. I don't like wine.

I wrote an article today using a workflow that started with a fountain pen (yeah, I still use them) and a yellow pad for a hand done mind map. Then I fired up FreeMind and refined my map, developing the skeleton for my article. Printed up the map and fired up Abiword for my first draft. Worked out nicely. I started using abiword for my drafts because it's fast, but mostly because I like the plugins. You can right click a word and look it up in either the dictionary or a thesaurus. Figured I needed to settle down and get some work done.

Henry, there is a new mind mapper in the repository called Labyrinth. It's a 0.4.0 release. Might be easier than using Draw. I played with it for awhile. Looks promising.

McD

---

### Post by HenryTSTabruck on 2008-06-11
John, I too do much note-taking and diagramming (mind maps, concept maps, & genograms) using a fountain pen (Namiki, retractable fountain pen, extra fine point, dense black ink on light green paper.  

Were you able to get Freemind (which installation package?) installed under Hearty Heron without changing the Java version?  I've tried intalling the Debian version several times--it installs, but won't fully open.  

I've tried Labyrinth, TiddlyWiki, and Zim, and plan to give AbiWord a spin.  Discovering all these applications through you and Eric has been delightful.

---

### Post by JohnMcD on 2008-06-11
Hi Henry,

I wrote a long reply and lost it somehow. I'll get back to you later. I should get back into the habit of doing my replies in gedit first.

McD

---

### Post by JohnMcD on 2008-06-11
Hi Henry,

Here goes again. This time I'm typing in gedit first. I have two Namikis, a retractable like yours and a fine nibbed Falcon. The Falcon is great for drawing. I have three other pens inked; a Mont Blanc (monster 149) my wife gave me years ago, a Pelikan with custom italic nib and a wonderful parker vacumatic. Been using Noodler's black in most of my pens for a few months.

I suppose I've been luck with FreeMind. I just installed 0.7.1 from the repository and it worked. I have an AMD64 system that I purchased about 6 weeks ago. I came with Gutsy preinstalled. The guy who sold me the machine sent me an iso image (4 GiB) of hardy for my machine once he had it running so I was able to do a clean install.

I'm a linux noob, still learning.

It seems other people have had problems with FreeMind and java in hardy. You need the sun version I believe.

I checked my open office and it's using Sun JRE 1.6. I also typed in the following commands in the terminal to get the java and freemind versions.

java -version

java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK 64-Bit Server VM (build 1.6.0-b09, mixed mode)

freemind -version

Looking for user properties:
/home/jmcd/.freemind/user.properties

User properties found.
Default (System) Look & Feel: com.sun.java.swing.plaf.gtk.GTKLookAndFeel

Hope this helps you.

Zim is working great for me. I like the way it handles URLs, etc., a feature I use a lot. Still learning.

This thread has turned into a nice dialog. Meeting new friends and helping each other is one of my favorite internet features.

McD

---

### Post by HenryTSTabruck on 2008-06-12
John, just when I thought I had enough pens, I find out about another irresistible instrument--I just ordered the Namiki Falcon, soft fine point--can't wait to try it out.  My current active-use collection is now down to 4 older Namiki retractables: fine, medium, broad, and one broad point that was grinded to an oblique by Pendamonium.com. 

Thank you for the FreeMind guidance.  I'm a new user of Linux/Ubuntu and have a lot to learn, but enjoy exploring and experimenting.  I still rely mostly on my Windows applications, including favorite programs like PersonalBrain, C-Map, MindManager, Ecco Pro, and Edge Diagrammer. Fortunately, some developers are recognizing the cross-platform advantages.

---

### Post by JohnMcD on 2008-06-12
Henry,

Always a temptation to buy that "one last pen" for your collection. I promise you'll like the Falcon. Bit fine for writing but with the soft nib, perfect for drawing. I have a custom ground retractable nib from pendamonium but I prefer the italic on my Pelikan. Got the custom Pelikan nib from Richard Binder a few years ago.

I'm also a complete Linux/Ubuntu newbie. There is so much to learn and I'm having fun doing it. My system is 100% ubuntu. I kept my windows box (put in another room) strictly for film scanning and photo editing. My film scanner won't work in Linux and I use Picture Window Pro for editing. I have an old NEC crt monitor hooked up. The windows system is nearly five years old and still going but who knows how long. That's one of the reasons I got a new system.

I'm trying to find the best Linux apps for my needs and I'm doing pretty well on that score. I have WordWeb Pro on my windows machine. I spent hours today fooling with the Gnome dictionary trying to get similar functionality. I managed to do a new external tool for gedit that pulls up the dictionary for the word under the cursor with a function key. Works nicely but I can't figure out how to get the dictionary to use wordnet and moby thesaurus instead of the default.

I found another dictionary, Fantasdic in the repository. I like it better because it's more customizable, but I can't get that to work with the external tools (yet). I decided to try Lyx today but ended up doing a complete uninstall. There's some problem with the libraries and it kept crashing. I saw the bug reports and it's supposedly fixed with a new release of Lyx, but that's not in the repositories. I'll wait.


McD

---

### Post by HenryTSTabruck on 2008-06-20
John,

My new Pilot Falcon, fine nib, arrived yesterday--it's an elegant pen--good weight and balance.  I filled it with Pelikan 4001 black ink and was able to write and sketch with the lightest pressure for fine lines, or heavier pressure for wider lines.  This is my first experience with a truly flexible nib.  Thank you for the suggestion.  Now, by contrast, my fine nib Namiki seems less smooth and almost too rigid.  

This new writing instrument may distract me a little from exploring Ubuntu.  I generally alternate sessions with Linux and Windows--just discovered a lean, fast, impressive Windows browser--Avant. 

Henry

---

### Post by JohnMcD on 2008-07-05
The Falcon is a wonderful instrument. It just feels right.

I've been very busy writing lately so I haven't had time for much exploration. I did get BrainStorm working under Wine. Missing a few features and the screen is a bit jumpy, but it works.

John

---

### Post by pokipoki08 on 2008-09-30
Based on the recommendation of this thread, I bought both the DOS Maxthink and had the paper manual sent to me (Singapore) by post. But Neil did not send the tutorial files (used in the manual) or the help files (pressing F1). Neil couldn't find those files either.

Will any Maxthink users please send them to me, notably Eric Weir, HenryTSTabruck and JohnMcD? I'd be grateful for those files because it's difficult to learn the advanced commands without any help/tutorial files.

If anyone needs proof of purchase, I'd post the Paypal receipt, $29 for Maxthink and another $29 for the manual & postage.

Thanks.

Maurice

PS: I managed to get Maxthink to resize to any window size (use any opengl video driver), by [COLOR="RoyalBlue"]editing dosbox.conf[/COLOR] (see below). I also managed to get Dvorak keymap working in dosbox.

```
**[COLOR="RoyalBlue"][sdl][/COLOR]**
# fullscreen -- Start dosbox directly in fullscreen.
# fulldouble -- Use double buffering in fullscreen.
# fullresolution -- What resolution to use for fullscreen: original or fixed size (e.g. 1024x768).
# windowresolution -- Scale the window to this size IF the output device supports hardware scaling.
# output -- What to use for output: surface,overlay,opengl,openglnb.
# autolock -- Mouse will automatically lock, if you click on the screen.
# sensitiviy -- Mouse sensitivity.
# waitonerror -- Wait before closing the console if dosbox has an error.
# priority -- Priority levels for dosbox: lowest,lower,normal,higher,highest,pause (when not focussed).
#             Second entry behind the comma is for when dosbox is not focused/minimized.
# mapperfile -- File used to load/save the key/event mappings from.
# usescancodes -- Avoid usage of symkeys, might not work on all operating systems.

fullscreen=false
fulldouble=false
[COLOR="RoyalBlue"]fullresolution=1440x900
windowresolution=1440x900
output=opengl[/COLOR]
autolock=true
sensitivity=100
waitonerror=true
priority=higher,normal
mapperfile=mapper.txt
usescancodes=true
```

mapper.txt (dvorak keyboard layout for dosbox)
```

hand_shutdown "key 290 mod1"
hand_capmouse "key 291 mod1"
hand_fullscr "key 13 mod2"
hand_pause "key 19"
hand_mapper "key 282 mod1"
hand_scrshot "key 286 mod1"
hand_decfskip "key 288 mod1"
hand_incfskip "key 289 mod1"
hand_cycledown "key 292 mod1"
hand_cycleup "key 293 mod1"
hand_recwave "key 287 mod1"
hand_caprawmidi "key 289 mod1 mod2"
hand_caprawopl "key 288 mod1 mod2"
hand_swapimg "key 285 mod1"
key_esc "key 27"
key_f1 "key 282"
key_f2 "key 283"
key_f3 "key 284"
key_f4 "key 285"
key_f5 "key 286"
key_f6 "key 287"
key_f7 "key 288"
key_f8 "key 289"
key_f9 "key 290"
key_f10 "key 291"
key_f11 "key 292"
key_f12 "key 293"
key_grave "key 96"
key_1 "key 49"
key_2 "key 50"
key_3 "key 51"
key_4 "key 52"
key_5 "key 53"
key_6 "key 54"
key_7 "key 55"
key_8 "key 56"
key_9 "key 57"
key_0 "key 48"
key_minus "key 39"
key_equals "key 93"
key_bspace "key 8"
key_tab "key 9"
key_q "key 120"
key_w "key 44"
key_e "key 100"
key_r "key 111"
key_t "key 107"
key_y "key 116"
key_u "key 102"
key_i "key 103"
key_o "key 115"
key_p "key 114"
key_lbracket "key 45"
key_rbracket "key 61"
key_enter "key 13"
key_capslock "key 301"
key_a "key 97"
key_s "key 59"
key_d "key 104"
key_f "key 121"
key_g "key 117"
key_h "key 106"
key_j "key 99"
key_k "key 118"
key_l "key 112"
key_semicolon "key 122"
key_quote "key 113"
key_backslash "key 92"
key_lshift "key 304"
key_z "key 47"
key_x "key 98"
key_c "key 105"
key_v "key 46"
key_b "key 110"
key_n "key 108" "key 108"
key_m "key 109"
key_comma "key 119"
key_period "key 101"
key_slash "key 91"
key_rshift "key 303"
key_lctrl "key 306"
key_lalt "key 308"
key_space "key 32"
key_ralt
key_rctrl "key 305"
key_printscreen "key 316"
key_scrolllock "key 302"
key_pause "key 19"
key_insert "key 277"
key_home "key 278"
key_pageup "key 280"
key_delete "key 127"
key_end "key 279"
key_pagedown "key 281"
key_up "key 273"
key_left "key 276"
key_down "key 274"
key_right "key 275"
key_numlock "key 300"
key_kp_divide "key 267"
key_kp_multiply "key 268"
key_kp_minus "key 269"
key_kp_7 "key 263"
key_kp_8 "key 264"
key_kp_9 "key 265"
key_kp_plus "key 270"
key_kp_4 "key 260"
key_kp_5 "key 261"
key_kp_6 "key 262"
key_kp_1 "key 257"
key_kp_2 "key 258"
key_kp_3 "key 259"
key_kp_enter "key 271"
key_kp_0 "key 256"
key_kp_period "key 266"
mod_1 "key 305" "key 306"
mod_2 "key 307" "key 308"
mod_3
```

---

### Post by JohnMcD on 2008-09-30
Love to help Maurice, but I couldn't find my help or tutorial files either. I always preferred the printed manual anyway and I did install and run MaxThink under DOSbox. The old Max is too clunky for me.

When Wine 1.0 was finally released, I managed to get Brainstorm running.

Lately I've been doing all my planning and thinking with a pen and a yellow pad or index cards. It's so simple.

John

---

