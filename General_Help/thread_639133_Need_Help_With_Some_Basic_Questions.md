---
title: "Need Help With Some Basic Questions"
date: 2007-12-12
forum: General Help
---

### Post by jlotempio on 2007-12-12
This is my first thread, so please, be nice. 

To begin, I'm not completely new to Ubuntu, but have seemed to get by for awhile without knowing some of the basics, things that I am embarrassed to admit that I don't know.  I am experienced in the following ways: 
I think I know more about installing/reinstalling Ubuntu than anyone would want to know (not really, but you get my drift)
I have no problem rearranging my desktop (wallpapers, themes, icons, fonts, etc.)
I've installed a number of things such as AWN.  
I'm comfortable with the command line, as well as editing any number of files whether is is my sources list, xorg.conf, etc. 
I have a good feel for the filesystem.
Not completely unfamiliar with installing programs from packages.
Set up my MX1000 to use all its 12 buttons.
I'm sure there is much more I'm failing to mention.  The point is, I've been through my fair share of How-To's, have run into any number of issues, and reinstalled countless times.  However, I just feel like there are some things that I am missing, things that I guess are not major, but would help me to further enjoy my Ubuntu experience.  

Some of the things I feel I am missing are as follows:
1.  Lingo - What is everything that I'm looking at?  
      a. Nautilus - as far as I understand it is like explorer for windows, but I don't understand how it also controls the desktop environment (whether to show icons or not, etc).
      b. Metacity - handles window borders?
      c. GTK - handles slidebars and other window components?
      d. Compiz - I know it is a compositor, but why are there different themes for it on say like gnome-look?  I though Metacity handled the window borders and such?  I thought compiz just handled all the fancy effects?
      e.  GDM - login screen?
2.  Also, where do I find the following
      a.  Icons for programs
      b.  Where are programs stored
      c.  Where would I find the icons for the taskbar that show up in the notification area for rythmbox.  There are two, I have found how to replace the one that shows up when rythmbox is playing, but not when it is stopped.  

These are just some of my questions, I'm sure there are so many more I can't think of at the moment.  But, if there are any other things you think that all Linux users should know, please feel free to share.  

I would appreciate all help.  I don't think these questions are too difficult, and I hope that there are some more experienced Ubuntu users that are willing to oblige.

---

### Post by skyjacker on 2007-12-12
1e - GDM is the Gnome Desktop Manager (a graphic user interface for Ubuntu.
2a - Try gnomelook [http://www.gnome-look.org/?PHPSESSID=eeec39ff820f519dc486f809d61a0d04](http://www.gnome-look.org/?PHPSESSID=eeec39ff820f519dc486f809d61a0d04), or kdelook [http://www.kde-look.org/](http://www.kde-look.org/) for icons and other "eye candy". By the way, welcome to the forum...

---

### Post by sowelie on 2007-12-12
I wouldn't call myself an expert, but I can help with a few of your questions.

1a - Nautilus as I understand it is like explorer, it is the file explorer, but the desktop is also controlled by nautilus.  I would imagine the logic is, nautilus already lays out icons in the file manager, why not do the same thing on the desktop.

1b - You got it.

1c - GTK renders all controls (widgets) for gnome, and is also available for use on other platforms.

1d - compiz does handle fancy effects and windows.  There are also a couple of window border managers that do a nice job with compiz.  I have had the best experience with Emerald.  The themes for Emerald are still listed under beryl on gnome-look.  The window borders rendered by Emerald are nice, and allow compiz to apply some of its effects to the window borders.

1e - Answered in above post.

2a - Gnome-look has icon themes but also has a lot of one-off icons.

2b - This is a bit more complicated.  It depends on how they are installed, but most are installed in /usr/bin/.

2c.  I am unsure on this one.

I hope this helps.  The biggest thing to remember, is that this operating system is modular.  There is almost always a choice involved.  A good example is the window border discussion.

---

### Post by p_quarles on 2007-12-12
Brief explanations between the lines:
> **jlotempio said:**
> Some of the things I feel I am missing are as follows:
1.  Lingo - What is everything that I'm looking at?
      a. Nautilus - as far as I understand it is like explorer for windows, but I don't understand how it also controls the desktop environment (whether to show icons or not, etc).
File manager, much like Windows Explorer but, as you noted, manages what parts of the filesystem are displayed on the desktop.
> b. Metacity - handles window borders?
Partly, but it's more generally a window manager. You can replace it with a number of alternatives.
> c. GTK - handles slidebars and other window components?
It's a toolkit for the GUI applications. The buttons, toolbars, sidebars, progress bars, etc., are all contained in the GTK libraries. Programmers can design applications to use those libraries, rather than designing an entirely new GUI interface for every application.
> d. Compiz - I know it is a compositor, but why are there different themes for it on say like gnome-look?  I though Metacity handled the window borders and such?  I thought compiz just handled all the fancy effects?
No, Compiz is an alternative window manager. When you're using it, you're no longer using Metacity. 
> e.  GDM - login screen?
It's the backend that manages the entire desktop interface. The other applications you mentioned all work "under" its authority.
> 2.  Also, where do I find the following
      a.  Icons for programs
In /usr/share/icons and /usr/share/pixmaps
> b.  Where are programs stored
Several places: /bin, /sbin, /usr/bin, /usr/sbin, and /usr/local/bin. The coreutils (base CLI apps) are in /bin. The vast majority of other apps are in /usr/bin.
> c.  Where would I find the icons for the taskbar that show up in the notification area for rythmbox.  There are two, I have found how to replace the one that shows up when rythmbox is playing, but not when it is stopped.  
In the icon folders I already mentioned.

Hope this helps.

---

### Post by jlotempio on 2007-12-13
First off, thanks so much for your help and your quick replies.  You are all certainly so kind for offering your support.  

Although most of my questions were answered, you may have raised some more.  

Just to note, I was wondering about where to find the icons for programs already located in my filesystem, not where to find them online for download.  The previous post answered this though, so thank you for that.  

However, why are applications in so many different places, as noted in the previous post?  Why is there not one central folder for all applications or programs to be kept?

Also, if I wanted to change my login screen, that would be under the GDM section of gnome-look for example, right?

And how would I go about installing themes downloaded for Compiz or Emerald?  Is it the same as just dragging it into the Appearance section under Preferences?  

Oh, and what are the widgets mentioned by sowelie for what GTK handles?

Thanks Again!

---

### Post by Lostincyberspace on 2007-12-13
Look on wikipedia for applications there is a lot of info there that should be fine for beginning users.

---

### Post by kpkeerthi on 2007-12-13
> 
However, why are applications in so many different places, as noted in the previous post? Why is there not one central folder for all applications or programs to be kept?

Read up on [The Linux Filesystem Hierarchy]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/foreward.html") 

> 
And how would I go about installing themes downloaded for Compiz or Emerald? Is it the same as just dragging it into the Appearance section under Preferences? 

No. You need to use Compiz Config Settings Manager. From terminal type ccsm. Or search and install from synaptic.

> 
Oh, and what are the widgets mentioned by sowelie for what GTK handles?

The buttons, toolbars, sidebars, progress bars, etc.,

---

### Post by jlotempio on 2007-12-13
Thanks again for your replies.

kpkeerthi, thanks for your post, it was helpful.  I have to say that I'm not looking forward to reading a book about the entire linux hierarchy, but sometimes that is what it takes and I want to learn.  Thanks for the link though.  

Are there any other ins and outs that all linux people should know?  Anything you guys wish you knew when you were a beginner that would have made your life a lot easier as a linux user?

Thanks

---

### Post by Lostincyberspace on 2007-12-13
> **jlotempio said:**
> 
Are there any other ins and outs that all linux people should know?  Anything you guys wish you knew when you were a beginner that would have made your life a lot easier as a linux user?

Don't screw up.

Good luck on that one though!

---

### Post by jlotempio on 2007-12-13
Don't screw up?  Oh, come on, the fix is just a reinstall away, right?  Luckily I learned about a separate /home partition early in the game.  

This reminds me of another thing....I know that the /home directory is where your personal documents are held, but what else.  Are your personal setting located there as well?

The reason I ask is if I do a reinstall with my /home folder on a separate partition (so I don't lose anything from it), what will be missing from my system after the reinstall (aside from programs I had installed previously)?

What other directories are useful to backup?  Where are all your personal settings and configurations kept?  So, if I've modded files such as my xorg.conf or sources, I should just make a copy of these and place them in my /home?

---

### Post by philinux on 2007-12-13
Go to home and press ctrl H and it will show your hidden sertings folders all preceeded with .

as in .mozilla

---

### Post by knutschr on 2007-12-13
> Are there any other ins and outs that all linux people should know?

You probably know, but I used Linux for a couple of weeks untill I learned I can use TAB key in terminal to fullfill writing say a long file name.

A comment to other:
Use whereis [program] to see where it is installed.
And, if you some day are in doubt, you can write whoami :)

---

### Post by Lostincyberspace on 2007-12-13
> **knutschr said:**
> You probably know, but I used Linux for a couple of weeks untill I learned I can use TAB key in terminal to fullfill writing say a long file name.

A comment to other:
Use whereis [program] to see where it is installed.
And, if you some day are in doubt, you can write whoami :)

```
lee@lee-desktop:~$ whoami
lee
 
```It really is use full if you are working on servers.

---

### Post by jlotempio on 2007-12-13
I am aware of how to show hidden files and folders in nautilus, but I don't know what all of those folders contain.  Are they all of the preferences and settings for my system, or are those located somewhere else in my filesystem.  

Also, what exactly does the whoami program do?  And what does TAB do in terminal?

---

### Post by p_quarles on 2007-12-13
The hidden files in your home folder contain your user's settings for applications. E.g., your browser's bookmarks file is in there.

whoami displays your login name -- not normally necessary for a desktop user.

The tab completion function is awesome. Say you have a file in your working directory called foo.bar, and you want to copy it somewhere. You can start by typing:
```
cp fo
```
Hit the tab key, and it will find the closest match(es) for what you have typed so far. It's a great timesaver, especially for long path/filenames.

---

### Post by jlotempio on 2007-12-13
p_quarles, thanks for the clarification.  What you mentioned was exactly what I was thinking, but I was looking for clarification, which is what you offered.  Thank you for that.

With the TAB feature in terminal, will it will in just the remainder of the filename for files that are in the current directory, or will it search the whole file system.  For example, what would be the quickest way to make a copy of your xorg.conf file?  Would typing in the following (while being in the / directory) :

cp xor 

and then hitting the TAB key fill in the corresponding /etc/X11/xorg.conf that I was trying to copy?

How would you go about completing this task?  Or, would you just navigate to the /etc/X11 directory and make the copy?

Also, what other sort of things do you guys find useful as far as shortcuts ( scripts, conky.rc's, aliases in terminal, etc.). 

Thanks for your input.  This is all helping me.  I am not a fulltime linux user, as I triple boot with XP and Vista (which I didn't pay for, don't worry) and I run OSX on my laptop.  However, I love Ubuntu and use it about 80-90% of the time, but am trying to get to the point that I can scrap my Windows partitions.  I just feel like linux is so powerful, and that I am the one holding me back from converting completely.  I wish I knew more about linux and how to really use it, which is why I'm here asking these questions.

---

### Post by Lostincyberspace on 2007-12-13
I posted the results of whoami in my last post. Tab is used to complete something program, file, or other. so instead of typing cd /home/user/Desktop all out you can type cd /h(tab)/u(tab)/De(tab). (tab)= press tab key

---

### Post by Lostincyberspace on 2007-12-13
You still have to specify the directory to copy it from but you can use tab completion to get there faster.

---

### Post by jlotempio on 2007-12-13
Awesome, thanks for the clarification.

---

### Post by knutschr on 2007-12-15
About file managers:
I agree that Dolphin is choosed for default manager in Ubuntu.
That one is good for people beeing newbies (any OS)

You won't use a PC for long, however, before you should use Konquerer.
I haven't seen a such thing anywhere!

It starts in root mode!!

---

