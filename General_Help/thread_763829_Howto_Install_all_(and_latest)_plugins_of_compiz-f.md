---
title: "Howto: Install all (and latest) plugins of compiz-fusion"
date: 2008-04-23
forum: General Help
---

### Post by Martje_001 on 2008-04-23
[SIZE="5"]PROJECT ABANDONED! PLEASE LOOK [HERE]("http://ubuntuforums.org/showthread.php?p=4876658#post4876658") FOR THE NEW PROJECT![/SIZE]

[COLOR="Red"]!! This is installing the latest compiz-fusion which might be unstable !![/COLOR]

[COLOR="Red"]**!! After installing, run compiz with fusion-icon (in application-menu) !!**[/COLOR]

[COLOR="DarkOrange"]!! If this script doesn't work for you, try [this]("http://telperion.wordpress.com/2008/03/10/compizfusion-makefusion9-script-per-compilazione/") ([original page]("http://telperion.wordpress.com/2008/04/02/compizfusion-makefusion9-aggiornamento//")) !!
[/COLOR]
First you have to remove compiz and all dependencies:
```
sudo apt-get remove compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compizconfig-settings-manager libcompizconfig0 libdecoration0 compizconfig-settings-manager python-compizconfig emerald
```

Then get compiz-git:
```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git_0.1-2_all.deb
sudo gdebi compiz-git_0.1-2_all.deb
```
And run it:
```
sudo compiz-git --install
```

Result:
[IMG]http://www.xs4all.nl/~mgj1/images/compiz-git.png[/IMG][IMG]http://www.xs4all.nl/~mgj1/images/compiz-git1_thumbnail.png[/IMG]
[IMG]http://www.xs4all.nl/~mgj1/images/compiz-git2_thumbnail.png[/IMG][IMG]http://www.xs4all.nl/~mgj1/images/compiz-git3_thumbnail.png[/IMG]

For more info go here:
[http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

Enjoy!

---

### Post by durand on 2008-04-23
If anyone gets this:

```

>> scripts <<

 * Cloning scripts
Initialized empty Git repository in /usr/share/compiz-git/scripts/scripts/.git/
remote: Counting objects: 70, done.
Receiving objects: 100% (70/70), 10.80 KiB, done.
remote: Compressing objects: 100% (66/66), done.
remote: Total 70 (delta 23), reused 0 (delta 0)
Resolving deltas: 100% (23/23), done.
 -> git-compiz script updated...Restart required!

```
....just run the script again... I got a bit confused at that point :D

It should take about 15 minutes to compile.

Nice howto btw! Hoping this works.

---

### Post by Martje_001 on 2008-04-23
Shouldn't take too long on a Dual Core ;). Thank you for trying it, let me know if you run into any trouble!

---

### Post by durand on 2008-04-23
It doesn't :). That script worked perfectly! Are there any release notes anywhere? I'm not sure how get the second picture with the expose or whatever it's called.

---

### Post by Martje_001 on 2008-04-23
That's expo. Super + E.

It's all in the compiz-manager (in your menu, under preferences).

---

### Post by durand on 2008-04-23
Thanks for pointing me in the right direction. I was looking for the Viewport Distance option to separate the different desktops.

---

### Post by techno-mole on 2008-04-23
im about to try this out, but before i do my i suggest that before you remove compiz etc etc that you run something like metacity --replace.
cheers.

---

### Post by durand on 2008-04-23
Shouldn't need to. Linux would store compiz in RAM so it will still work when you delete it.

---

### Post by Martje_001 on 2008-04-23
Durand is right. However, if you activate a new plugin or disable one, I believe compiz will crash (but that shouldn't be a big problem).

---

### Post by techno-mole on 2008-04-23
in my experience its always best to have a window manager to fall back on if what you are trying to do doesnt work.
which luckily for me is a good thing seeing as im now about to try this for a second time as something must have gone wrong the first time, no compiz ? as in not installed ?
hey its all good fun though :)

---

### Post by Martje_001 on 2008-04-23
If it still doesn't work after trying a few times; delete /usr/share/compiz-git and run it again.

---

### Post by techno-mole on 2008-04-23
its working :) cheers (dont know why it didnt work the first time)

a couple of questions (which may sound daft) all the icons in ccsm (eg the lamp for the animation plugin) are grey ? i take it this is because its the latest version ? (or did i do something wrong again :-))
the other thing is the photo wheel isnt there ? again i take it this is because it isnt in this version ?
(you wouldnt happen to know how i could install the photo wheel plugin )
cheers again.

Ignore the photo wheel bit, ive just installed it, cheers for the guide, out of all the compiz from git how too's this one has been the most effective and the easiest.
cheers.
PS - if any one wants to know how to install any plugins that arent installed with this method have a look at this - 

[http://forum.compiz-fusion.org/showthread.php?t=7895](http://forum.compiz-fusion.org/showthread.php?t=7895)

by the way im running the rc of hardy (downloaded and installed yesterday) and the method in the link i posted worked for me.

---

### Post by Martje_001 on 2008-04-23
The photowheel isn't there because it is unsupported. Tomorrow I'll show you how to install anything from the *git repo(1)*.
It is very strange that everything is grey, can you send me a screenshot?

(1) [http://gitweb.compiz-fusion.org/](http://gitweb.compiz-fusion.org/)

---

### Post by Het Irv on 2008-04-23
I followed your How-to,and after I restarted I only have one desktop and all of my windows open so that I cannot see the Title bar.  Any suggestions?

Everything looks like it is setup the same as it was before.

```
hetirv@hetirv-laptop:~$ compiz
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
hetirv@hetirv-laptop:~$ 
```

---

### Post by techno-mole on 2008-04-23
ive installed the photowheel, although it doesnt work (may not work with this version) not to worry, i did think it was a good thing, but it seems the person who built it hasnt done anything with it for a while, so it may not be around for long. it is cool though.
although not as cool as the cyclinder plugin, turning the cube into a cylinder is a good idea, looks good when you set the compiz screen saver of and running and let the gnome screen saver run on it.

anyway you should be able to see what i mean about the ccsm icons
cheers

---

### Post by blackvd on 2008-04-23
> **Het Irv said:**
> I followed your How-to,and after I restarted I only have one desktop and all of my windows open so that I cannot see the Title bar.  Any suggestions?

Everything looks like it is setup the same as it was before.

```
hetirv@hetirv-laptop:~$ compiz
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
hetirv@hetirv-laptop:~$ 
```

I'm having the same problem. Also I can't use alt+F2 to run a command now. Any clue to why this is happening?

---

### Post by sjprice on 2008-04-23
Yep, I just installed from the guide also and I have the same issues as the two previous posters. No title bar on the windows when using compiz as the window manager, using the Icon in the upper right, I can switch back to Metacity and get the title bars back.

Also, the icons are grey just like the pic above for mine also. I am also unable to switch themes in emerald when using that as the manager.

Any help?

---

### Post by sjprice on 2008-04-23
> **blackvd said:**
> I'm having the same problem. Also I can't use alt+F2 to run a command now. Any clue to why this is happening?

In the upper right hand of the desktop, you should have ht eCompiz Fusion Icon, If not start it from Applications >> System tools.

Right click the icon and switch the Window manager to Metacity. That is what worked for me.

---

### Post by blackvd on 2008-04-23
> **sjprice said:**
> In the upper right hand of the desktop, you should have ht eCompiz Fusion Icon, If not start it from Applications >> System tools.

Right click the icon and switch the Window manager to Metacity. That is what worked for me.

Thanks for the help I just ran metacity --replace to switch but now i have no compiz which is a bummer. Thinking maybe I should just uninstall this and reinstall the original packages.

---

### Post by blackvd on 2008-04-23
Awesome! Ok once I ran fusion-icon and changed window decorator to emerald everything works great! Only weird thing now is the ccsm with no icons.

---

### Post by sjprice on 2008-04-23
> **blackvd said:**
> Thanks for the help I just ran metacity --replace to switch but now i have no compiz which is a bummer. Thinking maybe I should just uninstall this and reinstall the original packages.

No problem, im about to head in that direction to go back to the original packages also.

---

### Post by mikeric on 2008-04-23
i ran everything twice and didnt get anything to work.

Im getting this error now to, if i try and update.
> You have 1 broken package on your system!

Use the "Broken" filter to locate it.

---

### Post by irunwithknives on 2008-04-23
When I try to install, after typing
```
sudo dpkg -i compiz-git_0.1-1_all.deb #Ignore errors
```
it says
```
irunwithknives@sh:~$ wget http://www.xs4all.nl/~mgj1/downloads/compiz-git_0.1-1_all.deb
--15:38:10--  http://www.xs4all.nl/~mgj1/downloads/compiz-git_0.1-1_all.deb
           => `compiz-git_0.1-1_all.deb.1'
Resolving www.xs4all.nl... 194.109.6.92
Connecting to www.xs4all.nl|194.109.6.92|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,558 (2.5K) [application/x-debian-package]

100%[====================================>] 2,558         --.--K/s             

15:38:10 (315.09 KB/s) - `compiz-git_0.1-1_all.deb.1' saved [2558/2558]

irunwithknives@sh:~$ sudo dpkg -i compiz-git_0.1-1_all.deb #Ignore errors
Selecting previously deselected package compiz-git.
(Reading database ... 105291 files and directories currently installed.)
Unpacking compiz-git (from compiz-git_0.1-1_all.deb) ...
dpkg: dependency problems prevent configuration of compiz-git:
 compiz-git depends on libx11-xcb-dev; however:
  Package libx11-xcb-dev is not installed.
dpkg: error processing compiz-git (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz-git
```

I don't know what to do... i cant figure out how to get libx11-xcb-dev, so any help would be wonderful!!!!

---

### Post by Aifel on 2008-04-23
> **irunwithknives said:**
> When I try to install, after typing
```
sudo dpkg -i compiz-git_0.1-1_all.deb #Ignore errors
```
it says
```
irunwithknives@sh:~$ wget http://www.xs4all.nl/~mgj1/downloads/compiz-git_0.1-1_all.deb
--15:38:10--  http://www.xs4all.nl/~mgj1/downloads/compiz-git_0.1-1_all.deb
           => `compiz-git_0.1-1_all.deb.1'
Resolving www.xs4all.nl... 194.109.6.92
Connecting to www.xs4all.nl|194.109.6.92|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,558 (2.5K) [application/x-debian-package]

100%[====================================>] 2,558         --.--K/s             

15:38:10 (315.09 KB/s) - `compiz-git_0.1-1_all.deb.1' saved [2558/2558]

irunwithknives@sh:~$ sudo dpkg -i compiz-git_0.1-1_all.deb #Ignore errors
Selecting previously deselected package compiz-git.
(Reading database ... 105291 files and directories currently installed.)
Unpacking compiz-git (from compiz-git_0.1-1_all.deb) ...
dpkg: dependency problems prevent configuration of compiz-git:
 compiz-git depends on libx11-xcb-dev; however:
  Package libx11-xcb-dev is not installed.
dpkg: error processing compiz-git (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz-git
```

I don't know what to do... i cant figure out how to get libx11-xcb-dev, so any help would be wonderful!!!!
I have the same problem. 
Turns out that the dependencies can't be resolved in 7.10. In Hardy however, they'll be easily available. So just wait a day for the upgrade.

---

### Post by pingpongboss on 2008-04-23
For everyone who can't get compiz to work from this script, check out this excellent script: [http://telperion.wordpress.com/2008/04/02/compizfusion-makefusion9-aggiornamento/](http://telperion.wordpress.com/2008/04/02/compizfusion-makefusion9-aggiornamento/)

I've been using it since Gutsy and it still works perfectly on Hardy. I like to experiment so I'm also taking a look at the OP's compiz-git script.

I also suggest the maker of compiz-git to take a look at that italian script since it does everything perfectly. Maybe take a few ideas and merge some code.

---

### Post by Aifel on 2008-04-23
> **pingpongboss said:**
> For everyone who can't get compiz to work from this script, check out this excellent script: [http://telperion.wordpress.com/2008/04/02/compizfusion-makefusion9-aggiornamento/](http://telperion.wordpress.com/2008/04/02/compizfusion-makefusion9-aggiornamento/)

I've been using it since Gutsy and it still works perfectly on Hardy. I like to experiment so I'm also taking a look at the OP's compiz-git script.

I also suggest the maker of compiz-git to take a look at that italian script since it does everything perfectly. Maybe take a few ideas and merge some code.
Thanks for the script.
Running it now, and will report back soon.
EDIT: It works! Thanks a lot pingpong.

---

### Post by justinhj on 2008-04-23
I'm getting 

> sudo dpkg -i compiz-git_0.1-1_all.deb #Ignore errors

(Reading database ... 131458 files and directories currently installed.)
Preparing to replace compiz-git 0.1-1 (using compiz-git_0.1-1_all.deb) ...
Unpacking replacement compiz-git ...
dpkg: dependency problems prevent configuration of compiz-git:
 compiz-git depends on libx11-xcb-dev; however:
  Package libx11-xcb-dev is not installed.
dpkg: error processing compiz-git (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz-git


And if I try to install libx11-xcb-dev I get 

Package libx11-xcb-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libx11-xcb-dev has no installation candidate

Maybe I need to add a source for it?

(uname -a 

 Linux ubuntu 2.6.22-14-generic  btw)

---

### Post by Martje_001 on 2008-04-24
Not sure if it's working, but here is the 'libx11-xcb-dev_2%3a1.1.3-1ubuntu2_i386' from hardy.

Or find it here:
[http://packages.ubuntu.com/search?keywords=libx11-xcb-dev&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libx11-xcb-dev&searchon=names&suite=all&section=all)

---

### Post by Martje_001 on 2008-04-24
> **pingpongboss said:**
> I also suggest the maker of compiz-git to take a look at that italian script since it does everything perfectly. Maybe take a few ideas and merge some code.
Can you give me the script? I don't understand the Italian language.

---

### Post by pingpongboss on 2008-04-24
> **Martje_001 said:**
> Can you give me the script? I don't understand the Italian language.

[http://www.mediafire.com/?2umcvycjtem](http://www.mediafire.com/?2umcvycjtem)

Should've linked to this page instead [http://telperion.wordpress.com/2008/03/10/compizfusion-makefusion9-script-per-compilazione/](http://telperion.wordpress.com/2008/03/10/compizfusion-makefusion9-script-per-compilazione/)

---

### Post by techno-mole on 2008-04-24
this may sound daft (ive probably installed it in the wrong way) but is the script posted by pingpongboss meant to create a shed load of folders in your home directory ?

---

### Post by josedb on 2008-04-24
i know this will sound funny buy i cannot uninstall the git version (i want to go back to older version)

---

### Post by techno-mole on 2008-04-24
never mind, i created a folder and put all the compiz related folders into it, everything still works.
both the methods in this thread worked well for me, so if you want the latest compiz and all the other stuff that comes with it, then try one of these out, easy and effective.

have you tried going to synaptic - so settings - administration - synaptic package manager, then serching for compiz ?
you should get a load of things with green boxes next to them, you can select anything compiz related and mark for removal.
or you could try running this in terminal -

sudo apt-get remove compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compizconfig-settings-manager libcompizconfig0 libdecoration0 compizconfig-settings-manager python-compizconfig emerald

just copy and paste it.

then re-boot your system.

---

### Post by Martje_001 on 2008-04-24
> **josedb said:**
> i know this will sound funny buy i cannot uninstall the git version (i want to go back to older version)
With my script?
```
sudo compiz-git --uninstall
```

---

### Post by techno-mole on 2008-04-24
ive just been messing with ccsm and i noticed that although using the makefusion9 script the photo wheel is installed, but wont function because for some reason not all the options are there, eg you cant set key bindings because the option isnt there,
ive tried re-installing that plugin and cant get it to work still, strange but true.

---

### Post by Het Irv on 2008-04-24
I had to uninstall the orginal script as well, I couldn't enable emerald, and my cube settings were not working.

---

### Post by justinhj on 2008-04-24
> **Martje_001 said:**
> Not sure if it's working, but here is the 'libx11-xcb-dev_2%3a1.1.3-1ubuntu2_i386' from hardy.

Or find it here:
[http://packages.ubuntu.com/search?keywords=libx11-xcb-dev&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libx11-xcb-dev&searchon=names&suite=all&section=all)

Thanks, I upgraded to Hardy and I see it now. I'll try this out again later today.

---

### Post by ricanelite on 2008-04-24
how can I have it run automatically so every time I either restart my computer I don't have to click on the Compiz-Fusion icon?

---

### Post by blackvd on 2008-04-24
Did anyone ever figure out the icon issue with ccsm? Not super important but still annoying.

---

### Post by sjprice on 2008-04-24
> **ricanelite said:**
> how can I have it run automatically so every time I either restart my computer I don't have to click on the Compiz-Fusion icon?

I did it by System>> Preferences>> Sessions>> +Add>> 
Name: Fusion-Icon 
Command: /usr/bin/fusion-icon

---

### Post by sjprice on 2008-04-24
> **blackvd said:**
> Did anyone ever figure out the icon issue with ccsm? Not super important but still annoying.

I finally got everything working by removing compiz-git, removing everything related to compiz in Synaptic, rebooting (an old Windows habit), adding compiz back in Synaptic, then running the script off of the Italian site posted above.

I now have all the icons in CCSM, Emerald works double clicking the theme to change, and I have Toolbars when using emerald, all of which did not work before.

---

### Post by benthegreat on 2008-04-24
The install worked fine, but I cant get compiz to do anything to my desktop. the icon comes up, and the settings menu works fine.

---

### Post by blackvd on 2008-04-24
> **sjprice said:**
> I finally got everything working by removing compiz-git, removing everything related to compiz in Synaptic, rebooting (an old Windows habit), adding compiz back in Synaptic, then running the script off of the Italian site posted above.

I now have all the icons in CCSM, Emerald works double clicking the theme to change, and I have Toolbars when using emerald, all of which did not work before.

Hm ...I don't want to have to do all over some icons since everything else works great. Must be looking in the wrong place for the icons? I don't know maybe I can find a solution somewhere.

---

### Post by DarkDancer on 2008-04-24
Hmmm, when Compiz is going, I don't get have any window borders and can't select a theme. If I go to terminal and type in emearld --replace, it just hangs there till I kill it. The cube works, but it's still a cube. what might I do? I've tried installing twice now.....

---

### Post by blackvd on 2008-04-24
This is really annoying emerald quit working on me again. So I'm trying to uninstall to try the Italian script but when I run ```
sudo compiz-git --uninstall
``` It just updates?


update: Ok screw it I deleted all things compiz on my system using mc and now I'm installing via the Italian script.

update: It works! For now and I have icons in ccsm. My advise: Avoid the first script!

---

### Post by Fireblend on 2008-04-24
Awesome, works perfectly except for the icons thing in CCSM, which is kinda annoying but I can live with, if anyone figures out a way to make them work do tell though. Thanks!

---

### Post by justinhj on 2008-04-25
I was having trouble getting this working. After the script there was just no compiz, no matter what I tried. 

Eventually I ran /usr/bin/fusion-icon and got an error, glxinfo not found. 

So I figured out you need to do 

sudo apt-get install mesa-utils

If you get the same problem as me that is.

---

### Post by Martje_001 on 2008-04-25
> **blackvd said:**
> This is really annoying emerald quit working on me again. So I'm trying to uninstall to try the Italian script but when I run ```
sudo compiz-git --uninstall
``` It just updates?
Fixed.

---

### Post by enixexpo on 2008-04-25
when I execute the command:

```
sudo compiz-git --install
```

It says:

> Please run this script with either "--install" or "--uninstall"

I've downloaded the Italian script, but not sure what to do with it. This is my first time using linux as I recently downloaded ubuntu 8.04.

What should I do?

---

### Post by pingpongboss on 2008-04-25
> **enixexpo said:**
> when I execute the command:

```
sudo compiz-git --install
```

It says:



I've downloaded the Italian script, but not sure what to do with it. This is my first time using linux as I recently downloaded ubuntu 8.04.

What should I do?

make a folder where you would like to store the source files. Move the script into that folder, and chmod +x it if it's not already executable. Then cd into that folder in a terminal. Run ./makefusion packages  and then  ./makefusion9 clone  and then  ./makefusion install

Keep the source folder.

Just google translate that italian site for more directions.

Edit: OP, i see that you've linked to that italian script in your original post. You probably want to also give a link to that site, so people know how to use the script. Or just make a small section yourself.

---

### Post by russo.mic on 2008-04-25
> **pingpongboss said:**
> make a folder where you would like to store the source files. Move the script into that folder, and chmod +x it if it's not already executable. Then cd into that folder in a terminal. Run ./makefusion packages  and then  ./makefusion9 clone  and then  ./makefusion install

Keep the source folder.

Just google translate that italian site for more directions.

Edit: OP, i see that you've linked to that italian script in your original post. You probably want to also give a link to that site, so people know how to use the script. Or just make a small section yourself.

The script in this post didn't work.  italian script worked first try.

Thanks Guys!

Russo

---

### Post by Martje_001 on 2008-04-25
> **enixexpo said:**
> when I execute the command:

```
sudo compiz-git --install
```

It says:



I've downloaded the Italian script, but not sure what to do with it. This is my first time using linux as I recently downloaded ubuntu 8.04.

What should I do?
Also fixed. 

Btw, the script is not mine. I only make it easy to execute the code and install dependencies.

---

### Post by Martje_001 on 2008-04-25
> **pingpongboss said:**
> Edit: OP, i see that you've linked to that italian script in your original post. You probably want to also give a link to that site, so people know how to use the script. Or just make a small section yourself.
Done ;)

I'm planning to make my own script to install compiz-fusion from git. Not a CLI fronted one, but a GUI.

---

### Post by Ub1476 on 2008-04-25
I noticed performance is much worse with Compiz git (75 frames s), is this normal? Also, every icon seems to be missing in ccsm.

---

### Post by enixexpo on 2008-04-25
> **pingpongboss said:**
> make a folder where you would like to store the source files. Move the script into that folder, and chmod +x it if it's not already executable. Then cd into that folder in a terminal. Run ./makefusion packages  and then  ./makefusion9 clone  and then  ./makefusion install

Keep the source folder.

Just google translate that italian site for more directions.

Edit: OP, i see that you've linked to that italian script in your original post. You probably want to also give a link to that site, so people know how to use the script. Or just make a small section yourself.

Thanks for the help! It worked great.

---

### Post by Smatt454 on 2008-04-25
Will this work for *Kubuntu *8.04?

---

### Post by blackvd on 2008-04-26
To update with the Italian script do I just rerun it? Cause I originally downloaded it to my desktop ran it and deleted everything. So can I just re download the script put it in a folder and rerun it to update? Little confused on this?

---

### Post by Martje_001 on 2008-04-26
> **blackvd said:**
> To update with the Italian script do I just rerun it? Cause I originally downloaded it to my desktop ran it and deleted everything. So can I just re download the script put it in a folder and rerun it to update? Little confused on this?
If it works with git, yes, it should update everything.

---

### Post by pingpongboss on 2008-04-26
> **blackvd said:**
> To update with the Italian script do I just rerun it? Cause I originally downloaded it to my desktop ran it and deleted everything. So can I just re download the script put it in a folder and rerun it to update? Little confused on this?

If you deleted the source files, you will have to rerun  ./makefusion9 clone   That command downloads/updates the source files.

Also, make sure that when you redownload the script you gedit it again to change the configuration options.

---

### Post by Vadi on 2008-04-26
Hm you should mention in instructions that you need to run the script twice.

---

### Post by andrebrait on 2008-04-26
this should be sticky

---

### Post by Vadi on 2008-04-26
This compiz is extremely laggy for some reason. Vanilla 8.04 one worked perfect, and this is an 8600gt with 169.12 drivers.

---

### Post by andrebrait on 2008-04-26
for some reason...

yeah, now you said, I noticed this

It's not good...

Anyway, how do I get other plugins?

---

### Post by Amranu on 2008-04-26
Uninstalling the first script doesn't seem to work at all for me, even though it says it does. The settings manager, emerald theme manager and icon etc it creates do not disappear, and everything on my system labeled compiz under synaptic is removed, yet for some reason activating effects under appearance still works (poorly)...

---

### Post by stathis21 on 2008-04-27
how do i uninstall this script???

---

### Post by Martje_001 on 2008-04-28
> **stathis21 said:**
> how do i uninstall this script???
```
sudo compiz-git --uninstall
sudo dpkg -r compiz-git
```

---

### Post by pingpongboss on 2008-04-28
The maker of the script should look into this post:

> this has a problem, it skips something if it is not updated, it should only do that for emerald, emerald-themes, and compiz, maybe bcop and ccsm, but it should never skip plugins, they won't be built against the newer compiz

you'll have to check what is relatively API independent, and add rules to skip those, or not skip any

Also, plugins-* builds against plugins-main, so there again, the others have to be rebuilt

Maybe this is the cause of all the missing icons in CCSM. Also, after updating today (using compiz-git --install), the widgets and buttons that you press to change keybindings no longer work. Plugins such as Cube Atlantis also stopped working. I believe this is due to what is described by the above quote.

Plugins that do not get updated should still be built after each update!

**Edit**: Also OP, you have a typo on your website download link. Version says 10-2 even though it's 1-2.

**Edit2**: Err... also, --uninstall is sort of broken. It not only gets rid of compiz (like it's supposed to) but also gets rid of the entire compiz-git program! Are you sure you want that? Isn't that what the DEB package is for? If I want to remove compiz-git, I will use apt-get remove compiz-git. Think about it.

**Edit3**: **--uninstall, reinstall DEB, --install** seems to have fixed the issue with plugins like Cube Atlantis not working. They work now. Icons in ccsm still do not show up. Widgets (trying to change keybindings and mousebindings) still do not work. Might be something to do with a recent commit that didn't go right. Errors when trying to change keybinding: ```
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/ccm/Settings.py", line 900, in RunKeySelector
    modifierSelector = ModifierSelector (currentMods)
  File "/usr/lib/python2.5/site-packages/ccm/Widgets.py", line 402, in __init__
    self._base_surface = cairo.ImageSurface.create_from_png (modifier)
cairo.Error: file not found
```

I may go back to the Italian script later to see if it has the same issues.

**Edit4**: Yup the issues seem to be only with the compiz-git script. Look below for more info. Going to be using the Italian script for now.

---

### Post by Vadi on 2008-04-28
I do hope someone can fix it up. We had a repository of latest compiz stuff for 7.04, but not 7.10 :(

---

### Post by pingpongboss on 2008-04-28
Alright, I've installed using the Italian script, and it does NOT remove the icons from CCSM and it does NOT have an error when changing keybindings/mousebindings. The problems many people face seem to be caused in part by the compiz-git script. I recommend that people using the Italian script found here for now: [http://telperion.wordpress.com/2008/03/10/compizfusion-makefusion9-script-per-compilazione/](http://telperion.wordpress.com/2008/03/10/compizfusion-makefusion9-script-per-compilazione/)

There has been 2 updates to the script since the last time I posted it. New file (v 9.017) is found here: [http://www.mediafire.com/?mzt3y2nsuxd](http://www.mediafire.com/?mzt3y2nsuxd)
OP, please update your links in your post.

---

### Post by bakersfield90 on 2008-04-28
```
--20:41:14--  http://www.xs4all.nl/~mgjl/downloads/compiz-git_0.1-2_all.deb
           => `compiz-git_0.1-2_all.deb'
Resolving www.xs4all.nl... 194.109.6.92
Connecting to www.xs4all.nl|194.109.6.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:41:14 ERROR 404: Not Found.
```

thats what i got.... help?

---

### Post by Shadius on 2008-04-28
I'm trying this right now. It's taking a while because my computer is not a dual core. I've got an old computer running Celeron. It seems to be working though. I got the same script that Durand had though. Will let you know if anything comes up.

---

### Post by alexsabree on 2008-04-28
very very very.. quick and easy

Thanks alot man :)

---

### Post by cipher_no1 on 2008-04-29
got this error when i did 
>  sudo dpkg -i compiz-git_0.1-2_all.deb #Ignore errors



Selecting previously deselected package compiz-git.
dpkg: regarding compiz-git_0.1-2_all.deb containing compiz-git:
 compiz-git conflicts with compiz-core
  compiz-core (version 1:0.7.4-0ubuntu6) is present and installed.
dpkg: error processing compiz-git_0.1-2_all.deb (--install):
 conflicting packages - not installing compiz-git
Errors were encountered while processing:
 compiz-git_0.1-2_all.deb

any sugestions am using hardy
thanx

---

### Post by Shadius on 2008-04-29
I tried to remove it, and did sudo apt-get install compizconfig-settings-manager, and it told me that some packages needed to removed so I removed them by following the prompts. However, I tried to install ccsm and it gave me this:

Setting up compizconfig-settings-manager (0.7.4-0ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing compizconfig-settings-manager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 compizconfig-settings-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)


Help, I'm new to Ubuntu! What does this mean? How do I fix this and get back Compiz Fusion the regular way!?

---

### Post by b3y0nd on 2008-04-29
The first method worked fine for me. I did have to manually install the dependencies, but once I did that everything seems to work fine. I am running 8.04 on an old ATI 9200 card.


You may have to note the dependencies and install those through synaptic. 

BTW... What are some of the default binding for the plugins for compiz ?

---

### Post by pingpongboss on 2008-04-29
> **bakersfield90 said:**
> ```
--20:41:14--  http://www.xs4all.nl/~mgjl/downloads/compiz-git_0.1-2_all.deb
           => `compiz-git_0.1-2_all.deb'
Resolving www.xs4all.nl... 194.109.6.92
Connecting to www.xs4all.nl|194.109.6.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:41:14 ERROR 404: Not Found.
```

thats what i got.... help?

Just download the file from this page [http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

> got this error when i did
Quote:
sudo dpkg -i compiz-git_0.1-2_all.deb #Ignore errors

Selecting previously deselected package compiz-git.
dpkg: regarding compiz-git_0.1-2_all.deb containing compiz-git:
compiz-git conflicts with compiz-core
compiz-core (version 1:0.7.4-0ubuntu6) is present and installed.
dpkg: error processing compiz-git_0.1-2_all.deb (--install):
conflicting packages - not installing compiz-git
Errors were encountered while processing:
compiz-git_0.1-2_all.deb

any sugestions am using hardy
thanx

Instead of installing it using dpkg, use ```
sudo gdebi compiz-git_0.1-2_all.deb
``` This will take care of the dependencies. The OP should update his guide.

Btw OP: your links to that italian site are broken. The script you link to is also outdated.

---

### Post by elonlon on 2008-04-29
I have problem look what it's say:
Failed to build plugins-main
->Abort? [Y/n]

I write Y it's OK?

---

### Post by Vadi on 2008-04-29
This thread is causing so many troubles...

---

### Post by Het Irv on 2008-04-29
I did a fresh install of 8.04 and I am waiting for all the bugs in this script to be worked out, or some more information on the Italian script to be shown.  I have a backup point that I can restore to, but I didn't like the way it when the first time I ran the OP's script.

---

### Post by Twitch6000 on 2008-04-29
Well this worked for me even though I denied to try it lol.
I still want to get the effects the other ways for hardy though.

---

### Post by ProfKaramba on 2008-04-29
When I choose Compiz as window manager I have effects but can't use the windows... The inside doesn't work.
My graphic card is an ATI, what can I do?

---

### Post by Shadius on 2008-04-29
I'm so frustrated with this. I removed the script and now I can't even get ccsm from the terminal. Hellllllllllllllpppp!!!

---

### Post by Twitch6000 on 2008-04-30
hey I am wondering how to get this to run on start up?Also I ran into a bug after restarting into ubuntu everything was wacked,It wouldn't let me use it and my windows were all wierd :(.

---

### Post by techno-mole on 2008-05-01
hello again.

i recently broke my system (not by messing with compiz) so i re-installed hardy, all went well.
now im trying to install compiz from git again, i tried the first method a while ago, so this time i thought id try the italian script (i have already tried this and found it worked) anyway so i run the script (the latest version of the script) but it does nothing, wont install compiz.
it clones git fine but when it comes to running the makefusion9 install part it runs and just towards the end of the process it throws out a couple of errors and says compiz not installed.
any ideas ?

---

### Post by Martje_001 on 2008-05-01
> I have problem look what it's say:
Failed to build plugins-main
->Abort? [Y/n]

I write Y it's OK?
Yes, that's ok

> This thread is causing so many troubles...
Yes it is..

> I did a fresh install of 8.04 and I am waiting for all the bugs in this script to be worked out, or some more information on the Italian script to be shown. I have a backup point that I can restore to, but I didn't like the way it when the first time I ran the OP's script.
Going to re-write it all

> When I choose Compiz as window manager I have effects but can't use the windows... The inside doesn't work.
My graphic card is an ATI, what can I do?
Run fusion-icon

> I'm so frustrated with this. I removed the script and now I can't even get ccsm from the terminal. Hellllllllllllllpppp!!!
```
sudo compiz-git --uninstall
sudo apt-get remove compiz-git
sudo apt-get autoremove
```

> hey I am wondering how to get this to run on start up?Also I ran into a bug after restarting into ubuntu everything was wacked,It wouldn't let me use it and my windows were all wierd .
Do you use fusion-icon?

---

### Post by Martje_001 on 2008-05-01
> **pingpongboss said:**
> Instead of installing it using dpkg, use ```
sudo gdebi compiz-git_0.1-2_all.deb
``` This will take care of the dependencies. The OP should update his guide.

Btw OP: your links to that italian site are broken. The script you link to is also outdated.
Both are fixed now. Thank you for answering some questions. I was very busy last week.

---

### Post by techno-mole on 2008-05-01
okay got it working now, although i couldnt get the italian scritp to work, just wouldnt play the game, so i decided to try the original method (first post by Martje_001) which (as it did the first time) worked perfectly, it didnt install all the things the italian script did (its easy enough to install them though, extra plugins)

i dont understand why the italian script didnt work this time round.

i would also like to point out (dont know if this has been fixed) but when i opened ccsm all the icon appear as they should eg - they arent little grey box type icons ? so all is well, im off to see if i can get the photo wheel plugin to work, i know its not that fancy, but i like it :-)

---

### Post by Martje_001 on 2008-05-01
Glad it worked!

---

### Post by ProfKaramba on 2008-05-01
> **Martje_001 said:**
> 

Run fusion-icon



Hi

Thanks for your help. But that happens when I'm using ccsm! I just switch from metacity to compiz and the inside of windows never work anymore until I go back to metacity... any hint?

---

### Post by Martje_001 on 2008-05-01
> **Vadi said:**
> Hm you should mention in instructions that you need to run the script twice.
No, that's not alway the case..

---

### Post by Martje_001 on 2008-05-01
> **ProfKaramba said:**
> Hi

Thanks for your help. But that happens when I'm using ccsm! I just switch from metacity to compiz and the inside of windows never work anymore until I go back to metacity... any hint?
Strange, do you have borders? Does it grey out? Can you make a screenshot?

---

### Post by Fenris_rising on 2008-05-01
good tut its compiling even as i type. i love linux!
you can tell im a newby cant you :lolflag: brilliant OS
so much nicer than XP and owt M$ learning curves a little steep
but hey no pain no gain.

ok had the greyed out icons in the compiz manager  ho hum so i went to the italian
site as refered to i have down loaded the makefusion9-017.tar.gz. from that point im lost i have looked at the translated instructions but its all flying over my head slightly. anyone care to hold my hand and help me through please.i have uninstalled the compiz stuff ready to try again.

regards

Fenris

---

### Post by ProfKaramba on 2008-05-01
> **Martje_001 said:**
> Strange, do you have borders? Does it grey out? Can you make a screenshot?

The windows that were already opened (like firefox in this case) I can see the inside but can't click or do anything, the new windows that I open after change to compiz, stay blank (like terminal in this case)

Is a problem with drivers or what? :\

[[IMG]http://img363.imageshack.us/img363/7858/screenshotdl6.th.png[/IMG]](http://img363.imageshack.us/my.php?image=screenshotdl6.png)

---

### Post by Martje_001 on 2008-05-01
> **ProfKaramba said:**
> Is a problem with drivers or what? :\

[[IMG]http://img363.imageshack.us/img363/7858/screenshotdl6.th.png[/IMG]](http://img363.imageshack.us/my.php?image=screenshotdl6.png)
I think so. Please try the Italian script to see if that works.

---

### Post by ProfKaramba on 2008-05-01
how do I run it? Sorry I'm a noob

---

### Post by pingpongboss on 2008-05-01
For those people who are having trouble with the Italian script, have you tried running ```
./makefusion9 packages
``` to install dependencies?

Also keep in mind that you have to edit the script before executing it. If you're on ubuntu-hardy, make sure the repo you download from is "master" not master-noxcb.

---

### Post by Fenris_rising on 2008-05-02
oh bugger! your kidding. oh well thats on the back burner for now.

regards

Fenris

---

### Post by squidmaster on 2008-05-02
yeah man, not having emerald work when I upgrded to 8.04 was REALLY getting annoying haha.

---

### Post by ProfKaramba on 2008-05-02
After running the italian script the problem is still here...

Probably is something with the drivers.. I have a ATI X1400 mobile...

any ideas?

---

### Post by 565Customz on 2008-05-02
mine seems to get to the 

    *compiling new version

and then it stops, been sitting here for bout 20 minutes. is that normal?

---

### Post by Het Irv on 2008-05-02
Depending on your processor, yes it could be.  If you have an older computer it will take longer.

---

### Post by 5735guy on 2008-05-04
MANY MANY Thanks for this. Quite Simply AWESOME :):):guitar::):)

---

### Post by Martje_001 on 2008-05-04
> **5735guy said:**
> MANY MANY Thanks for this. Quite Simply AWESOME :):):guitar::):)
Make sure you use the new script!

[http://ubuntuforums.org/showthread.php?p=4876658#post4876658](http://ubuntuforums.org/showthread.php?p=4876658#post4876658)

---

### Post by zain7478 on 2008-05-04
hi,
i tried your scripts and it works fine!
thanks 
but... it took me more than 1 hour!!!
i almost gave up...
thanks.

---

### Post by Martje_001 on 2008-05-04
Haha, never give up I always say ;)

---

### Post by TrusigheR on 2008-05-05
I used this script when I first installed 8.04 a few weeks ago, then I decided to do a fresh install and I used your newer script to install compiz from git. Your new script didn't work at all for me, it kept giving me errors, fusion-icon wouldn't work, it said compiz wasn't installed when it was installed, I had so many problems with the new script you made. I decided to try out this old script, and it works just fine. No errors when trying to install, nothing. It worked right off the bat. I hope you don't remove this script for that newer one until you get that one working.

---

### Post by rated_emman on 2008-06-18
HI GUYS! before i try to install this, i have the advanced desktop settings with desktop cubes wobbly windows and stuff.. when i installed this, those are all gone WAHHHHH! :(

how do i put it back? when i go to system>perf>... there's none saying advanced desktop settings like before with the desktop cubes and everything! :( helpp plzzz..
im using hardy heron 8.04... plzz how do i put it back? :-s


thanks

---

### Post by talsemgeest on 2008-06-18
Kiba dock has nothing to do with the compiz effects, so I cant see how it got rid of it. Just go to synaptic, search for ccsm and reinstall it.

---

