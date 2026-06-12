---
title: "Tagging Idea: Nautilus, Files"
date: 2007-05-25
forum: General Help
---

### Post by wyth on 2007-05-25
I'm not sure if this is the right place to put this, but I had an idea I'd like to get some feedback on.

How useful would a file tagging feature be in Ubuntu/Linux?  What I'm thinking is a way to add tags to any file, and have a tagging search feature in nautilus.  (Does konqueror/dolphin offer this?)  

For instance, I have quite a few articles about Stanley Kubrick that I'm using for my PhD work.  Some go in some folders because they're related to that material, some go in others.  However, if I could tag each file -- kubrick, 2001, symbolism, etc. -- and then run a search on just the tag, I could get every necessary file related to that search term.  The way I'm imagining it, the tags could exist in the properties dialog, along with notes, permissions, emblems, etc.  You could also go into some frontend (tag cloud?) to see what tags you have, and add or delete tags.

I think this is kind of what beagle/deskbar is for, but beagle is constantly indexing things, and a lot of people (like me) remove it because it throttles the fan and the cpu to sometimes frightening levels.  But tagging is something that can be done very lightly; we do it with our mp3 collections all the time and snap such features into our blogs with little trouble.

So -- useful feature, pipe dream, or outright dumb idea?  

(And should this post be someplace else?)

---

### Post by wyth on 2007-05-25
Got some poll responses; any comments?

---

### Post by wyth on 2007-05-25
bump

---

### Post by wyth on 2007-05-26
badabump

---

### Post by fragos on 2007-05-26
Interesting, F-Spot has this but its there because it insists on placing all photos in folders by the day the pic was shot.  You could create something like that for yourself by creating folders for the tags and using symbolic links to the files stored in those tag folders.  If you want to get one step fancier, you can write a nautilus script to create the link and store it where you want.  There is a similarity to emblems buts those are just visual.

---

### Post by wyth on 2007-05-27
If I knew how to go about it I'd make such a script, and then offer it to anyone.  But the more I thought about this, the more I thought this would have to be something implemented at the Gnome end of things, and not with the distribution.  If you were to incorporate such a feature into nautilus, that'd be up to the Nautilus developers, no?

---

### Post by fragos on 2007-05-27
Anyone can get the source, implement a change and offer it to the nautilus team for consideration for inclusion.  Its all part of the GPL licensing.  The nautilus scripts on the other hand are addons not unlike a an extension or plugin that can stand alone as a separate package.  Nautilus scripts can be written in any scripting langauge with usefull script as small as one or two commands.  I suggested them because they are much simpler programing in C for example.  Google "nautilus scripts" and you'll see many are already available for use or modification to meet your personal needs.

---

### Post by wyth on 2007-05-27
I just found some scripts that will do it.  When I get it squared away, I'll post again.

---

### Post by fragos on 2007-05-27
I'll be curious to see the squared results.  There's a nautilus script I use frequently and I thought you might find it handy.  In ~/.gnome2/nautilus-scripts create a text file called perhaps "Open as Administrator" with the following three lines of text in it.

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo "gnome-open $uri" &
done

You'll need to make the file executatble with permissions.  It does what the label I suggested  and opens files as root with whatever the normal application would be.  If you open a directory with it you get a root instance of nautilus.  You may need to restart X to get before the script is added to the right click menu.

Your writing is very interesting -- a deep thinker.

---

### Post by wyth on 2007-05-28
Okay, I've got something going here, witht he help of [leaftag]("http://www.chipx86.com/wiki/Leaftag") and a few [nautilus scripts]("http://idea.zanestate.edu/archives/2006/09/adding-metadata-keywords-or-tags-to-files-with-leaftag-in-ubuntu-linux/").

[Leaftag]("http://www.chipx86.com/wiki/Leaftag") is designed specifically to do what I was looking for.  However, development really stopped maybe a year ago, and doesn't look like it's continuing, and the four packages need to be compiled.  You'll need to get the dev files for a few things; I needed libglib2.0-dev, the libsqlite devs, and python-gtk2-dev.  There's a deb of libleaftag [here]("http://apt.debian.org.tw/pool/libl/libleaftag/libleaftag0_0.3.0-1_i386.deb"); I compiled at first, and it didn't take.  The deb did the trick for me.

Leaftag is a command-line deal, yet is supposed to [integrate with Deskbar]("http://raphael.slinckx.net/blog/2006-03-06/deskbar-and-leaftag-last-exit") -- but not for me, probably because I removed Beagle.

No matter.  [Over here]("http://idea.zanestate.edu/archives/2006/09/adding-metadata-keywords-or-tags-to-files-with-leaftag-in-ubuntu-linux/") you can get some nautilus scripts that will work with the sqlite database to add, search and display all the tags from the context menu. It's fast, light-weight, slick, and does just what it should.

I'm just now starting to work with it, but it seems like it's going to do the trick.  If this works well enough, I may put up a how-to.  I've seen a few other people asking how to get this all rolling.

---

### Post by fragos on 2007-05-28
The howto would be great.  I for one have been wanting to dig deaper into nautilus scripts.  Your howto would be instructive and helpful.

---

### Post by wyth on 2007-05-29
I may or may not post a how-to; I'm seeing some problems with this setup.  I have it going, but when I use the scripts to search for tags, it brings up a window with a bunch of broken links to the tagged files.  The files exist, they're tagged, and I can work it via the command line, but something with the scripts (and maybe the sqlite database) is bringing up wrong info.

So... still a work in progress.

---

### Post by fragos on 2007-05-29
Not everything that people post on the web for other to use works correctly.  Best of luck with it.  At the very least it will represent a learning exorsize.  I for one, always learn more when I have a real problem to solve.

---

### Post by wyth on 2007-06-09
Ladies and Gentlemen, I may have hit a near-holy grail for search and tagging.  

So I didn't get leaftag to work.  The software hasn't really been developed in over a year, and may just not be a compatibility issue.

But I recently updated to Feisty (and solved [my ATI video card issue]("http://ubuntuforums.org/showthread.php?t=224332"), so I'm thrilled), removed Beagle, and discovered Tracker.  Beagle was wrecking my system with its resource-greed, and I was looking for an alternative (which is partly what got me thinking about tagging in the first place).  Tracker's written in C, isn't sitting on top of Mono, and is just a lot lighter and more efficient, I found.  It is, however, still under development; 0.5.4 is in the repositories, but 0.6 is on the way, with considerable improvements.  Because it's still new, if you want it to index more than just /home/USER, you need to go into /home/USER/.Tracker/tracker.cfg and add the directories (it says where).  

And there's some interesting development going on. It's all based on the freedesktop standards and is becoming increasingly extensible and added into other programs. It's slated to be incorporated into Nautilus in Gutsy. The one feature I found -- and this is the main thing -- is file tagging. Once the right python extension is added, you get a tags tab in the properties of any file. Tag a file, and that tag becomes searchable in Tracker. Nice. (Need python-nautilus for it to work.)

It also has a deskbar-applet plugin (libdeskbar-tracker in the repositories), but I found that this -- and even the standard applet -- would crash Tracker if I had them on the panel.  It's a bug; something to do with the order that dbus starts vs. Tracker's indexer program *trackerd.*  This should get ironed out, and it's no showstopper, because if you just leave out the deskbar applet plugin, and don't add Tracker to the panel (it sits in Applications/Accessories), you're fine.

Below are the links I've gathered that are most useful.  Replacing Nautilus with the Tracker-ready Nautilus deb is useful; it gets you Nautilus with Tracker directly integrated into it.   I'd suggest reading all the comments on those pages, though; they offer a few little tweaks that are necessary to get things going.

It takes a little bit of effort, but so far I'm finding it well worth the work.

[Ubuntu Documents page on Tracker]("https://help.ubuntu.com/community/MetaTracker")
[The Tracker project page]("http://www.gnome.org/projects/tracker/index.html")
[An updated Nautilus deb with integrated tracker]("http://www.madman2k.net/comments/76")
[Nautilus python extension for tagging]("http://www.madman2k.net/comments/56")
[For the svn adventurous]("http://doc.gwos.org/index.php/LatestTracker")

---

### Post by fragos on 2007-06-09
You certainly have dug into this with a vengance.  Thank you for sharing your findings.  I avoided Beagle because it's such a constant resource hog.  Tracker looks like a superior solution worth trying.  I've been using Feisty for some time and love it.  I love change and am always an early adopter of new Ubuntu releases.

---

### Post by henriquemaia on 2007-06-12
This is a great idea.

---

### Post by Elijah on 2007-07-07
bump

gotta agree with this, I'm tired of managing with folders and directories. I just wanted management similar to how del.icio.us categorizes things.

---

### Post by wyth on 2007-07-07
I don't want to sway anyone's DE choice, but I recently switched to KDE in an attempt to [see if a different desktop environment would work better with my video card]("http://ubuntuforums.org/showthread.php?t=487295") (it does).  

KDE is switching to Dolphin for the file manager, and integrating Nepomuk tagging and semantic metadata into Dolphin.  This won't be out really until KDE4 is released, but at least it's clearly in the works.  (Info [here]("http://nepomuk-kde.semanticdesktop.org/xwiki/bin/view/Main/"), [here]("http://liquidat.wordpress.com/2007/05/31/semantic-desktop-and-kde-4-state-and-plans-of-nepomuk-kde/"), and [here]("http://liquidat.wordpress.com/2007/05/31/semantic-desktop-and-kde-4-state-and-plans-of-nepomuk-kde/").)

---

### Post by tehkain on 2007-07-17
> **wyth said:**
> Ladies and Gentlemen, I may have hit a near-holy grail for search and tagging.  

Below are the links I've gathered that are most useful.  Replacing Nautilus with the Tracker-ready Nautilus deb is useful; it gets you Nautilus with Tracker directly integrated into it.   I'd suggest reading all the comments on those pages, though; they offer a few little tweaks that are necessary to get things going.



Just wanted to jump in and say I seen this a month back while searching for tagging. This is a dream come true... hopefully this is pushed into gutsy.

I have been looking for this for so long that i even resorted to making my own app. Sadly it was not built on tracker and only worked in a select directory. So a week or so ago I started working my new project for the ubuntu mobile and embedded OS, it is called TouchTag(name is not final). The app uses a tag cloud type interface made for touch screen devices. Tracker integration is gonna be tough but it is my goal.

[http://en.wikipedia.org/wiki/Tag_cloud](http://en.wikipedia.org/wiki/Tag_cloud)

---

### Post by TheOtherShoe on 2007-08-08
> **wyth said:**
> Ladies and Gentlemen, I may have hit a near-holy grail for search and tagging. 

If you would like another option for your list, I created some Nautilus scripts that take advantage of Tracker's tagging support: [http://ubuntuforums.org/showthread.php?p=3156590#post3156590]("http://ubuntuforums.org/showthread.php?p=3156590#post3156590")

---

### Post by rigdzinthar on 2007-08-22
tagging would be "delicious"...

---

### Post by el3ktro on 2007-08-23
I was always wondering why we don't completely rely on tagging when storing & searching for files. When looking at MP3 files - they have tags for artist, title, album etc. - and you have to give them a file name. Why is that? I'd love to see a file system which relies on tags ONLY. There would be some automatic tags (like the size of a picture, the date a file was created, the length of a audio file etc. - and manual tags, which you can add for yourself. Perhaps those tags could also be "cascaded" like you can do it with F-Spot - you can add tags, and sub-tags. This would actually not be much different than a folder structure that you have today - with the difference that you could re-organize your stuff with a simple mouse click. For example, I could tell Nautilus to sort my pictures after the tag "location", so I'd have a folder-like structure, one "folder" for each location with all pictures taken at that location in them. A simple click, and I could sort my folders after people, so I had a "folder" structure sorted after the people seen on the photos. With "traditional" folders, you could EITHER create a folder for each location and put your photos in there, OR create a folder for each person.

What works for music files & photos could work for ALL files that usually reside within /home, so I'd like to see a filesystem, or some kind of a plugin for a filesystem, which implements filesystem-wide tagging for all files and abandoning filenames+folders. This way, if you copy such a file over to another computer, you'd see the same tags there.

Tom

---

### Post by TheOtherShoe on 2007-08-23
The latest versions of Epiphany do some fun stuff with tagging for bookmarks. You apply tags the same way you do in any other application - but when displaying the bookmarks Epiphany uses an algorithm to automatically choose tag hierarchies. For example, if you have a bunch of bookmarks tagged "news", and you also have some things tagged "news" and "Ubuntu news", then "Ubuntu news" is displayed as a sub-group. In Epiphany that means that "Ubuntu news" bookmarks appear in a sub-menu under "News".

The problem with abandoning the file name system is that it is important for lots of system software to have an unambiguous way to look up a file. With tags there is nothing to prevent one from tagging two files with exactly the same tags. But that's no barrier to creating a file manager that uses only tags while leaving the underlying operating system to continue using file names. I would like to see such a thing.

---

### Post by wyth on 2007-10-20
So tagging is implemented via Tracker in Gutsy.  Anyone tried it out yet? I've been pretty busy, and know I'd be more productive if I was using it, but haven't sat down to work things out yet.

---

### Post by flomar on 2008-02-09
hi,

i'm using TheOtherShoes nautilus script for tagging my stuff. it took my one day (including brakes for 'trackerd' and 'nautilus') to tag my files (pictures, documents, artwork,..) with ca. 30000+ tags in total. it's already working very well i can search using the tags in the tracker-search-tool in an easy way!

however im missing one feature, a TagCloud. I'm using [PaperBox]("http://live.gnome.org/PaperBox") for browsing through my collection of PDF documents via a TagCloud, its great! Does anybody know an application to browse your whole (tracker)database via a TagCloud?

thanks in advance,
Flo

---

### Post by jazzgossen on 2008-03-06
> **flomar said:**
> 
i'm using TheOtherShoes nautilus script for tagging my stuff. 

What is that? I tried apt-cache search and google, but couldn't find any information on TheOtherShoes.

---

### Post by TheOtherShoe on 2008-03-06
> **jazzgossen said:**
> What is that? I tried apt-cache search and google, but couldn't find any information on TheOtherShoes.

flomar is referring to a collection of scripts that I wrote. You can find them in [this thread](http://ubuntuforums.org/showthread.php?p=3156590#post3156590).

[QUOTE=flomar]i'm using TheOtherShoes nautilus script for tagging my stuff. it took my one day (including brakes for 'trackerd' and 'nautilus') to tag my files (pictures, documents, artwork,..) with ca. 30000+ tags in total. it's already working very well i can search using the tags in the tracker-search-tool in an easy way!

however im missing one feature, a TagCloud. I'm using PaperBox for browsing through my collection of PDF documents via a TagCloud, its great! Does anybody know an application to browse your whole (tracker)database via a TagCloud?[/QUOTE]

I'm really glad that my scripts are useful to you! But I'm afraid I don't know of any application that allows you to browse files with a tag cloud. Though I agree that it is a conspicuously missing feature. I think that a Nautilus sidebar plugin might work quite well.

On the other hand, I have read persuasive arguments saying that the way to go is to browse files using applications dedicated to particular kinds of files. For example, if you could get these applications to read tracker tags, using F-Spot to browse pictures, Amarok to browse music, and so on. Though these applications could also use some work in implementing powerful tag-based navigation.

---

### Post by yanpai on 2008-03-07
Is it (tagging & tag cloud) possible in a KDE desktop?

---

### Post by TheOtherShoe on 2008-03-07
> **yanpai said:**
> Is it (tagging & tag cloud) possible in a KDE desktop?

There is nothing to prevent you from using Tracker in KDE. The only tracker search tool that I am aware of is written in GTK; but I don't think that Tracker depends on Gnome in any other way. And I believe that KDE has good support for GTK applications.

There are other searching and indexing tools that have more Qt-friendly frontends - like [Strigi](http://strigi.sourceforge.net/). But I don't know specifically of any tool other than Tracker that allows tagging.

Since my tagging scripts are Nautilus-only, you would have to find other means of tagging files. Perhaps a similar set of scripts for Konqueror or Dolphin would not be difficult to write.

As for tag clouds; I don't know of any KDE applications that let you browse files by cloud. So in that respect you would be in the same boat that Gnome users are in.

It happens that I have been learning Qt programming for another project though. So maybe I will be able to design a tag-based file browser at some point. If anyone has suggestions for what that should look like, you can send them along to me and I will write them all down.

---

