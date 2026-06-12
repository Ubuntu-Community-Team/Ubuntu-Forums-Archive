---
title: "installing apps does not always add menu items"
date: 2004-11-02
forum: General Help
---

### Post by tariq on 2004-11-02
i'm anew user ...  i unmasked the "universe" repositories to install scribus and lyx (amongst other things).

scribus did appear in the new menu ... but lyx didn't.  some other itens such as games didn't.

is there a good way to ensure that installed apps from ubuntu packages do appear for **all** users? myself i don't mind launching them from the command line but the intended users will not know this and are not command line users. 

i did explore /etc/menu and /lib/menus (memory might not be correct here) ... but it didn't work.

i've previously given them mandrake - becuase even if the menus were cluttered and the desktop not so clean - at least everying was available to them from the menu!

---

### Post by Joeb on 2004-11-02
[QUOTE=tariq]i'm anew user ...  i unmasked the "universe" repositories to install scribus and lyx (amongst other things).

scribus did appear in the new menu ... but lyx didn't.  some other itens such as games didn't.

is there a good way to ensure that installed apps from ubuntu packages do appear for **all** users? myself i don't mind launching them from the command line but the intended users will not know this and are not command line users. 

i did explore /etc/menu and /lib/menus (memory might not be correct here) ... but it didn't work.

i've previously given them mandrake - becuase even if the menus were cluttered and the desktop not so clean - at least everying was available to them from the menu![/QUOTE]


Unfortunately, whether an app creates the menu entry is up to the packager of the application.  I don't believe there is a way to force it to occur.  I believe the apps that come from the Ubuntu repositories do create the menu entries, but Universe apps aren't actually supported and maintained by Ubuntu.  

There should be a header or information listed about the person who packaged the app in the description.  You could send an email to that person to request they add the menu.

---

### Post by mercurus on 2004-11-02
[QUOTE=tariq]scribus did appear in the new menu ... but lyx didn't.  some other itens such as games didn't.

is there a good way to ensure that installed apps from ubuntu packages do appear for **all** users? myself i don't mind launching them from the command line but the intended users will not know this and are not command line users.[/QUOTE]

The debian-style menu structure does seem to be there, but I can't quite work out how it fits together. My /usr/lib/menu is full of links, but I lack an update-menu script to meld them together. I do have a /usr/bin/desktop-menu-tool but I don't find its man page particularly enlightening.

Would it be plausible to setup a standard desktop on one machine, and simply copy the contents of ~/.gnome2 into each users' home directory (or host them centrally) so as to give everyone the same menu items and icons ?

I'm sure there is a better, more elegant solution ... but it escapes me :(

Cheers
mercurus

---

### Post by tariq on 2004-11-02
[QUOTE=mercurus]The debian-style menu structure does seem to be there, but I can't quite work out how it fits together. My /usr/lib/menu is full of links, but I lack an update-menu script to meld them together. I do have a /usr/bin/desktop-menu-tool but I don't find its man page particularly enlightening.

Would it be plausible to setup a standard desktop on one machine, and simply copy the contents of ~/.gnome2 into each users' home directory (or host them centrally) so as to give everyone the same menu items and icons ?

I'm sure there is a better, more elegant solution ... but it escapes me :(

Cheers
mercurus[/QUOTE]

yes - the /usr/lib/menu is where the apps are supposed to put menu entries but there is a place in /etc which is where you the administrator place your overrides. i coudn't get it to work.

the update-menu program is not installed by default - it comes with the menu package which you must install using the normal tools (apt-get, synaptic). i've not come across the usr/bin/desktop-menu-tool but it may just be user-specific .. not global.

i'll have another explore later to see if i can get the menus to work.

---

### Post by mercurus on 2004-11-02
[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions)

If you scroll down to the "How do I customize the Applications menu?" section, the following gem appears:

"To change the Applications menu for all users, go to applications-all-users:/// in Nautilus. You will need root privileges to change this."

So you can setup any recalcitrant packages universally as root, and they should be available for all users.

Cheers
mercurus

---

### Post by tariq on 2004-11-02
thanks to the last poster - that was veyr useful advice (i'm not a gnome / nautilus person myself .. i use xfec and the command line!)

just to check: 
 * i will install packages one by one
 * for each installed package i will check that it appears in the menu
 * if it does not i shall do as the above poster suggested

however - do i need to log out and back in to be sure the installed app did not add a menu item. i say this as there may be a "refresh menus" which some install scripts may/may not call.

am i right? is therea refresh-menus command i can do myself without having to logout and back in again between application installs.

forgibe my lack of gnome knowledge!

thanks

---

### Post by jwb on 2004-11-02
[QUOTE=tariq]

however - do i need to log out and back in to be sure the installed app did not add a menu item. i say this as there may be a "refresh menus" which some install scripts may/may not call.

am i right? is therea refresh-menus command i can do myself without having to logout and back in again between application installs.

[/QUOTE]

Good question..... I'd like to know that myself. Done that once or twice..... added a menu item manually, log in later, and there's two of them. I like Gnome A LOT, but that's one of the irritating behaviours that I can't stand.

---

### Post by Joeb on 2004-11-02
You know, that this has been an interesting discussion, but it still misses the point that application packagers should be adding the menu support in their packages.  If they did that, then there wouldn't be a need to go back and manually do all of this.  Some of them do, but unfortunately, many do not (and won't until people harp on it).

---

### Post by az on 2004-11-02
Debian has probably the most advanced menu support in linux distributions.

Ubuntu does not use it.

Ubuntu uses gnome menus.

If you install a kde desktop on debian, you get a kde menu system with a debian entry which is redundant because it lists all of the installed packages, not just the kde ones.  The same goes for gnome.  Ubuntu does not seem to use the debian menus.

All debian packages add entries to the debian menu.

I guess it makes for really neat menus, but loses some compatibility with the packages from Universe....

---

### Post by tariq on 2004-11-03
this is considered a "*worst bug*" according to the "2 weeks with ununtu" article on osnews:

  [http://www.osnews.com/story.php?news_id=8754&page=2](http://www.osnews.com/story.php?news_id=8754&page=2)

---

### Post by ~zoey~ on 2004-11-09
I have followed all of the various links and suggestions in this thread with no luck whatsoever.

What I am trying to do is add a link for the program grisbi somewhere [anywhere!] in the menu.

Could someone please write the directions out for me in newbie speak?  I installed grisbi using synaptic and it is there, just doesn't show up anywhere.

Thanks, zoey   :???:

---

### Post by WW on 2004-11-09
Click on Applications

Slide your cursor down to "Office", and slide it over into the submenu.

RIGHT-click in the submenu (on anything)

Slide your cursor down to "Entire menu", and then click on "Add new item to this menu"

A "Create Launcher" window will pop up.

Enter the data:

```
Name:          Grisbi
Generic name:
Commont:
Command:       grisbi
```

Click on OK.

---

### Post by ~zoey~ on 2004-11-09
Thank you, thank you, thank you!  I decided that I wanted to run the 'real ubuntu' with gnome and not kde and now I can do so happily.  I appreciate all the help from this great forum.

zoey :o  =D>  :o

---

### Post by ispmike on 2004-11-10
[QUOTE=WW]Click on Applications

Slide your cursor down to "Office", and slide it over into the submenu.

RIGHT-click in the submenu (on anything)

Slide your cursor down to "Entire menu", and then click on "Add new item to this menu"

A "Create Launcher" window will pop up.

Enter the data:

```
Name:          Grisbi
Generic name:
Commont:
Command:       grisbi
```

Click on OK.[/QUOTE]


Wow, I didn't know it was this easy to edit the Gnome menu. Thanks...

---

### Post by jmjohn on 2008-07-06
> Click on Applications

Slide your cursor down to "Office", and slide it over into the submenu.

RIGHT-click in the submenu (on anything)

Slide your cursor down to "Entire menu", and then click on **"Add new item to this menu"**

Hmm.  For some reason, in my Hardy install, I don't have this option, which is why I am reading this post.

Further, a year and a half ago, when I first tried Ubuntu, I didn't install it partially out of frustration that it didn't automatically add menu items.  Seriously, this is big for newbies.

---

### Post by jmjohn on 2008-07-06
Okay.  I figured it out.  

Instead of the above directions:

Right click on the Ubuntu symbol that launches the menu.  Click "Edit Menus".

Now, add or remove items from the menu structure.

---

