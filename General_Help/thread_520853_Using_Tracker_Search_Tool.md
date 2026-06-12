---
title: "Using Tracker Search Tool"
date: 2007-08-08
forum: General Help
---

### Post by limberlegs on 2007-08-08
Hello, all.

I'm sorry for such a newb-ish question, but how do you use the Tracker Search Tool?  I have the program installed but it doesn't give me any response when I try to search.  How do I make it index my files?  Do I have to add tags to things?

Thanks for your help!

---

### Post by limberlegs on 2007-08-08
Anyone?  Am I wrong in thinking that many people use this program?

---

### Post by cwgannon on 2007-08-11
Hey there,

I'm new to Ubuntu, but I've got Tracker working as well as I know that it can.  Here's what I did:

Searched in Synaptic for Tracker and installed three packages: tracker, tracker-search-tool, tracker-utils.

Those installed, I ran trackerd from the command line, and it indexed my home directory within seconds.

To edit the directories it indexes and modify other parameters, browse to .Tracker in your home directory (you may have to show hidden files with Ctrl-H), and open tracker.cfg.  I found out how to modify this file well enough by reading [http://www.freesoftwaremagazine.com/blogs/desktop_search_tools_gnu_linux_tracker_recoll_strigi_deskbar]("http://www.freesoftwaremagazine.com/blogs/desktop_search_tools_gnu_linux_tracker_recoll_strigi_deskbar")

Finally, to add it to my top panel, I went to Add a Panel and created an Application Launcher, pointing it to the Tracker Search Tool entry that the prior installation had added to the Accessories folder.

Anyway, I hope that helps.  I know the instructions I've provided aren't the greatest, but I don't know all that much about this jazz.  I, like you perhaps, am just getting my feet wet still.

---

### Post by Drakkor on 2007-10-19
Hmm......... I have no .tracker in my hidden home files , and can't find a tracker.cfg !
Right now it only searches my boot drive, I want it to search other mounted drives and
partitions. :confused:

---

### Post by sancho panza on 2007-10-19
Go to Sys>Prefs>indexing prefs to set your tracker preferences.

---

### Post by marcelo.matos on 2007-10-23
My Tracker directory is in:

/home/user_name/.config/tracker

My tracker seem to be working now, I don't know how I made it, but I noticed that I need to enter at least 3 words to make the search start.
 
Hope it helps!

---

### Post by blom on 2007-10-23
For me the tool seems to find most things I've tested but doesn't seem to find short words.  For example, I have and office document called "firstname surname cv.odf", and if I search on either first name or surname the document appears in the results, but not if I search for "CV".

All in all it seems to be an improved tool, but still a little frustrating

*edit*  Well, it seems that it just doesn't like to search for anything of 2 letters or less... probably intentional, but it just so happened that was the search criteria I wanted...

---

### Post by cwgannon on 2007-10-23
@ **blom**:

To index words that are only two characters long:
[LIST=1]
[*]Navigate to ~/.config/tracker
[*]Make a backup copy of tracker.cfg
[*]Open tracker.cfg
[*]Search for "MinWordLength"
[*]Modify value to 2 (or 1)
[*]Save file
[*]Logout and login again (or just restart Tracker)
[/LIST]

(Thanks to marcelo.matos for hunting down the new Tracker config file.)

---

### Post by swmmng on 2007-10-24
My tracker will return a result, but not show it to me.  That is, it shows one result in the categories, as "All FIles (1)," and "Search results: 1 item," but I cannot for the life of me figure out how to see what it found.

---

### Post by Drakkor on 2007-10-25
Yeah, mine did work before, but not now,it seems quite buggy so far. :(
In fact , I have had to kill the trackerd process several times because it
was using 100% cpu !

---

### Post by cwgannon on 2007-10-25
I too had to kill mine several times for eating my CPU alive.

**To fix it:**

System --> Preferences --> Indexing Preferences

Performance tab:
Increase throttling (drag the slider toward the slow end, of course)
Enable "Minimize memory usage"

Feel free to click around in there and customize the rest of your settings.  If they were all default before changing the above, trackerd will stop using your entire CPU for minutes (hours?) at a time.

---

### Post by Drakkor on 2007-10-25
Yeah,thanks cwgannon, that really worked for the cpu usage,but still having problems accessing search in other directories besides the home/username directory, I have 
added them in preferences,but stll the tracker tool finds no files ! :confused:

---

### Post by cwgannon on 2007-10-25
> **Drakkor said:**
> Yeah,thanks cwgannon, that really worked for the cpu usage,but still having problems accessing search in other directories besides the home/username directory, I have 
added them in preferences,but stll the tracker tool finds no files ! :confused:

Sorry, Drakkor.  I'm going to have to defer to somebody more familiar with Tracker on that one.  The best I can recommend is to actually open up your tracker.cfg file (~/.config/tracker) and be sure that the directories you are adding through the Indexing Preferences GUI coincide with those in the configuration file.  (Were it me, I'd uninstall Tracker, delete its config file, and reinstall.)

Here's the relevant portion of my tracker.cfg, in case there is something you can gain from checking against it:
```

[Watches]
# List of directory roots to index and watch seperated by semicolons
WatchDirectoryRoots=/home/christopher;/media/stores;
# List of directory roots to index but not watch (no live updates but are refreshed when trackerd is next restarted) seperated by semicolons
CrawlDirectory=
# List of directory roots to not index and not watch seperated by semicolons
NoWatchDirectory=
# Set to false to prevent watching of any kind
EnableWatching=true
```

I must say, though, that Tracker does not seem like it was prepped well enough to be released with Gutsy.  Maxing out a user's CPU with a background process that said user is likely unaware is running does not seem sensible.  Ggranted, the option to allow Tracker to function as such should remain, but the default settings for Tracker need to be adjusted so that Tracker remains unobtrusive.

---

### Post by Drakkor on 2007-10-25
Agreed to all above,lol. Actually I for one have had more problems with Gutsy than any other version, been through Dapper/Edgy/Fiesty !
You can change your tracker.config file by going to System>Preferences>IndexingPreferences>Files Tab and add to the watched directories,
but maybe there's some permission problems ? I don't know,lol

---

### Post by cwgannon on 2007-10-25
I was actually just suggesting you edit the config file by hand to ensure that it was matching what the GUI was giving (though I can't say I had any reason to believe they wouldn't match).

I noticed from your screenshot that you are watching three directories aside from your own home directory.  Have you tried removing, say, / from that list to see if that does anything?  Like you said, maybe it's related to permissions for some reason neither of us has considered.

All that said, again, it would be swell if somebody a bit more in the know could help us out here.  It's surprising to see a bundled tool like this get no love on these forums.

---

### Post by Drakkor on 2007-10-25
Yeah,they are actually changed in the tracker.cfg file as well,see here as I changed it,and then you just reload.

---

### Post by filologen on 2007-10-26
On my 7.10 installation II have the exact same problem as swmmng described: 

"My tracker will return a result, but not show it to me"

Has anyone else seen this and been able to solve the problem?

Btw: It used to work!

---

### Post by sancho panza on 2007-10-26
See if the first post on [this page]("http://ubuntuforums.org/showthread.php?t=578923&page=2") helps. It worked for me.
First kill trackerd via terminal or sys monitor.
Then get tracker to reindex by typing ***trackerd -v 2 -R** * in the terminal.
Complete indexing could take an hour or so, but once thats done, it seems to show up results and stuff.
Hope that helps...

---

### Post by filologen on 2007-10-26
Thanks for your advice sancho panza, but I had already tried that. I have even tried to completely remove tracker-search-tool and reinstall it, but I still have the same problem: a get the categories and the number of hits but no display of results :(

This is strange, especially because it used to work.

---

### Post by jamiemcc on 2007-10-26
You know there is a separator between the cats and the results - you probably have yours all the way to your right which obscures the result window

simply resize the separator by moving your mouse to the right handside and drag to your left

I guess we should include to prevent you from obscuring the results completley

---

### Post by mdurham on 2007-10-26
Hi guys, is tracker supposed to search hidden (.xxx) files? Mine doesn't seem to, is there a way to make it do this?

---

### Post by filologen on 2007-10-27
jamiemcc, thank you so much. I feel _really_ stupid, but was fooled by my theme settings which hid the separator for me. 

I guess this is one of the reasons to avoid GUIs ;)

Thanks again, it solved my problem :)

---

### Post by jamiemcc on 2007-10-27
> **mdurham said:**
> Hi guys, is tracker supposed to search hidden (.xxx) files? Mine doesn't seem to, is there a way to make it do this?

tracker does not index hidden directories as such

certain specific hidden directies like .evolution and .pidgin will be indexed but ther eis no way for a user to specify one

---

### Post by mdurham on 2007-10-27
> **jamiemcc said:**
> tracker does not index hidden directories as such

certain specific hidden directies like .evolution and .pidgin will be indexed but ther eis no way for a user to specify one

Thanks for the info jamiemcc, that seems a bit limiting to me, I'm always looking for things in conf files and the like. I wonder what the designers thinking was?
Cheers, Mike

---

### Post by jamiemcc on 2007-10-29
its actually quite sensible 

why would a user want to search hidden stuff?

also like I said hidden directories are used by apps to store settings and data so they need to be treated separately anyhow

---

### Post by penguinhugger on 2007-10-30
Btw guys, does anybody know how to change the kind of files displayed under the "Documents" tag among the search results? In my case Tracker never includes office documents like presentations and excel files: PDFs and DOCs are the only ones on the list, which often forces me to browse quite a lot before getting to the document I was looking for.

---

### Post by dmber on 2007-10-31
> **jamiemcc said:**
> its actually quite sensible 

why would a user want to search hidden stuff?

also like I said hidden directories are used by apps to store settings and data so they need to be treated separately anyhow
why would i want to search hidden stuff?  for that exact reason!  it's hidden...i don't know where it is.  if it's not hidden, i know where it is.

i, too, figured tracker would be useful for finding conf files and whatnot, but i guess not.  to be honest, i'm not sure what it's even for if it can't search hidden files.

---

### Post by mdurham on 2007-10-31
> **dmber said:**
> why would i want to search hidden stuff?  for that exact reason!  it's hidden...i don't know where it is.  if it's not hidden, i know where it is.

i, too, figured tracker would be useful for finding conf files and whatnot, but i guess not.  to be honest, i'm not sure what it's even for if it can't search hidden files.

I quite agree, I thought that 'choice' was a keyword in Linux.
Cheers, Mike

---

### Post by AndyCooll on 2007-11-16
> **jamiemcc said:**
> You know there is a separator between the cats and the results - you probably have yours all the way to your right which obscures the result window

simply resize the separator by moving your mouse to the right handside and drag to your left

I guess we should include to prevent you from obscuring the results completley

Nope, that doesn't resolve the issue for me. Under categories I can see the summary of results, but nothing ever displays in the "Search Results" section (i.e. the right-hand pane), and I can see the seperator clearly in the middle of the screen.

:cool:

---

### Post by zoryn on 2007-11-18
Same problem, shows categories ( e.g. Files(29) ), but no results.

---

### Post by satkata on 2007-11-27
Check in your "tracker.cfg" Line 63 and look if the option name itself is correctly written.
This option is not accessible trough the gui and I was pretty amazed discovering that in my case there was a syntax error.

before

# Sets no. of divisions of the index file
Dvisions=4

after:

# Sets no. of divisions of the index file
D**[COLOR="Red"]i[/COLOR]**visions=4

I had never touched that line, don't even understand what is the option for.
Whatever, after I corrected the mistake, tracker is working fine so far, reliable as it was in Feisty.
Anyway I let tracker now reindex everything, because I had sometimes 1 or 2 categories in the results, where there were entries, but everything else was responding and working fine.

---

### Post by Subban on 2007-11-27
> **satkata said:**
> Check in your "tracker.cfg" Line 63 and look if the option name itself is correctly written.
This option is not accessible trough the gui and I was pretty amazed discovering that in my case there was a syntax error.

before

# Sets no. of divisions of the index file
Dvisions=4

after:

# Sets no. of divisions of the index file
D**[COLOR="Red"]i[/COLOR]**visions=4

I had never touched that line, don't even understand what is the option for.
Whatever, after I corrected the mistake, tracker is working fine so far, reliable as it was in Feisty.
Anyway I let tracker now reindex everything, because I had sometimes 1 or 2 categories in the results, where there were entries, but everything else was responding and working fine.

I have had problems with Tracker as well, the syntax error you mention as also in my config, have corrected it and will see if it helps it function properly now.

---

### Post by mdurham on 2007-11-27
> Check in your "tracker.cfg" Line 63 and look if the option name itself is correctly written.
Can you tell me, where is this file? Thanks.

---

### Post by cwgannon on 2007-11-28
~/.config/tracker/tracker.cfg

(~ is your home directory.)

---

### Post by satkata on 2007-12-13
Now, I would suggest, you update to the new released version of tracker, 0.6.4

It's more polished now and all issues are gone.

---

### Post by ckth on 2007-12-20
> **satkata said:**
> Check in your "tracker.cfg" Line 63 and look if the option name itself is correctly written.
This option is not accessible trough the gui and I was pretty amazed discovering that in my case there was a syntax error.

before

# Sets no. of divisions of the index file
Dvisions=4

after:

# Sets no. of divisions of the index file
D**[COLOR="Red"]i[/COLOR]**visions=4

I had never touched that line, don't even understand what is the option for.
Whatever, after I corrected the mistake, tracker is working fine so far, reliable as it was in Feisty.
Anyway I let tracker now reindex everything, because I had sometimes 1 or 2 categories in the results, where there were entries, but everything else was responding and working fine.

I had the same problem as many here- the categories list was populated but the items wouldn't show. 
Correcting the syntax error as shown above and re-indexing solved it. Thanks, satkata.

---

### Post by AndyCooll on 2007-12-24
As I reported in my earlier entry to this thread,  I was finding that Tracker wouldn't display the results of files that were contained on my server and mounted via nfs.

I'm not sure if the following is what actually fixed the problem, but suddenly everything now seems to be working as it should!
I manually added the nfs mounted path to "Additional paths to index and watch" under the Files tab (System > Preferences > Indexing Preferences).
Under that tab is actually an entry "Index Mounted Directories", but I'm sure this was already ticked when it wasn't working properly. Anyway, it's working now. 

And when it's working properly Tracker is a great tool, I can see finally why others have been raving about it!

:cool:

---

### Post by tjpren on 2007-12-25
Hi all,

I've been reviewing the post, as I have also installed tracker, and found it it to be rather ordinary.  Any help as to why in my system>>preferences. I don't have Indexing Preferences ?

I can manually alter the tracker.cfg (again thanks to the post).

Also, how do I make it search the entire HD ?  Do I have to add all folders and semicolons?  My linux partition is File System - do I just add that ?

Any ideas appreciated.

---

### Post by marinero on 2007-12-31
Hi tjpren,
I think adding your whole drive in the "Indexing Preferences" would do the job. But are you sure you really want to be doing that?

Make sure after you do that that you kill the "trackerd" process and you restart it doing a "trackerd -R"

tp

---

### Post by AndyCooll on 2007-12-31
> I've been reviewing the post, as I have also installed tracker, and found it it to be rather ordinary.  Any help as to why in my system>>preferences. I don't have Indexing Preferences ?
You could check under System > Preferences > Main Menu. That's a graphical menu configuration tool. see if it's simply not ticked.

> Also, how do I make it search the entire HD ?  Do I have to add all folders and semicolons?  My linux partition is File System - do I just add that ?
Assuming you've got the above working:
System > Preferences > Indexing Preferences > Files. Add "/" (without the speech marks). I'd agree with marinero though, are you really sure you want to be doing that?

:cool:

---

### Post by gleble on 2008-01-19
I have just reinstalled tracker-search-tool and it is searching E-mails beautifully but nothing else. Does anyone know what is wrong

---

### Post by gleble on 2008-01-19
ran```
 trackerd -R
``` and all is fine

---

### Post by olavjunior on 2008-01-25
No, I have the same problem. The tracker is showing that there is x number of hits, but not all of them are shown.. I have installed the latest version 0.6.4 to solve this, but it didn't help.

EDIT: Upgrading actually solved it. Just had to reindex. Here's the backport: [https://bugs.launchpad.net/gutsy-backports/+bug/175676](https://bugs.launchpad.net/gutsy-backports/+bug/175676)

---

