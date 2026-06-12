---
title: "Search app that lets me drag-and-drop results (like in Windows)?"
date: 2008-05-01
forum: General Help
---

### Post by OzzyFrank on 2008-05-01
OK, first off I have to say it amazes me that nothing has been done about the **absolutely crappy** search feature in Nautilus, as (I hate to say it) it is vastly inferior to the generic Search in Windows. I mean, I search for ".deb" on an Ubuntu CD and the result is zero?? Hehe... that's pretty pox!

I use Catfish, as it is superior beyond measure to the Nautilus search feature, yet it still suffers from a lack of a feature I have come to depend upon in Windows. This is the ability to drag-and-drop the results... like if you did a search for *.deb files in subfolders and wanted to be able to drag all the hits to another folder. From what I have seen, this is impossible. The best one can do is take note of the folder names and go into each one individually and drag the files (after manually selecting them) that way.

Is there a search program (that actually works and finds what I want, unlike Nautilus) that will let me do more than right-click and choose Open? Like let me drag the listed files to wherever I please, like Windows lets me do?

---

### Post by OzzyFrank on 2008-05-11
So there isn't one? If you're a programmer, please make one!!

---

### Post by OzzyFrank on 2008-05-17
So there isn't an app like this in Linux? Maybe I should just hassle the Catfish developers to enable drag/drop from the results pane? I just figured such a basic (and useful) Windows feature as this had been emulated by now, but seems that is wishful thinking, hehe...

---

### Post by Ralph L on 2008-05-31
I agree with you that the Nautilus search function is unacceptable (at least in Gutsy).  In addition to the problems you note, it won't find many files.  For example, when trying to get Linux up and running, I had no idea what the various directories were for.  So when I got help from the Forum saying change "xyz" file, I tried to search the entire disk.  More often than not Nautilus didn't find the file I was looking for evan though it really was present.  I finally gave up on using Linux and went back to my Windows system.  The reason I am posting this message is because I was hoping the problem had been fixed in Hardy.  If anybody knows when it will be fixed, please notify me and I will try again.  A friend suggested that I try Kubuntu, although I hate to start fiddling with another very time consuming system.

Ralph

---

### Post by OzzyFrank on 2008-05-31
Yes, I've complained about Nautilus not finding files in an earlier post. Basically I did some tests when I noticed I wasn't getting results, and the conclusion was that Nautilus is **appallingly pathetic** as a search tool! I mean, not finding files in a folder while you're looking straight at them?? Or type in a word and it doesn't find the 3 files that have that in the name, but then lists 137 other files that don't have that word in the file and/or folder name?????

Anyway, I found my answer from that thread: don't use Nautilus for searching - use Catfish. Easy to use, fast, accurate - just install it through Synaptic. The default is only to search the user's home folder, but you can chooose the filesystem (ie: root of the drive) from a pull-down menu.

Personally, I wouldn't give up on distro/OS just coz the search tool sucks, but if it matters that much, go back and give Ubuntu a second shot with Catfish as your search tool. Also, Google Desktop is also easily available for Ubuntu.

But yeah... some work needs to be done on Nautilus (though this is not the jurisdiction of the Ubuntu team).

---

### Post by LaRoza on 2008-05-31
I would like to point out that Nautilus has a single developer who has to deal with real life at the moment and that it is entirely free. 

For heavy duty searching, you can use the command line to do some amazing things.

[http://linux.about.com/od/commands/l/blcmdl1_find.htm](http://linux.about.com/od/commands/l/blcmdl1_find.htm)

---

### Post by OzzyFrank on 2008-06-01
"I would like to point out that Nautilus has a single developer who has to deal with real life at the moment and that it is entirely free."

**Yes, it is free, and many of us understand there are small groups - even individuals - who develop these things. However, when it is an essential part of Gnome, in effect, and the distros which use it, perhaps this one person with lots going in his life should consider recruiting others to help with the development of Nautilus. And while it is indeed free (which is a good thing, since in Linux most things are!), it shouldn't be immune to criticism, about its flaws, and possible improvements (especially if people have been going on about the shortcomings and suggesting improvements for some time - as in the case of the severely flawed search feature). Also, if it all becomes too much for one developer, and that person does not wish to collaborate with others, then perhaps this should be made clear to the public, so others can either continue the development, or the search for a new file manager/browser for Gnome-based distros can begin.**

"For heavy duty searching, you can use the command line to do some amazing things."

[B]um... yes... but even for those of us quite comfortable with the command-line, doing searching in this way can be a drag (ie: remembering specific options/switches for commands etc). Especially if you have a good GUI search tool like Catfish. And lets not forget the newbies: telling them to use the terminal to search coz the search app/feature doesn't work is not going to continue to attract more users. Read one of the posts in this thread and you will see this is not an imaginary concern.

What I would like to know, however, is why - when the Linux search apps seem to just use commands like _find_ etc - the search feature in Nautilus is SO abominably inaccurate... I mean, how did it get SO bad?[/B]

---

### Post by LaRoza on 2008-06-01
> **OzzyFrank said:**
> 
**Yes, it is free, and many of us understand there are small groups - even individuals - who develop these things. However, when it is an essential part of Gnome, in effect, and the distros which use it, perhaps this one person with lots going in his life should consider recruiting others to help with the development of Nautilus. **

[B]um... yes... but even for those of us quite comfortable with the command-line, doing searching in this way can be a drag (ie: remembering specific options/switches for commands etc). Especially if you have a good GUI search tool like Catfish. And lets not forget the newbies: telling them to use the terminal to search coz the search app/feature doesn't work is not going to continue to attract more users. Read one of the posts in this thread and you will see this is not an imaginary concern.

What I would like to know, however, is why - when the Linux search apps seem to just use commands like _find_ etc - the search feature in Nautilus is SO abominably inaccurate... I mean, how did it get SO bad?[/B]
I am sure he would love help, do what you can.

The man pages are always there. I don't use Nautilus, so I offered the best search option I know. I didn't forget the newbies, I also don't care (in this instance) about them. It is not my interest to constantly attract new users.

I don't know, look at the source and see what the developer is doing.

---

