---
title: "How do I add a new empty file to a folder using the file manager in ubuntu 18.04"
date: 2018-09-15
forum: General Help
---

### Post by Tom_Carr on 2018-09-15
How do I add a new empty file to a folder using the file manager in ubuntu 18.04

---

### Post by mc4man on 2018-09-15
Use gedit to create an empty file in the  ~/Templates folder. Name it whatever you wish, ex. Untitled Document

---

### Post by deadflowr on 2018-09-15
What should work is you create a a folder called Templates where your top level folders are 
(like where the Pictures, Videos, and Music Folders are in your home folder)
and then create a single file called something like Empty Document and put it in the Templates folder.
Once that's done Create a new document should show.
from a terminal to do all at once run
```
mkdir Templates
cd Templates
touch Empty\ Document
```

Graphically, open the Text Editor and save (without doing anything), then create a folder and name it Templates then name the file to save.
(The name of the document can be anything you want, but note it'll be the name that show when you create a new document, so...)

The out of the box create a new document feature is gone and probably won't come back (at least any time soon)

ninja'd.
what I get for mumbling about the house.

---

### Post by Tom_Carr on 2018-09-16
> [COLOR=#000000]The out of the box create a new document feature is gone and probably won't come back (at least any time soon[/COLOR]

Why was it removed?

---

### Post by deadflowr on 2018-09-16
> **Tom_Carr said:**
> Why was it removed?

I think Gnome developer Carlos Soriano explains the reasoning here:
[https://bugzilla.gnome.org/show_bug.cgi?id=687139#c15]("https://bugzilla.gnome.org/show_bug.cgi?id=687139#c15")

And it's not really removed, but changed.

---

### Post by Tom_Carr on 2018-09-16
Thanks for  the link to the explanation.   I disagree with Carlos Sariano on this, but it is not a big deal once you understand it.

---

### Post by The Cog on 2018-09-16
Seems very user hostile to me. But I hear that gnome has been that way, busy removing features for quite a while.

You could try a different file manager. Thunar (default with Xubuntu) has an option to create files.

---

### Post by Tom_Carr on 2018-09-17
> [COLOR=#000000]Seems very user hostile to me. But I hear that gnome has been that way, busy removing features for quite a while.[/COLOR]

What else has it removed?

---

### Post by deadflowr on 2018-09-17
> **Tom_Carr said:**
> What else has it removed?

One I can think of off the top of my head would be split view or extra pane setting.
Which allowed you to open two panes with different folders in one window.

But they removed it, for whatever reason.
It made it really easy to copy or move from one place to another, as all you had to do was open both locations, one in each pane, and right click select the move or copy to and it would give an option to copy to the other pane. No hoops to go through, just a plain and simple setup.
But that's been gone for years now. I think it was removed right after 12.04 was released.

Other file managers such as dolphin, caja and nemo have that feature though.
So not all's lost, I guess. Just a pain (pun intended) that nautilus doesn't anymore. 

I'm sure there are other features gone as well, but I cannot think what they were right now.

---

### Post by The Cog on 2018-09-17
> **Tom_Carr said:**
> What else has it removed?
I don't know. I haven't looked at Gnome since before Unity was released - I have used Xubuntu for a long time now. But I do remember seeing complaints in these forums about Gnome features being removed from time to time. I'm not sure, but I think these complaints mostly referred to Gnome-3.

---

### Post by Tom_Carr on 2018-09-17
I'm going to try another file manager.  Which would you recommend?

---

### Post by deadflowr on 2018-09-17
nemo
You might look into [mc3man's nemo ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/bionic-noprop").

As posted it's built with unity in mind, but should work with gnome-shell.
Nemo is what nautilus was (and in some cases, what many think it should still be)

You want to install from the ppa as oppose to the nemo version in Ubuntu's repositories because the default nemo from the repos also installed the cinnamon desktop.
The ppa excludes all that. So no unwanted bloat.

---

### Post by oldrocker99 on 2018-09-17
You can also try nano to create a file. Just create an empty file and save it under whatever name you like.

I started using nano 10 years ago, and it has become my go-to editor when I am working in my /etc directory. All the commands are in the margins, so you can see that W(rite Out) saves the file.

---

