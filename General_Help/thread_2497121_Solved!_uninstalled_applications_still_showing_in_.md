---
title: "Solved! uninstalled applications still showing in Show Applications"
date: 2024-04-23
forum: General Help
---

### Post by the-roaring-girl on 2024-04-23
All right...I made the jump to Linux a few days ago and overall, loving it! But despite considering myself fairly tech-savvy, I'm clearly on a learning curve adjusting from Windows and am currently struggling to figure out how to fix my own mistake (?).

I installed iTunes, accidentally installing the most current version which is apparently not compatible with Ubuntu yet. Okay, no problem - I got iTunes working with an older version easy enough! The problem is, the OG iTunes installation attempt is still showing up under Show Applications (separate from the correctly installed iTunes), along with Apple Software Update and About iTunes and no matter what I do or have tried, it will not uninstall. I've tried Terminal, Synaptic, Ubuntu Software, Wine Uninstaller, I've tried manually deleting every itunes file still hanging around the c drive...nada. 

As far as I can tell, iTunes IS uninstalled (even the correct-version, which I uninstalled in case that was the problem) but it still shows up in Show Applications. It doesn't open, but it is still showing up there and it's driving me crazy!

---

### Post by Impavidus on 2024-04-24
The more you know about Windows, the more you have to unlearn when transitioning to Linux. Although the GUI can be somewhat similar, underneath they are very different.

Without knowing how exactly you installed iTunes, I cannot say how to uninstall it. But the thing shown in List Applications comes from a .desktop file. So there must be a .desktop file somewhere in a directory searched by Show Applications, referencing iTunes. It normally looks in /usr/share/applications, /usr/local/share/applications (if that exists) or ~/.local/share/applications. ~ stands for your own home directory, a file or directory starting with a dot is hidden. A proper uninstall script should remove that .desktop file, but you may have to do it manually, depending on how you installed the software.

---

### Post by TheFu on 2024-04-24
If the uninstall of iTunes didn't clean up everything that was installed, you'll need to hunt down where the *{something}.desktop* file is located.  There are a few common places. I'd use to tool called 'locate' to find all .desktop files, then filter those results for something that looks like itunes.  The command would be this:
```
$ locate .desktop | egrep -i itune
```

There may be a GUI way. I just don't know it. I'm too old to learn a new GUI every few years, when it isn't necessary.

That command will find the old and the new .desktop files, so you'll want to check carefully (or modify the menu name displayed in one of the files so you know which .desktop file can be removed.  .desktop files are just ASCII text, so any simple editor or a "pager" can be used to view them.  Pagers show a file 1 screen at a time.  **more** and **less** are pagers with similar, but different capabilities.  **less** has more features, like going backwards. Neither use a mouse or scrolling through the mouse (well, not really), regardless of what you may see and think works with the mouse.

Usually, proper applications would remove all files they install that aren't per-username/individual and aren't just "settings".  Settings are either system-wide or personal.  
Removing with a "remove", doesn't remove system-wide or personal settings, ever.
Removing with a "purge", removes system-wide settings, but not personal settings.

To remove personal settings or personal data, that's a manual thing.  Depending on the installation method, the settings and even the program may have been installed system-wide OR for just 1 user.  There are times when both methods are useful.

Also, sometimes menus are created/updated only at session startup, so logging out and logging in again (shouldn't need to reboot), should get the menus rebuilt, removing old programs.  Non-native Linux programs often get the install/remove stuff wrong. 

There's history behind why things are the way they are, both native and non-native applications.  **As a general rule, it is best to find a native program and use that if you can.**

---

### Post by the-roaring-girl on 2024-04-24
Thank you both! The locate command helped me find it - and it was lurking in a hidden file. Problem solved!

---

### Post by TheFu on 2024-04-24
> **the-roaring-girl said:**
> Thank you both! The locate command helped me find it - and it was lurking in a hidden file. Problem solved!

A) glade you found it. 

B) all files we don't see are "hidden".   That's the nature of not finding something we seek.  Until it is found, it is hidden. ;)

C) When a problem is solved, the way to help everyone out and make a flag in the forum DB is to use the Thread Tools button near the top of every page, then choose "Mark SOLVED".  That will help others search for answers to find it without having to do inefficient "text" searches.  It will also modify the title with "SOLVED" which tells everyone - looking for help AND wanting to offer help - that it is solved.  Only the person who started the thread can mark it SOLVED, unlike some other support tools (cough ... google support pages).

locate is handy, but only updated once a day. It isn't live, but it is FAST, if the file has been there at least since the last update ran.  To find brand new files, 'find' is the tool for that and it is slow.  Actually, it is probably faster to just force the locate DB to be updated.  50/50 on that. Depends on the type and total amount of storage and changed files.  The 'find' program is a beast.  It is one of the few that seeing the top 50 examples of uses really helps people, as opposed to reading the built-in documentation.

---

### Post by dragonfly41 on 2024-04-25
[COLOR=#000000]> There may be a GUI way. I just don't know it.

Adding Recoll to the list of options.[/COLOR]

---

### Post by TheFu on 2024-04-25
> **dragonfly41 said:**
> [COLOR=#000000]

Adding Recoll to the list of options.[/COLOR]

**Recoll** does so much more than **locate**.  It is harder to setup and takes much longer to run the file indexing.  For the specific tasks that recoll does - it is like having a local google just for your system, it is amazing.  I use it but not for system stuff, just to be able to find documents, videos, music, autiobooks, epub files, PDFs, emails.  Recoll looks inside every type of file that it can, using helper tools for that.  I don't know about the default locations used by Recoll, since my DB is larger and needs to be placed in a storage area that's large enough to hold it.
```
$ du -shc /d/D2/recoll-index/
12G     /d/D2/recoll-index/
12G     total
```

12G is a huge amount of storage just for indexed data, but it is the index for over 20TB worth of files.  **Recoll** is FAST - like - Google Fast. It does take a long time to do the indexing for any new/modified files. I run that update daily, but I had to set that up myself. My crontab line is:
```
10 4 * * * export RECOLL_CONFDIR=/d/D2/recoll-index/recoll ; nice /usr/bin/recollindex > /dev/null 2>&1 
```
So at 4:10am daily, it runs at a low priority to keep the DB updated.

For comparison, the DB that **locate** uses is less than 200MB.
```
$ du /var/lib/mlocate/mlocate.db
168M    /var/lib/mlocate/mlocate.db
```

---

### Post by dragonfly41 on 2024-04-25
TheFu, I'm sure that I found Recoll after reading one of your threads. Thank you.
Recoll is truly a powerhouse. Yes it does requirea very large indexdb but these can be pushed into backup drive and partial indexing pursued. That is, dynamically switched in a library of indexdb Much like Firefox profiles as an analogy
Regarding &#8220;system stuff&#8221; my workflow strategy now is to place commands inside conceived notional containers - CherryTree *.ctd containers in fact.
Then I use Recoll to locate these &#8220;containers&#8221; (extension *.ctd) which in CherryTree can be nodes containng CodeBoxes (multiple syntaxes, scripts). And indeed supporting documents including images, screenshots. All in an XML format. The only customisation needed was to map CherryTree container (*.ctd) to CherryTree App through Preferences  > Use interface > Choose editor applications > Native Viewers > application/xml cherrytree %f.  Otherwise Desktop Default shows XML structure.
I might for example have a container to access Microsoft Azure with all the required access (login, resources) held in one container (docker like).
So I query: ext:ctd .. corrected to *.ctd the MIME type for single CT documents. There are other types.
This thinking of assets as nodes takes us into vector databases.

---

### Post by TheFu on 2024-04-25
FWIW, CherryTree is like a personal notebook/wiki.  A few friends use it and love it.  They've tried to convert me, but if it doesn't work from a shell/ssh prompt, it isn't for me. ;)  Years ago, I tried to use Basket Notes (a KDE program) when I searched for an MS-OneNote clone.  Having the ability to embed images was good at the time and if I used GUIs more, it might be useful today.

I keep notes in "vimwiki" myself.  The entire wiki can be exported to HTML for use on tablets/phones.  I bet CherryTree can do that too.  vim-based tools aren't for everyone, or even most people.  vim has built-in recursive searching, so I don't need recoll, though I could have vim shell out to run a recoll query

But I think we can all agree, for what Recoll does, it certainly is one of the best options. There are others, but each has some things I don't really like too much.  Even recoll has some things I don't like much. It wouldn't surprise anyone here that I only use the Recoll GUI during setup. For day-to-day searches, I use the CLI interface with a wrapper script. ;)

For most end-users, **Recoll** could become a _must have tool_, once they get used to it.  The GUI isn't great, but the performance is sub-second for all queries thanks to the way the indexes are stored.

---

### Post by dragonfly41 on 2024-04-25
TheFu, let me try to convince you in this experiment that CherryTree can also be your &#8220;CLI with wrapper script&#8221;.
Install cherrytree.
[https://www.giuspen.net/cherrytree/](https://www.giuspen.net/cherrytree/)
Create CherryTree document, [recommendation] save as type *.ctd (although there are several choices with different extensions - (important to know when searching in Recoll).
Create a ROOT node (perhaps holding metadata)
Create a child node. Multiple nodes can be created.
Inside any node in the hierarchical tree structure .. Insert CodeBox(s).
In popup window click on radio button Automatic Syntax Highlighting
Click on button below Automatic Syntax Highlighting .. and here is the power engine .. choose from the sub list shown in File > Preferences > Preferences [Shift + Alt + P] > Plain Text and Code ...

c                c
c-sharp        cs
cpp            cpp
dosbatch  bat
go                go
java            java
perl            pl
powershell    ps1
python        py
python3    py
rust            rs
sh                sh

Now you can if you wish add your own custom commands which act on the code embedded in each CodeBox
HaXe or PHP for example.

Note that above short tist is a subset of possibilities. 
When you click on Preferences > Automatic Syntax Highlighting you see others.

Having written your script (sh, rust or perl?) in a CodeBox we can simply hit the Run button to right of each displayed CodeBox to execute the script in the chosen language. sh or rust or perl or other.
And you can mix CodeBoxes with different languages in each CherryTree node .. as many as you choose.

But more .. when you actually Insert CodeBox [Shift+Alt+D] into any node
and click on the syntax bar we see that there are multiple other possibilities beyond the default set.  We see .. multiple other choices of languages for each CodeBox.

Thus we can hold mixed instructions, screenshots and CodeBoxes in each node.
We can also create links to CodeBoxes or nodes. Truly versatile and much more than a &#8220;notebook&#8221;.

Think of each document as an eLearning container.
It teams well with Recoll. At least for my custom contrived workflows.

In my view if we uploaded such containers to these discussion threads it would save lot of time. avoiding repeated advice offered on frequent subjects.

And yes CherryTree documents can be exported as HTML
I even have a CherryTree document (*.ctd) orchestrating Recoll searches. And orchestrating CherryTree.

But the possibilities do not end here. Any CherryTree document can be viewed in an XML editor (XMLCopyEditor)  and contents dynamically parsed by xquery. But that is for another day.

[PostScript:]
Command Line mode.
[https://giuspen.net/cherrytreemanual/#_command_line](https://giuspen.net/cherrytreemanual/#_command_line)

in response to ..

> [COLOR=#000000]but if it doesn't work from a shell/ssh prompt, it isn't for me[/COLOR]

---

### Post by TheFu on 2024-04-25
Nice try.  Good for others seeking a note taking application.

I prefer plain text, perhaps with a markdown.  I've been burned too many times.  

My order of desired notes/data sharing:
[LIST=1]
[*]Plain Text
[*]Markdown ( textile, but markdown is only slightly worse)
[*]HTML
[*]RTF
[*]XML-based documents using any ODF tool (yaml, json are the same level and hate)
[*]PDF and proprietary forums. 
[/LIST]

---

