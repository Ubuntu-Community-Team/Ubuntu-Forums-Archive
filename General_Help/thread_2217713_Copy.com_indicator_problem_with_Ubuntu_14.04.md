---
title: "Copy.com indicator problem with Ubuntu 14.04"
date: 2014-04-18
forum: General Help
---

### Post by uzumakifahim on 2014-04-18
I've just installed Ubuntu 14.04. As my default online storage, after installing Copy client on Ubuntu 14.04, the Copy indicator is not showing in the top panel. For this reason I'm unable to use Copy properly. It works perfectly on Ubuntu 12.04.

How can overcome this problem? I need solve this problem very quickly. 

Please help experts. Thanks in advance.

---

### Post by bapoumba on 2014-04-18
How did you install it ?
Please see here : [http://ubuntuforums.org/showthread.php?t=2215788&p=12989766#post12989766](http://ubuntuforums.org/showthread.php?t=2215788&p=12989766#post12989766)

---

### Post by uzumakifahim on 2014-04-18
Thanks for your reply. 

I've installed Copy agent 1.43.0290 version.

I've installed Copy by the following steps:
1. At first I've copied the .tgz file in Downloads folder in my Home directory. 
2. Extract the .tgz file.
3. Enter into the copy folder and then x86 (my system is 32-bit)
4. Double-click the CopyAgent and the installation process starts and completed successfully
5. A folder named Copy has created in my home directory and my files started syncing immediately.

Only problem is that there is no indicator on the panel. :(

---

### Post by bapoumba on 2014-04-18
Here are the complete steps I used, the link is my previous quoted post. I fiddled around a bit to have it autostart on reboots.
[http://ubuntuforums.org/showthread.php?t=2217206&page=3&p=12989518#post12989518](http://ubuntuforums.org/showthread.php?t=2217206&page=3&p=12989518#post12989518)

You have to run the overlay process, and I proceeded as indicated, installing all the files in /opt/copy.

---

### Post by uzumakifahim on 2014-04-18
The commands giving the following outputs :

```
/opt/copy$ ./CopyAgent &
[1] 2511
fahim@fahim-G41-M7:/opt/copy$ QGtkStyle was unable to detect the current GTK+ theme.


```

What can I do now?

---

### Post by bapoumba on 2014-04-18
Which Ubuntu flavor are you running ?
Have you tried with a standard theme ?

---

### Post by uzumakifahim on 2014-04-18
I'm using the default theme of Ubuntu 14.04. Not even tried to change it. Please check the screenshots.

---

### Post by miki-michalko on 2014-04-18
Hello,
I have same problem.
I have tried to install  *sudo apt-get install libappindicator1*. After that I have copy agent, but just with sync icon (no other options).

---

### Post by bapoumba on 2014-04-18
I guess it has to do with unity, look down the first page and the second. There is a workaround with a ppa that I cannot test (lubuntu here).
[https://copy.zendesk.com/entries/28050018-Ubuntu-13-10-indicator-icon-?](https://copy.zendesk.com/entries/28050018-Ubuntu-13-10-indicator-icon-?)

---

### Post by uzumakifahim on 2014-04-18
Unfortunately, same problem continuing after the following the instructions in the link you given. Still showing no indicator, even after installing libappindicator1. :(

---

### Post by bapoumba on 2014-04-18
Which version do you have ?
```
Installed: 12.10.1+13.10.20130920-0ubuntu4
```

Running your error :
```
QGtkStyle was unable to detect the current GTK+ theme
```
brings up some bugs related to 13.03 such as this one : QGtkStyle was unable to detect the current GTK+ theme

---

### Post by uzumakifahim on 2014-04-18
So, this is a bug continuing from 13.10 :confused: . What can I do now? I really need Copy to work smoothly, espeacially in the absence of Ubuntu One.:(

---

### Post by bapoumba on 2014-04-19
I do not know what happened to the links in my previous post, I need to get used to the new Chromium and change my cope/pasting routines :)

Anyway, this one is related to vlc, but I guess it can apply here, there are a few workarounds that I cannot test as the icon and overlays are working here and I am not using unity :
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/1094360](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/1094360)

---

### Post by moteprime on 2014-04-19
I'm having the same problems as you.
There are two things wrong here.

One. The indicator not working are because copy put it in the Systray, a standardized panel thing that's used everywhere, but that Canonical figured they didn't like, so they removed it in 13.04 and it's been missing since. There are some fixes made for 13.03 and 13.10, but they are not yet updated for 14.04
[http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html](http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html)

Two. The gtk theme thing. The "QGtkStyle was unable to detect the current GTK+ theme" error you can get fixed by installing "libgnomeui-0".
After that i get a new error: "Gtk-Message: Failed to load module "canberra-gtk-module"", that one usually comes then i start copyagent, so i don't know if it's a problem. I tried some of all the goggled fixes installing bunches of gtk canberra stuff, but it does not make any difference.

My Agent are not running. And if i look in the /.copy/trace.txt file i can see that it exits with: "CopyAgent::YCopyMain:Application finished executing".
It looks like it cannot find a folder under user a Jenkins, which does not exist.
I attached the trace file. 

The weird thing is that the copy agent worked absolutely fine in the Trusty beta (Dev) versions of 14.04

---

### Post by bapoumba on 2014-04-19
```
19/04/2014 08:58:49 0x00000000b461b740 CopyAgent::YCopyApp:OS type 'lin' version 0
19/04/2014 08:58:49 0x00000000b461b740 YAgentSyncInstance:Setting root path to '/home/bapoumba_lxde/Copy'
19/04/2014 08:58:49 0x00000000b461b740 YAgentSyncInstance:Root path is set to '/home/bapoumba_lxde/Copy'
19/04/2014 08:58:52 0x00000000a21ecb40 YAgentSyncInstance:Not adding already cached root '/home/bapoumba_lxde/Copy'
19/04/2014 08:58:52 0x00000000a21ecb40 YAgentSyncInstance:Setting root path user id '/home/bapoumba_lxde/Copy' 11071453
19/04/2014 08:58:52 0x00000000a21ecb40 YAgentSyncInstance:Database version '1.43.0319' is compatible with min version '0.7.0000'
```

This is what I have that differs from yours. Above the first line here, similar trace.
Not sure why it is looking for a user that does not exist. Did you upgrade your 14.04 install to go to the final release or did you fresh install over ?
Has the Jenkins user ever existed on your machine ? Is the copy website correct when you log in from a browser ?

Quite weird. Have you tried installing copy again ?

---

### Post by moteprime on 2014-04-19
I made i clear installation of 14.04 (64bit), and just downloaded the latest copyagent from copy. ran the copy agent, and got the "QGtkStyle" error. installed "libgnomeui-0" and got the canberra error instead. then i installed all kinds of gtk and canberry files according to every solution i could find on the net. none worked. But i have seen the canberra error before, and have had no problem with it. (it was in trusty beta to)
because of all the crap i installed, i did a clear installation once more, and are kinda stuck now.

Edit. No Jenkins ever.

---

### Post by bapoumba on 2014-04-19
Not sure why it is not looking at the proper /home/user..

When I first installed it, I used [http://ubuntuforums.org/showthread.php?t=2217206&page=3&p=12989518#post12989518](http://ubuntuforums.org/showthread.php?t=2217206&page=3&p=12989518#post12989518)
I do not recall what I messed up but I decided to erase all the files (except the tar file) and start over as there was no uninstall procedure I could see. I guess you could give that a shot. It has to point at your /home/user.

---

### Post by moteprime on 2014-04-19
Well. Except for the right-click function of the indicator, it seems to work now.
I just moved the contents of the x86_64 dir to /opt/copy and ran the agent from there. It started up, i could login and it even put in an entry in startup apps that point to /opt/copy/CopyAgent
I still gives me the "Gtk-Message: Failed to load module "canberra-gtk-module", but doesn't seem to matter

From system monitor i can see the agent using cpu, and i have a about 2 2mbit/s download.

---

### Post by bapoumba on 2014-04-19
Well, I guess that sounds good :)

---

### Post by uzumakifahim on 2014-04-19
> **moteprime said:**
> Well. Except for the right-click function of the indicator, it seems to work now.
I just moved the contents of the x86_64 dir to /opt/copy and ran the agent from there. It started up, i could login and it even put in an entry in startup apps that point to /opt/copy/CopyAgent
I still gives me the "Gtk-Message: Failed to load module "canberra-gtk-module", but doesn't seem to matter

From system monitor i can see the agent using cpu, and i have a about 2 2mbit/s download.


Almost same thing here. Copy is also working fine except the indicator with it's menu. As the menu is not showing, I'm unable to "pause syncing" option. I've tried with Dropbox and Skype, indicator of these two application are working just fine.

I've made a support ticket at Copy.com, waiting for their official reply.:(

---

### Post by bapoumba on 2014-04-20
> **uzumakifahim said:**
> Almost same thing here. Copy is also working fine except the indicator with it's menu. As the menu is not showing, I'm unable to "pause syncing" option. I've tried with Dropbox and Skype, indicator of these two application are working just fine.

I've made a support ticket at Copy.com, waiting for their official reply.:(

Is the support ticket public so that others can +1 or upvote or whatever if the option is available ?

---

### Post by uzumakifahim on 2014-04-20
I've just posted regarding this problem in the community forum and this public. The link is : [https://copy.zendesk.com/entries/54819558-Why-Copy-indicator-is-missing-on-Ubuntu-14-04-](https://copy.zendesk.com/entries/54819558-Why-Copy-indicator-is-missing-on-Ubuntu-14-04-)

I hope many people will vote this post to get their attention. Unfortunately, I've contacted with Copy.com official support but they haven't responded yet.

---

### Post by bapoumba on 2014-04-21
I've added a link to this thread. I had to try 3 times before I got the captcha correct :)

---

### Post by mgmiller on 2014-04-21
I have voted up the thread at copy.com and also left a message explaining the importance of supporting Ubuntu 14.04 properly.

---

### Post by bapoumba on 2014-04-21
Hopefully, with the new release and the new Ubuntu users coming for a solution after Ubuntu One drops off will help get attention.

---

### Post by pr-nizar on 2014-04-30
Hi guys! I had the same problems as you and wanted to share the updates with you; I still have problems but I think we're close to a fix.
I have a Ubuntu 14.04 x86_64 with Unity desktop.
To install CopyAgent:
- I downloaded it from [copy.com]("https://copy.com/install/linux/Copy.tgz")
- I extracted it to /opt/copy
- I even made a /usr/share/applications/copy.desktop shortcut
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=CopyAgent
Icon=/opt/copy/logo.png
Exec=/opt/copy/x86_64/CopyAgent
Comment=Sync your files across computers and to the web
Categories=Network;FileTransfer;
Terminal=false
StartupNotify=false
GenericName=File Synchronizer
```
[CENTER](from here the [logo.png file]("https://lh6.googleusercontent.com/-KbChyLdIAzM/U2D8vNZBEwI/AAAAAAAACDs/t1lPrumNFj0/logo.png"))[/CENTER]

- The CopyAgent launched and was actually syncing but without an indicator
- I installed libappindicator1 and libcanberra-gtk-module (some dependencies?!)
```
sudo apt-get install libappindicator1 libcanberra-gtk-module
```
- I made an .icons folder in my home
```
mkdir -p ~/.icons
```
[center](CopyAgent created some icons on that folder. For the menu?!)[/center]

After doing all of that the indicator is showing but the menu is still messed up: some menu items are showing while others are not!

[CENTER][IMG]http://i.stack.imgur.com/eAJgc.png[/IMG][/CENTER]

I've already opened a thread in [askubuntu]("http://askubuntu.com/questions/449331/how-to-get-copy-com-notification-icon-on-unity-on-trusty-to-work?noredirect=1#comment602196_449331") and a guy is presenting what seems to be [a fix for 32bits systems]("http://askubuntu.com/questions/457675/the-indicator-icon-of-copy-com-disappeared-or-the-menu-is-unreadable/457680#457680") that doesn't work with 64bits systems (my case).

Any suggestions?

---

### Post by bapoumba on 2014-04-30
I have this in /home/bapoumba/.config/autostart/CopyAgent, but this is lubuntu 32-bits and the menu is working :
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
StartupNotify=false
GenericName=File Synchronizer
Categories=Network;FileTransfer;
Exec=/opt/copy/CopyAgent
Icon=/home/bapoumba/.icons/copy-root_folder.png
Name=CopyAgent
Comment=Sync files across computers, mobile devices, and to the web
X-GNOME-Autostart-enabled=true

```

---

### Post by emersonebfreire on 2014-05-06
Hello guys,

The link below solved my problem with indicator icon of Copy:

[http://askubuntu.com/questions/457675/the-indicator-icon-of-copy-com-disappeared-or-the-menu-is-unreadable](http://askubuntu.com/questions/457675/the-indicator-icon-of-copy-com-disappeared-or-the-menu-is-unreadable)

Hope this helps.

---

### Post by mgmiller on 2014-05-07
> **emersonebfreire said:**
> Hello guys,

The link below solved my problem with indicator icon of Copy:

[http://askubuntu.com/questions/457675/the-indicator-icon-of-copy-com-disappeared-or-the-menu-is-unreadable](http://askubuntu.com/questions/457675/the-indicator-icon-of-copy-com-disappeared-or-the-menu-is-unreadable)

Hope this helps.

Have you had any other indicator problems since using the ppa?  For example, is your printer indicator still working?  I have read that the gurqn ppa prevents the printing indicator and others from appearing.

One work around I have been experimenting with in 14.04 unity in a virtual machine is just... *sudo apt-get install libappindicator1.  Then I create a .icons folder in home and finally, open the folder where the copy exectable is in terminal and enter the command... *./CopyAgent &     This will put an icon in the launcher.  Right click the icon and click to lock it to the launcher.  Left clicking this icon will bring up the main copy interface.  To pause syncing, just click log out.  To restart it, enter your username and password and click to log in again.  It's not as elegant as the gurqn ppa, but it's less intrusive on the system and you don't install an untrusted ppa that could break something else.  Since the U1 icon is no longer in the launcher, the copy icon simply replaces it.

---

### Post by Chris_Burrell on 2014-05-09
Well, I just came up with a work-around that also seems to have fixed it for me.

I'm running 14.04, upgraded from 13.10. I've tried most of the fixes described in this thread without success.

This morning I installed Kubuntu Desktop, and when I logged in to KDE, the menu worked. I was able to alter my preferences (which was my aim all along) to chance which folders were being synced.

I've now logged out of KDE and back into Unity, and amazingly, the menu is now working for me.

HTH,

C

---

### Post by etibasset on 2014-05-25
I have the same problem. I noticed that runnung the CopyAgent as root (kdesudo), solves it (even it is probably not recommended to run it as root).

---

### Post by benrboone on 2014-06-04
this worked for me on a 64 bit install of 14.04 upgrade from 13.10

it also worked for me on my laptop which was a clean install of 14.04 64 bit

This the first time I have had the menu working in over a year


step1:


so the proper way to get your (a) copy icon back is to first install this ppa 
sudo apt-add-repository ppa:gurqn/systray-trusty
sudo apt-get update
sudo apt-get upgrade

 


step2:

kill the copy agent ( i use system monitor to do so)

step3:  install sqlite to modify copy  agent datatbase (if the update doesn't work there is a line to return it to its previous settings later on)

 sudo apt-get install sqlite3


cd $HOME/.copy


echo 'UPDATE config2 SET value=0 WHERE option="csmBlackWhiteIconsV2" ;' | sqlite3 config.db  

(more details here:

[http://askubuntu.com/questions/457675/the-indicator-icon-of-copy-co](http://askubuntu.com/questions/457675/the-indicator-icon-of-copy-co)...)

after restarting copyagent and or logging out and logging in, it is fixed)

(to undo any change if it fails for you

echo 'UPDATE config2 SET value=1 WHERE option="csmBlackWhiteIconsV2" ;' | sqlite3 config.db)

---

### Post by mc4man on 2014-06-06
I had moved to copy as a replacement for ubuntuone in 14.04 & saw no issues getting a working menu (ubuntu session
Likely that is because my unity install had the systray enabled prior to copy being installed so no other commands, edits were needed
(I maintain a 14.04 build here that's slightly advanced from others, this has 14.10 updates & a fix for unity launcher pips
[https://launchpad.net/~mc3man/+archive/systray-white](https://launchpad.net/~mc3man/+archive/systray-white)

Just to note - 
copy is a qt4 app, usually qt4 apps get indicator support thru sni-qt which may work ok (smplayer), or not very well (vlc).  In the case of copy it doesn't seem to work with sni-qt or if it does,  it does so poorly. The systray icon for copy does work well.
(smplayer & vlc both support the systray though it can only be had if the sni-qt package is removed.

The only little issue in unity/ambiance is the menu is wrong color, (white), & wrong highlighted background (blue
The menu can be adjusted thru qt4-qtconfig  though that app can be extremely  frustrating to use & any changes should be checked against any other qt4 app for suitability.
(- simply switching gui style from Desktop settings to GTK+ will give proper  highlighted background color, any other changes need to be done via "Tune Palette" . The cleanlooks style isn't that bad either.

Have come close here to getting a better looking menu but as mentioned  qt4-qtconfig is a pita to use. If inclined I'd back up ~/.copy first & keep in mind every time you open qt4-qtconfig it may return some values to default

Would love to find where qtconfig settings changes are saved but haven't as of yet..

---

### Post by 3v1n0 on 2014-06-06
I've debugged this issue a little, and it's not actually a copy bug.
But a libdbusmenu issue, that might happen also with other indicators (see [bug #1086563]("https://bugs.launchpad.net/libdbusmenu/+bug/1086563"))

If you're *brave enough* you might want to try the fix by compiling by yourself [my libdbusmenu]("https://code.launchpad.net/~3v1n0/libdbusmenu/really-recreate-menu/+merge/222419") (using the --with-gtk=2 configure flag, if you need it only for copy)

Quick instructions, that will fix your CopyAgent:
```

bzr branch lp:~3v1n0/libdbusmenu/really-recreate-menu libdbusmenu
cd libdbusmenu
sudo apt-get build-dep libdbusmenu-gtk4
./autogen.sh --with-gtk=2
make install DESTDIR=$PWD/install
sudo cp install/usr/local/lib/libdbusmenu-gtk.so.* $SAME_DIRECTORY_WHERE_YOUR_CopyAgent_IS

```

---

### Post by mc4man on 2014-06-06
> **3v1n0 said:**
> I've debugged this issue a little, and it's not actually a copy bug.
But a libdbusmenu issue, that might happen also with other indicators (see [bug #1086563]("https://bugs.launchpad.net/libdbusmenu/+bug/1086563"))

If you're *brave enough* you might want to try the fix by compiling by yourself [my libdbusmenu]("https://code.launchpad.net/~3v1n0/libdbusmenu/really-recreate-menu/+merge/222419") (using the --with-gtk=2 configure flag, if you need it only for copy)

Quick instructions, that will fix your CopyAgent:
```

bzr branch lp:~3v1n0/libdbusmenu/really-recreate-menu libdbusmenu
cd libdbusmenu
sudo apt-get build-dep libdbusmenu-gtk4
./autogen.sh --with-gtk=2
make install DESTDIR=$PWD/install
sudo cp install/usr/local/lib/libdbusmenu-gtk.so.* $SAME_DIRECTORY_WHERE_YOUR_CopyAgent_IS

```
Thanks Marco  - that works quite well, proper colors & all
(gather it doesn't use sni-qt as I don't have it installed for better vlc icon

(- for user that just have extracted copy in Home folder no need to use sudo to cp

---

### Post by mc4man on 2014-06-06
> **AleveSicofante said:**
> ```
prompt:~$ cd libdbusmenu
pablo@T400:~/libdbusmenu$ sudo apt-get build-dep libdbusmenu-gtk4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
** E: You must put some 'source' URIs in your sources.list**
prompt:~/libdbusmenu$
```
I usually don't have any source repositories. Which should I put in my sources.list file in order to install build-dep or libdbusmenu-gtk4?

Open up Software & Updates & check the "Source code" box (it may then show a line or checkmark, doesn't matter

---

### Post by ohremd on 2014-06-07
This is great, thank you! And now a _**stupid**_ question. 

How exactly does the last command have to look like: "[COLOR=#000000][FONT=Ubuntu Mono]sudo cp install/usr/local/lib/libdbusmenu-gtk.so.* $SAME_DIRECTORY_WHERE_YOUR_CopyAgent_IS"

[/FONT][/COLOR]Like this for example?: "[COLOR=#000000][FONT=Ubuntu Mono]sudo cp install/usr/local/lib/libdbusmenu-gtk.so.* /home/blablub/CopyClient/[/FONT][/COLOR]x86_64[COLOR=#000000][FONT=Ubuntu Mono]"[/FONT][/COLOR]

Thanks a lot!

---

### Post by AleveSicofante on 2014-06-07
My CopyAgent executable is in /opt/copy (I put it there). That was my "[COLOR=#000000][FONT=Ubuntu Mono]$SAME_DIRECTORY_WHERE_YOUR_CopyAgent_IS".

[/FONT][/COLOR] If you're not sure where your CopyAgent executable is, try finding it:[COLOR=#000000][FONT=Ubuntu Mono]

```
sudo find / -name CopyAgent
```


[/FONT][/COLOR]

---

### Post by ohremd on 2014-06-07
Works like a charm! Thank you! =d>

---

### Post by ancleessen4 on 2014-06-07
@3v1n0 
Worked for me on 64bit - thanks!

---

### Post by melitz on 2014-06-07
Worked for me too!!! Trusty 14.04 x32!! Thanks!!

---

### Post by opensas on 2014-06-07
Thanks a lot, it seems to work ok

could anybody please tell me now how to get rid of all of the build dependencies that where installed with apt-get build-dep???

thanks a lot

---

### Post by wn1ytw on 2014-06-07
worked on 1 laptop, 1 more to go...  THANKS!

---

### Post by zovalik on 2014-06-08
Not working for me. Clean install 14.04 64bit. Still no Copy in systray ;(

---

### Post by jaci87 on 2014-06-08
It works for me.

*Grazie 3v1n0* :)

---

### Post by moteprime on 2014-06-10
14.04 (64) Can't get it working either.

---

### Post by AleveSicofante on 2014-06-10
> **zovalik said:**
> Not working for me. Clean install 14.04 64bit. Still no Copy in systray ;(

> **moteprime said:**
> 14.04 (64) Can't get it working either.

Can you paste the output of the commands shown on your terminal?

---

### Post by zovalik on 2014-06-11
> **AleveSicofante said:**
> Can you paste the output of the commands shown on your terminal?

What commands do you mean? From [**[COLOR=#000000]@3v1n0[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841884") guide?

I will do next fresh install i try to do this one more time.

---

### Post by mc4man on 2014-06-11
A SRU  for  14.04 is in the works so updated libdbusmenu packages should be available shortly. (I've tested new packages on 14.04, work fine with copy
Otherwise take a look here [http://www.webupd8.org/2014/06/fix-copycom-indicator-menu-for-ubuntu.html](http://www.webupd8.org/2014/06/fix-copycom-indicator-menu-for-ubuntu.html)

---

### Post by zovalik on 2014-06-11
This is workaround for broken menu, correct? So it's not working for me becouse I don't have Copy icon in systray at all :/

---

### Post by AleveSicofante on 2014-06-11
> **zovalik said:**
> What commands do you mean? From [**[COLOR=#000000]@3v1n0[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841884") guide?

Yes. But there might be actually no need anymore. If you follow the link posted by Marco ([http://www.webupd8.org/2014/06/fix-copycom-indicator-menu-for-ubuntu.html](http://www.webupd8.org/2014/06/fix-copycom-indicator-menu-for-ubuntu.html)) you can find precompiled libraries. You might as well wait for the patched libraries to be put by him on the official Ubuntu repos.

You shouldn't need a fresh install. Ubuntu is not like Windows... ;-)

---

### Post by AleveSicofante on 2014-06-11
> **zovalik said:**
> This is workaround for broken menu, correct? So it's not working for me becouse I don't have Copy icon in systray at all :/

I suggest you delete whatever you have put in your system regarding Copy (including any startup application related to it), then install Copy from a new PPA: [http://www.webupd8.org/2014/06/install-copycom-client-in-ubuntu-or.html](http://www.webupd8.org/2014/06/install-copycom-client-in-ubuntu-or.html), then use the link I posted above to repair the broken libraries.

---

### Post by zovalik on 2014-06-11
I did fresh install anyway, it's testing machine so it's not problem ;)

Copy installed from PPA, still no Copy icon in systray.

---

### Post by AleveSicofante on 2014-06-11
> **zovalik said:**
> I did fresh install anyway, it's testing machine so it's not problem ;)

Copy installed from PPA, still no Copy icon in systray.

Did you actually launch CopyAgent?

---

### Post by zovalik on 2014-06-12
Yes, app is working, sync is ok. I'm not so stupid ;)

---

### Post by AleveSicofante on 2014-06-22
Copy has released a newer version of its client including the patched libraries, so I suggest you try it. Just remove completely your current Copy client installation and download the latest version from copy.com.

---

### Post by mgmiller on 2014-06-27
I just installed the newest version of the copy software direct from copy.com in a fresh install of 14.04 64 bit.  No hacks or modifications of any kind were needed.  It just works.  The panel indicator now functions exactly as it did in 12.04.  It may have taken them about a year, but in the end they got it right before 14.04.1 was released.  I will be upgrading my last 2 12.04 machines as soon as the point release rolls around in July and I am now confident that copy will continue to work just as before.  :p

---

### Post by AleveSicofante on 2014-06-27
> **mgmiller said:**
> It may have taken them about a year, but in the end they got it right before 14.04.1 was released.

It wasn't *them*, it was Marco Trevisan, an Ubuntu developer, who catched the bug (which was on "our" side). I don't know if Copy.com developers communicated with Marco. I do know, however, they have been quite silent and not publicly addressing the issue at all. They just released a new version including Marco's patches without saying a word to their customers, who've been asking for a long time. They're definitely not nice to their Linux customers at all. :(

---

### Post by v-steve-k on 2014-08-03
> **uzumakifahim said:**
> Thanks for your reply. 

I've installed Copy agent 1.43.0290 version.

I've installed Copy by the following steps:
1. At first I've copied the .tgz file in Downloads folder in my Home directory. 
2. Extract the .tgz file.
3. Enter into the copy folder and then x86 (my system is 32-bit)
4. Double-click the CopyAgent and the installation process starts and completed successfully
5. A folder named Copy has created in my home directory and my files started syncing immediately.

Only problem is that there is no indicator on the panel. :(

Thank you, this worked for me.

---

### Post by mgmiller on 2014-08-03
>  					[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **uzumakifahim** 					[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12991799#post12991799") 				

 				Thanks for your reply. 

I've installed Copy agent 1.43.0290 version.

I've installed Copy by the following steps:
1. At first I've copied the .tgz file in Downloads folder in my Home directory. 
2. Extract the .tgz file.
3. Enter into the copy folder and then x86 (my system is 32-bit)
4. Double-click the CopyAgent and the installation process starts and completed successfully
5. A folder named Copy has created in my home directory and my files started syncing immediately.

Only problem is that there is no indicator on the panel. :sad:



The problem here is you are using an older version.  The current version is 1.45.0363.  This version fixes all the indicator problems in Ubuntu 14.04.  Make sure you downloaded the installer directly from [www.copy.com/home](www.copy.com/home).  Scroll to the bottom and on the left side click on the Download link.  It should give you the Linux installer.  That being said, I had originally installed a much older version (which was current at the time)  in 12.04, which worked perfectly, and I noticed over time that it upgraded itself to the current version automatically.  I never saw activity in software updater about it.  I think it just does it itself in the background.  I don't know how to trigger its upgrade function.  Maybe log off and on or just restart the computer?

---

### Post by ironfrown on 2014-08-30
> **uzumakifahim said:**
> I've just installed Ubuntu 14.04. As my default online storage, after installing Copy client on Ubuntu 14.04, the Copy indicator is not showing in the top panel.

Get a new version of Linux distribution of Copy and reinstall it. I have downloaded version 1.46.0380 (placed it in /opt) and started the CopyAgent, which installed the indicator and created an entry in Startup Applications. It seems that apart from Dropbox (and formerly UbuntuOne), this is the only cloud client which actually works in Ubuntu 14.04 (to include Grive, OneDrive and OwnCloud) and gives you 15Gb of data free.

---

