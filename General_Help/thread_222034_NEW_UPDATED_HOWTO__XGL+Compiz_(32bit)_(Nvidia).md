---
title: "NEW UPDATED HOWTO : XGL+Compiz (32bit) (Nvidia)"
date: 2006-07-24
forum: General Help
---

### Post by Beamerboy on 2006-07-24
I decided to write a new HOWTO for setting up XGL+Compiz because the one in the "One thread to rule them all" thread at the top of this forum is lacking and over complicated.  This definitely works for 32Bit Dapper and should work for 64Bit as well although I haven't tried it so I can't confirm with certainty, hense why I added 32 Bit to the subject of this thread.

The first part of this thread is also Nvidia Specific (as I don't have an ATI card so I have never setup xgl drivers for ATI) however, the rest of the HOWTO (once you get past the Xgl driver setup) should also work for ATI etc.

OK let's get started.

First we want to make sure we have the Nvidia Xgl drivers installed and working under Xorg, so open a terminal (gnome-terminal will do) and type the following:

```

sudo gedit /etc/apt/sources.list

```
This will open your sources.list in a gnome friendly editor, scroll to the bottom and add the following:

```

deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net/ dapper main

```

Save the file, go back to your terminal and type this:

```

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -

```

Then this:

```

sudo apt-get update

```
Once it has finished type the following:
```

sudo apt-get upgrade

```

Now we need to install and configure the Nvidia Glx drivers for Xorg, so type the following in your terminal:

(Note: You can ignore this step if you have already setup Xgl drivers).
```

sudo apt-get install nvidia-glx

```

The above command will download and install the Glx drivers now you want to configure them.  There are many ways to configure your xorg.conf, most of which are beyond the scope of this HOWTO, this HOWTO only covers adding Xgl support to your xorg.conf if you want to configure things like twinview (dual head support) and xinerama (one desktop across multiple monitors) please type *man nvidia-xconfig* from the terminal.

To add Glx support type the following from your terminal

```

sudo nvidia-xconfig

```
[Just a little helper here since the above command tends to set just one resolution mode, if you do *sudo nvidia-xconfig --mode=1600x1200* (change 1600x1200 for the resolution you want) you can change mode from within xorg by using ctrl+alt+ +/- (plus to increase, - to decrease)]

Restart your Xorg server with ctrl+alt+backspace.  This will take you back to the login screen, log back in.

OK so lets confirm Xorg is now using the correct drivers, this can be done by typing the following from a terminal:

```

glxinfo

```

If you scroll up the output near the top you should have this line:

**client glx vendor string: NVIDIA Corporation**

And about halfway down you should have this line:

**OpenGL vendor string: NVIDIA Corporation**

If the OpenGL vendor string says Mesa, you need to check your /etc/X11/xorg.conf file and make sure your video device is using **Driver "nvidia"** and not **Driver "nv"**.  If you followed the instructions above this should not be an issue.

If you want to see your OpenGL in action type the following from a terminal:

```

glxgears

```

Now lets setup your gnome login to load Xgl instead of Xorg.  To do this you need to edit a file called gdm.conf-custom, so type the following from your terminal:

```

sudo gedit /etc/gdm/gdm.conf-custom

```

At the very bottom of the file add the following lines:

```

0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true

```

Save the file and go back to the terminal, it is time to download and install Xgl and Compiz.  Type the following in your terminal:

```

sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes

```

That will install Xgl, Compiz and all the goodies.  Now we need to write our startup script and add it to our session startup.  Let's write it first, from the terminal type:
```

sudo gedit /usr/bin/startcompiz

```

Enter the following text then save the file:

```

#!/bin/sh
compiz-start &

```

Now we need to make it exectuable so type the following from the terminal:

```

sudo chmod 755 /usr/bin/startcompiz

```

And finally we need to add it to our session startup.  the easiest way to do this is to click on the "System" menu in the gnome panel at the top of your screen (providing you are using the default gnome configuration).  Select "Preferences" then at the bottom select "Sessions".  Click on the "Startup Programs" tab and click the "Add" button.  Type the following:

```

/usr/bin/startcompiz &

```

And click on "OK"

As an alternative to the script you could of course just add both command (**cgwd &**  and  **compiz --replace gconf &**) directly to the session startup programs

OK all should be good to go now.  I recommend at this point that you actually reboot your computer as opposed to just restarting X with ctrl+alt+backspace.  But before you do, please read this last section and take some notes for what you need to do once you log back in.

It is likely that you will have no theme selected when you reboot and no title bars on your windows.  If you click on the "System" menu link on your top gnome panel and goto Preferences and select CGWD Themer, it will load the theme manager for compiz.  Then simply select one of the themes in the top panel of the CGWD Themer by left clicking it, and you will see the themes change in real time.

You should have what are known as "Wobbly" windows try dragging a window to see what I mean.  Also ctrl+alt+left/right arrow will put you in cube view mode for selecting a desktop.

You can edit the plugins configurations for all the cool effects by typing the following in a terminal:

```

gconf-editor &

```

The plugins are located under apps>compiz where there are two sections.  The General section is for configuring which plugins to load and the Plugins section is for configuring each individual plugin.

If you have any problems with this HOWTO please pop into #Xgl on irc.freenode.net and look for Paladine, if I am not there, I am sure someone else would be more than happy to help.

Also get on over to [http://www.compiz.net](http://www.compiz.net) and have a look around the forums for more information on themes and plugins.

Enjoy.

**Troubleshooting Guide**

Due to the fact that no HOWTO can fit everyone's system, I have added this section for troubleshooting.  Obviously this section willgrow to cover as many issues as are brought to my attention.

***"I can't get titlebars to show or themes to change"***
If you have followed the guide including the last section regarding Compiz Themer you should have titlebars.  However, if your colour depth is set higher than 24 titlebars won't work.  If this scenario fits you should have an error if you type **cgwd --replace &** from the terminal and get the following error:

```

compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0x3a000f2 to texture

```

You need to type **sudo gedit /etc/X11/xorg.conf** in a terminal and look for your "Screen Section" which should look something like this:

```

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

You need make sure that **DefaultDepth** is set to 24
Also make sure that the SubSection "Display" Depth is not set to 32 (it may have several depths from 1-24, so long as the only Depth set is not higher than 24 you can leave this SubSection unedited.)

Save the file and restart Xgl by doing ctrl+alt+backspace and logging back in.  Make sure you recheck the Compiz Themer to confirm that you have selected a theme and set the default bar layout in the "General" tab.

If you are still unable to see the window decorations, please come to the #Xgl irc channel on irc.freenode.net and ask for assistance.


***"I have no keyboards listed in gnome-keyboard-preferences?"***
Firstly, gnome-keyboard-preferences is normally accessed via the System Menu (on your gnome-panel) (system>preferences>keyboard>Layouts Tab).

If you see no keyboards listed (which will effect your alt and windows keys) check your /etc/X11/xorg.conf to make sure you are not using the Xkb extension.  Look for the following line in the "Section Modules"

```

load "xkb"

```

If you have that line you need to make a change to /etc/gdm/gdm.conf-custom as follows:

**Replace**
```

command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb

```
**with**
```

command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo

```
In other words remove the **-kb** from the end of that line and restart  Xgl with **ctrl+alt+backspace** (should be enough but if you still have problems try a reboot).

As always, if your problems persist try and join #Xgl or #Ubuntu-Xgl irc channels on irc.freenode.net where someone will no doubt assist you (I am normally there too).

Enjoy.

---

### Post by !nkubus on 2006-07-24
Nice howto :)

---

### Post by Beamerboy on 2006-07-24
> **!nkubus said:**
> Nice howto :)

Thanks, I just hope I didn't miss anything out :)  I am pretty sure it is all there though.

---

### Post by ketsugi on 2006-07-24
Is Compiz themeable yet? Or is there only just the one window manager theme? I don't really like the default that I saw a few months back and I'm really liking my current Gnome theme...

---

### Post by Beamerboy on 2006-07-24
> **ketsugi said:**
> Is Compiz themeable yet? Or is there only just the one window manager theme? I don't really like the default that I saw a few months back and I'm really liking my current Gnome theme...

Yes it is themeable, if you look in the HOWTO you will notice we download an install gcompizthemer and gcompizthemer-themes.  The first is the application that allows you to choose and edit themes, the latter is a set of themes for using with Compiz Themer.

Beamerboy.

---

### Post by it.henrik on 2006-07-24
thnx for the howto

one thing... 
chmod +x /usr/bin/startcompiz 
should prob be
sudo chmod +x /usr/bin/startcompiz

My alt-key doesnt work for me anymore .. any ideas?

---

### Post by Beamerboy on 2006-07-24
> **it.henrik said:**
> thnx for the howto

one thing... 
chmod +x /usr/bin/startcompiz 
should prob be
sudo chmod +x /usr/bin/startcompiz

My alt-key doesnt work for me anymore .. any ideas?

Fixed the sudo chmod.

Regarding your alt key goto 
System>Preferences>Keyboard  (the systemmenu on your gnome panel)

Click on the Layout Options tab
Second option down"Alt/Win Key Behaviour

(Mine isset to Super is matched to the win-keys (default))

That should fix it for you.

---

### Post by !nkubus on 2006-07-24
I tried your nice howto but it gives me the follozing error

```

 cgwd: no process killed
compiz.real: No composite extension
Couldn't load theme.  Reverting to defaults.

``` :-k 

and sometimes this one

```

cgwd: no process killed
compiz.real: No composite extension
cgwd: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.

``` :-k 

thanks for your help :)

---

### Post by JoWilly on 2006-07-24
Xmodmap is not needed and no script is needed. Make it shorter and easier with :

1. Remove xmodmap and add "-kb" to gdm.conf-custom like this:

```
command=/usr/bin/Xgl :0 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer -kb
```

2. do not complicate things with a script. Just add:

"compiz --replace gconf" and "gnome-window-decorator" to the gnome session startup.


Everything else is nice.

---

### Post by RickShelton on 2006-07-24
I get the following error.

pfloyd@pfloyd-desktop:~$ sudo apt-get install xserver-xgl compiz-gnome cgwd gcompizthemer gcompizthemer-themes
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package cgwd

Any ideas, I searched for the cgwd package with no luck
Thanks.
Rick

---

### Post by Vicfred on 2006-07-25
pretty howto i will try it :P thx

---

### Post by Beamerboy on 2006-07-25
!nkubus and Rick did you both resolve your issues?

Asking me question in the thread is not the best way to do it, you should try and catch me or someone else on the freenode irc server in #xgl as I am a great deal more attentive there than I am on the forums.

Also I don't want this HOWTO to turn into another Xgl thread from hell, which is how all the rest seem to have gone.  So if you need assistance, please come to the #Xgl on irc.freenode.net

Sorry I didn't reply sooner, I was busy and then sleeping.

---

### Post by reykjavic on 2006-07-25
I had the same problem as rick, and because i'm a linux and IRC noobling, i have no idea how to contact you over irc - anyway, i followed your guide, and did everything, but when i ran the lines.  I just installed ubuntu last night on my laptop (at the cost of reformatting my HD and killing xp).  I can log into the xgl enviro, but none of the windows have any buttons or anythying, and you can't move anything, which i believe is because i ahve no theme.

Thanks a lot

```

sudo apt-get isntall cgwd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package cgwd

sudo apt-get install gcompizthemer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcompizthemer

sudo apt-get install gcompizthemer-themes
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcompizthemer-themes

```

---

### Post by fragmented_user on 2006-07-25
sounds like you need to edit your /etc/apt/sources.list or make sure you downloaded all pgp keys . check out this link [http://xgl.compiz.info/](http://xgl.compiz.info/)

---

### Post by reykjavic on 2006-07-25
psyche, i fixed it so it would download
```

sudo gedit etc/apt/sources.list

```
added 
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

then ran
```

sudo apt-get update

```
and then the sudo apt-get install blah blah from your walkthrough - and so far so good!

---

### Post by RickShelton on 2006-07-25
In the how-to it had souces-list not sources.list
Thats why mine failed to update properly.
Rick

---

### Post by Beamerboy on 2006-07-25
> **RickShelton said:**
> In the how-to it had souces-list not sources.list
Thats why mine failed to update properly.
Rick

Ooops, my apologies, I have corrected the problem now.  Sorry I never got back sooner, I have been very busy all day.

---

### Post by nrayever on 2006-07-25
let's see how this new howto works.

nrayever

---

### Post by hanzomon4 on 2006-07-26
Suggestions: 
Add -xorgAc to gdm.conf-custom 
like this > [server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -xorgAc  -accel glx:pbuffer -accel xv:fbo
flexible=true
 Do this so you can run apps like CPU-games on the regular xserver
by using "DISPLAY=:93 game" to launch your app.
Also you may want to use "compiz-start.py", which can be found at [compiz.net,]("http://www.compiz.net/viewtopic.php?id=1170")to start, and stop compiz or metacity, and edit compiz themes(as long as you have gcompizthemer installed). Well thats my 2 cents.

---

### Post by orb9220 on 2006-07-26
Ok a question if I implement this on my fx5200 with two monitors at a resolution 2560x1024 how does it behave. Does the cube position itself at the center of the screen which would split the cube half on one and half on the other monitor. Which would be ugly and unusable to me.

Thanks for the hard work.

---

### Post by patbuntu on 2006-07-26
I'm having problems with apt-get.  I edited my sources.list and downloaded the pgp key, but I get:

```
E: Couldn't find package cgwd
```

When I do a apt-get update, it connects to the repository fine, and says something like

IGN: 

for each file in the repository.  I'm not at my machine so I can't post the output right now though.

If I look in the software manager app I can see the pgp key has been added.  Any suggestions?

I'm on AMD64 by the way

Thanks

-Pat

---

### Post by RAOF on 2006-07-26
Hi.  I'm the builder of the AMD64 packages for Quinn.  Currently, there's some problem with my uploading to Quinn's repository, so the packages in there are rather old.

For AMD64 you're better off using the [ubuntu.systemadministrator.org](ubuntu.systemadministrator.org) and [ubuntu.moshen.de](ubuntu.moshen.de) mirrors, at least until I get uploading to Quinn's repositories sorted out.

Although the mirrors don't **currently** have cgwd in them yet - they'll be sync'd later this evening, and **then** they'll get the newer packages.

---

### Post by patbuntu on 2006-07-26
Thanks for the info.

> For AMD64 you're better off using the ubuntu.systemadministrator.org and ubuntu.moshen.de mirrors, at least until I get uploading to Quinn's repositories sorted out.

Do I add these to my sources.list in the same way?

Thanks again

-Pat

---

### Post by Beamerboy on 2006-07-26
> **orb9220 said:**
> Ok a question if I implement this on my fx5200 with two monitors at a resolution 2560x1024 how does it behave. Does the cube position itself at the center of the screen which would split the cube half on one and half on the other monitor. Which would be ugly and unusable to me.

Thanks for the hard work.

I use dual 6600GTs in my box with one monitor on each card giving a total resolution of 3200x1200.  Having dual monitors I prefer to be "inside" the cube as it makes changing desktops very panoramic (it is literally like being-inside- the environment of my PC).  See [This Screenshot](http://www.paladine.org.uk/images/windows+linux.png).

Of course whether you are in the cube or outside the cube it -has- to display each screen on each screen, it can't do it any other way and I don't understand why you think this would be unusable.  You only see the cube when you switch desktop (or are playing around), the cube is not visible (or rather it is statically positioned and zoomed into 1 face) when you are actually using your applications, so again, your statement about being unuseable makes absolutely no sense whatsoever.

Do you expect the cube to split into 2 or something?  Because that isn't going to happen.

Instead of trying to find excuses not to install it based on what you think will be unusuable without actually having a real concept of the environment, try installing it and then seeing if you like it.

---

### Post by Beamerboy on 2006-07-26
> **RAOF said:**
> Hi.  I'm the builder of the AMD64 packages for Quinn.  Currently, there's some problem with my uploading to Quinn's repository, so the packages in there are rather old.

For AMD64 you're better off using the [ubuntu.systemadministrator.org](ubuntu.systemadministrator.org) and [ubuntu.moshen.de](ubuntu.moshen.de) mirrors, at least until I get uploading to Quinn's repositories sorted out.

Although the mirrors don't **currently** have cgwd in them yet - they'll be sync'd later this evening, and **then** they'll get the newer packages.

Thanks for adding that info, I will include it in the troubleshooting section later this evening when my guests have left.  Thanks also for your amd64 repos which I have myself used in the past.

---

### Post by John.Michael.Kane on 2006-07-26
Theres no 64bit **cgwd** support atleast when i tried to test this howto:. These files seem to be 64bit ready (xserver-xgl compiz-gnome gcompizthemer gcompizthemer-themes). I think once you have 64bit cgwd support your guide will work for both arcutectures.

---

### Post by Beamerboy on 2006-07-26
> **SD-Plissken said:**
> Theres no 64bit **cgwd** support atleast when i tried to test this howto:. These files seem to be 64bit ready (xserver-xgl compiz-gnome gcompizthemer gcompizthemer-themes). I think once you have 64bit cgwd support your guide will work for both arcutectures.

Yup thats why I put 32Bit in the topic.  However, the updated packages (including cgwd) should be available sometime today, check the following repos:

ubuntu.systemadministrator.org and ubuntu.moshen.de which are mirrors or RAOF's 64bit repo.

Raof was kind enough to post in this thread earlier today that the 64bit updates will be available sometime this evening.  At which point, yes this guide should be both 32bit and 64bit friendly :)
[QUOTE=RAOF]
Hi. I'm the builder of the AMD64 packages for Quinn. Currently, there's some problem with my uploading to Quinn's repository, so the packages in there are rather old.

For AMD64 you're better off using the ubuntu.systemadministrator.org and ubuntu.moshen.de mirrors, at least until I get uploading to Quinn's repositories sorted out.

Although the mirrors don't currently have cgwd in them yet - they'll be sync'd later this evening, and then they'll get the newer packages.[/QUOTE]

---

### Post by MarkSheely on 2006-07-27
Very helpful how-to.  Works like a charm on my Dell E1705 (nVidia GeForce Go 7900 GS).  

Thanks,
Mark

---

### Post by patbuntu on 2006-07-27
Still no joy with the 64 bit packages.

I tried the following:

```
wget http://ubuntu.systemadministrator.org/2F306651.gpg -O- | sudo apt-key add -
```

and added:

```
deb http://ubuntu.systemadministrator.org dapper eyecandy
deb-src http://ubuntu.systemadministrator.org dapper eyecandy
```

to my sources.list.  Then:

```
sudo apt-get install xserver-xgl compiz-gnome cgwd gcompizthemer gcompizthemer-themes
```

All packages were found except gcompizthemer-themes.  I removed this and installed the rest, and rebooted.  I got a blue, very cluttered 'x-server died' type screen.  Pretty much the only readable text I could see was libglitz.s? not found.

Am I just being impatient here, or is there another step I am missing?

Thanks again

-Pat

---

### Post by John.Michael.Kane on 2006-07-27
patbuntu I just tried the packages,and xorg conked out. the packages are there for 64bit,however. I think theres a step needed for 64bit thats not in this guide.

---

### Post by srikat on 2006-07-27
BeamerBoy, thanks very much for the guide.

I got it working using your instructions in the first post (comp specs in my signature). But have the following probs:

1. when alt+tab is released, the window doesn't become active...have to press Esc

2. keyboard number pad isn't working

Any ideas?

I jotted down the steps briefly at [http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D](http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D)

---

### Post by John.Michael.Kane on 2006-07-27
srikat which version of ubuntu did you get this working on 32 or 64 bit?

---

### Post by srikat on 2006-07-27
SD: 64 bit

My desktop specs:

AMD Athlon 64, 1800 MHz (9 x 200) 3000+ | nVIDIA GeForce 6100 (128 MB)

---

### Post by Beamerboy on 2006-07-27
> **srikat said:**
> BeamerBoy, thanks very much for the guide.

I got it working using your instructions in the first post (comp specs in my signature). But have the following probs:

1. when alt+tab is released, the window doesn't become active...have to press Esc

2. keyboard number pad isn't working

Any ideas?

I jotted down the steps briefly at [http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D](http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D)

If you goto system>preferences>keyboard and make sure all the keyboard settings are correct.

---

### Post by Beamerboy on 2006-07-27
Those of you on 64Bit make sure you have all the dependencies installed (like glitz etc.).  You can find a full list of the dependencies in synaptic by doing a search for XGL and looking at it's properties.  I would advise you do this for compiz and XGL.

---

### Post by mikedpirone on 2006-07-27
Everytime I try to get the packages I get this error. Not sure what to do. If anyone can help THANK YOU! I've been trying to get this working for days now.

Reading package lists... Done
Building dependency tree... Done
cgwd is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gcompizthemer: Depends: cgwd (>= 0.7) but 0.6 is to be installed
E: Broken packages

---

### Post by Beamerboy on 2006-07-27
> **mikedpirone said:**
> Everytime I try to get the packages I get this error. Not sure what to do. If anyone can help THANK YOU! I've been trying to get this working for days now.

Reading package lists... Done
Building dependency tree... Done
cgwd is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gcompizthemer: Depends: cgwd (>= 0.7) but 0.6 is to be installed
E: Broken packages

Are you installing on 64bit or 32bit?

---

### Post by spin2cool on 2006-07-27
I have the above problem as well 
(gcompizthemer: Depends: cgwd (>= 0.7) but 0.6 is to be installed)

---

### Post by audun1 on 2006-07-27
i also have that problem 

Følgende pakker har uinnfridde avhengighetsforhold:
  gcompizthemer: Avhenger av: cgwd (>= 0.7) men 0.6 skal installeres
E: Ødelagte pakker


i am using 32bit

---

### Post by Beamerboy on 2006-07-27
Which repos are you using?  I just checked dependencies here for gcompizthemer and it requires cgwd >= 0.2.

I also just did a full update and upgrade myself and never had any errors.

Can you please join #xgl or #ubuntu-xgl on irc.freenode.net so I can try and resolve these issues for you.

Thanks

---

### Post by QuinnStorm on 2006-07-27
I messed up when I tried to push cgwd 0.7, I've re-sent it, it should hit soon.

---

### Post by John.Michael.Kane on 2006-07-27
srikat tried your write-up, and xorg crashed. so whatever you did is not listed in your write-up. for me atleast xgl/compiz can't run on 64bit.

---

### Post by Beamerboy on 2006-07-27
> **QuinnStorm said:**
> I messed up when I tried to push cgwd 0.7, I've re-sent it, it should hit soon.


Thanks Quinn, I just noticed this myself on a re-update.

Everyone getting the dependency issue for cgwd please try a sudo apt-get update again in the next 30 minutes or so, Quinn has just added the new version of cgwd to the repo so it should be coming through shortly.

---

### Post by spin2cool on 2006-07-27
Try again - it should work now.  Quinn fixed the problem.

[http://www.compiz.net/viewtopic.php?pid=17288#p17288](http://www.compiz.net/viewtopic.php?pid=17288#p17288)

---

### Post by John.Michael.Kane on 2006-07-27
Who are the updates for 32bit or 64bit users? beta testing this stuff is cool and all when it works,however.dpkg-reconfiguring ones system cause of xorg crashed cause the guides are not right can wear on testers.

---

### Post by Beamerboy on 2006-07-27
Everyone hold on for a minute, there is a problem with the latest cgwd.  Quinn is actively working on fixing it as we speak, so there will be another update coming shortly.

Apologies for the inconvenience but please remember this is still very much a project in development and sometimes unexpected things will happen.  But because they happen they can be investigated, fixed and learned from, which means we get closer to a stable release.

I just received word that Quinn is pushing the fixed cgwd to her repo now.  Try and give it 10-20 minutes though, we don't all want to hit the repo at once :)

---

### Post by John.Michael.Kane on 2006-07-27
Beamerboy so these updates are for 32bit user's??

---

### Post by Beamerboy on 2006-07-27
> **SD-Plissken said:**
> Beamerboy so these updates are for 32bit user's??

Yes they are for quinns repo.  I don't know if the 64bit versions have been upgraded yet, I suspect not but if you have the 64bit repos added to your sources.list try and do an update and see if they are there.

To everyone else (32bit users), the latest cgwd update fixes the problems reported here tonight, but be aware you will need to delete any files in ~/.compiz/plugins or compiz will fail to start.  However, this shouldn't effect most of the people who have used this guide, so this is just a heads up.

---

### Post by John.Michael.Kane on 2006-07-27
Beamerboy thanks for the guide. though i can't test it. since it 32bit based.

---

### Post by Beamerboy on 2006-07-27
> **SD-Plissken said:**
> Beamerboy thanks for the guide. though i can't test it. since it 32bit based.

Well this guide doesn't officially support 64bit yet which is why I put 32bit in the subject line for the thread.  At the moment there is some fragmentation between 32bit and 64bit due to the packages being built in two different places by different people.

These people are volunteers who do this in their own time without being paid, so it is unfair to criticise any delays between Quinn updating her repo and the relevant packages being built in the 64bit repo.  Especially given tonight's adventures with cgwd, which means RAOF would have had to rebuild cgwd twice for the latest update.

RAOF does his best to build 64bit packages as quickly as he can, but you should remember that he also maintains a lot of other packages in his repo besides Quinn's packages.  I personally think RAOF and Quinn do a sterling job.

Just keep checking the 64bit repos for the latest updates.

Also if you are having dependency issues with 64bit, read the error message you get (which tells you what it is dependent on) then install the required package.  This should fix any issues you come across which are not directly related to the compiz packages.

I am not running 64bit anymore so I can't provide support for both as I don't have an environment to test things in.  Patience is the name of the game, the 64bit updates will come through.

---

### Post by John.Michael.Kane on 2006-07-27
I know that they do this of their own time,and did not criticise anyone. sorry you feel that i did.


As I said before you can all the 64bit packages built if theres no documents/howto for getting them installed how is one to test them.

---

### Post by Beamerboy on 2006-07-27
> **SD-Plissken said:**
> I know that they do this of their own time,and did not criticise anyone. sorry you feel that i did.


As I said before you can all the 64bit packages built if theres no documents/howto for getting them installed how is one to test them.

The comment regarding criticism was just a general comment, and wasn't directed at you.

Once you have the dependencies installed, 64bit should not be an issue apart from the time delay on updates.  From my understanding once you have installed the non-compiz dependencies (libglitz etc) you should be able to install and update compiz packages with ease.

---

### Post by patbuntu on 2006-07-27
> From my understanding once you have installed the non-compiz dependencies (libglitz etc) you should be able to install and update compiz packages with ease.

libglitz is what did it for me. Works fine now :D 

Nice one

-Pat

---

### Post by John.Michael.Kane on 2006-07-27
Beamerboy i installed all dependencies used your guide,and the write-up posted by the other user, and xorg crashed. I tried to get xgl/compiz working under 64bit more then three times it's no go.

---

### Post by Beamerboy on 2006-07-27
> **SD-Plissken said:**
> Beamerboy i installed all dependencies used your guide,and the write-up posted by the other user, and xorg crashed. I tried to get xgl/compiz working under 64bit more then three times it's no go.

Can you try and join the irc channels on irc.freenode.net either #xgl or #ubuntu-xgl myself and othr people are in there and happy to help.  I don't want to turn this into a support thread or it just spirals out of control.

---

### Post by John.Michael.Kane on 2006-07-27
Beamerboy i'm in both those channels under the same name here,and i asked for help. someone said i needed  libsvg-cairo_0.1.6-1_amd64.deb which they sent me,and told me to use the ubuntu wiki,and it still did not work under 64bit. right now i feel this xgl.compiz stuff is catered for 32bit users,and the 64bit users are being told to fend for themselfs. every guide is 32bit based does not transfer over to 64bit.


since you do not want this thread to turn this into a support thread or it just spirals out of control. i will not post here any more.

---

### Post by fig_jam_uk on 2006-07-27
OMG OMG OMG this is frikkin kewl, I love it thanks soooo much for the how to :KS

---

### Post by srikat on 2006-07-27
SD,

There were few things that I did and not document in my brief guide since I wasn't sure if those made any difference. I shall post them up here later in the evening (IST). Don't give up hope. What do you have to lose? At the max, you will change back to X if it crashes again.

---

### Post by srikat on 2006-07-28
SD,

One thing I didn't include in the [quick guide]("http://tiddlyspot.com/ubuntu/#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D") was that I've downloaded and installed packages at [http://ubuntu.systemadministrator.org/dists/dapper/eyecandy/](http://ubuntu.systemadministrator.org/dists/dapper/eyecandy/)

I didn't get all of those, but only till the libwnck section. I already had some of them, so just installed the missing ones...Perhaps I also had all/some from the section 'mesa' onwards.

I am not sure if those made any difference for xgl install.

---

### Post by John.Michael.Kane on 2006-07-28
srikat after being frustrated it's working.to get all the files i had to use quinn's repos and Falcon generated repository. maybe i could write a guide for it theres alot of steps. anyway compiz seems to work on 64bit.

---

### Post by Fedcer on 2006-07-28
Hi, when I do:

```

glxinfo

```

instead of saying "client glx vendor string: NVIDIA Corporation", it says "client glx vendor string: SGI". I did a quick google search and apparently it means that it is using the mesa libraries instead of the nvidia ones.
Any idea how to fix this ?

Thanks,

Fedcer

EDIT: Nevermind, fixed it.

-

---

### Post by Adrian_b on 2006-07-28
Hi, your guide is really good and easy to follow, however, i have 2 problems now..
I can't use the numbers on my number-pad on the right unless i press SHIFT+number...
Also, i'd like to play my 3D-games and i knew there was a guide on this forum describing a way to let every game run in it's own X-server, however, i can't find it anywhere...

(And maybe you should include an uninstall guide too :D )

---

### Post by andril on 2006-07-28
Thanks for all the support with this - can someone provide what entries I should see in the sessions windows to ensure my installation is correct?

This would be an awesome addisition to Arnieboy's Automatix (hint-hint) :KS 

Thanks In Advance

---

### Post by ZeusABJ on 2006-07-29
First off let me just say this:

THIS IS AN UNBELIEVABLY AWESOME GUIDE!!!!

Setting up XGL by following your steps made the whole process a no brainer! You get 5 starts:

:KS :KS :KS :KS :KS 

Now I do have questions based on some minor XGL-related issues I've encountered:

Terminal Server Client seems to have issues with transparency (it appears washed out and partially transparent) is there any way to fix this?

When using ALT-TAB to move between windows it seems to get "stuck" and the only way to get out of it is to hit ESC. Is there a way to make ALT+TAB behave normally again (ie releasing the keys leaves you on the window you selected)?

Is there any sort of GUI-based configuration panel for XGL out there? I'm not the best command line guru and I'd rather not dig through the configuration editor every time I want to make a minor change. I know SLED has an XGL control panel of sots. Is there something similar for Ubuntu?

Thanks in advance!

---

### Post by yossman on 2006-07-29
just wanted to mention, we followed your walkthrough for the Xgl setup on nvidia cards, and it worked awesome -- it came up fine on reboot, we didn't even have to select a theme, everything just worked.  thanks so much for posting your howto. ;-)

yossman

---

### Post by srikat on 2006-07-29
Regarding the Alt-tab problem, see [http://ubuntuforums.org/showpost.php?p=1307590&postcount=31](http://ubuntuforums.org/showpost.php?p=1307590&postcount=31) where I posted the same. 

You can see the fix at [http://tiddlyspot.com/ubuntu/index.html#%5B%5BFixing%3A%20Numpad%20keys%20not%20working%20and%20alt%2Btab%20not%20working%20properly%5D%5D](http://tiddlyspot.com/ubuntu/index.html#%5B%5BFixing%3A%20Numpad%20keys%20not%20working%20and%20alt%2Btab%20not%20working%20properly%5D%5D)

Reg. GUI to control compiz's settings, this is the reply I got:

> <goibhniu> it's a bit out of sync but gset-compiz
<goibhniu> and gcompizthemer
<goibhniu> and everything else is in gconf-editor
<goibhniu> you may need to install them
<goibhniu> gset-compiz is still handy for configuring the plugins, you can't do that with gcompizthemer alone

I have 'compiz themer' under System -> Prefs

I don't know how to get to "gset-compiz'.

> **ZeusABJ said:**
> First off let me just say this:

THIS IS AN UNBELIEVABLY AWESOME GUIDE!!!!

Setting up XGL by following your steps made the whole process a no brainer! You get 5 starts:

:KS :KS :KS :KS :KS 

Now I do have questions based on some minor XGL-related issues I've encountered:

Terminal Server Client seems to have issues with transparency (it appears washed out and partially transparent) is there any way to fix this?

When using ALT-TAB to move between windows it seems to get "stuck" and the only way to get out of it is to hit ESC. Is there a way to make ALT+TAB behave normally again (ie releasing the keys leaves you on the window you selected)?

Is there any sort of GUI-based configuration panel for XGL out there? I'm not the best command line guru and I'd rather not dig through the configuration editor every time I want to make a minor change. I know SLED has an XGL control panel of sots. Is there something similar for Ubuntu?

Thanks in advance!

---

### Post by Shadowline on 2006-07-29
I'm having a h*ll of a time getting XGL to work. I had it working on a previous install of dapper just fine. I followed the updated guide to the letter. Now when ever I log into gnome and the startcompiz script run's it crashs back to gdm. The nvidia drivers are installed, glxgears run fine, my xorg.conf is correct, I'm at a total lose as to how to fix it.
](*,)

---

### Post by Beamerboy on 2006-07-30
> **Shadowline said:**
> I'm having a h*ll of a time getting XGL to work. I had it working on a previous install of dapper just fine. I followed the updated guide to the letter. Now when ever I log into gnome and the startcompiz script run's it crashs back to gdm. The nvidia drivers are installed, glxgears run fine, my xorg.conf is correct, I'm at a total lose as to how to fix it.
](*,)

If you pop onto irc later I will try and help you.  I notice you were there last night unfortunately I was sleeping for the first time in 3 days so I missed you.

---

### Post by ZeusABJ on 2006-07-30
Thanks for the help! And now let me help with this:

> **srikat said:**
>  I don't know how to get to "gset-compiz'.

Here you go:

```
 sudo apt-get install gset-compiz 
```

Enjoy!

---

### Post by andril on 2006-07-30
Line appeared right below the Top Panel after I ran the update for "cgwd" any fixes?](*,)

---

### Post by Beamerboy on 2006-07-30
> **andril said:**
> Line appeared right below the Top Panel after I ran the update for "cgwd" any fixes?](*,)

Andril if you need help with xgl/compiz related stuff, you really should join the irc channels on freenode (referenced several times in this thread already).  Troubleshooting on a forum is too fragmented and just makes threads unmanageable.

---

### Post by Vlatko on 2006-07-31
after running this command ```
sudo apt-get install xserver-xgl compiz-gnome cgwd gcompizthemer gcompizthemer-themes
```
i get the following error:
```
vlatko@vlatko-desktop:~$ sudo apt-get install xserver-xgl compiz-gnome cgwd gcompizthemer gcompizthemer-themes
Reading package lists... Done
Building dependency tree... Done
Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cgwd has no installation candidate
```

i am on dapper 64, i am still all new at this, hope someone can help out.

---

### Post by andril on 2006-07-31
Thanks to all writers of the How-To and the input from the readers. I finally got it all working without errors and clutter. But I have yet to get the icon to work with my current setup. But thanks again :D

---

### Post by Taiden on 2006-07-31
I want to give a big thumbs up to you for making this how-to. After completely raping my original Ubuntu install, I decided to have a go from the beginning. This not only set up XGL for me, but it also installed nvidia drivers. two birds with one stone, just that much closer to a complete base for my linux box! :D

---

### Post by RAOF on 2006-07-31
> **Vlatko said:**
> after running this command ```
sudo apt-get install xserver-xgl compiz-gnome cgwd gcompizthemer gcompizthemer-themes
```
i get the following error:
```
vlatko@vlatko-desktop:~$ sudo apt-get install xserver-xgl compiz-gnome cgwd gcompizthemer gcompizthemer-themes
Reading package lists... Done
Building dependency tree... Done
Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cgwd has no installation candidate
```

i am on dapper 64, i am still all new at this, hope someone can help out.
The 64bit cgwd packages still haven't made it into Quinn's repositories.  If you check out [ubuntu.systemadministrator.org](ubuntu.systemadministrator.org), you'll find the packages you're after.

Essentially, add 
```
deb http://ubuntu.systemadministrator.org dapper eyecandy
```
to your sources.list, and try again.

---

### Post by alcamus on 2006-07-31
Many thanks for a very lucid, simple installation guide. Xgl + Compiz: Sweet! And to think, a few weeks ago I sweated about upgrading all my machines to Windows Vista. Now I'd rather fight than switch.

---

### Post by Vlatko on 2006-08-01
[QUOTE=RAOF]The 64bit cgwd packages still haven't made it into Quinn's repositories. If you check out ubuntu.systemadministrator.org, you'll find the packages you're after.

Essentially, add 
Code:
deb [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
to your sources.list, and try again.[/QUOTE]
thank you. will try when i get off work and report if i have further troubles with the how-to.

---

### Post by Vlatko on 2006-08-01
after the last step and the reboot of the computer, x won't start. i get a blue screen saying x is not configured properly, do you want to view the log, bla, bla. restart x when configured properly.

so i ran the ```
sudo nano /etc/gdm/gdm.conf-custom
``` command and removed these lines ```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```

saved the file and rebooted. everything started up fine, no troubles at all. i am running dapper amd64 version. anyone knows what is the problem?

---

### Post by Vlatko on 2006-08-01
i reinstalled the 32bit version and saved myself a world of trouble. excellent how to guide. :)

---

### Post by kalej on 2006-08-03
when trying to install gcompizthemer gives me this error..

root@kalej-laptop:/home/kalej# apt-get install gcompizthemer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gcompizthemer: Depends: cgwd (>= 0.9) but it is not going to be installed
E: Broken packages

is cgwd 0.9 available for download?

thks

---

### Post by zerolives on 2006-08-03
Same problem as above poster.

---

### Post by hopstah on 2006-08-04
in for later when it's been fixed.

---

### Post by chucknorris on 2006-08-04
Yeah I lost all my themes..Strange update :)

---

### Post by Beamerboy on 2006-08-04
The bug in CGWD Themer has now been fixed and I have changed the HOWTO to take the new themer into account.  Please update using:

```

sudo apt-get update

```

Followed by:

```

sudo apt-get upgrade

```

If you still have problems installing cgwd do the following:

```

sudo apt-get install cgwd

```

This should automatically uninstall gcompizthemer, gcompizthemer-themes and install cgwd (which deprecates the previous two packages).

If you still have problems you can manually uninstall gcompizthemer from synaptic and then either update/upgrade or install cgwd.

---

### Post by SonicTempest on 2006-08-04
I just reinstalled Xgl + Compiz using the updated instructions here. It's working pretty well, but I'm having two problems:

1) The Alt+Tab problem mentioned earlier in the thread...I clicked the link for the fix but I get some HTTP error when it tries to access the page. Similarly when using the taskbar application switcher right-click controls (resize, move, etc) I can't get out of those modes without hitting the Esc button.

2) I can't install any themes! Importing the .cgwdtheme files from the desktop doesn't add them to the list. Although manually extracting the contents and adding them to /.cgwd/themes seems to work.

---

### Post by hopstah on 2006-08-04
to fix the alt-tab thing, remove the -kb section of the addition to the -custom file mentioned in the howto.

---

### Post by Beamerboy on 2006-08-05
There is a new package now called cgwd-themes which contains most of the old themes updated for the new version of cgwd.

You can install it by using the following command

```

sudo apt-get install cgwd-themes

```

I have just edited the HOWTO to reflect this change.  There are now plenty of themes to choose from as with the old gcompizthemer-themes package.

Enjoy.

---

### Post by apocalypso on 2006-08-05
Excellent HOWTO mate, keep up the good work! I followed the guidelines given on the previous Howto and things just didn't work *this* sweet... [-X Now I have a very pleasant and fully functional XGL+Compiz experience, thanks a lot!!! :D

---

### Post by em3raldxiii on 2006-08-06
I followed this guide and got everything working just peachy.  Looks great, and is highly entertaining.

However, I have an nVidia Geforce FX5600 video card, and video is ALWAYS very dark (as is a number of other aspects), so I usually use the nVidia settings manager to boost brightness and gamma.  Now, however, it's all gone and EVERYTHING looks just a wee bit dark & dingy ... 

I installed the gset-compiz package which gives me control over the brightness of my windows, but it only allows me to DECREASE brightness, not increase, so this doesn't help me.

Has anyone come up with a quick-fix for this?  Any help would be greatly appreciated.

---

### Post by Beamerboy on 2006-08-06
> **em3raldxiii said:**
> I followed this guide and got everything working just peachy.  Looks great, and is highly entertaining.

However, I have an nVidia Geforce FX5600 video card, and video is ALWAYS very dark (as is a number of other aspects), so I usually use the nVidia settings manager to boost brightness and gamma.  Now, however, it's all gone and EVERYTHING looks just a wee bit dark & dingy ... 

I installed the gset-compiz package which gives me control over the brightness of my windows, but it only allows me to DECREASE brightness, not increase, so this doesn't help me.

Has anyone come up with a quick-fix for this?  Any help would be greatly appreciated.

Check the trailfocus plugin.  I recommend you use gconf-editor as gset-compiz doesn't work with all the plugins anymore.  In gconf-editor goto apps>compiz>plugins>trailfocus

---

### Post by foxy123 on 2006-08-06
I have a problem with switching keyboard layouts in xfce. I cannot do it in XGL. However if I log into Gnome session then log out and log in to xfce session it works. Very wierd. Any help please!

---

### Post by Beamerboy on 2006-08-06
> **foxy123 said:**
> I have a problem with switching keyboard layouts in xfce. I cannot do it in XGL. However if I log into Gnome session then log out and log in to xfce session it works. Very wierd. Any help please!

Ihave never used xfce so unfortunately I am not in a position to help.  Someone else may be able to though.

---

### Post by John.Michael.Kane on 2006-08-06
foxy123 if you can hit up the folks on #xgl or #ubuntu-xgl on irc they were very help with advice.

---

### Post by Snocrash on 2006-08-06
Hi...

Thanks......The guide worked fine for me except for one problem. Xine-ui no longer works for me. I have re-installed it, tried to build it from repo source, and built it from native source. It just won't work. I know....I know.....I can use totem, or mplayer, or aviplay, or any of the others, but the simple fact is I have been using xine and xine-ui for years and I like it better then the others.....

Any suggestions??????

Specs:
Nvidia Gforce 5700 ultra
Dapper
Stock repo Nvidia driver


Thanks.....

Sno

---

### Post by eleazar123 on 2006-08-06
Thank you very much for this howto.  It got me up and running in under 15minutes!  Not an easy feat :)

Anyways,
Thanks!

-eleazar123:D

---

### Post by em3raldxiii on 2006-08-07
Yah, tried the trailfocus thing, but that's not the issue.

Even in XORG I have to brighten everything a little ... my vidcard + monitor combo seem to result in slightly dark+high-contrast everything.  In otherwords, whites are bright, but all darkish things are uniformly dark.  If I use a dark theme, for example, all dark gradients are just jet black.  But luckily, I can use the nVidia settings to decrease contrast and increase brightness/gamma and it looks perfectly normal.

Now, though, with XGL/Compiz I don't have those controls.  A white page looks fine, especially with black text.  But, for example, all the coffee-beans under usernames on this page look the same color ... super-dark brownish black.  And movies are horrendously dark - as are 3D games.  If I had a brightness control that could BOOST brightness.  And Compriz's BS plugin doesn't do the trick at all.

Any thoughts?  I really appreciate everyone's help :D

Thanks

---

### Post by hopstah on 2006-08-07
> **foxy123 said:**
> I have a problem with switching keyboard layouts in xfce. I cannot do it in XGL. However if I log into Gnome session then log out and log in to xfce session it works. Very wierd. Any help please!

you need to remove the -kb at the end of the line in the stuff that is added to the gdm.conf-custom file.  i don't know why this -kb is in there, it's only caused problems for me and the people i've talked to.

i hope it helps you out too.

---

### Post by bergersau on 2006-08-08
To turn of compiz (As setup by this howto.)

Just disable this setting below from within System, Preferances, Sessions,  Startup Programs.


Quote:
And finally we need to add it to our session startup.  the easiest way to do this is to click on the "System" menu in the gnome panel at the top of your screen (providing you are using the default gnome configuration).  Select "Preferences" then at the bottom select "Sessions".  Click on the "Startup Programs" tab and click the "Add" button.  Type the following:

```

/usr/bin/startcompiz &

```

And click on "OK"

---

### Post by nwgray on 2006-08-08
I finally see (literally) what all the fuss is about. Compiz is great!! Your How To has been the only one that worked for me.

Thanks a lot!

---

### Post by foxy123 on 2006-08-11
> **hopstah said:**
> you need to remove the -kb at the end of the line in the stuff that is added to the gdm.conf-custom file.  i don't know why this -kb is in there, it's only caused problems for me and the people i've talked to.

i hope it helps you out too.

thanks for the tip but it's not a problem. With '-kb' a keyboard indicator crashed the panel in xfce anyway, so I removed it.

The problem seems to be with xkb though I am not sure.

The thing is if I log into Gnome I have the following:

```
~$ xprop -root | grep XKB 
_XKB_RULES_NAMES(STRING) = "base", "pc101", "gb,ru", ",winkeys", "grp:ctrl_shift_toggle"
 _XKB_RULES_NAMES_BACKUP(STRING) = "base", "pc101", "us", "", ""

```
So I can for example do:

```
 ~$ setxkbmap -layout 'gb,ru(winkeys)' -option "grp:ctrl_shift_toggle"
```

to set my keyboard layouts manually. However, if I try the same thing in xfce session, I've got the following
```
xprop -root | grep XKB
```
gives me nothing and

```
:~$ setxkbmap -layout 'gb,ru(winkeys)' -option "grp:ctrl_shift_toggle"
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Segmentation fault
```

It looks like Gnome loads something that xfce does not or my xfce installation is screwed up in some way. Also if I log into xfce after logging into Gnome, everything works fine.

Any help would be appreciated.

---

### Post by theSeinfeld on 2006-08-16
I get the same error as well :confused:. It is not from Gnome...more like the Xgl server doesn't support the XKB :mad:? I am using KDE and CGWD as a Window Manager. Even if I use only the Xgl without Compiz, I still get the error. I hope that there will be some fix soon...:D 

Cheers,
Peter

---

### Post by theSeinfeld on 2006-08-16
Ok, I solved the XKB error/problem. It seems that it is a problem with the way the Xgl was compiled (as I suspected). Hence, here is the way to fix the:
```

$ setxkbmap
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Segmentation fault

```

[LIST=1] First, check out if your Xgl has the correct path to the compiled xkb directory. Type:
```

$ strings `which Xgl` |grep compiled
/usr/share/X11/xkb/compiled/
Couldn't open compiled keymap file %s

```
So, your XKB files are supposed to be compiled at this location, but, if you have Kubuntu like me, you will see that the directory contains:
```

$ ls -al /usr/share/X11/xkb/compiled/
total 12
drwxr-xr-x 2 root root 4096 Aug 16 18:28 .
drwxr-xr-x 3 root root 4096 Jun 20 20:54 ..
-rw-r--r-- 1 root root  644 Jun 25 03:57 README.compiled

```
And, that file said:
```

$ cat /usr/share/X11/xkb/compiled/README.compiled

The X server uses this directory to store the compiled version of the
current keymap and/or any scratch keymaps used by clients.  The X server
or some other tool might destroy or replace the files in this directory,
so it is not a safe place to store compiled keymaps for long periods of
time.  The default keymap for any server is usually stored in:
     X<num>-default.xkm
where <num> is the display number of the server in question, which makes
it possible for several servers *on the same host* to share the same
directory.

Unless the X server is modified, sharing this directory between servers on
different hosts could cause problems.

```
_So, there is a problem with that directory that causes problems._
[/LIST]
[LIST=2]
Second, you should check that you have a right direcotry for the XKB. In my case, and in you have a good/normal installation of XKB you should have a directory in /etc/X11/xkb. Now, all you have to do is:
```

$ cd /usr/share/X11/
$ mv xkb/ xkb.old
$ ln -s /etc/X11/xkb xkb

```
Restart X and voila \\:D/ 
[/LIST]
Hope this helped some people...

Enjoy,
Peter

---

### Post by foxy123 on 2006-08-17
> **theSeinfeld said:**
> Ok, I solved the XKB error/problem. It seems that it is a problem with the way the Xgl was compiled (as I suspected). Hence, here is the way to fix the:
```

$ setxkbmap
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Segmentation fault

```

[LIST=1] First, check out if your Xgl has the correct path to the compiled xkb directory. Type:
```

$ strings `which Xgl` |grep compiled
/usr/share/X11/xkb/compiled/
Couldn't open compiled keymap file %s

```
So, your XKB files are supposed to be compiled at this location, but, if you have Kubuntu like me, you will see that the directory contains:
```

$ ls -al /usr/share/X11/xkb/compiled/
total 12
drwxr-xr-x 2 root root 4096 Aug 16 18:28 .
drwxr-xr-x 3 root root 4096 Jun 20 20:54 ..
-rw-r--r-- 1 root root  644 Jun 25 03:57 README.compiled

```
And, that file said:
```

$ cat /usr/share/X11/xkb/compiled/README.compiled

The X server uses this directory to store the compiled version of the
current keymap and/or any scratch keymaps used by clients.  The X server
or some other tool might destroy or replace the files in this directory,
so it is not a safe place to store compiled keymaps for long periods of
time.  The default keymap for any server is usually stored in:
     X<num>-default.xkm
where <num> is the display number of the server in question, which makes
it possible for several servers *on the same host* to share the same
directory.

Unless the X server is modified, sharing this directory between servers on
different hosts could cause problems.

```
_So, there is a problem with that directory that causes problems._
[/LIST]
[LIST=2]
Second, you should check that you have a right direcotry for the XKB. In my case, and in you have a good/normal installation of XKB you should have a directory in /etc/X11/xkb. Now, all you have to do is:
```

$ cd /usr/share/X11/
$ mv xkb/ xkb.old
$ ln -s /etc/X11/xkb xkb

```
Restart X and voila \\:D/ 
[/LIST]
Hope this helped some people...

Enjoy,
Peter

Thanks a lot! You are great. It worked nicely for me.

---

### Post by blastus on 2006-08-17
I followed the guide and it does not work for me. How do I uninstall all this? 

My desktop is pretty much fried; all the windows are garbled and corrupted and much slower now. I cannot even open up a terminal to type in commands, when I go to open up a terminal it shows "Starting Terminal..." and then after a while it just disappears.

---

### Post by TheRingmaster on 2006-08-18
well my install went flawlessly and the effects are stunning. One question though, How do I change the top and bottom picture of the cube?

---

### Post by John.Michael.Kane on 2006-08-18
jpazindustries you can use gconf-editor or gset-compiz. gset-compiz is a little dated,however. it does work.

---

### Post by TheRingmaster on 2006-08-18
> **SD-Plissken said:**
> jpazindustries you can use gconf-editor or gset-compiz. gset-compiz is a little dated,however. it does work.
what do I do when I get there?

---

### Post by nonex on 2006-08-19
cgwd: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
 compiz.real: GLX_EXT_texture_from_pixmap is missing
 compiz.real: Failed to manage screen: 0
 compiz.real: No managable screens found on display :0.0
Edit/Delete Message

??????? no start xgl!!!](*,)

---

### Post by BoneyOne on 2006-08-19
Did exactly as outlined and not a single change after a restart of xserver.
Doubt it will help much but going to try to reboot.

Odd, though, no errors anywhere, just doesn't seem to load.

EDIT: After reboot the logon screen was out of place and colors all messed up. Logged in anyway, x crashed back to login. So now, I guess it's toast and yet another clean reload (it's easier than trying to do a hack job of uninstallation).

---

### Post by priceyza on 2006-08-19
Hi I followed this howto exactly. and everything went fine untill i rebooted and loged back in. My problem is that if i do anything that requires using the cpu alot or even a little, eg opening firfox, everything freezes and i cant do anything i have to reboot . My computer is an AMD 64 +3200, 1GB Ram, Nvidia Geforce 6200 (turbocache) 

If any body can help it would be greatly appreciated.

---

### Post by BoneyOne on 2006-08-19
Is this a problem with the Geforce 6200's? 
I also have a 6200 in mine. Could it be a driver issue?

---

### Post by John.Michael.Kane on 2006-08-19
Those who need help with thi howto: should try loging on IRC channel[COLOR="Red"]** #xgl**[/COLOR] make sure you detail your problem/s be ready to post any error msg script info. 

the reason i'm suggesting this is i'm not sure if Beamerboy checks this howto anymore.




[COLOR="Red"]**If you use these it's at your own risk these have not been tested on a 32bit setup**[/COLOR]
If you want you can try  using this this for loading Xgl
```
0=Xgl

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl -fullscreen -br -accel xv:fbo -accel glx:pbuffer
flexible=true
```

And this for loding compiz
```
#!/bin/sh 
compiz --replace gconf &
cgwd --replace & 
```

---

### Post by skyhopper88 on 2006-08-20
Nevermind...I'm retarded...

---

### Post by nonex on 2006-08-20
How to increase Scale, with included xgl? In nvidia X server setting there are no adjustments!

---

### Post by Blaxter on 2006-08-25
> X Error of failed request: BadLength (poly request too large or internal Xlib length error)
    Major opcode of failed request: 143 (XGL)
    Minor opcode of failed request: 1 (X_GLXRender)
    Serial number of failed request: 184
    Current serial number in output stream: 185
](*,) ](*,) I don't know what more try to do

I have a geforce mx440, I read at [http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#BadLength_.28poly_request_too_large_or_internal_Xlib_length_error.29_with_nvidia_mx440_.2F_FX_5200_.2F_FX_5700](http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#BadLength_.28poly_request_too_large_or_internal_Xlib_length_error.29_with_nvidia_mx440_.2F_FX_5200_.2F_FX_5700)
i should do something like that
```
LD_PRELOAD=/usr/lib/opengl/nvidia/lib/libGL.so Xgl :1 -ac -accel xv -accel glx:pbuffer &

```but i dunno where i should put it :-k

---

### Post by d3dsh33ps on 2006-08-25
great job..there were a lot of post, but yours cut out all the bull shit.
thanks again:KS

---

### Post by Beamerboy on 2006-08-26
> **SD-Plissken said:**
> Those who need help with thi howto: should try loging on IRC channel[COLOR="Red"]** #xgl**[/COLOR] make sure you detail your problem/s be ready to post any error msg script info. 

the reason i'm suggesting this is i'm not sure if Beamerboy checks this howto anymore.




[COLOR="Red"]**If you use these it's at your own risk these have not been tested on a 32bit setup**[/COLOR]
If you want you can try  using this this for loading Xgl
```
0=Xgl

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl -fullscreen -br -accel xv:fbo -accel glx:pbuffer
flexible=true
```

And this for loding compiz
```
#!/bin/sh 
compiz --replace gconf &
cgwd --replace & 
```

I do, I am just busy getting ready for college at the moment so I don't have a great deal of time.

---

### Post by Clark Nova on 2006-08-26
Having problems with getting the themes to change. 

I've got my drivers installed correctly and I followed the guide step by step  and restarted my system as the guide tells me to but when I restart I don't have any themes selected and the Themer app doesn't change them for me. I checked my xorg.conf file and everything is set to 24-bit colour depth as it should be.

Anything I might try? I'm scracting my head a bit[-o< 

S754 AMD 3200 64 (running on 32-bit installation)
Gefore 6200 fx
1024mb RAM

---

### Post by Dinerty on 2006-08-26
Just wanted to say thanks to Beamerboy troubleshooting section I now have a very sexy looking xgl/compiz config

Thank you mate

---

### Post by em3raldxiii on 2006-08-27
Any updates on fixing video overlay brightness?  Or just overall brightness/contrast?  So far, everything is still a little too dark and I can't seem to access any options to brighten it.

---

### Post by ekerazha on 2006-08-27
> **JoWilly said:**
> 
2. do not complicate things with a script. Just add:

"compiz --replace gconf" and "gnome-window-decorator" to the gnome session startup.

I agree.

---

### Post by JoWilly on 2006-08-27
> **ekerazha said:**
> I agree.

Yep.

Be aware that "gnome-window-decorator" was replaced by "cgwd".

---

### Post by ekerazha on 2006-08-27
> **JoWilly said:**
> Yep.

Be aware that "gnome-window-decorator" was replaced by "cgwd".
Yeah... if you use cgwd ;)

---

### Post by burnick on 2006-09-03
java applications (such as the cross-platform GroupWise client) will not draw their window contents, but will instead just show a blank gray window <- how do u fix this?

---

### Post by beetlejelly on 2006-09-04
Thanks! this worked great! :biggrin:

---

### Post by Coolit on 2006-09-07
Thanks for a great Howto :) worked great:D

But.....I just did an update as there is new packages released and it broke compiz:( XGL seems to be working fine, but no compiz effects and no window boarders.

Guess I'll need to wait for the next update (hope its soon!) as I only got 30min with it working lol.

EDIT:Just looked in "sessions" and there is a "?" next to compiz, so its not started, this confirms its just compiz thats broke I guess. I also tried starting compiz from the cmd line, no errors, but nothing happens, the cursor just sits blinking.

---

### Post by Coolit on 2006-09-07
The problem has been fixed by an update, its all working now :)

---

### Post by Beamerboy on 2006-09-12
Sorry folks, I am no longer supporting this HOWTO see the following thread for the reasons why:

[http://www.ubuntuforums.org/showthread.php?t=255908](http://www.ubuntuforums.org/showthread.php?t=255908)

---

### Post by nismoskys on 2006-09-13
i am sorry that you're leaving, but i'd just like to say THANK you SO MUCH. i just used ur guide to install xgl+compiz and this is my first time actually using it. it runs great and its so amazing. thanks again.

---

### Post by u01p2109 on 2006-12-15
&#1047;&#1072;&#1084;&#1077;&#1090;&#1100;&#1090;&#1077;, &#1074;&#1084;&#1077;&#1089;&#1090;&#1086; cgwd &#1074;&#1099;&#1073;&#1080;&#1088;&#1072;&#1077;&#1090;&#1089;&#1103; emerald

---

