---
title: "Installing Proe Wildfire 2 In Ubuntu 7.04 Feisty Fawn"
date: 2007-06-19
forum: General Help
---

### Post by cyanide on 2007-06-19
Hi everyone,

I use Ubuntu feisty fawn as my main OS. I have been trying for the past year to install Proe Wildfire 2 on it with varying degrees of success. I am hoping some one in this forum will guide me through the install properly.

In the previous version of Ubuntu ie Ubuntu 6.10 Edgy Eft, I was able to run the installation script. However,ever time I tried to run the Proe script ,I got the error message "setenv: too many variables"

In the latest version of Ubuntu,ie Ubuntu 7.04 Fesity Fawn, I am not even able to run the installation script. I get the error " bash:shell not found".

These are the pages I followed to install proe,

[http://forum.ubuntu.org.cn/viewtopic.php?t=3425](http://forum.ubuntu.org.cn/viewtopic.php?t=3425)
[http://blogs.ittoolbox.com/linux/locutus/a...der-linux-12695](http://blogs.ittoolbox.com/linux/locutus/a...der-linux-12695)

Proe Wildfire is essential for my research.

Any help is greatly appreciated.

Regards

---

### Post by ivob66 on 2007-07-29
Hello,

here what I did yesterday to install Pro/E Wildfire 2 on a AMD64 machine, running Ubuntu 7.0.4. There are some packages and libraries that need to be installed to get the PTC installation script running. For AMD64, I copied some libraries from a non-64 machine to the /usr/lib32 directory. There probably is a better way to get these libraries, but it worked for me.

Good luck! Ivo

--------------------------------------------------------------------------------------------

Pro/Engineer Wildfire 2 installation on AMD64, Ubuntu Feisty Fawn, 27 july 2007

1) Pro/E uses a C-shell:
--> sudo apt-get install csh

2) Pro/E needs the portmapper deamon. If NFS (portmapper) has NOT been installed:
--> sudo apt-get install nfs-common

3) copy the complete Pro/E CD from /media/cdrom0 to /cdptc:
--> sudo mkdir /cdptc
--> cd /cdptc
--> sudo cp -r /media/cdrom0/* .

4) Install the library libXm.so.3:
--> sudo apt-get install libmotif3

5) AMD64 only:
--> sudo apt-get install ia32-libs

6) Install libstdc++-libc6.2-2.so.3

6a) Non-64 bits installation:
--> sudo apt-get install libstdc++2.10-glibc2.2

6b) AMD64:
The library must be copied from a non-64 bits installation.
--> copy (from a non-64 bit installation) the /usr/lib/libXm.so.3 file to /usr/lib32 (on the AMD64 PC)

The same for the following libraries. These are not essential, but Pro/E will wait several minutes before starting up if these libraries are missing:
libgtk-1.2.so.0
libgdk-1.2.so.0
libglib-1.2.so.0
libgmodule-1.2.so.0

7) Start the PTC installation script:
--> cd /cdptc
--> sudo ./setup
The graphical installation screen should pop-up. 
Check that the host-id that is shown in this screen is compatible with your license file
(especially when having more than 1 network card!)

8.) Install Pro/E in the usual way.
   
9) Check if Pro/E starts:
--> /usr/local/ptc/proeWildfire2.0/bin/proe

10) Make a desktop launcher to the  command:
- right-click in the background of the desktop and select 'create launcher'
- Use the 'browse' option to select the start script

11) To start Pro/E in a particular directory, so that you can put
there a (project specific) config.pro file, create a script with something like
the following lines:

#!/bin/csh -f

# Define the variable PRO_STDS; can be used in the config.pro:
setenv PRO_STDS /home/user/pro_stds

# Go to the startup directory:
cd /home/user/proe_work

# Start Pro/E:
/usr/local/ptc/proeWildfire2.0/bin/proe

(and then make sure that the launcher points to this startup script)

--------------------------------------------------------------------------------------------------------

---

### Post by Qdlaty on 2007-11-11
Any suggestions how to install Wildfire 3 under Gutsy?

My company gave me a gift by buying additional license of Pro/E for Linux but local service has no idea how to install it. He just sent me the CD and left the note "help yourself".

I'm trying to run setup script but all I receive is either
* Syntax error: "elif" unexpected (expecting "then")*
under Bash
or
[I]rundir=/media/disk-2/CD1: Command not found.
fullscrname=setup: Command not found.
scrname=setup: Command not found.rundir=/media/disk-2/CD1: Command not found.
fullscrname=setup: Command not found.
scrname=setup: Command not found.
fullscrpath=: Command not found.
fullscrpath: Undefined variable.
fullscrpath=: Command not found.
fullscrpath: Undefined variable.[/I]
under csh.

---

### Post by HsChen07 on 2007-12-12
> **ivob66 said:**
> Hello,

here what I did yesterday to install Pro/E Wildfire 2 on a AMD64 machine, running Ubuntu 7.0.4. There are some packages and libraries that need to be installed to get the PTC installation script running. For AMD64, I copied some libraries from a non-64 machine to the /usr/lib32 directory. There probably is a better way to get these libraries, but it worked for me.

Good luck! Ivo

--------------------------------------------------------------------------------------------

Pro/Engineer Wildfire 2 installation on AMD64, Ubuntu Feisty Fawn, 27 july 2007

1) Pro/E uses a C-shell:
--> sudo apt-get install csh

2) Pro/E needs the portmapper deamon. If NFS (portmapper) has NOT been installed:
--> sudo apt-get install nfs-common

3) copy the complete Pro/E CD from /media/cdrom0 to /cdptc:
--> sudo mkdir /cdptc
--> cd /cdptc
--> sudo cp -r /media/cdrom0/* .

4) Install the library libXm.so.3:
--> sudo apt-get install libmotif3

5) AMD64 only:
--> sudo apt-get install ia32-libs

6) Install libstdc++-libc6.2-2.so.3

6a) Non-64 bits installation:
--> sudo apt-get install libstdc++2.10-glibc2.2

6b) AMD64:
The library must be copied from a non-64 bits installation.
--> copy (from a non-64 bit installation) the /usr/lib/libXm.so.3 file to /usr/lib32 (on the AMD64 PC)

The same for the following libraries. These are not essential, but Pro/E will wait several minutes before starting up if these libraries are missing:
libgtk-1.2.so.0
libgdk-1.2.so.0
libglib-1.2.so.0
libgmodule-1.2.so.0

7) Start the PTC installation script:
--> cd /cdptc
--> sudo ./setup
The graphical installation screen should pop-up. 
Check that the host-id that is shown in this screen is compatible with your license file
(especially when having more than 1 network card!)

8.) Install Pro/E in the usual way.
   
9) Check if Pro/E starts:
--> /usr/local/ptc/proeWildfire2.0/bin/proe

10) Make a desktop launcher to the  command:
- right-click in the background of the desktop and select 'create launcher'
- Use the 'browse' option to select the start script

11) To start Pro/E in a particular directory, so that you can put
there a (project specific) config.pro file, create a script with something like
the following lines:

#!/bin/csh -f

# Define the variable PRO_STDS; can be used in the config.pro:
setenv PRO_STDS /home/user/pro_stds

# Go to the startup directory:
cd /home/user/proe_work

# Start Pro/E:
/usr/local/ptc/proeWildfire2.0/bin/proe

(and then make sure that the launcher points to this startup script)

--------------------------------------------------------------------------------------------------------

I have done with your method to install Wildfire 3.0 M080 in my Ubuntu gutsy(7.10) AMD64 System. The installation went well, but when I run the software by:
             cd /home/****/Working
             LANG=EN
             /usr/local/ptc/proeWildfire3.0/bin/proe1 
I've got an error:
                   [B]  [COLOR="Red"] setenv: Too many arguments.[/COLOR]
  And about 2 minutes later it gives me another warning: [COLOR="Red"]WARNING: Name Server is shutting down due to timeout reached.[/COLOR][/B]

But the software of this version goes very well in gutsy i386 version.

          I want to know how to deal with the problem.

Thanks very much!

---

### Post by ds_eng on 2008-01-06
I too am getting the "setenv: Too many arguments" error. I'm running metacity on 7.10. I've been unable to resolve. I've followed the directions below and the info on this site: [http://blogs.ittoolbox.com/linux/locutus/archives/how-to-install-proengineer-under-linux-12695?e=unrec#commentsForm](http://blogs.ittoolbox.com/linux/locutus/archives/how-to-install-proengineer-under-linux-12695?e=unrec#commentsForm)

---

### Post by salariua on 2008-02-22
Guys, 

following this link[ blogs.ittoolbox.com]("http://blogs.ittoolbox.com/linux/locutus/archives/how-to-install-proengineer-under-linux-12695") you can find how to solve the language problem.

You should put the export line at the beginning of the proe start script.

Inset this in the start script : "export LANG=en_US"

It worked for me.

I am running 7.10   - the Gutsy Gibbon AMD64 and Proe W3.080

---

### Post by HsChen07 on 2008-04-01
> **salariua said:**
> Guys, 

following this link[ blogs.ittoolbox.com]("http://blogs.ittoolbox.com/linux/locutus/archives/how-to-install-proengineer-under-linux-12695") you can find how to solve the language problem.

You should put the export line at the beginning of the proe start script.

Inset this in the start script : "export LANG=en_US"

It worked for me.

I am running 7.10   - the Gutsy Gibbon AMD64 and Proe W3.080
Hi salariua!
Thanks for your help,but
I'm sorry I haven't got it.
Can you describe more detail?
thanks again!

---

### Post by 6dof on 2008-04-01
Hi, I'm following ivob66's instructions to install WF3 on to Ubuntu 8.04 and I'm getting this error:

Starting PTC.Setup, please wait ...
*machinename*:~/temp/ptc/disk1$ /home/ddominick/temp/ptc/disk1/dsrc/i486_linux/obj/redirect: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

I've installed the library according to the instructions.

Any ideas?

---

### Post by Dubstar_04 on 2008-04-06
I am also getting:

sandal@MediaBox:~$ /usr/local/ptc/proeWildfire3.0/bin/proe
sandal@MediaBox:~$ setenv: Too many arguments.

After a clean 7.10 64bit install!!

It worked great on 32bit!

Any Ideas?

---

### Post by salariua on 2008-04-28
> **HsChen07 said:**
> Hi salariua!
Thanks for your help,but
I'm sorry I haven't got it.
Can you describe more detail?
thanks again!

Well...

It was a while a go when I did my install but basically, after installing the additional required files that IVOB66 is mentioning I have changed the resolution to 800x600 (don't know why but didn't worked if not) and run proe install. One important thing is that I have told the install to make the shortcuts for me. I end up having a lot of shortcuts on the Desktop and have moved them under a proe folder on the desktop just to clean the screen a bit.

 Then I have made a script using this web site [here]("http://blogs.ittoolbox.com/linux/locutus/archives/how-to-install-proengineer-under-linux-12695?e=unrec#commentsForm").


Quote"

cat > lproe.sh << "EOF"
export LANG=en_US
/path/to/proe/proe
EOF

chmod +x lproe.sh

"end of quote

I have made a panel shortcut button that is linked to the script newly made.

Let me upload the files (proe shortcut made by ptc install) and the script maybe it will help you.

Really the person we should be thanking is IVOB66 (he's my hero). :)

---

### Post by pumelloman on 2008-05-18
Basically what was said above works for me, (first post), however there is one additional step I had to take.

I'm running an Intel Core 2 Duo, and 64-bit 8.04 Hardy. What I had to do was replace the libXm.so.3 with the 32 bit version.

Using this link, find the file libmotif3_2.2.3-2_i386.deb
[http://ftp.debian.org/debian/pool/non-free/o/openmotif/](http://ftp.debian.org/debian/pool/non-free/o/openmotif/)

then navigate to the folder you've saved it in, and force the install. 
[B]Note, this will probably mess up any other processes that need that file.
[/B]
According to this post: [http://backports.ubuntuforums.com/showthread.php?t=39556](http://backports.ubuntuforums.com/showthread.php?t=39556)
[INDENT]"Please note that this method conflicts with any packages which require 64bit libmotif3 and only should be used for closed source coded applications like the Citrix client."[/INDENT]

sudo dpkg -i --force-architecture libmotif3_2.2.3-2_i386.deb

This might bugger up my computer really good, I'll post later if I have some results.

---

### Post by pumelloman on 2008-05-18
So it does work. However Synaptic is being annoying and continuing to tell me that the libXm.so.3 package is Broken (with good cause).

I will keep this package on hand and install it every time I plan on using Pro/E for an extended period. Not a very good fix but it does work.
Any suggestions?

I also had an issue with "UTF-8 language" as well and Pro/E starting, but typing in this code:
```
export LANG=en_US
```
fixed that.

---

### Post by salariua on 2008-05-20
> **pumelloman said:**
> So it does work. However Synaptic is being annoying and continuing to tell me that the libXm.so.3 package is Broken (with good cause).

I will keep this package on hand and install it every time I plan on using Pro/E for an extended period. Not a very good fix but it does work.
Any suggestions?

I also had an issue with "UTF-8 language" as well and Pro/E starting, but typing in this code:
```
export LANG=en_US
```
fixed that.

Do you have any problems with proe at all in hardy (8.04) ? I have told the update manager to go ahead and update my version from 7.10 to 8.04 automatically and now proe is behaving slow on the pull-up menus. If I want to do any feature operation like (chamfer, revolve, or any) and I hit the bottom buttons like (options, properties, shape, location ...etc) it comes up very slowly (2-3 seconds) and the fan really goes up (guess it uses a lot of cpu - whole system is slow).

It eats the whole processor and that happens when I scroll trough the menus (file, edit, view...) or use the  dash board menu to get feature properties (placement, options, properties, profile....).

Do you have this problem with your version?

using v3M080 Hardy AMD64

---

### Post by kyle.p on 2008-05-24
> **salariua said:**
> Do you have any problems with proe at all in hardy (8.04) ? I have told the update manager to go ahead and update my version from 7.10 to 8.04 automatically and now proe is behaving slow on the pull-up menus. If I want to do any feature operation like (chamfer, revolve, or any) and I hit the bottom buttons like (options, properties, shape, location ...etc) it comes up very slowly (2-3 seconds) and the fan really goes up (guess it uses a lot of cpu - whole system is slow).

It eats the whole processor and that happens when I scroll trough the menus (file, edit, view...) or use the  dash board menu to get feature properties (placement, options, properties, profile....).

Do you have this problem with your version?

using v3M080 Hardy AMD64

I am having the same issue. I didn't notice the dashboard going like that when I ran 7.10, but I just (last night) upgraded to 8.04 and those menus slowly "creep" up. Kind of irritating. 

Its pretty fast with using any other tools. It renders the part well while I am working on it / moving it around. No hesitation in using sketcher or extruding etc. Only thing (at this point) is the dashboard.  Worth noting that I haven't really done anything in it since the upgrade to 8.04. I only just did a basic extrusion to confirm your issue on my computer.

I have an AMD64 too.

Did you install all of the 32bit libraries that the ivob66 recommended (but not required)? 

These are the:
libgtk-1.2.so.0
libgdk-1.2.so.0
libglib-1.2.so.0
libgmodule-1.2.so.0

I am not sure of the relevance of these, but plan on checking them out first since I don't have them installed.

---

### Post by kyle.p on 2008-05-24
Not sure if I installed those packages properly (or all the proper ones), but I tried and I still have the issue.

I really need this to work as smooth as it did last week. Otherwise I am better off using Pro/E under windows...and that just sucks.

---

### Post by salariua on 2008-05-25
> **kyle.p said:**
> Not sure if I installed those packages properly (or all the proper ones), but I tried and I still have the issue.

I really need this to work as smooth as it did last week. Otherwise I am better off using Pro/E under windows...and that just sucks.

You sure have touched a spot there with the windows .... Especially since there is no linux version of proe v4.

I haven't installed the libraries after the upgrade but I see you have and the problem persists.

The rest of the program works great (really nice) but this dashboard problems are holding me down. If only to specify a name for the extrude feature it needs 3-5 seconds then I loose my work tempo.

---

### Post by pumelloman on 2008-05-27
So salariua PM'ed me and asked me if I was having the same issue with the "creeping" Pro/E window. To be more specific, when you want to extrude something, and click "Placement" in the bottom left corner, it slooooooooowly pops up.

I have a clean install of the amd64 8.04 Hardy Heron, and it also did the creeping thing for me as well.

Not only that, but I found out something else interesting. If you have Compiz enabled, (that is, System -> Appearance -> Visual Effects, then something selected other than the "None" option), Pro/E will not start. It will pop up a grey window that says "UI Decorations" or "UI Decoration", and will not start up. Turning off Compiz solves this problem.

Sorry salariua, Pro/e is not nice and quick in a fresh install either. I can understand what you mean by killing your tempo, but I guess at least it works (albeit somewhat slowly). I'm curious if 32 bit has all these problems? I kind of doubt it.

For anyone that's curious, the Spaceball Navigator PE also works in Pro/E in Ubuntu.

---

### Post by salariua on 2008-05-28
> **pumelloman said:**
> 
I have a clean install of the amd64 8.04 Hardy Heron, and it also did the creeping thing for me as well.

Not only that, but I found out something else interesting. If you have Compiz enabled, Pro/E will not start.

Sorry salariua, Pro/e is not nice and quick in a fresh install either. I can understand what you mean by killing your tempo, but I guess at least it works (albeit somewhat slowly). I'm curious if 32 bit has all these problems? I kind of doubt it.

For anyone that's curious, the Spaceball Navigator PE also works in Pro/E in Ubuntu.

I knew about the compiz issue, and actually it's not a problem for me cause I need all my resources.
I also don't know if it will work with 8.04 32 bit.
Space Navigator is great. I have the notebook edition and it's a very nice thing to have on 3d CAD. I wish they would have some more support for it under linux (for google earth or so...) but .. maybe in time.

Some more tips: I am using btnx to get my extra buttons on the mouse to work (mouse not space navigator) and now I have ctrl and shift right there at hand.
I have written to the btnx guys to see if I can get them to read the 3dconnexion devices so we can program the buttons and movements for other programs like picture viewers to zoom and pan, but have no answer till now. Keep pushing ... that's what we need to do.

Well.... It seems I need to go back to the 7.10 version of Ubuntu for proe.

---

### Post by makzimu on 2008-06-19
hei pumelloman,

just wondering how you got the space navigator working, could you detail how to do this?

---

### Post by salariua on 2008-06-19
> **makzimu said:**
> hei pumelloman,

just wondering how you got the space navigator working, could you detail how to do this?

For me it was easy. I have just used the drivers on the disk. There's a section for the linux version.

The [COLOR="Blue"]_[diver]("http://www.3dconnexion.com/support/downloads.php")_[/COLOR] comes as free download and I have attached the installation info file given in the driver folder. I am sure that after you unzip it it has the info inside. But you need to connect the space navigator to usb and start the driver before you start proe. 
the command to start the driver is: /etc/3DxWare/daemon/3dxsrv -d usb
I have made a shortcut on the bar next to the proe shortcut.

Check the attachment.

---

### Post by hambone79 on 2008-06-22
Just an FYI for everyone...

The problem with the windows opening extremely slow has something to do with libxcb-xlib. I am currently running Fedora 9 on my primary workstation and it completely broke my installation of Pro/E WF 3.0 when I upgraded from Fedora 8. Because of the piss poor NVidia/Xorg support in Fedora 9, I had to roll my Xorg installation back to the Fedora 8 version. When I did this and installed the Fedora 8 version of libxcb-xlib, my choppy interface problems went away (although I still have problems with no text displaying in any of the menus in Fedora 9).

I'm still trying to learn my way around Kubuntu 8.04, but if someone knows how to fix this or if it is possible to roll back to the older version of the libxcb libraries, I think this will fix the problem. Either way, I think this would classify as a bug since it only seems to be a problem in the newest version of libxcb.

---

### Post by hambone79 on 2008-06-23
Looks like others are experiencing similar problems due to this bug:


[https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311](https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311)

---

### Post by salariua on 2008-06-24
> **hambone79 said:**
> Just an FYI for everyone...

The problem with the windows opening extremely slow has something to do with libxcb-xlib. I am currently running Fedora 9 on my primary workstation and it completely broke my installation of Pro/E WF 3.0 when I upgraded from Fedora 8. Because of the piss poor NVidia/Xorg support in Fedora 9, I had to roll my Xorg installation back to the Fedora 8 version. When I did this and installed the Fedora 8 version of libxcb-xlib, my choppy interface problems went away (although I still have problems with no text displaying in any of the menus in Fedora 9).

I'm still trying to learn my way around Kubuntu 8.04, but if someone knows how to fix this or if it is possible to roll back to the older version of the libxcb libraries, I think this will fix the problem. Either way, I think this would classify as a bug since it only seems to be a problem in the newest version of libxcb.


I will try the old libraries and tell you if that's the solution. Mean while you can do the same by going [here]("http://packages.ubuntu.com/search?keywords=libxcb-xlib&searchon=all&suite=gutsy&section=all")

So I did install the libraries from Gutsy as you suggested and still the same problem. Well.. I'm still stuck.

---

