---
title: "K3b question"
date: 2005-05-16
forum: General Help
---

### Post by YaAqoB on 2005-05-16
Hello all.
Some how I managed to undock K3b's project view and I can't for the life of me figure out how to redock it. ](*,) 
I have to have it open as a separate window now. 
Anybody have any ideas?

---

### Post by jeremy on 2005-05-17
[QUOTE=YaAqoB]Hello all.
Some how I managed to undock K3b's project view and I can't for the life of me figure out how to redock it. ](*,) 
I have to have it open as a separate window now. 
Anybody have any ideas?[/QUOTE]
 just under the 'X' (close window) in the project view window is a little arrow, click it and the window will dock (click it again to un-dock).

---

### Post by YaAqoB on 2005-05-17
Thanks for that.
There is no little arrow there. I know which one you mean though as the file viewer etc has it and will allow docking and undocking. The Project view how ever don't have one. :(
Another Issue I'm having is that if i'm burning a DVD it will only burn at 2x and a CD at 25x.
Using XP I burn at 8x for a DVD and 40x for a CD.
Is the fact that they are reading from a NTFS drive slow down the buring process?
Any other ideas for the Project view problem?

---

### Post by YaAqoB on 2005-05-17
Any Ideas anyone?
Cheers

---

### Post by apollyonis on 2005-05-17
If there's any space in the margin underneath the X, minimize, etc., then you should be able to double click it to redock and undock, even without the arrow. My margin shows up as gray dots.

---

### Post by YaAqoB on 2005-05-17
Thanks for your help.
I still have a problem though.
I have this grey dotted line you talk about and nothing happens when I double click it.
If I double click it in the file browser view it works fine. Just not in the project view.
Is there a config file I can edit to force it to be docked. Or is there some thing I can do to return it to its default state?

---

### Post by jeremy on 2005-05-18
heres a pic of mine, at least you should see where the arrow should be...

---

### Post by apollyonis on 2005-05-18
Ok, if that didn't work, yes there is a config file you can alter.
Do this in terminal: 

sudo gedit ~/.kde/share/config/k3brc

You'll have this line : 

project_view:type=NULL_DOCK

Change it to this : 

project_view:type=DOCK

If that doesn't fix it, I don't know what will.  :razz:

---

### Post by YaAqoB on 2005-05-18
Wicked, Thanks for your help. I'll try it when I get back home to Ubuntu.
I appreciate your help.

---

### Post by YaAqoB on 2005-05-18
Ok I have changed that null_dock to dock and that gave me back my arrow to redock it.
But the arrow does not work so I'm assuming something else is wrong in there. I have paisted the contents of that file. 
Can you see what else i have to change??


[Audio project settings]
default pregap=150

[Cddb]
cddb server=Http freedb.org:80
cgi path=~cddb/cddb.cgi
local cddb dirs=~/.cddb/
proxy port=8080
proxy server=
proxy settings type=kde
save cddb entries locally=true
use local cddb query=true
use manual cgi path=false
use proxy server=false
use remote cddb=false

[DVD image writing]
last written image=$HOME/Desktop/MoreStuff/temp/TELEPHONE_D1A.ISO

[Data project settings]
Add hidden files=true
Add system files=false

[Devices]
TSSTcorp CD/DVDW TS-H552U=11025,7000,auto,auto
device_search_path=/dev/hdc

[Docking Config]
Main:Geometry=0,0,961,782
Main:dock=project_view
Main:view=directory_tree,contents_view
Main:visible=true
NameList=project_view,directory_tree,contents_view,audio_player,directory_tree\\,contents_view
Version=0.0.5
audio_player:dockBackTo=
audio_player:dockBackToPos=0
audio_player:geometry=88,157,640,409
audio_player:stayButton=false
audio_player:tabCaption=Audioplayer
audio_player:tabToolTip=
audio_player:type=NULL_DOCK
audio_player:visible=false
contents_view:dockBackTo=directory_tree
contents_view:dockBackToPos=4
contents_view:geometry=131,80,1119,864
contents_view:stayButton=false
contents_view:tabCaption=Contents View
contents_view:tabToolTip=
contents_view:type=DOCK
contents_view:visible=false
directory_tree,contents_view,project_view:first_name=directory_tree,contents_view
directory_tree,contents_view,project_view:last_name=project_view
directory_tree,contents_view,project_view:orientation=0
directory_tree,contents_view,project_view:parent=yes
directory_tree,contents_view,project_view:sepPos=3981
directory_tree,contents_view,project_view:stayButton=false
directory_tree,contents_view,project_view:type=GROUP
directory_tree,contents_view:first_name=directory_tree
directory_tree,contents_view:last_name=contents_view
directory_tree,contents_view:orientation=1
directory_tree,contents_view:parent=yes
directory_tree,contents_view:sepPos=2643
directory_tree,contents_view:stayButton=false
directory_tree,contents_view:type=GROUP
directory_tree:stayButton=false
directory_tree:tabCaption=Directory Tree
directory_tree:tabToolTip=
directory_tree:type=DOCK
project_view:dockBackTo=
project_view:dockBackToPos=8
project_view:geometry=20,534,1095,454
project_view:stayButton=false
project_view:tabCaption=Project View
project_view:tabToolTip=
project_view:type=DOCK
project_view:visible=false

[External Programs]
cdrdao default=/usr/bin/cdrdao
cdrdao user parameters=
cdrecord default=/usr/bin/cdrecord.mmap
cdrecord user parameters=
dvd+rw-format default=/usr/bin/dvd+rw-format
dvd+rw-format user parameters=
eMovix user parameters=
growisofs default=/usr/bin/growisofs
growisofs user parameters=
mkisofs default=/usr/bin/mkisofs
mkisofs user parameters=
normalize user parameters=
readcd default=/usr/bin/readcd
readcd user parameters=
search path=/usr/bin/,/usr/local/bin/,/usr/sbin/,/usr/local/sbin/,/opt/schily/bin/,/sbin
sox default=/usr/bin/sox
sox user parameters=
tccat user parameters=
tcdecode user parameters=
tcextract user parameters=
tcprobe user parameters=
tcscan user parameters=
transcode user parameters=
vcdxbuild user parameters=
vcdxminfo user parameters=
vcdxrip user parameters=

[General Options]
Allow overburning=false
Cdrdao buffer=32
Cdrecord buffer=4
Manual buffer size=false
Manual writing app selection=false
No cd eject=false
Show Document Header=true
Show progress in system tray=true
Show splash=true
Temp Dir=/tmp/kde-james
auto rewritable erasing=false
check system config=true
config version=0.11.23
current theme=crystal
current_writer=/dev/hdc
hide main window while writing=false

[KFileDialog Settings]
Recent Files=$HOME/Desktop/MoreStuff/Torrent Download/XP Pro 64/xp64.corp-xiso.cue,$HOME/Desktop/MoreStuff/temp/FELLOWSHIP.ISO,$HOME/Desktop/MoreStuff/temp/TELEPHONE_D1A.ISO

[TipOfDay]
RunOnStart=false
TipLastShown=2005,5,14,8,35,21

[Video project settings]
Play each Sequence/Segment=1
Time to wait after each Sequence/Segment=2
Use Playback Control=false
Use numeric keys to navigate chapters=false

[Welcome Widget]
welcome_actions=file_new_audio,file_new_data,file_new_dvd,tools_copy_cd,tools_write_dvd_iso,tools_write_cd_image,tools_copy_dvd

[file view]
Separate Directories=false
Show Preview=false
Show hidden files=false
Sort by=Name
Sort case insensitively=true
Sort directories first=true
Sort reversed=false
View Style=Simple
last url=/

[image writing]
last written image=$HOME/Desktop/MoreStuff/Torrent Download/XP Pro 64/xp64.corp-xiso.cue

[main_window_settings Toolbar mainToolBar]
Index=0

[main_window_settings Toolbar projectToolBar]
IconText=IconOnly
Index=1

[main_window_settings Toolbar quickDirSelector]
IconText=IconOnly
Index=2

[main_window_settings Toolbar toolsToolBar]
IconText=IconOnly
Index=1

---

### Post by apollyonis on 2005-05-18
The main thing I see that could be causing it is that project view isn't part of the main. So...change this line : 

```
Main:view=directory_tree,contents_view
```

To read this : 

```
Main:view=directory_tree,contents_view,project_view
```

See if that works. I know that if I delete project_view from that line, it does some freakish stuff, but not what you stated so I'm not sure if that's it.
Also, I doubt the orientation would screw it up, but feel free to change 

```
directory_tree,contents_view,project_view:orientation=0
```

to 

```
directory_tree,contents_view,project_view:orientation=1
```

Edit: Lol. I don't know what it's breaking the line right in the middle of the word view and orientation.  :?

---

### Post by accmariano on 2005-05-18
Hi, 

I had have same problem. The only way I fixed it was loging in with another user and then copy all default config files of k3b from the home folder of that user to my user.

Hope it help you

Regards
Mariano

---

### Post by YaAqoB on 2005-05-19
How do i copy the files from a new user across? 
What dirs or files do I copy and from where?

---

### Post by YaAqoB on 2005-05-19
Don't worry.
Thanks for all your help.
I got pissed off and deleted that config file and when it started it thought it was the first tiem and every thign was default.
I can even dock and undock :)
Buggered if I know what went wrong though.
Thanks again.

---

### Post by hantms on 2005-06-04
Just wanted to add that I had the very same problem.  Very weird indeed. And indeed just renaming that config file as something else fixes the problem. (Make sure K3B isn't running when you do that or it'll rewrite the wrong config file.

---

