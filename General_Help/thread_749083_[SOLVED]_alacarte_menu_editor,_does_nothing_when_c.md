---
title: "[SOLVED] alacarte menu editor, does nothing when clicked"
date: 2008-04-08
forum: General Help
---

### Post by Greenducky on 2008-04-08
Hey guys when i right click on the ubuntu start button and click edit menu nothing happens.
also when i hit alt + f2 and then type alacarte & nothing happens.
also when i go to menu preferences and then click mainmenu nothing happens.

by the way if you are reading this and are unaware of what i am talking about. all three things are trying to launch the same
program called alacarte. alacarte is a menu editor to edit the programs that you see and dont see in the menu

This is what it lookes like when i try it in a terminal.
__________________________________________________ __________________________________________________ ________________________-

mint@mint-desktop:~$ alacarte &
[1] 31504
mint@mint-desktop:~$ Traceback (most recent call last):
File "/usr/bin/alacarte", line 36, in <module>
main()
File "/usr/bin/alacarte", line 32, in main
app = MainWindow(datadir, version, sys.argv)
File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
self.editor = MenuEditor()
File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
self.__loadMenus()
File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
self.applications.dom = xml.dom.minidom.parse(self.applications.path)
File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1915, in parse
return expatbuilder.parse(file)
File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 926, in parse
result = builder.parseFile(fp)
File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 207, in parseFile
parser.Parse(buffer, 0)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 13, column 52

__________________________________________________ __________________________________________________ ________________


Please help me.
I tried uninstalling it from synaptic and then reinstalling it and then reloading plugins on the menu. and nothing. i've restarted x and rebooted.
even when i try to change the session to safe gnome mode. and log inn it still dont work.
it worked fine earlier today, only thing i did between now and then is install adobe cs2 in wine doors.
I hope someone can make some sense of this.
__________________

---

### Post by erginemr on 2008-04-08
Following this link that deals with the same problem:
[http://ubuntuforums.org/showthread.php?t=411139](http://ubuntuforums.org/showthread.php?t=411139)

it appears your menu file is somehow broken. I remember to have a similar problem in the Gnome menu, which had passed away when I reset the menu cache folder:
```
mv ~/.config/menus ~/.config/menus.bak
```
Then, all menus should reset themselves upon a session restart. You can delete the backup folder with:
```
rm -r ~/.config/menus.bak
```
when you make sure that everything works as expected, or you may consider to restore it with 
```
rm -r ~/.config/menus
mv ~/.config/menus.bak ~/.config/menus

```
if this doesn't solve your alacarte related problem. 

You can do the same operations graphically under Nautilus (Gnome File Manager) as well.

---

### Post by Greenducky on 2008-04-08
erginemr  thank you so friggin much. 

I am a linux Mint user, but i know that mint uses gutsy repos, and pretty much
everything else still looks like ubuntu. I was in the mint forums and some users told me to post on this forum and see what i got. 

well i did what you said and poof, everything is back to normal. i was so close to reinstalling. and then you threw me a lifesaver. 

Thank you

---

### Post by erginemr on 2008-04-08
This is great! :KS I was having a pretty bad work day, with a truck load of jobs to attend to... :(

And you made my day, buddy! So, take care and thank you in return. ):P

P.S. 
1) You can always use Ubuntu Forums to solve your problems, since, as you also said, Ubuntu and Mint are like close relatives.
2) As a final reminder: **To close a thread **-> Select **"mark this thread as solved"** from the thread tools menu. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

