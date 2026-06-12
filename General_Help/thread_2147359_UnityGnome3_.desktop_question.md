---
title: "Unity/Gnome3 .desktop question"
date: 2013-05-21
forum: General Help
---

### Post by xeddog on 2013-05-21
I have two machines that I would like some info on how to configure .desktop files.  One machine is a Ubuntu 13.04 (Unity) guest machine on a host computer running Ubuntu 12.04 with VirtualBox, and the other is Ubuntu-GNOME (Gnome shell and NO Unity) on a separate real machine.  If it matters, all machines are 64-bit.  

On both machines, I have managed to create a .desktop file for a php program I want to run.  In the .desktop file I have the php command line specified on the exec= line, and Terminal=true specified.  It works, but I have to manually resize the terminal window every time I launch it.  So I would like to pass some parameters to the underlying terminal command as well.  Specifically in my case, I would like to pass --geometry parameters to the terminal.  Is there any relatively easy way to do this?  From my searches so far, I fear not, and if that is the case it is just one more reason why I don't care for Unity or Gnome shell.  If there is a way to do it, there may yet be hope.  


Thanks,

X


P.S.  I have also used gnome-terminal on the exec line and then specified Terminal=false, and it works that way.  It just seems like if you are going to specify "Terminal=true" then there should be a way to pass paramters to the terminal.

---

### Post by cipherboy_loc on 2013-05-21
If it works with Terminal=false, why not use that? Otherwise, you could modify the command to do something like: `resize -s **<lines> <columns>** ; **<your command>**`, (specifying the desired height and width as numbers), which in theory should work to resize the window. Also, you could specify it in a launching shell script (.sh) which would simply run that command and then your program.


Thanks,
Cipherboy LOC

---

### Post by xeddog on 2013-05-21
Cipherboy- I am using it with Terminal=false and it is working fine.  I modified the .desktop file with the Exec= parameter like so: 

Exec=gnome-terminal --geometry=140x45 --command="php /var/www...."

I could even add placement coordinates and a title, etc.  But my reason for asking the question was because it just seemed that since you CAN code Terminal=true then you should be able to send those parameters to that terminal session as well.  In this case maybe something like "Terminal=true --geometry=140x45 or some such.  I know that not everyone uses gnome-terminal, but as far as I know all terminal programs accept several parameters.  It just seemed to me that you should be able to put what you really want executed on the Exec= line, and terminal parameters on the terminal line or at least somewhere independent from the Exec= line.



X

btw,  I just tried the Exec= line starting with the terminal parameters like "Exec=--geometry=140x45 ...." and coding Terminal=true, but it wouldn't work at all.  Unity couldn't even find the .desktop file even though it passed the desktop-file-validate and desktop-file-install.

---

### Post by cipherboy_loc on 2013-05-21
I think, though, the problem with adding such options is that they are highly terminal specific. Off the top of my head I cannot give specific examples, but even for geometry I think they differ, hence, the program launching the desktop file would need to have knowledge of specific terminal options for that to work properly. Considering that the majority of .desktop files are likely for graphical applications not requiring the terminal, terminal options are thus relatively unused. However, if support for different terminal applications is needed, again, I would point to a "launching" shell script which would start by detecting the environment (GNOME, KDE, XFCE, or other), trying to get the default (as seen [here]("https://bbs.archlinux.org/viewtopic.php?id=112848")), or as fall back, checking which terminal emulators are installed on the system and choosing the one with the most options. Then, depending on the terminal emulator, you can set geometry via command line options and then launch your program within that terminal. 


Just an idea,
Cipherboy

---

### Post by xeddog on 2013-05-24
I can certainly see what you are talking about.  It would be a big problem if you were the type that switched de's now and again.  But it seems to me that "in general" most people will have only one environment, they will know which environment that is, and will then have a pretty good idea which terminal program they are using.  Then it is a simple matter of running the programs --help to see the options, or use the man page.  Even if you do specify the wrong options the only thing that will happen (most likely) is that it won't run.  And if you are saavy enough to run multiple de's then you are most likely also saavy enough to have a .desktop file for each environment.  Then too, if you are saavy enough to create a .desktop file for either Unity or GNOME3 in the first place, you will also have a pretty good idea which environment you are using and therefore which terminal program is default.

I also realize that this is just mouse nuts in the grand scheme, and that for many people I am trying to make a problem where there isn't one.  But in my opinion this is one of the types of little things will keep Linux from becoming more mainstream.  Things that should be very simple and very quick to do, like creating a launcher, are more than "mainstreamers" want to deal with.  I think mainstream users would feel that having to open a terminal window to do ANYTHING is too much.  They just want to sit down at the computer and use it, not spend large amounts of time figuring out how to do things, much less things that should be simple.  I am pretty much one of those people and I was getting a little aggravated at having to take the better part of a half of a day just to create a launcher in Unity to launch a python script in a terminal window, then another hour or two figuring out how to get parameters to the terminal, and then the right parameters.

The next thing I have to spend time doing is figure out how to change the terminal launcher to launch a new terminal window by default instead of switching to the already open window.  And then to add the ability to open a root terminal as an option.

Chill pill taken, Rant off,

X

---

