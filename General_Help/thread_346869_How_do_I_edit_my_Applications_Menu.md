---
title: "How do I edit my Applications Menu?"
date: 2007-01-26
forum: General Help
---

### Post by omghax on 2007-01-26
Gah, it's bugging me because I try not to post on the forums - just search. But I have given up and now I need help, :(

I'm running Dapper Drake 6.06 LTS (I think that's what it's called), and I've installed Cedega and Wine. I love them both, but they don't love me in the same way. They've both decided to install themselfs in my Applications Menu (top left), and I can't find out a way to get rid of them. I've even tried using the 'Alacarte Menu Editor' to get rid of them, seem's I don't have permission or something to remove them.

I read in another thread that they're XML files, but I don't even know where to start looking. :(


This isn't an urgent problem, just a big annoyance everytime I open up my menu.

-- Thanks, :)

---

### Post by kosmic on 2007-01-26
There is an application called - ***Alacarte*** that can help you out :)

In edgy it is installed by default, but in dapper it is not :( just search in synaptic for it

---

### Post by omghax on 2007-01-26
I don't mean to be rude, but when I installed Edgy on my other computer I found that it was the other way around.

Alacarte was on my Dapper Drake installation, and not on my Edgy one.

I already said I tried using it, but it wont let me remove them - not sure why. Is there a way I can run it through root to do it?

---

### Post by kosmic on 2007-01-26
HI in edgy Alacarte should be in ->SYSTEM->PREFERENCES->A STRANGE NAME (it is not called alacarte, don't know why)

You can run alacarte in a terminal window like -> ***sudo alacarte*** and try to see if you can edit the menu then :)

---

### Post by omghax on 2007-01-26
Nope, still can't edit it.

Any other idea's? :confused:

---

### Post by SexyStud on 2007-01-27
I have this same problem. I can't edit my Applications menu, not even in with sudo/gksudo.

I tried sudo su, then launching alacarte. I can edit now, but the menu that shows up in alacarte is completely different from the one I truly have! (doesn't happen if I don't sudo su first)

---

### Post by shironeko on 2007-01-27
> **SexyStud said:**
> I have this same problem. I can't edit my Applications menu, not even in with sudo/gksudo.

I tried sudo su, then launching alacarte. I can edit now, but the menu that shows up in alacarte is completely different from the one I truly have! (doesn't happen if I don't sudo su first)

If you do Sudo with alacarte, you're editing the Root menu.
You want to edit, your own menu. No Sudo is needed.

Simply write alacarte, or go to System, Preferences, Menu Layout (or something like that).

---

### Post by omghax on 2007-01-27
*sigh*

Here's a picture of the menu open, yes I know where it is and how to open it.

**The Problem:** I can only edit SOME of the menu's, not all of them. Like, for example... TransGaming and Wine.

I'm curious on how the Menu's work, because like I said before -- I heard it was an XML file. I thought if I'd ask here, someone would instantly know what I was talking about and help me out. But it seems I'm going to have to look through more threads, :/

---

### Post by WW on 2007-01-27
omghax,

It appears that the menu data is stored in (at least) two places:
   /etc/xdg/menus
and
  ~/.config/menus
On my system (running 6.06), each of these contains a file called applications.menu.

I know nothing about editing these by hand.  For all I know, it may be Fraught With Peril (tm).  

WW

---

### Post by SexyStud on 2007-01-27
> **shironeko said:**
> If you do Sudo with alacarte, you're editing the Root menu.
You want to edit, your own menu. No Sudo is needed.

Simply write alacarte, or go to System, Preferences, Menu Layout (or something like that).

That is the original problem. Without doing "sudo", I can't edit. The program loads etc, but no changes can be made to the menu items.

---

### Post by JamieC on 2007-01-27
Try using the following command:-

Gnome:
```

gksudo alacarte

```

KDE:
```

kdesu alacarte

```

---

### Post by omghax on 2007-01-27
> **SexyStud said:**
> That is the original problem. Without doing "sudo", I can't edit. The program loads etc, but no changes can be made to the menu items.

Yay, someone who understands my problem! Too bad he has the same problem... :(

---

### Post by SexyStud on 2007-01-28
> **JamieC said:**
> Try using the following command:-

Gnome:
```

gksudo alacarte

```


Done it, same problem with sudo: I can edit it, but what shows up is not my menus, but the root menus.

---

### Post by Amaroq on 2007-02-06
> **WW said:**
> omghax,

It appears that the menu data is stored in (at least) two places:
   /etc/xdg/menus
and
  ~/.config/menus
On my system (running 6.06), each of these contains a file called applications.menu.


I don't know a whole lot about linux yet, but I'm guessing that the ~/.config/menus one is for your own personal menu and /etc/xdg/menus is for some systemwide menu thing, seeing as how ~ is your home directory while / is the root directory.

*looks at them both* Hmm... that ~/.config/menus one seems to be dependant on the /etc/xdg/menus one. It seems, to me anyway, to just have some settings in it to ovverride the main one.

The main one seems to declare a bunch of stuff. Instructions to read certain things, I think. Now... where is it reading that stuff from?

EDIT: Er... yeah. xD It's an XML file. I don't really know XML, so I'm just guessing here. The program or whatever that displays the menu must read it and have stuff already in itself that knows what to do based on the XML file. I'm rather curious about how to write a script that adds/removes certain things from it, so I'm more interested in how to modify files to achieve the desired affect rather than using a menu editor.

---

### Post by tesseract420 on 2007-02-06
Here's some more blind alleys trying to solve this problem:

sudo/gksudo alacarte doesn't work. It's still not possible to highlight or click on a menu item or category (in my case, the Debian menu, which is installed but you can't edit0.

The automatix forum suggests that if a menu item is unpopulated it can't be edited. They suggested populating the menus by: sudo update-menus, however, when I do this I get a bash error saying "update command not found" or "update-menus" command not found.

The Debian Menu program is menu-xdg. It shows up as being installed in Alacarte, but does not appear on the Menu bars. In 6.06 at least, System--Preferences--Menus and Toolbars does not address the issue or permit you to edit the applications menu.

Finally, rightclicking on the menu item in Alacarte just displays properties with no other options.

Anyone have any other ideas?

---

### Post by Amaroq on 2007-02-06
Ooh, I think I found something guys!

look in /usr/share/applications

There's a crapload of icons in there. Pick one that you're familiar with and open it in a text editor. I picked XMMS.desktop

Scroll down, there should be a line something like this.
```
Categories=Application;AudioVideo;
```

Now, in /etc/xdg/menus/applications.menu there is a block of code like this:
```
  <!-- Multimedia -->
  <Menu>
    <Name>Multimedia</Name>
    <Directory>Multimedia.directory</Directory>
    <Include>
      <And>
        <Category>AudioVideo</Category>
      </And>
    </Include>
  </Menu>   <!-- End Multimedia -->
```

Notice that Category tag. The AudioVideo parts match up between the two files.

There is also an ~/usr/share/applications
It only has one item in it.

I'm guessing the one with the ~ is your own personal one, while the / one is systemwide.

This means that you don't need to edit the applications.menu, but rather you can add and remove .desktop items. The Categories= line of the .desktop files define where in the menu they should go. Though I also noticed that at the top of the applications.menu is the following block of code:
```
  <Name>Applications</Name>
  <Directory>Applications.directory</Directory>
```
This must be important as well. It's most likely the main Applications section. It's within <Menu> tags, and the other sections within it are in their own <Menu> tags, the <Menu> tags of the subsections nested within the Applications' main <Menu> tags.

The only mystery that remains is where on earth are the .directory files kept?

EDIT: Found it. Ran a locate .directory on it and found that they seem to be in two locations.

First one, for me, is ~/.local/share/desktop-directories
second one, is /usr/share/desktop-directories

I believe we now know everything we need to edit them manually. Anything I haven't covered can be learned and reasoned by opening these .desktop and .directory files in a text editor and by looking at the above mentioned configuration files in one as well.

---

### Post by islander_810 on 2007-02-09
I too had the same prob and this is what i did, tho mind you it's only a workaround and not a solution. Sorry purists...

Go to /usr/share/applications

There all(?) the applications installed are listed even though they may not be displayed. Anyway, find the one you want to display, in my case i'll use gvim as an eg.

edit the gvim.desktop file
" sudo vim gvim.desktop "

Near the end, is a line called:
NoDisplay=True

Just delete it and it'll be displayed

---

### Post by viper on 2007-02-09
> **kosmic said:**
> HI in edgy Alacarte should be in ->SYSTEM->PREFERENCES->A STRANGE NAME (it is not called alacarte, don't know why)

You can run alacarte in a terminal window like -> ***sudo alacarte*** and try to see if you can edit the menu then :)

In Edgy Alacarte is called Menu Layout

---

### Post by spimby on 2007-02-09
> **omghax said:**
> Yay, someone who understands my problem! Too bad he has the same problem... :(

I have the same problem with Alacarte. I can launch it (with or without sudo, gksudo, etc) I can highlight, and doubleclick on any menu item and even double click and see it's properties.  What I can't do, is check or uncheck any of the "Show" boxes.  Ughh..Driving me....mad...](*,)

---

### Post by omghax on 2007-02-10
Well, I got rid of the WINE stuff from showing... thank God. But I can't get rid of the TransGaming folder in the menu, I'll ask on their forum but... I would think that the Ubuntu Community could help me out because I thought it was a simple task.

Thanks, :D

---

### Post by Amaroq on 2007-03-20
You could probably manually do it from information that we have already posted in this topic, such as deleting the appropriate file or adding the NoDisplay=True to the end of it. I'd say that the second choice would be the better one, as it can be easily undone if you so desire.

I'd also guess that the ubuntu community can help you with this better than transgaming can, as our area of knowledge is ubuntu itself, which is what you are dealing with in this issue, whereas transgaming's knowledge centers around whatever specific software they produce.

---

### Post by srt4play on 2007-03-20
> **omghax said:**
> Gah, it's bugging me because I try not to post on the forums - just search. But I have given up and now I need help, :(

I'm running Dapper Drake 6.06 LTS (I think that's what it's called), and I've installed Cedega and Wine. I love them both, but they don't love me in the same way. They've both decided to install themselfs in my Applications Menu (top left), and I can't find out a way to get rid of them. I've even tried using the 'Alacarte Menu Editor' to get rid of them, seem's I don't have permission or something to remove them.

I read in another thread that they're XML files, but I don't even know where to start looking. :(


This isn't an urgent problem, just a big annoyance everytime I open up my menu.

-- Thanks, :)

[http://www.ubuntuforums.org/showthread.php?t=260588](http://www.ubuntuforums.org/showthread.php?t=260588)

---

### Post by sdil on 2007-03-20
It very easy, just left click in menu bar and choose edit menu. :lolflag:

---

### Post by deodatus on 2007-03-25
> **sdil said:**
> It very easy, just left click in menu bar and choose edit menu. :lolflag:

It doesn't work.  Alacarte is BROKEN!!!

---

