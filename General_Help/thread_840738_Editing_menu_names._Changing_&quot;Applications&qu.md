---
title: "Editing menu names. Changing &quot;Applications&quot; to &quot;Programs&quot;."
date: 2008-06-25
forum: General Help
---

### Post by Atean_Linux on 2008-06-25
I've tried searching all over the internet on how to do this.

I am trying to change the default panel's Main menu names. For example: From "Applications" to "Programs". And from "Places" to "Folders". How can I do this? What files do I need to edit?

Thank you.

---

### Post by badfish591 on 2008-06-25
to be honest, i don't think you can do this. you may be stuck with those names.

---

### Post by nkri on 2008-06-25
Go to System>Help and Support.

Search "Gnome 2.14 Desktop System Administration Guide"

Click on the link.

On the right pane, go to "Customizing Menus"

Find Section 2.5; the instructions for editing menus are in there.

Good luck!

---

### Post by el-mar01 on 2008-06-26
> **Atean_Linux said:**
>  From "Applications" to "Programs". And from "Places" to "Folders". How can 

That is illogical ... the places menu contains more than folders so why call it Folders ?? .. plus the Applications Places System menus are the cornerstone of the GNOME desktop .. not sure why you would want to change it.

---

### Post by Atean_Linux on 2008-06-26
> **el-mar01 said:**
> That is illogical ... the places menu contains more than folders so why call it Folders ?? .. plus the Applications Places System menus are the cornerstone of the GNOME desktop .. not sure why you would want to change it.


Why would I want to change it... Hmm...

Well, maybe if you knew that I customized the "Places" menu to only contain links to Folders, then maybe it wouldn't sound so illogical. Would it? Maybe it makes perfect sense to rename the menu to "Folders" now. No?

And, those 3 menus are the cornerstone to Gnome? I didn't know that.

And, are you really not sure why I would like to rename the menus?
Strange... You see, I am having difficulty trying to understand you, because as far as I'm concerned, that's what Open-Source is all about!

That is the reason why I ditched Windows XP. Because of the Open-Source concept. Anyone should have the right to modify and improve on any and all software as they see fit.

I completely support this concept. I feel so strongly about it that I specifically signed up for programming classes in hopes that one day I can do my part in helping this concept expand even further.

I am supporting it by word of mouth and all. Telling everyone I know about the greatness that I discovered a month ago. I have gotten 3 people to switch already. 2 of them I installed it for them.

I believe that I at least deserve the right to come on these forums and ask a question about customizing MY desktop without being interrogated or answered with more questions of your own. But for all the other curious few, there are my reasons. In the beginning of this message.

I want to thank everyone that responded with useful information. And this being my first thread on the forums and all, I will hope that these forums are filled with more people like those, and less people like you.

Thank you.

---

### Post by suprfish on 2008-06-28
I am also wondering how to do this; specifically, modifying the 'places' menu (i.e. adding more folders other than 'Documents' and 'Music'). There doesn't seem to be a way to do so.

> **Atean_Linux said:**
> 
I believe that I at least deserve the right to come on these forums and ask a question about customizing MY desktop without being interrogated or answered with more questions of your own. But for all the other curious few, there are my reasons. In the beginning of this message.

I want to thank everyone that responded with useful information. And this being my first thread on the forums and all, I will hope that these forums are filled with more people like those, and less people like you.

I hope you weren't too put off by el-mar01, I'm sure his intention was to be helpful :)

---

### Post by dizee on 2008-06-28
> **suprfish said:**
> I am also wondering how to do this; specifically, modifying the 'places' menu (i.e. adding more folders other than 'Documents' and 'Music'). There doesn't seem to be a way to do so.
I think you can add them as shortcuts in Nautilus and then they show up there.

as for renaming the "places" menu itself, that'd probably require re-compiling from modified source code. the language translation teams manage it though so it's definitely possible.

---

### Post by suprfish on 2008-06-28
Add them as shortcuts? What do you mean?
I have a suspicion that it can be modified with gconf-editor..

---

### Post by suprfish on 2008-06-28
Nevermind, it is ~/.gtk-bookmarks, or just Bookmarks -> Add bookmark... can't believe I didn't see that.

---

### Post by Atean_Linux on 2008-06-30
> **suprfish said:**
> Nevermind, it is ~/.gtk-bookmarks, or just Bookmarks -> Add bookmark... can't believe I didn't see that.


Yes, I found out how to do that a little while before creating this thread. But, through my explorations I found out a couple of pretty interesting things.


>  If you add the applet titled "Gnome Menu" (which is the 'Applications' and 'Places' and 'System' Menus merged into one) and then you go into gconf-editor and you change the menu-path to "applications:/", then the Gnome Menu no longer shows all the menus merged, instead it only shows the Applications menu. So it does the same as just clicking on the 'Applications' menu. But when I logged off and logged back in the whole applet had transformed itself into the Custom Menu of 'Applications Places System'. It was strange, and I dont know what causes it to completely change like that.

>  I began experimenting a little bit and tried to type "applications:/" into nautilus and it showed an error message. So I did 'gksu nautilus' and then it showed the message "/home/atean/applications couldn't be found". I found this very interesting.



So where does "applications:/" lead to? I am now wondering if it leads to the 'Applications.directory' file that I discovered a few days back. I edited it along with another file I found and the menu still said "Applications" but I atleast managed to change the name of the menu SOMEWHERE, because now the 'Menu Editor' thinks the menu is called "Programs", but the Menu name still shows up as "Applications", as pictured below.


[IMG]http://i252.photobucket.com/albums/hh37/ateanboy/Screenshot.png[/IMG]



So, in the end of it all I accross this conclusion: The only way to change the menu names is to get the source code of the Custom Menu bar used in Ubuntu, and modify it, and compile it, and install the new applet, and use that new menu applet instead of the one that comes with Ubuntu.

So, my new question is, does anyone know where I can find the source code for the "Applications' 'Places' and 'System' menu applet?

---

### Post by Atean_Linux on 2008-06-30
> **suprfish said:**
> I am also wondering how to do this; specifically, modifying the 'places' menu (i.e. adding more folders other than 'Documents' and 'Music'). There doesn't seem to be a way to do so.



I hope you weren't too put off by el-mar01, I'm sure his intention was to be helpful :)


Lol. I hope so too... But unfortunately I used to be a long-time member at another Gaming-related forum and I guess I'm still used to going into that Defensive mode at the slightest sense of sarcasm or ignorance.... My apologies.

---

### Post by daviddailey86 on 2009-05-14
Not sure if this is any help to you now, but here...

[http://gnome-hacks.org/hacks.html?id=28](http://gnome-hacks.org/hacks.html?id=28)

---

### Post by Pepe Lebuntu on 2009-09-18
Another option you have is to switch out of gnome, and go for something like XFCE (Xubuntu). I've now ditched Xubuntu and gone to GNOME for other reasons, but one of the things I loved was that you could easily change the names of the Applications and Places menu. I'm TOTALLY with the OP here - if this is OpenSource, I should be able to change these to whatever I want, especially so they take up less space.

I want to call them "What' "Where" "Way": Applications is about answering the question, "WHAT do I want to do?", Places is about answering the question "WHERE do I get my files, etc?", and System is about "In what WAY do I want my system to do stuff?". 

It'd be a beautiful thing - if I didn't have to hack around the backdoor to do it.

---

