---
title: "File manager windows"
date: 2023-07-05
forum: General Help
---

### Post by John Jason Jordan on 2023-07-05
I spend hours every day manipulating files, i.e., renaming or moving from one folder/drive to another. The computer itself has a couple 1TB SSDs, but they are not an issue. The problem is a 32TB enclosure holding four 8TB NVMe drives in RAID0. This is mirrored nightly to a 32TB NAS with four spinny disks, also in RAID0. The enclosure with the NVMe drives is my working storage because it is connected directly to the computer with Thunderbolt 3, making it *fast*.The mirroring to the spinny disks takes quite a while, but I don't care because I'm asleep. There are about 43,500 folders and files, totaling about half the capacity.

For a long time I used PCManFM for my work, but it has fixed (too narrow) sizes for its renaming window, and it can't even remember the (too narrow) width of the main window, leaving me either constantly dragging windows bigger or living with truncated filenames. I recently switched to Thunar, and it is very much better at these problems, but it has a new problem that I hope someone here can advise me on.

Today is a typical day: I have four Thunar windows open. One is just looking at the NAS mirror RAID, and is not a big problem. Three are looking at the NVMe RAID, each at different locations. One location is the source folder for files that are being converted, and another is the output folder where the conversions end up. Each conversion takes about half an hour+, so I must often access the output folder to verify that the most recent conversion was good, and then the source folder to select the next file to be converted. Another window is looking at the root of the NVMe RAID, because it contains about 4200 folders, each with several files, and I'm changing my naming conventions, resulting in hundreds of filename changes every day. I'm progressing through the folders alphabetically, and I want the view to be where I'm currently working. Having the view suddenly change to the top or the bottom means lots of scrolling to get back to where I was working.

Now, the problem. I'm working away changing filenames and suddenly I need to interrupt this work and attend to the conversions, if only for a few minutes. After finishing with the conversions I go back to the window where I am doing the file and folder name changes, and guess what? The view of this window is now the view of the output folder, not where I was working previously. I can get back to where I was, but it involves a lot of clicking and scrolling around. More to the point, the window view, assuming no file deletions or additions, *should never change by itself*. WTH is going on?

I should add that when I launch Thunar it brings up one window, which uselessly points at my home folder. I click and scroll to the NVMe RAID and get to work. I open additional windows by going to File > New window. Sometimes I open new windows by right clicking on the Thunar icon in the panel and then select 'open a new instance.' Note that I never, ever use tabs. How can I drag and drop files from one drive to another if they're all in tabs?

I should add that bookmarks are not the answer. I have 20-30 bookmarks, but if I used bookmarks here I'd be creating and then deleting a dozen bookmarks every day. More trouble than it's worth.

One more fact which may lead to an answer: Thunar crashes several times a day. It's always when I'm doing something - clicking to move up to a parent folder, or something equally ordinary. I've never noticed a pattern. But here's the point: When Thunar crashes, *all the windows instantly disappear*. This tells me that the windows are somehow connected. Now, PCManFM crashed now and then too, but when it did, only the window I was working in disappeared. Why?

All suggestions and observations gratefully received!

---

### Post by MAFoElffen on 2023-07-05
For what you say you do, have you thought about GNU Midnight Commander? Just a thought.

---

### Post by John Jason Jordan on 2023-07-06
> **MAFoElffen said:**
> For what you say you do, have you thought about GNU Midnight Commander? Just a thought.

I dislike two-pane file managers. I'd much rather have different views in different windows. 

Today I have arrived at the conclusion that thee is either a bug or a deliberate design decision making Thunar change the view presented by a window without user input. This is unacceptable, so in my world Thunar is now history. Moving on, I am fiddling with other file managers to see what they offer. Currently I'm working with Dolphin, but the developers apparently thought that no one could ever have a question, so there is no documentation, at least not accessible from the program window. 

This discussion is over for me. I'd mark it solved, but it's not solved; in fact, that's why I'm moving on. :)

---

### Post by dragonfly41 on 2023-07-06
Although question is "solved" you do not give any clues as to why you need to view files to change filenames daily.

The only clue is .. "Linguistics on Linux".

I would approach this by using automation scripts rather than viewing files in Thunar or whatever.

You could write python automation scripts and add it to a little utility named Albert in apps.

And I would look at Recoll and Algolia as examples.

That is, you hit an assigned control key (I use Enter at bottom right of keyboard) and up pops a command query for you to type to drive the chosen automation script.

You can explore concordance analysis engines where batches of files (corpora) are processed. Such as works of Shakespeare. Look at SketchEngine.eu to get an idea.  The corpora can be analysed while you sleep.

An excellent desktop tool is AntConc.

So my guess is that you need to rethink your production workflow.

---

### Post by John Jason Jordan on 2023-07-06
@dragonfly41,

Thank you for your suggestions. Unfortunately, none of what I am doing can be automated. Every filename is utterly unique, there are not even common words. The only things that are the same are the extensions that designate file types, but these are the one part of the filename that I do NOT need to change.

There are approximately 4200 folders, each containing one to four or five files. The names of these sub-files partially echo the name of the folder, but never the same way, and the echo is not 100%; sometimes it's the first few letters, sometimes parts of the middle, or the last, sometimes not at all; consistency doesn't exist. Worse, some came from outside people who added periods between words and their name or address in the filename. The periods I could handle with AI, but there aren't that many of them, and so far I haven't run into two files with the same junk in them. And because of the lack of consistency, yes, I do need to view each filename in order to figure out how to fix it.

A for linguistics, that is my academic passion, but it has nothing at all to do with the present problem. I'm sorry if the tagline misled you.

I spent a lot of time today trying other file managers, and it's depressing. Most are missing at least some basic features of a file manager or there are other problems that render them unusable. I'm amazed at all the issues. I ought to write a comprehensive critique of what's wrong with Ubuntu file managers.

---

### Post by MAFoElffen on 2023-07-07
Dang... Reading your first post, I was thinking about some type of scripts might work also, but you point out some very good points hwy that won't work. I''ve ran into the same problems with audio files ad their metadata that some people edit them to. 

That is a challenge I find in trying to write programs to help people rescue their installed Linux Systems... Linux let's you change things so very much, and setup things 100's of ways, that still work... Before the don't. LOL So hard to outguess what someone might do.

Which brings up a point you also brought up... The suite that Ubuntu uses (such as their Flavor's file managers)... They are from upstream sources. They were not written by Canonical. And they aqre available for Linux as a whole (usually). Just as, if you see a file manager used by another Distro, you can probably use it on Ubuntu or any other Linux Distro.

Here's a short list:
[Gnome/Files]("https://wiki.gnome.org/Apps/Files") (aka Nautilus) is from the GNU Gnome project. This is the one I use the most. Lots of features, but heavy and high overhead.
[Gnome Commander]("https://wiki.gnome.org/Apps/Commander"). From Gnome. To me is similar to Midnight Commander.
[Thunar]("https://docs.xfce.org/xfce/thunar/start") is part of the XFCE project. 
[Konqueror]("https://docs.kde.org/stable5/en/konqueror/konqueror/filemanager.html") is from the KDE project. 
[Dolphin]("https://apps.kde.org/dolphin/") is part of the KDE project. The KDE docs are available for download here: [https://docs.kde.org/index.php?language=en](https://docs.kde.org/index.php?language=en)
PCmanFM came from the LXDE project. Very light weight and fast. Not much features. This one I use on the Ama-Gi LiveCD.
PCmanFM-Qt is a Qt4 port from PCmandFM.
[Midnight Commander]("https://midnight-commander.org/") has been around for a very long time and others try to compared themselves to it... I alos use this on the Ama-Gi LiveCD.
[XFE (XFile Explorer)]("http://roland65.free.fr/xfe/")

I got tired of providing links, but you can also google these:
[ViFM]("https://vifm.info/")
Worker
Ranger
Sunflower
4Pane
Krusader
Nemo
nnn
Double Commander
SpaceFM
Worker
XTree
muCommander
emelFM2
ROX Desktop
Total Commander
FreeCommander
Dired
Far Manager
ForkLift
Path Finder
Sunflower
Explorer++
File Commander
PathMinder

Many more out there. Like I said, the short list.

---

### Post by John Jason Jordan on 2023-07-07
Thanks fo the list of Linux file managers. I had already heard of most of them and, for one reason or another have decided against them. But there are still several options to explore.

One of those is Nemo, which I've been using all day. There are a couple issues, one of which is finding a user forum or mailing list or someplace where I can ask questions and see what others are doing. 

And one of the questions is the Nemo window. When I first launched it the window was about 8cm x 10cm, with everything inside all scrunched up. I dragged the window out to a decent size and worked for a while to familiarize myself with it. Then I tried File > New window, and it opened a new window. Unfortunately, this window was also 8cm x 10cm with the insides all messed up. And after another hour of using it I exited the program for about an hour. When I came back I re-launched it, and got the same small messed up window as before. C'mon people, just about every program I use remembers the size of its window when it is closed, and reopens with the same size and configuration. I'm not a programmer, but if all programs do it, it can't be that tough to implement.

My final question for users is about tabs. I read that Nemo has tabs, and that they are detachable. Well, my Nemo gots no tabs, and I can't find any reference to tabs in any of the menus or documentation. If it does have tabs and they are detachable, this might be the way to get multiple independent windows open with different views of the drives. 

I'm happy to say that I used it continuously all day and it never crashed. Wait! Shouldn't have said that out loud. :(

---

### Post by TheFu on 2023-07-07
I'd use **qmv**.  This way, my editor, which is crazy powerful, can be used to rename the files.  I'd also automate as much as possible.  I rename photos after getting home from a trip. It is multi-stepped.  The first step is to remove junk in the names and standardize to lower-case. Perhaps this will provide some ideas:
```
#!/bin/bash
rename 's/^IMG_.//g' IMG*
rename 's/JPG$/jpg/' *JPG
rename 's/^013//g' 013*

#  MVI_0426.MOV  --> 0426.mov
rename 's/^MVI_//g' *MOV
rename 's/MOV$/mov/g' *MOV
rename 's/MP4/mp4/g' *MP4

# Fix Panorama photos
rename 's/.jpg/-pano.jpg/g' ST*
rename 's/ST._0//g' ST*

chmod -x *jpg *mov
```

If there are 3 typical input filenames, I'd have 3 different cases for renaming them.  With Perl regex, grouping parts of filenames isn't hard.
Of course, there's a point where a human needs to type in the more descriptive parts of the names and I do that with **qmv** while viewing the images using **geeqie**.

Replacing the periods in a filename with '_' is easy.   
```
rename 's/\./_/g' *
```
Then I'd just need to put back any extension.
```
rename 's/_jpg/.jpg/g' *pg
rename 's/_mov/.mov/g' *
rename 's/_mp4/.mp4/g' *

```
Easy. Renaming thousands of files can be handled in a few seconds.

---

### Post by MAFoElffen on 2023-07-07
Nemo came from a fork of Nautilus, by the Cinnamon Desktop Dev's at Mint. Is very customizable, and has many plugins for it. Caja is another fork of Nautilius.

Because both are forks of Nautililus, both work with Nautilus automation scripts. Though there might be some slight differences that might have to be tweaked, just in the paths and syntax they use between main and the forks.

But you can automate things in Nemo... To help yourself out using it, for tasks you do.

---

### Post by dragonfly41 on 2023-07-07
This thread interests me since I have long had at the back of my mind how to scan through many folders and files scattered around my desktop. Getting order out of chaos. And I conclude that automation is necessary.

I favour using Krusader as one tool which like many other applications can be automated.

Now turning to the "in fashion" ChatGPT I tried this query and ChatGPT "joined the dots" of my rough plan.

This was my opening query:

**Given a Ubuntu desktop with thousands of folders containing files of different types and unknown content what plan can automate inspection of every folder and file and where there is doubt call on human inspection?**
**Consider using the following tools to support automation of this forensic inspection of a chaotic desktop.**
**Actiona as UI emulator or pyautogui to drive desktop tools such as Krusader using either Krusader commands or x,y points on screen.**
**Krusader with useractions to inspect folders and files**
**Albert with python extensions and using the popup query field to give human commands in the workflow.**
**Zotero to form an index of reorganised folder**
**Can app qmv contribute to this forensic workflow.**
**Can forensics tools help with identifying metadata of folders and files.**


Came up with a nice blueprint which I will try out.

I will post a link if it works out (but not immediately). Try ChatGPT yourself.

And I do think that an understanding of linguistics should help in understanding the context of each inspected file.

In the interim (before I have time to try a proof of concept) although dual pane file manager is not favoured do try Krusader and see what can be done therein with "useractions" (in toolbar). In my concept Krusader will be driven from automation scripts which hold the "rules" of forensic inspection.


P.S. Krusader has tabs.

---

### Post by TheFu on 2023-07-07
I worked in document management from 1995-2001.  This work was for a huge publisher and an agency of the govt creating technical documentation, which included images, engineering diagrams, text and custom fonts.

I did a quick search for linguistics organization and found something called a TIMIT structure. [http://www.ling.helsinki.fi/kit/2009s/clt231/NLTK/book/ch11-ManagingLinguisticData.html](http://www.ling.helsinki.fi/kit/2009s/clt231/NLTK/book/ch11-ManagingLinguisticData.html)  I try to never re-invent a wheel that has already been invented. TIMIT is probably old news to everyone here, except me.

---

### Post by John Jason Jordan on 2023-07-08
In re linguistics, yes, I have degrees in it. But my files are 99% videos, although typically each includes one or more audio channels. Lx won't be a bit of help. There might be ways to organize them by things like length, video resolution, or something else, but none of those would be useful. And I should add before anyone gets excited, I produced all of them personally and none of them have any connection with the DMCA. :) Also, these files are from a different side of my life that has nothing to do with my academic work. There are linguists who work in AI, but my interests have always been in historical lx. It would take me  far longer to learn how to use the AI tools you are discussing than it's worth, and I'm convinced that they would accomplish nothing for me anyway. I can complete my present task in a few days more, and I also gain the benefit of reminding myself about some of the files that I have not thought about for a long time. Some here may have thought I was doing this to reorganize my files, but no, I'm just cleaning up. An alphabetical list is all the organization that I need.

---

