---
title: "theme problem i think"
date: 2008-02-05
forum: General Help
---

### Post by chee on 2008-02-05
here is my problem.  i booted up ubuntu and an error came up which does happen every once in a while, that said there was some type of error in the starting my theme, i think.  unfortunately i didn't pay enough attention since i usually just reboot after i see this.  so i clicked OK and my desktop came up but with no toolbars at the top or bottom.  so i rebooted but it still does the same thing.  my desktop all works and i actually created some lauch icons for firefow and amsn to get by until i figure it out.  i went into a failsafe terminal session and tried removing and installing metacity, compiz and beryl but nothing did the trick.   any help would be greatly appreciated as i am still very new and a little lost as to where to even start.

---

### Post by cdaringe on 2008-02-05
that sounds pretty obnoxious.

try making a launcher to "gnome-terminal"

then run

```
gnome-appearance-properties %F
```

disable all visual effects and/or change your theme and see what happens!
keep us updated

---

### Post by chee on 2008-02-05
thanks for the help,  but unfortunately there were no visual effects on. so there was nothing to turn off.  i even tried changing my theme (not that that should do anything but who knows) to no avail.  the other thing i have noticed ( and this may not mean anything) is that whenever i boot up it starts out with a window of my files open.  like my /home/chee file is always open.  like i said that probably has nothing to do with it but i just noticed it.   any guesses are more then welcome. :)

---

### Post by cdaringe on 2008-02-05
there are probably faster ways to do these things...but i dont know them. so ill keep throwing you my 10 cents until either a) somebody else pitches in or b) we figure it out.

in a terminal
try```
metacity --replace
```
then we might get some terminal output if any errors happen when loading the WM.  that could help.  if that doesnt yield anything useful...
try installing xfce and see if THAT boots up fine
```
sudo synaptic
```then. install xubunutu-desktop or simply
```
sudo apt-get install xubuntu-desktop
```
log out using
```
gnome-session-save --kill
```
choose xfce in your sessions. use your normal login info and see if THAT gets you anywhere.
i realize that this may be a round about way of solving your problem (or finding answers for that matter) but at least its somethin! good luck

---

### Post by chee on 2008-02-05
"Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/wes/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/wes/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/wes/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored."

this is what is said when i put metacity --replace

---

### Post by chee on 2008-02-05
the xubuntu solution worked fine and everything on there works well actually.  so my next question is,  is there a way to fix the gnome settings (as i had them all perfect) or is there a way to just get rid of gnome all together and modify this xubuntu to get similar.  or do i need to bother getting rid of gnome even.  

BTW,  i do really appreciate the help and this has gotten me back on my feet so to speak.  so thanks again for the help.

---

### Post by cdaringe on 2008-02-05
sure! (glad were making some progress. i cant tell you how many times people on THIS forum have saved my butt)

Again, disclaimer, i dont know exactly how to make this all happen, but heres what id try first.
open a synaptic, in the left column browse to status. click 'installed.'  browse down to the gs.  id probably mark a few of the critical gnome features for** reinstallation**. (perhaps gnome-themes (which seems to be a source of your problems), gtk2-engine, and ubuntu-desktop).

if that doesnt work, open up your home folder, hold ctrl and hit h to show all of your hidden folders.  rename .gnome to .gnomebackup. erase your .gnome folder, then try logging in again.  this reset your profile on our linux machines at school.  if that doesnt do it, you best rename your .gnomebackup to .gnome.

see how those work out

---

### Post by chee on 2008-02-06
ok i am a little lost on the last part of that one.  so i rename .gnome to be .gnomebackup.  then you said erase the .gnome folder.  but i just renamed it .gnomebackup so there is no .gnome.  like i said i am a little lost here :).  plus i have .gnome and .gnome 2 .  not sure which one to rename.

---

### Post by chee on 2008-02-06
and now i have another problem.  i tried sudo apt-get install gnome.  bad idea.  now it boots up with a blank background and an open terminal but no button or text and i can't do anything.  i think i made a mistake :(.  luckily i can still use xfce.  but i definitely made it worse.

---

### Post by cdaringe on 2008-02-06
sorry about that! yea, i wasn't thinking entirely straight.  you dont need to erase it if you just renamed it.  the end goal was that when you booted up, perhaps a new .gnome would be generated.  IF IT DIDNT, you could rename your .gnomebackup to .gnome. if that didnt work, definitely rename your folder back to .gnome
so nothin did the trick eh?

do this
```
gksu users-admin
```
add a new user.
then, go to the login menu, and log into gnome using this new user info.  this ought narrow it down on whether its a setting in your user acct or in the gnome config files

---

### Post by chee on 2008-02-06
so get this.   i log in to xfce and it has done the same thing.  no top panel and no bottom panel.  i tried creating a new login name and it worked.  got none of my files now but we can work on that atleast that narrows it down.  seems weird to me that it would happen in xfce too,  and so quickly.

so any suggestions on where to go from here since we now know it has to do with the settings in my user account?  oh and i do really appreciate any help as it is saving me from using my windows app ( which is only an 8gig corporate edition with nothing on it,  plus i can't even remember how to use it :)  )

---

### Post by chee on 2008-02-06
so thought i posted another reply but i must not have.  i made another user profile and it works fine.  not sure if i can get all my files from the old profile to the new one.  but now we know that it has to do with my profile configurations.  the strange thing is that now it does the same thing in xfce.  ????? not sure where to go from here, but i appreciate the help so far.

also,  just a side note that my mom had a virus that did the same thing on here computer,  but she runs windows so i know it couldn't be linked but she said it was identical in nature.

---

### Post by cdaringe on 2008-02-06
if you want access to your files while logged in, there a few things you can do

1st, you can tell your new account that its ok to use your old accounts home folder

```
sudo chown YOURNEWUSERNAME:YOURNEWUSERNAME /home/YOUROLDUSERNAME
```
(chown user:group objecttobechanged is the format)

so then you can just browse to /home/YOUROLDUSERNAME and access your files

2nd you can 
```
sudo nautilus
```
this will open nautilus in root giving you access to everything.  you can browse to your home/OLDUSERNAME and do stuff there.  this method is usually discouraged because nautilus calls on other apps/routines/etc/i-dont-know that reduce safety. i do it all the time when i need to...its faster. but discouraged.

if youd like, you can transfer most of your programs settings over to your new user acct.  not everything will merge perfectly, but for the most part, it works.  if you look in your old acct folder, do a ctrl + h, the other .XXXX folders are many of your program config folders.  you can drag those into your new account home, and some will use those settings. certain things, such as the .gnome folder, you dont want to do.  do this w/ caution. you dont really risk breaking much stuff, but sometimes everything isnt always compatible.  im not a linux pro. im still kinda of newbalicious (2 years using?)

when you reinstalled stuff, which packages did you reinstall. im suprised that after reinstalling gnome and ubuntu-desktop not everything was back to shape.  id say keep your .gnome saved as .gnomebackup, change your theme back to 'human,' and reinstall those two again, including the gtk-engine one. (perhaps try reinstalling some libgtk libraries, libmetacity stuff... im runnin on blanks here. everything that could be related!)

if that does't work, see if theres a new .gnome folder in your directory.  well see if the reinstall actually generated one

this guy also seems to have a solution.  again, use caution.  anything with **rm** means you will be REMOVING those directories. i usually like to rename things as xxxx.backup or whatnot, that way if i realllly screw it up, i can just revert back to the original.
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by chee on 2008-02-07
we have success.  i used the link provided and it worked just fine.  i haven't checked all my files but the ones i really need are all there.  so far so good.  plus now i can search for some cool new theme. ha!  the plus side is that now i have another user profile i can use incase my primary one messes up,  and i can still get to all the files in the first user.  good backup plan i think.  thatnks  again for all the help.  i would be lost without it,  and computerless.  plus i feel like i have actually learned a bit through this while ordeal.

---

### Post by cdaringe on 2008-02-07
very cool man. glad we could figure it out!

---

