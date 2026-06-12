---
title: "Open With shows folders instead of apps"
date: 2007-10-22
forum: General Help
---

### Post by raydar on 2007-10-22
Probably a dumb question, but now a friend of mine who's completely new to Linux is getting this too, and wants my help, so here goes:

The "Open With" dialog (as in right-click, Open With) has for me always presented a list of folders to go hunting through for an executable file (see attached image)--not a handy list of applications to choose from.  I'm new enough to Linux that I don't know for sure where to look for the right file to select for a given application, and half the time after a few tries I give up and attempt some other way (like downloading the file & opening it via a File dialog).

All the posts I've found here speak as though the user can just click a radio button next to an app's name in the Open With dialog and be done.  But on two completely different Ubuntu installations of my own, and now my friend's Ubuntu installation, we get the list of folders, not apps.  How do we get our machines to show the apps instead?

[ATTACH]47331[/ATTACH]

[ATTACH]47332[/ATTACH]

---

### Post by raydar on 2007-10-23
Okay, I figured out my problem--apples and oranges:  The "open with" dialog I screenshot[ted?] above is a _Firefox_ "open with" dialog, which lists folders instead of apps, and which I was getting from a MIDI file link on a web page.  On the other hand, when I right-click the file as it sits on my desktop, I get _Gnome's_ "open with" dialog, and that has the list of applications.  

So I found that Firefox's file associations are set in Edit-->Preferences-->content-->file types-->manage, and thought I was about to solve my MIDI-link-playing problem.  But MIDI files are not included in the available file types, and there's no "add" (or remove) button!  There's a search feature, but why?--there are only 23 entries.  

I was silly for not discerning which "open with" box I was actually talking about, and Firefox is silly for not letting MIDI files be associated with an application. :P

Too bad Firefox can't (or at least doesn't) get at the list of installed applications for its own "open with" dialog, or if that could be a security/privacy issue, then too bad it can't cause Gnome to pop up Gnome's "open with" dialog with those apps nicely listed.  I tried mining Gnome's "Applications" menu for the path, using System-->Preferences-->Main Menu and right-clicking to check applications' properties, but that gives me only the command--not the path (clicking "Browse" opens my home folder, not a folder the command pertains to).  Doing a search for files by that command name can be inconclusive, with >1 file by same name and few file extensions, or me being too new to Linux to know what location means "this is it."  Is there something else more handy that I'm overlooking?

---

