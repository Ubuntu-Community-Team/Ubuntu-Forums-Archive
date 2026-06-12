---
title: "System management requires a better file manager than Files!"
date: 2016-10-14
forum: General Help
---

### Post by aajax on 2016-10-14
I'm afraid that the standard file manager, which appears to simply be called Files, that comes with Ubuntu is inadequate for the purpose of system management/administration.  First and foremost is the need to both see and act on all directories, files, links, etc.  Another important consideration is that since this is something needed for troubleshooting purposes it should have minimal dependencies.  This certainly means that it should not depend on the desktop environment.  In that, it should be something that can be invoked from a terminal session when the desktop is broken.  Whether or not it uses a GUI (i.e., depends on X Windows) is unclear to me.

From my limited experience with Linux and some research I've identified 2 candidates.  First is Midnight Commander which I think has been widely deployed, is very established but old, and looks to have minimal dependency.  Second is Xfe which is advertised as being lean and mean with minimal dependency but it uses a GUI which apparently utilizes the Fox Toolkit whose purpose is to achieve cross platform applicability which while nice does not seem necessary.  However, the Ubuntu package for Xfe says it needs to install 56 new packages.  This is not what I would have thought is meant by lean.  The packages notably include things like Audacious (an audio player), and ffmpeg (a video transcoder) which I find bazarre.

This leaves me with 2 questions as follows:

[LIST=1]
[*]What file manager fits the bill?  (which of course includes those I've not discovered)
[*]Can anyone explain either why Xfe drags in so many other packages?  Or if not possibly where I might look for an explanation?
[/LIST]

---

### Post by bab1 on 2016-10-14
> **aajax said:**
> I'm afraid that the standard file manager, which appears to simply be called Files, that comes with Ubuntu is inadequate for the purpose of system management/administration.  First and foremost is the need to both see and act on all directories, files, links, etc.  Another important consideration is that since this is something needed for troubleshooting purposes it should have minimal dependencies.  This certainly means that it should not depend on the desktop environment.  In that, it should be something that can be invoked from a terminal session when the desktop is broken.  Whether or not it uses a GUI (i.e., depends on X Windows) is unclear to me.

From my limited experience with Linux and some research I've identified 2 candidates.  First is Midnight Commander which I think has been widely deployed, is very established but old, and looks to have minimal dependency.  Second is Xfe which is advertised as being lean and mean with minimal dependency but it uses a GUI which apparently utilizes the Fox Toolkit whose purpose is to achieve cross platform applicability which while nice does not seem necessary.  However, the Ubuntu package for Xfe says it needs to install 56 new packages.  This is not what I would have thought is meant by lean.  The packages notably include things like Audacious (an audio player), and ffmpeg (a video transcoder) which I find bazarre.

This leaves me with 2 questions as follows:

[LIST=1]
[*]What file manager fits the bill?  (which of course includes those I've not discovered)
[*]Can anyone explain either why Xfe drags in so many other packages?  Or if not possibly where I might look for an explanation?
[/LIST]
If you are going to be a successful as a Linux system administrator you will need to learn the terminal (Bash shell) and scripting.  There is no need to install a GUI file manager at all.  No reliance on x-server or dependencies.

---

### Post by sgage on 2016-10-14
I agree with what Bab1 said. However, if you want sort of a middle ground, I've used FileRunner for many many years as my power file manager. I agree that 'Files' (aka Nautilus), is pitifully inadequate, and as someone who has watched its evolution from the beginning with all the fanfare and whatnot, can't believe that after all these years this is where the flagship file manager of Gnome is at. Oh well.

---

### Post by oldos2er on 2016-10-14
I haven't used xfe, but you could try installing it with the --no-install-recommends option so it won't pull in audacious, etc. I prefer mc myself. Another good CLI file manager is ranger.

---

### Post by aajax on 2016-10-14
I do understand the need for using the CLI and have a fairly good grasp of the basic commands and can write simple scripts.  However, a file manager (browser) is still very handy for doing many things.  Calling it middle ground fits pretty good with what I had in mind.  Thanks for the suggestions.

---

### Post by aajax on 2016-10-14
BTW I think I'm also an Old OS/2 useER.

---

### Post by oldos2er on 2016-10-15
Always nice to see a former OS/2 user


Sunflower is a nice GUI fm, it uses gtk2 (I think) with minimal dependencies.

---

### Post by aajax on 2016-10-15
I tried the "--no-install-recommends" suggestion.  This looks very promising.  The new packages that will be installed was reduced from 56 to 3 (or 2 additional packages).  The 2 extras were something called xfe-themes and libfox-... (which was expected).  It will take some time using it to make any assessment as to superiority but this does qualify as lean in my mind.  It looks like Audacious dragged in a lot of extra packages that might have already been there if this computer were configured for some serious Audio/Video processing but that's not the present case.

Both filerunner and sunflower appear to be things that have not been packaged for Ubuntu which for the moment causes me to prefer Xfe.  Also based on google searching of the web Xfe appears to be widely used whereas neither sunflower or filerunner showed up in my searches.

BTW, OS/2 is long gone but I still use and prefer my PS/2 keyboards!

---

### Post by cariboo on 2016-10-15
Removed duplicate post.

---

### Post by Qew on 2016-10-15
There's no reason why you can't really try both Xfe and Midnight Commander to see which you prefer. I run with mc, which is powerful, configurable and can be run from an xterm or virtual terminal. It's also lean and doesn't have many dependencies. Forget that it might appear "old", for it's as capable as any of the GUI file managers out there. Give it a whirl.

---

