---
title: "{HOW-TO} Installing Elements for Compiz Fusion"
date: 2008-06-07
forum: General Help
---

### Post by PatrickFisher on 2008-06-07
Good day every! Elements for Compiz fusion, the plugin that combines Snow, Stars, Autumn, Fireflies and Bubbles into one sweet package, is now available at [http://www.elementsplugin.com]("http://www.elementsplugin.com")

To install it, just download **[the install script]("http://www.elementsplugin.com/downloads/elementsinstall.sh")**, navigate to it in Terminal, and run:

```
bash ./elementsinstall.sh
```

Check out the video **[here]("http://www.elementsplugin.com/videos/")** to see how easy it is!

Have a great weekend, everyone.

---

### Post by Mr dirt on 2008-06-07
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-bcop is already the newest version.
compiz-dev is already the newest version.
libxcomposite-dev is already the newest version.
libpng12-dev is already the newest version.
libsm-dev is already the newest version.
libxrandr-dev is already the newest version.
libxdamage-dev is already the newest version.
libxinerama-dev is already the newest version.
libstartup-notification0-dev is already the newest version.
libgl1-mesa-dev is already the newest version.
libgl1-mesa-dev set to manually installed.
libtool is already the newest version.
libxslt1-dev is already the newest version.
xsltproc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--16:23:24--  http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz
           => `/home/jimmy/.elements/elements.tar.gz'
Resolving www.elementsplugin.com... 69.89.31.238
Connecting to www.elementsplugin.com|69.89.31.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 118,200 (115K) [application/x-gzip]

100%[====================================>] 118,200      241.91K/s             

16:23:25 (241.59 KB/s) - `/home/jimmy/.elements/elements.tar.gz' saved [118200/118200]

images/
images/fireflies2.svg
images/snow1.png
images/plugin-elements.png
images/fireflies1.svg
images/bubbles1.png
images/bubbles2.png
images/autumn1.png
images/stars1.png
images/autumn2.png
images/snow2.png
plugin.info
Makefile
elements.xml.in
elements.c
convert   : elements.xml.in -> build/elements.xml
bcop'ing  : build/elements.xml -> build/elements_options.h
bcop'ing  : build/elements.xml -> build/elements_options.c
schema    : build/elements.xml -> build/compiz-elements.schema
compiling : elements.c -> build/elements.lo
compiling : build/elements_options.c -> build/elements_options.lo
linking   : build/libelements.la
install   : /home/jimmy/.compiz/plugins/libelements.so
install   : /home/jimmy/.compiz/metadata/elements.xml
install   : build/compiz-elements.schema
install   : /home/jimmy/.compiz/images/plugin-elements.png
install   : /home/jimmy/.compiz/images/snow1.png
install   : /home/jimmy/.compiz/images/bubbles1.png
install   : /home/jimmy/.compiz/images/fireflies2.svg
install   : /home/jimmy/.compiz/images/bubbles2.png
install   : /home/jimmy/.compiz/images/fireflies1.svg
install   : /home/jimmy/.compiz/images/snow2.png
install   : /home/jimmy/.compiz/images/autumn2.png
install   : /home/jimmy/.compiz/images/autumn1.png
install   : /home/jimmy/.compiz/images/stars1.png
jimmy@jimmy-desktop:~/Desktop$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:00f5 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


```

How can I remove that file, and do I need to?

---

### Post by Mr dirt on 2008-06-07
Well It works regardless, dont know if I have something not working right in there.

---

### Post by PatrickFisher on 2008-06-07
> **Mr dirt said:**
> 

How can I remove that file, and do I need to?

I assume you mean you want to remove the whole plugin?

```

cd ~/.elements
sudo make uninstall
make clean
compiz --replace &

```

Oh! Wait! You mean that file that shows an compiz warning. You don't need to remove it, it actually has nothing to do with the Elements plugin. It's another plugin, it does that on mine too, I don't know which one.

---

### Post by Mr dirt on 2008-06-07
Cool this thing is awesome, thanks.

---

### Post by OldGamer on 2008-07-14
Great plug-in!  It was exactly what I was looking for.  I was just wondering though, in the video on the site, it shows the different backgrounds on the cube.  I had set mine to do that too, but with nautilus set to not show the desktop, I also don't get the 'elements'.  When I set nautilus to show the desktop, I get the 'elements', but lose my different wallpapers.  Could someone tell me how to get both things working at the same time?  I am using Hardy Heron.

OldGamer

---

### Post by PatrickFisher on 2008-07-15
> **OldGamer said:**
> Great plug-in!  It was exactly what I was looking for.  I was just wondering though, in the video on the site, it shows the different backgrounds on the cube.  I had set mine to do that too, but with nautilus set to not show the desktop, I also don't get the 'elements'.  When I set nautilus to show the desktop, I get the 'elements', but lose my different wallpapers.  Could someone tell me how to get both things working at the same time?  I am using Hardy Heron.

OldGamer

Unfortunately, you're not going to like the solution :) Because of the way Compiz works, you have to activate the "Draw over windows" property. In other words, it's really annoying. I was only running that way so I could quickly throw together the video without editing. It's **possible** that I could fix this up in a future version, but I know it won't be easy. I've been really busy lately, and haven't even got time to work on my new, more functional plugin. But if I do figure out how to do it, I'll make sure to message you. Or, if you'd like, email me (pat@elementsplugin.com) and I'll send you an email update instead.

---

### Post by Mr dirt on 2008-07-15
Hey man do you know how to get this plugin working with 7.6? It was working fine until I upgraded, now the elements plugin will not stay checked or enabled.

---

### Post by PatrickFisher on 2008-07-15
> **Mr dirt said:**
> Hey man do you know how to get this plugin working with 7.6? It was working fine until I upgraded, now the elements plugin will not stay checked or enabled.

You need to install the version that's on git. This is the way it's going to work, in order for everyone to be happy:

The version of Compiz that is default installed on Ubuntu (currently 0.7.4) will be supported via my website and the Ubuntu install script.

The git version of Compiz (currently 0.7.6) will be supported by the version of Elements on git.

It's a bit of a compromise with the Compiz Fusion devs. I hope it works for you.

---

### Post by Mr dirt on 2008-07-15
Thanks man, where can I find the git for elements?

---

### Post by Mr dirt on 2008-07-21
Where art thou Mr Fisher?

---

### Post by PatrickFisher on 2008-07-21
> **Mr dirt said:**
> Where art thou Mr Fisher?

I art(?) moving to a different city :) It's a long and distracting process.

[http://gitweb.compiz-fusion.org/?p=users/pat/elements;a=summary](http://gitweb.compiz-fusion.org/?p=users/pat/elements;a=summary)

---

### Post by Mr dirt on 2008-07-22
Thanks again man, one question how do you install the dam thing? Good luck on your move btw.

---

### Post by PatrickFisher on 2008-07-23
> **Mr dirt said:**
> Thanks again man, one question how do you install the dam thing? Good luck on your move btw.

Ugh. There's some stupid way of doing it involving cloning repositories and stupid crap like that (I *REALLY* hate git), but the easiest way (that I use) is to click the "snapshot" link, download, extract, navigate to that directory in terminal, then run "make", "sudo make install"

That should do it.

---

### Post by Mr dirt on 2008-07-24
Thanks worked perfect you da man!!

---

### Post by samsiteone on 2008-08-06
> **Mr dirt said:**
> Thanks worked perfect you da man!!

Nothing is working for me...
Ubuntu 8.04....... I've had Ubuntu for 4 days, worked around everything to get things to work and this plugin got me stuck.
Every time I put in a command from any forum including this one that looks the best, I get command not found or some similar thing.
Other than that... I'm falling in love with this Linux thing.
Ubuntu is absolutely amazing (when things work).:confused:

---

### Post by PatrickFisher on 2008-08-06
Hey buddy, welcome to Ubuntu.

I'd say chances are, you aren't in the right directory when you're entering the commands. Say you download this script to a folder your home folder named "Downloads". To navigate to that directory in terminal, you'd use this line:

cd ~/Downloads

The "cd" is just "change directory, the "~" is a shortcut to your home folder, and "Downloads", of course, is the name of the directory you want to go to. Careful, it's case-sensitive. THEN you can run whatever command you wanted (sudo bash ./elementsinstall.sh)

---

### Post by samsiteone on 2008-08-07
I GOT IT! WOOOOOOOOOOOOO...
And I have not seen any one write about it in any forum this way either.
EASY AS HECK,
#1 Open up your terminal, 
#2 get your elementsinstall.sh (not the .tar.gz)...
#3 drag the file into your terminal.
#4 terminal will say: $ /home/user/Desktop/elementsinstall.sh
#5 Hit enter.
#6 When the file script pops up copy everything from star to finish and paste in to terminal. Hit enter, Done.


Faster than it sounds on the explanation, all you do is drag and drop the .sh file hit enter, then paste the whole script in hit enter. :guitar:

---

### Post by PatrickFisher on 2008-08-07
Wow. Huh. Cool.

---

### Post by amadeus266 on 2008-08-08
How to uninstall? Doesn't work for me.

---

### Post by PatrickFisher on 2008-08-10
> **amadeus266 said:**
> How to uninstall? Doesn't work for me.

Well, chances are you're not using the version of Compiz that's supported through the website. God, I hate the confusion this causes, and I've brought it up with the Compiz Fusion developers, who are stuck in the Linux world of the 90s. Anyways, until hell freezes over, if you want to get this working, you're going to have to know what version of compiz you're running. If you don't, run this command in the terminal:

```

compiz --version
```

If it output is "compiz 0.7.7" (or 0.7.6), you'll need to get the version of Elements off of the Compiz git. That's at 

[http://gitweb.compiz-fusion.org/?p=users/pat/elements;a=summary](http://gitweb.compiz-fusion.org/?p=users/pat/elements;a=summary)

click "snapshot", download, unzip, navigate to the directory in terminal, run 

```

make
sudo make install

```

If it's anything less than 0.7.4, Elements isn't supported.

If it's 0.7.4/0.7.5 You probably just don't have Elements configured properly, it's not hard, just activate through "ccsm/compizconfig-settings-manager", and make sure you've got the keybindings set properly.

If you really want to uninstall, just run these commands:

```

cd ~/.elements
sudo make uninstall
make clean

```

---

### Post by amadeus266 on 2008-08-10
this is what I get:```
convert   : elements.xml.in -> build/elements.xml
bcop'ing  : build/elements.xml -> build/elements_options.h
bcop'ing  : build/elements.xml -> build/elements_options.c
schema    : build/elements.xml -> build/compiz-elements.schema
compiling : elements.c -> build/elements.loelements.c: In function &#8216;elementsInitScreen&#8217;:
elements.c:1114: error: incompatible type for argument 2 of &#8216;compAddTimeout&#8217;
elements.c:1114: error: too many arguments to function &#8216;compAddTimeout&#8217;
elements.c: In function &#8216;elementsDisplayOptionChanged&#8217;:
elements.c:1418: error: incompatible type for argument 2 of &#8216;compAddTimeout&#8217;
elements.c:1418: error: too many arguments to function &#8216;compAddTimeout&#8217;
make: *** [build/elements.lo] Error 1

```

I have compiz version 0.7.6 and I followed your instructions to the letter (twice) but still doesn't work. in fact it broke my original stars and fireflies plugins. Not that I use them anyway but frustrating nonetheless.

---

### Post by PatrickFisher on 2008-08-10
Yeah, that's because you don't have the right version downloaded. Those errors are caused by trying to install the 0.7.4 version on a 0.7.6 install. 

Are you sure you're following the right directions?

> If it output is "compiz 0.7.7" (or 0.7.6), you'll need to get the version of Elements off of the Compiz git. That's at

[http://gitweb.compiz-fusion.org/?p=u...ents;a=summary](http://gitweb.compiz-fusion.org/?p=u...ents;a=summary)

click "snapshot", download, unzip, navigate to the directory in terminal, run

```

make
sudo make install

```



Anyways, the uninstall directions are there too. It shouldn't break Stars or Fireflies, they probably never worked in the first place (they have the exact same issue with version problems as Elements)

I'm sorry for the difficulty this caused, but there is unfortunately nothing I can do, the CF devs' lack of interest in backwards compatibility will mean I'm having this same issue every few months.

---

### Post by desmondstclair on 2008-08-31
Hello everyone,

I am quite new to linux and am running Ubuntu Studio 8.04.1. I have had a blast running this operating system and Compiz Fusion is breathtaking. I'm pretty much sold once I get around this learning curve.

That being said, I've run into the same snag that many here have faced and am in some need of assistance. I'm running the latest version of Compiz Fusion and that is working great and I'm currently trying to install elements and am having a lot of trouble.

I've tired installing in several ways but have had no success. When I drag the "elementsinstall.sh" file to the terminal, I get this message:

desmond@MediaCntr:~$ '/home/desmond/Downloads/elementsinstall.sh'
bash: /home/desmond/Downloads/elementsinstall.sh: Permission Denied

I realise that I may have my folder permissions set too high, and so I right clicked on the folder, gone to Properties and have set that the owner, group and others have Folder access set to: Create and delete files. I've also kept the box checked that says, "Allow executing file as a program". 

I still get the same error even after a system restart.

If anyone could offer assistance, I would be very grateful.

Thanks for taking the time to read my post.

Cheers,
Desmond

---

### Post by davethewave on 2008-09-03
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-bcop is already the newest version.
compiz-dev is already the newest version.
libxcomposite-dev is already the newest version.
libpng12-dev is already the newest version.
libsm-dev is already the newest version.
libxrandr-dev is already the newest version.
libxdamage-dev is already the newest version.
libxinerama-dev is already the newest version.
libstartup-notification0-dev is already the newest version.
libgl1-mesa-dev is already the newest version.
libtool is already the newest version.
libxslt1-dev is already the newest version.
xsltproc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mkdir: cannot create directory `/root/.elements': File exists
--02:53:35--  http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz
           => `/root/.elements/elements.tar.gz'
Resolving www.elementsplugin.com... 69.89.31.238
Connecting to www.elementsplugin.com|69.89.31.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 118,200 (115K) [application/x-gzip]

100%[========================================>] 118,200       54.33K/s             

02:53:38 (54.28 KB/s) - `/root/.elements/elements.tar.gz' saved [118200/118200]

images/
images/fireflies2.svg
images/snow1.png
images/plugin-elements.png
images/fireflies1.svg
images/bubbles1.png
images/bubbles2.png
images/autumn1.png
images/stars1.png
images/autumn2.png
images/snow2.png
plugin.info
Makefile
elements.xml.in
elements.c
compiling : build/elements_options.c -> build/elements_options.loIn file included from build/elements_options.c:19:
build/elements_options.h:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.h:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetOverWindows’
build/elements_options.h:107: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggle’
build/elements_options.h:127: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetSnowRotate’
build/elements_options.h:131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleSnowCheck’
build/elements_options.h:142: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.h:162: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetAutumnRotate’
build/elements_options.h:166: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleAutumnCheck’
build/elements_options.h:173: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.h:189: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetBubblesRotate’
build/elements_options.h:193: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleBubblesCheck’
build/elements_options.h:200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.h:216: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetFirefliesRotate’
build/elements_options.h:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleFirefliesCheck’
build/elements_options.h:227: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.h:251: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetStarsRotate’
build/elements_options.h:255: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleStarsCheck’
build/elements_options.h:262: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c:25: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c:26: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsVTable’
build/elements_options.c:44: error: array type has incomplete element type
build/elements_options.c: In function ‘elementsGetUpdateDelay’:
build/elements_options.c:54: error: dereferencing pointer to incomplete type
build/elements_options.c:56: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetUpdateDelayOption’:
build/elements_options.c:60: error: dereferencing pointer to incomplete type
build/elements_options.c:62: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetUpdateDelayNotify’:
build/elements_options.c:66: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetScreenDepth’:
build/elements_options.c:72: error: dereferencing pointer to incomplete type
build/elements_options.c:74: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetScreenDepthOption’:
build/elements_options.c:78: error: dereferencing pointer to incomplete type
build/elements_options.c:80: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetScreenDepthNotify’:
build/elements_options.c:84: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetOverWindows’
build/elements_options.c: In function ‘elementsGetOverWindowsOption’:
build/elements_options.c:96: error: dereferencing pointer to incomplete type
build/elements_options.c:98: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetOverWindowsNotify’:
build/elements_options.c:102: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:106: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggle’
build/elements_options.c: In function ‘elementsGetToggleOption’:
build/elements_options.c:114: error: dereferencing pointer to incomplete type
build/elements_options.c:116: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleNotify’:
build/elements_options.c:120: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetNumSnowflakes’:
build/elements_options.c:126: error: dereferencing pointer to incomplete type
build/elements_options.c:128: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetNumSnowflakesOption’:
build/elements_options.c:132: error: dereferencing pointer to incomplete type
build/elements_options.c:134: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetNumSnowflakesNotify’:
build/elements_options.c:138: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetSnowSize’:
build/elements_options.c:144: error: dereferencing pointer to incomplete type
build/elements_options.c:146: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetSnowSizeOption’:
build/elements_options.c:150: error: dereferencing pointer to incomplete type
build/elements_options.c:152: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetSnowSizeNotify’:
build/elements_options.c:156: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetSnowSpeed’:
build/elements_options.c:162: error: dereferencing pointer to incomplete type
build/elements_options.c:164: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetSnowSpeedOption’:
build/elements_options.c:168: error: dereferencing pointer to incomplete type
build/elements_options.c:170: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetSnowSpeedNotify’:
build/elements_options.c:174: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetSnowSway’:
build/elements_options.c:180: error: dereferencing pointer to incomplete type
build/elements_options.c:182: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetSnowSwayOption’:
build/elements_options.c:186: error: dereferencing pointer to incomplete type
build/elements_options.c:188: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetSnowSwayNotify’:
build/elements_options.c:192: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:196: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetSnowRotate’
build/elements_options.c: In function ‘elementsGetSnowRotateOption’:
build/elements_options.c:204: error: dereferencing pointer to incomplete type
build/elements_options.c:206: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetSnowRotateNotify’:
build/elements_options.c:210: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:214: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleSnowCheck’
build/elements_options.c: In function ‘elementsGetToggleSnowCheckOption’:
build/elements_options.c:222: error: dereferencing pointer to incomplete type
build/elements_options.c:224: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleSnowCheckNotify’:
build/elements_options.c:228: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetToggleSnowKeyOption’:
build/elements_options.c:234: error: dereferencing pointer to incomplete type
build/elements_options.c:236: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleSnowKeyNotify’:
build/elements_options.c:240: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetWindDirection’:
build/elements_options.c:246: error: dereferencing pointer to incomplete type
build/elements_options.c:248: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetWindDirectionOption’:
build/elements_options.c:252: error: dereferencing pointer to incomplete type
build/elements_options.c:254: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetWindDirectionNotify’:
build/elements_options.c:258: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:262: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c: In function ‘elementsGetSnowTexturesOption’:
build/elements_options.c:270: error: dereferencing pointer to incomplete type
build/elements_options.c:272: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetSnowTexturesNotify’:
build/elements_options.c:276: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetNumLeaves’:
build/elements_options.c:282: error: dereferencing pointer to incomplete type
build/elements_options.c:284: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetNumLeavesOption’:
build/elements_options.c:288: error: dereferencing pointer to incomplete type
build/elements_options.c:290: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetNumLeavesNotify’:
build/elements_options.c:294: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetLeafSize’:
build/elements_options.c:300: error: dereferencing pointer to incomplete type
build/elements_options.c:302: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetLeafSizeOption’:
build/elements_options.c:306: error: dereferencing pointer to incomplete type
build/elements_options.c:308: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetLeafSizeNotify’:
build/elements_options.c:312: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetAutumnSway’:
build/elements_options.c:318: error: dereferencing pointer to incomplete type
build/elements_options.c:320: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetAutumnSwayOption’:
build/elements_options.c:324: error: dereferencing pointer to incomplete type
build/elements_options.c:326: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetAutumnSwayNotify’:
build/elements_options.c:330: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetAutumnSpeed’:
build/elements_options.c:336: error: dereferencing pointer to incomplete type
build/elements_options.c:338: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetAutumnSpeedOption’:
build/elements_options.c:342: error: dereferencing pointer to incomplete type
build/elements_options.c:344: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetAutumnSpeedNotify’:
build/elements_options.c:348: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:352: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetAutumnRotate’
build/elements_options.c: In function ‘elementsGetAutumnRotateOption’:
build/elements_options.c:360: error: dereferencing pointer to incomplete type
build/elements_options.c:362: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetAutumnRotateNotify’:
build/elements_options.c:366: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:370: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleAutumnCheck’
build/elements_options.c: In function ‘elementsGetToggleAutumnCheckOption’:
build/elements_options.c:378: error: dereferencing pointer to incomplete type
build/elements_options.c:380: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleAutumnCheckNotify’:
build/elements_options.c:384: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetToggleAutumnKeyOption’:
build/elements_options.c:390: error: dereferencing pointer to incomplete type
build/elements_options.c:392: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleAutumnKeyNotify’:
build/elements_options.c:396: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:400: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c: In function ‘elementsGetLeafTexturesOption’:
build/elements_options.c:408: error: dereferencing pointer to incomplete type
build/elements_options.c:410: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetLeafTexturesNotify’:
build/elements_options.c:414: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetNumBubbles’:
build/elements_options.c:420: error: dereferencing pointer to incomplete type
build/elements_options.c:422: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetNumBubblesOption’:
build/elements_options.c:426: error: dereferencing pointer to incomplete type
build/elements_options.c:428: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetNumBubblesNotify’:
build/elements_options.c:432: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetBubblesSize’:
build/elements_options.c:438: error: dereferencing pointer to incomplete type
build/elements_options.c:440: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetBubblesSizeOption’:
build/elements_options.c:444: error: dereferencing pointer to incomplete type
build/elements_options.c:446: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetBubblesSizeNotify’:
build/elements_options.c:450: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetViscosity’:
build/elements_options.c:456: error: dereferencing pointer to incomplete type
build/elements_options.c:458: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetViscosityOption’:
build/elements_options.c:462: error: dereferencing pointer to incomplete type
build/elements_options.c:464: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetViscosityNotify’:
build/elements_options.c:468: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:472: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetBubblesRotate’
build/elements_options.c: In function ‘elementsGetBubblesRotateOption’:
build/elements_options.c:480: error: dereferencing pointer to incomplete type
build/elements_options.c:482: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetBubblesRotateNotify’:
build/elements_options.c:486: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:490: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleBubblesCheck’
build/elements_options.c: In function ‘elementsGetToggleBubblesCheckOption’:
build/elements_options.c:498: error: dereferencing pointer to incomplete type
build/elements_options.c:500: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleBubblesCheckNotify’:
build/elements_options.c:504: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetToggleBubblesKeyOption’:
build/elements_options.c:510: error: dereferencing pointer to incomplete type
build/elements_options.c:512: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleBubblesKeyNotify’:
build/elements_options.c:516: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:520: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c: In function ‘elementsGetBubblesTexturesOption’:
build/elements_options.c:528: error: dereferencing pointer to incomplete type
build/elements_options.c:530: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetBubblesTexturesNotify’:
build/elements_options.c:534: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetNumFireflies’:
build/elements_options.c:540: error: dereferencing pointer to incomplete type
build/elements_options.c:542: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetNumFirefliesOption’:
build/elements_options.c:546: error: dereferencing pointer to incomplete type
build/elements_options.c:548: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetNumFirefliesNotify’:
build/elements_options.c:552: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetFireflySize’:
build/elements_options.c:558: error: dereferencing pointer to incomplete type
build/elements_options.c:560: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetFireflySizeOption’:
build/elements_options.c:564: error: dereferencing pointer to incomplete type
build/elements_options.c:566: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetFireflySizeNotify’:
build/elements_options.c:570: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetFireflySpeed’:
build/elements_options.c:576: error: dereferencing pointer to incomplete type
build/elements_options.c:578: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetFireflySpeedOption’:
build/elements_options.c:582: error: dereferencing pointer to incomplete type
build/elements_options.c:584: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetFireflySpeedNotify’:
build/elements_options.c:588: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:592: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetFirefliesRotate’
build/elements_options.c: In function ‘elementsGetFirefliesRotateOption’:
build/elements_options.c:600: error: dereferencing pointer to incomplete type
build/elements_options.c:602: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetFirefliesRotateNotify’:
build/elements_options.c:606: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:610: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleFirefliesCheck’
build/elements_options.c: In function ‘elementsGetToggleFirefliesCheckOption’:
build/elements_options.c:618: error: dereferencing pointer to incomplete type
build/elements_options.c:620: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleFirefliesCheckNotify’:
build/elements_options.c:624: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetToggleFirefliesKeyOption’:
build/elements_options.c:630: error: dereferencing pointer to incomplete type
build/elements_options.c:632: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleFirefliesKeyNotify’:
build/elements_options.c:636: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:640: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c: In function ‘elementsGetFirefliesTexturesOption’:
build/elements_options.c:648: error: dereferencing pointer to incomplete type
build/elements_options.c:650: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetFirefliesTexturesNotify’:
build/elements_options.c:654: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetNumStars’:
build/elements_options.c:660: error: dereferencing pointer to incomplete type
build/elements_options.c:662: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetNumStarsOption’:
build/elements_options.c:666: error: dereferencing pointer to incomplete type
build/elements_options.c:668: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetNumStarsNotify’:
build/elements_options.c:672: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetStarsSize’:
build/elements_options.c:678: error: dereferencing pointer to incomplete type
build/elements_options.c:680: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetStarsSizeOption’:
build/elements_options.c:684: error: dereferencing pointer to incomplete type
build/elements_options.c:686: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarsSizeNotify’:
build/elements_options.c:690: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetStarsSpeed’:
build/elements_options.c:696: error: dereferencing pointer to incomplete type
build/elements_options.c:698: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetStarsSpeedOption’:
build/elements_options.c:702: error: dereferencing pointer to incomplete type
build/elements_options.c:704: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarsSpeedNotify’:
build/elements_options.c:708: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetStarOffsetX’:
build/elements_options.c:714: error: dereferencing pointer to incomplete type
build/elements_options.c:716: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetStarOffsetXOption’:
build/elements_options.c:720: error: dereferencing pointer to incomplete type
build/elements_options.c:722: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarOffsetXNotify’:
build/elements_options.c:726: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetStarOffsetY’:
build/elements_options.c:732: error: dereferencing pointer to incomplete type
build/elements_options.c:734: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetStarOffsetYOption’:
build/elements_options.c:738: error: dereferencing pointer to incomplete type
build/elements_options.c:740: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarOffsetYNotify’:
build/elements_options.c:744: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:748: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetStarsRotate’
build/elements_options.c: In function ‘elementsGetStarsRotateOption’:
build/elements_options.c:756: error: dereferencing pointer to incomplete type
build/elements_options.c:758: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarsRotateNotify’:
build/elements_options.c:762: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:766: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleStarsCheck’
build/elements_options.c: In function ‘elementsGetToggleStarsCheckOption’:
build/elements_options.c:774: error: dereferencing pointer to incomplete type
build/elements_options.c:776: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleStarsCheckNotify’:
build/elements_options.c:780: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetToggleStarsKeyOption’:
build/elements_options.c:786: error: dereferencing pointer to incomplete type
build/elements_options.c:788: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleStarsKeyNotify’:
build/elements_options.c:792: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:796: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c: In function ‘elementsGetStarsTexturesOption’:
build/elements_options.c:804: error: dereferencing pointer to incomplete type
build/elements_options.c:806: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarsTexturesNotify’:
build/elements_options.c:810: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetDisplayOption’:
build/elements_options.c:816: error: dereferencing pointer to incomplete type
build/elements_options.c:818: warning: control reaches end of non-void function
build/elements_options.c: At top level:
build/elements_options.c:820: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsDisplayOptionInfo’
build/elements_options.c:867: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsSetDisplayOption’
build/elements_options.c: In function ‘elementsOptionsGetDisplayOptions’:
build/elements_options.c:1240: error: dereferencing pointer to incomplete type
build/elements_options.c:1243: warning: control reaches end of non-void function
build/elements_options.c: At top level:
build/elements_options.c:1245: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsInitScreen’
build/elements_options.c: In function ‘elementsOptionsFiniScreen’:
build/elements_options.c:1264: error: ‘elementsPluginVTable’ undeclared (first use in this function)
build/elements_options.c:1264: error: (Each undeclared identifier is reported only once
build/elements_options.c:1264: error: for each function it appears in.)
build/elements_options.c:1265: warning: ‘return’ with a value, in function returning void
build/elements_options.c:1267: error: dereferencing pointer to incomplete type
build/elements_options.c:1267: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:1272: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsInitDisplay’
build/elements_options.c: In function ‘elementsOptionsFiniDisplay’:
build/elements_options.c:1302: error: ‘elementsPluginVTable’ undeclared (first use in this function)
build/elements_options.c:1303: warning: ‘return’ with a value, in function returning void
build/elements_options.c:1305: error: dereferencing pointer to incomplete type
build/elements_options.c:1307: warning: implicit declaration of function ‘freeScreenPrivateIndex’
build/elements_options.c:1307: warning: nested extern declaration of ‘freeScreenPrivateIndex’
build/elements_options.c:1309: warning: implicit declaration of function ‘compFiniDisplayOptions’
build/elements_options.c:1309: warning: nested extern declaration of ‘compFiniDisplayOptions’
build/elements_options.c: At top level:
build/elements_options.c:1314: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsInit’
build/elements_options.c: In function ‘elementsOptionsFini’:
build/elements_options.c:1331: error: ‘elementsPluginVTable’ undeclared (first use in this function)
build/elements_options.c:1332: warning: ‘return’ with a value, in function returning void
build/elements_options.c:1335: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
build/elements_options.c:1335: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
build/elements_options.c: At top level:
build/elements_options.c:1346: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/elements_options.lo] Error 1
compiling : build/elements_options.c -> build/elements_options.loIn file included from build/elements_options.c:19:
build/elements_options.h:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.h:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetOverWindows’
build/elements_options.h:107: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggle’
build/elements_options.h:127: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetSnowRotate’
build/elements_options.h:131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleSnowCheck’
build/elements_options.h:142: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.h:162: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetAutumnRotate’
build/elements_options.h:166: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleAutumnCheck’
build/elements_options.h:173: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.h:189: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetBubblesRotate’
build/elements_options.h:193: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleBubblesCheck’
build/elements_options.h:200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.h:216: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetFirefliesRotate’
build/elements_options.h:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleFirefliesCheck’
build/elements_options.h:227: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.h:251: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetStarsRotate’
build/elements_options.h:255: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleStarsCheck’
build/elements_options.h:262: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c:25: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c:26: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsVTable’
build/elements_options.c:44: error: array type has incomplete element type
build/elements_options.c: In function ‘elementsGetUpdateDelay’:
build/elements_options.c:54: error: dereferencing pointer to incomplete type
build/elements_options.c:56: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetUpdateDelayOption’:
build/elements_options.c:60: error: dereferencing pointer to incomplete type
build/elements_options.c:62: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetUpdateDelayNotify’:
build/elements_options.c:66: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetScreenDepth’:
build/elements_options.c:72: error: dereferencing pointer to incomplete type
build/elements_options.c:74: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetScreenDepthOption’:
build/elements_options.c:78: error: dereferencing pointer to incomplete type
build/elements_options.c:80: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetScreenDepthNotify’:
build/elements_options.c:84: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetOverWindows’
build/elements_options.c: In function ‘elementsGetOverWindowsOption’:
build/elements_options.c:96: error: dereferencing pointer to incomplete type
build/elements_options.c:98: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetOverWindowsNotify’:
build/elements_options.c:102: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:106: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggle’
build/elements_options.c: In function ‘elementsGetToggleOption’:
build/elements_options.c:114: error: dereferencing pointer to incomplete type
build/elements_options.c:116: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleNotify’:
build/elements_options.c:120: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetNumSnowflakes’:
build/elements_options.c:126: error: dereferencing pointer to incomplete type
build/elements_options.c:128: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetNumSnowflakesOption’:
build/elements_options.c:132: error: dereferencing pointer to incomplete type
build/elements_options.c:134: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetNumSnowflakesNotify’:
build/elements_options.c:138: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetSnowSize’:
build/elements_options.c:144: error: dereferencing pointer to incomplete type
build/elements_options.c:146: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetSnowSizeOption’:
build/elements_options.c:150: error: dereferencing pointer to incomplete type
build/elements_options.c:152: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetSnowSizeNotify’:
build/elements_options.c:156: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetSnowSpeed’:
build/elements_options.c:162: error: dereferencing pointer to incomplete type
build/elements_options.c:164: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetSnowSpeedOption’:
build/elements_options.c:168: error: dereferencing pointer to incomplete type
build/elements_options.c:170: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetSnowSpeedNotify’:
build/elements_options.c:174: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetSnowSway’:
build/elements_options.c:180: error: dereferencing pointer to incomplete type
build/elements_options.c:182: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetSnowSwayOption’:
build/elements_options.c:186: error: dereferencing pointer to incomplete type
build/elements_options.c:188: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetSnowSwayNotify’:
build/elements_options.c:192: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:196: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetSnowRotate’
build/elements_options.c: In function ‘elementsGetSnowRotateOption’:
build/elements_options.c:204: error: dereferencing pointer to incomplete type
build/elements_options.c:206: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetSnowRotateNotify’:
build/elements_options.c:210: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:214: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleSnowCheck’
build/elements_options.c: In function ‘elementsGetToggleSnowCheckOption’:
build/elements_options.c:222: error: dereferencing pointer to incomplete type
build/elements_options.c:224: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleSnowCheckNotify’:
build/elements_options.c:228: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetToggleSnowKeyOption’:
build/elements_options.c:234: error: dereferencing pointer to incomplete type
build/elements_options.c:236: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleSnowKeyNotify’:
build/elements_options.c:240: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetWindDirection’:
build/elements_options.c:246: error: dereferencing pointer to incomplete type
build/elements_options.c:248: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetWindDirectionOption’:
build/elements_options.c:252: error: dereferencing pointer to incomplete type
build/elements_options.c:254: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetWindDirectionNotify’:
build/elements_options.c:258: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:262: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c: In function ‘elementsGetSnowTexturesOption’:
build/elements_options.c:270: error: dereferencing pointer to incomplete type
build/elements_options.c:272: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetSnowTexturesNotify’:
build/elements_options.c:276: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetNumLeaves’:
build/elements_options.c:282: error: dereferencing pointer to incomplete type
build/elements_options.c:284: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetNumLeavesOption’:
build/elements_options.c:288: error: dereferencing pointer to incomplete type
build/elements_options.c:290: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetNumLeavesNotify’:
build/elements_options.c:294: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetLeafSize’:
build/elements_options.c:300: error: dereferencing pointer to incomplete type
build/elements_options.c:302: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetLeafSizeOption’:
build/elements_options.c:306: error: dereferencing pointer to incomplete type
build/elements_options.c:308: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetLeafSizeNotify’:
build/elements_options.c:312: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetAutumnSway’:
build/elements_options.c:318: error: dereferencing pointer to incomplete type
build/elements_options.c:320: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetAutumnSwayOption’:
build/elements_options.c:324: error: dereferencing pointer to incomplete type
build/elements_options.c:326: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetAutumnSwayNotify’:
build/elements_options.c:330: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetAutumnSpeed’:
build/elements_options.c:336: error: dereferencing pointer to incomplete type
build/elements_options.c:338: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetAutumnSpeedOption’:
build/elements_options.c:342: error: dereferencing pointer to incomplete type
build/elements_options.c:344: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetAutumnSpeedNotify’:
build/elements_options.c:348: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:352: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetAutumnRotate’
build/elements_options.c: In function ‘elementsGetAutumnRotateOption’:
build/elements_options.c:360: error: dereferencing pointer to incomplete type
build/elements_options.c:362: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetAutumnRotateNotify’:
build/elements_options.c:366: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:370: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleAutumnCheck’
build/elements_options.c: In function ‘elementsGetToggleAutumnCheckOption’:
build/elements_options.c:378: error: dereferencing pointer to incomplete type
build/elements_options.c:380: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleAutumnCheckNotify’:
build/elements_options.c:384: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetToggleAutumnKeyOption’:
build/elements_options.c:390: error: dereferencing pointer to incomplete type
build/elements_options.c:392: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleAutumnKeyNotify’:
build/elements_options.c:396: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:400: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c: In function ‘elementsGetLeafTexturesOption’:
build/elements_options.c:408: error: dereferencing pointer to incomplete type
build/elements_options.c:410: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetLeafTexturesNotify’:
build/elements_options.c:414: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetNumBubbles’:
build/elements_options.c:420: error: dereferencing pointer to incomplete type
build/elements_options.c:422: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetNumBubblesOption’:
build/elements_options.c:426: error: dereferencing pointer to incomplete type
build/elements_options.c:428: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetNumBubblesNotify’:
build/elements_options.c:432: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetBubblesSize’:
build/elements_options.c:438: error: dereferencing pointer to incomplete type
build/elements_options.c:440: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetBubblesSizeOption’:
build/elements_options.c:444: error: dereferencing pointer to incomplete type
build/elements_options.c:446: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetBubblesSizeNotify’:
build/elements_options.c:450: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetViscosity’:
build/elements_options.c:456: error: dereferencing pointer to incomplete type
build/elements_options.c:458: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetViscosityOption’:
build/elements_options.c:462: error: dereferencing pointer to incomplete type
build/elements_options.c:464: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetViscosityNotify’:
build/elements_options.c:468: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:472: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetBubblesRotate’
build/elements_options.c: In function ‘elementsGetBubblesRotateOption’:
build/elements_options.c:480: error: dereferencing pointer to incomplete type
build/elements_options.c:482: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetBubblesRotateNotify’:
build/elements_options.c:486: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:490: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleBubblesCheck’
build/elements_options.c: In function ‘elementsGetToggleBubblesCheckOption’:
build/elements_options.c:498: error: dereferencing pointer to incomplete type
build/elements_options.c:500: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleBubblesCheckNotify’:
build/elements_options.c:504: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetToggleBubblesKeyOption’:
build/elements_options.c:510: error: dereferencing pointer to incomplete type
build/elements_options.c:512: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleBubblesKeyNotify’:
build/elements_options.c:516: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:520: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c: In function ‘elementsGetBubblesTexturesOption’:
build/elements_options.c:528: error: dereferencing pointer to incomplete type
build/elements_options.c:530: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetBubblesTexturesNotify’:
build/elements_options.c:534: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetNumFireflies’:
build/elements_options.c:540: error: dereferencing pointer to incomplete type
build/elements_options.c:542: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetNumFirefliesOption’:
build/elements_options.c:546: error: dereferencing pointer to incomplete type
build/elements_options.c:548: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetNumFirefliesNotify’:
build/elements_options.c:552: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetFireflySize’:
build/elements_options.c:558: error: dereferencing pointer to incomplete type
build/elements_options.c:560: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetFireflySizeOption’:
build/elements_options.c:564: error: dereferencing pointer to incomplete type
build/elements_options.c:566: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetFireflySizeNotify’:
build/elements_options.c:570: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetFireflySpeed’:
build/elements_options.c:576: error: dereferencing pointer to incomplete type
build/elements_options.c:578: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetFireflySpeedOption’:
build/elements_options.c:582: error: dereferencing pointer to incomplete type
build/elements_options.c:584: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetFireflySpeedNotify’:
build/elements_options.c:588: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:592: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetFirefliesRotate’
build/elements_options.c: In function ‘elementsGetFirefliesRotateOption’:
build/elements_options.c:600: error: dereferencing pointer to incomplete type
build/elements_options.c:602: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetFirefliesRotateNotify’:
build/elements_options.c:606: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:610: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleFirefliesCheck’
build/elements_options.c: In function ‘elementsGetToggleFirefliesCheckOption’:
build/elements_options.c:618: error: dereferencing pointer to incomplete type
build/elements_options.c:620: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleFirefliesCheckNotify’:
build/elements_options.c:624: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetToggleFirefliesKeyOption’:
build/elements_options.c:630: error: dereferencing pointer to incomplete type
build/elements_options.c:632: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleFirefliesKeyNotify’:
build/elements_options.c:636: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:640: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c: In function ‘elementsGetFirefliesTexturesOption’:
build/elements_options.c:648: error: dereferencing pointer to incomplete type
build/elements_options.c:650: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetFirefliesTexturesNotify’:
build/elements_options.c:654: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetNumStars’:
build/elements_options.c:660: error: dereferencing pointer to incomplete type
build/elements_options.c:662: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetNumStarsOption’:
build/elements_options.c:666: error: dereferencing pointer to incomplete type
build/elements_options.c:668: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetNumStarsNotify’:
build/elements_options.c:672: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetStarsSize’:
build/elements_options.c:678: error: dereferencing pointer to incomplete type
build/elements_options.c:680: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetStarsSizeOption’:
build/elements_options.c:684: error: dereferencing pointer to incomplete type
build/elements_options.c:686: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarsSizeNotify’:
build/elements_options.c:690: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetStarsSpeed’:
build/elements_options.c:696: error: dereferencing pointer to incomplete type
build/elements_options.c:698: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetStarsSpeedOption’:
build/elements_options.c:702: error: dereferencing pointer to incomplete type
build/elements_options.c:704: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarsSpeedNotify’:
build/elements_options.c:708: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetStarOffsetX’:
build/elements_options.c:714: error: dereferencing pointer to incomplete type
build/elements_options.c:716: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetStarOffsetXOption’:
build/elements_options.c:720: error: dereferencing pointer to incomplete type
build/elements_options.c:722: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarOffsetXNotify’:
build/elements_options.c:726: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetStarOffsetY’:
build/elements_options.c:732: error: dereferencing pointer to incomplete type
build/elements_options.c:734: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsGetStarOffsetYOption’:
build/elements_options.c:738: error: dereferencing pointer to incomplete type
build/elements_options.c:740: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarOffsetYNotify’:
build/elements_options.c:744: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:748: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetStarsRotate’
build/elements_options.c: In function ‘elementsGetStarsRotateOption’:
build/elements_options.c:756: error: dereferencing pointer to incomplete type
build/elements_options.c:758: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarsRotateNotify’:
build/elements_options.c:762: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:766: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsGetToggleStarsCheck’
build/elements_options.c: In function ‘elementsGetToggleStarsCheckOption’:
build/elements_options.c:774: error: dereferencing pointer to incomplete type
build/elements_options.c:776: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleStarsCheckNotify’:
build/elements_options.c:780: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetToggleStarsKeyOption’:
build/elements_options.c:786: error: dereferencing pointer to incomplete type
build/elements_options.c:788: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetToggleStarsKeyNotify’:
build/elements_options.c:792: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:796: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/elements_options.c: In function ‘elementsGetStarsTexturesOption’:
build/elements_options.c:804: error: dereferencing pointer to incomplete type
build/elements_options.c:806: warning: control reaches end of non-void function
build/elements_options.c: In function ‘elementsSetStarsTexturesNotify’:
build/elements_options.c:810: error: dereferencing pointer to incomplete type
build/elements_options.c: In function ‘elementsGetDisplayOption’:
build/elements_options.c:816: error: dereferencing pointer to incomplete type
build/elements_options.c:818: warning: control reaches end of non-void function
build/elements_options.c: At top level:
build/elements_options.c:820: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsDisplayOptionInfo’
build/elements_options.c:867: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsSetDisplayOption’
build/elements_options.c: In function ‘elementsOptionsGetDisplayOptions’:
build/elements_options.c:1240: error: dereferencing pointer to incomplete type
build/elements_options.c:1243: warning: control reaches end of non-void function
build/elements_options.c: At top level:
build/elements_options.c:1245: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsInitScreen’
build/elements_options.c: In function ‘elementsOptionsFiniScreen’:
build/elements_options.c:1264: error: ‘elementsPluginVTable’ undeclared (first use in this function)
build/elements_options.c:1264: error: (Each undeclared identifier is reported only once
build/elements_options.c:1264: error: for each function it appears in.)
build/elements_options.c:1265: warning: ‘return’ with a value, in function returning void
build/elements_options.c:1267: error: dereferencing pointer to incomplete type
build/elements_options.c:1267: error: dereferencing pointer to incomplete type
build/elements_options.c: At top level:
build/elements_options.c:1272: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsInitDisplay’
build/elements_options.c: In function ‘elementsOptionsFiniDisplay’:
build/elements_options.c:1302: error: ‘elementsPluginVTable’ undeclared (first use in this function)
build/elements_options.c:1303: warning: ‘return’ with a value, in function returning void
build/elements_options.c:1305: error: dereferencing pointer to incomplete type
build/elements_options.c:1307: warning: implicit declaration of function ‘freeScreenPrivateIndex’
build/elements_options.c:1307: warning: nested extern declaration of ‘freeScreenPrivateIndex’
build/elements_options.c:1309: warning: implicit declaration of function ‘compFiniDisplayOptions’
build/elements_options.c:1309: warning: nested extern declaration of ‘compFiniDisplayOptions’
build/elements_options.c: At top level:
build/elements_options.c:1314: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elementsOptionsInit’
build/elements_options.c: In function ‘elementsOptionsFini’:
build/elements_options.c:1331: error: ‘elementsPluginVTable’ undeclared (first use in this function)
build/elements_options.c:1332: warning: ‘return’ with a value, in function returning void
build/elements_options.c:1335: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
build/elements_options.c:1335: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
build/elements_options.c: At top level:
build/elements_options.c:1346: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/elements_options.lo] Error 1
Checking for Xgl: not present. 
root@lover:/home/david/Desktop# Detected PCI ID for VGA: 01:00.0 0300: 10de:0175 (rev a3) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

```
:confused:

---

### Post by cyper on 2009-02-10
Look here what i got with installing elements:
```
anton@bilochka:~/download$ sudo bash elementsinstall.sh
&#1063;&#1080;&#1090;&#1072;&#1085;&#1085;&#1103; &#1087;&#1077;&#1088;&#1077;&#1083;&#1110;&#1082;&#1110;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1110;&#1074;... &#1042;&#1080;&#1082;&#1086;&#1085;&#1072;&#1085;&#1086;
&#1055;&#1086;&#1073;&#1091;&#1076;&#1086;&#1074;&#1072; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1083;&#1077;&#1078;&#1085;&#1086;&#1089;&#1090;&#1077;&#1081;                
Reading state information... &#1042;&#1080;&#1082;&#1086;&#1085;&#1072;&#1085;&#1086;               
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; compiz-bcop.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; compiz-dev.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; libxcomposite-dev.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; libpng12-dev.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; libsm-dev.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; libxrandr-dev.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; libxdamage-dev.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; libxinerama-dev.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; libstartup-notification0-dev.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; libgl1-mesa-dev.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; libtool.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; libxslt1-dev.
&#1042;&#1078;&#1077; &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1085;&#1072;&#1081;&#1085;&#1086;&#1074;&#1110;&#1096;&#1072; &#1074;&#1077;&#1088;&#1089;&#1110;&#1103; xsltproc.
&#1086;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0, &#1074;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0 &#1085;&#1086;&#1074;&#1080;&#1093; &#1087;&#1072;&#1082;&#1091;&#1085;&#1082;&#1110;&#1074;, &#1076;&#1083;&#1103; &#1074;&#1080;&#1076;&#1072;&#1083;&#1077;&#1085;&#1085;&#1103; &#1074;&#1110;&#1076;&#1084;&#1110;&#1095;&#1077;&#1085;&#1086; 0 &#1087;&#1072;&#1082;&#1091;&#1085;&#1082;&#1110;&#1074;, &#1110; 0 &#1087;&#1072;&#1082;&#1091;&#1085;&#1082;&#1110;&#1074; &#1085;&#1077; &#1086;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
--16:01:28--  http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz
           => `/home/anton/.elements/elements.tar.gz'
&#1042;&#1080;&#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1085;&#1103; &#1110;&#1084;&#1077;&#1085;&#1110; www.elementsplugin.com... 69.89.31.238
&#1047;'&#1108;&#1076;&#1085;&#1091;&#1102;&#1089;&#1100; &#1079; www.elementsplugin.com|69.89.31.238|:80... &#1087;&#1110;&#1076;'&#1108;&#1076;&#1085;&#1072;&#1085;&#1086;.
HTTP-&#1079;&#1072;&#1087;&#1080;&#1090; &#1085;&#1072;&#1076;&#1110;&#1089;&#1083;&#1072;&#1085;&#1086;, &#1086;&#1095;&#1110;&#1082;&#1091;&#1102; &#1074;&#1110;&#1076;&#1087;&#1086;&#1074;&#1110;&#1076;&#1110;... 200 OK
&#1044;&#1086;&#1074;&#1078;&#1080;&#1085;&#1072;: 81*464 (80K) [application/x-gzip]

100%[====================================>] 81*464       86.19K/s              

16:01:29 (85.96 KB/s) - `/home/anton/.elements/elements.tar.gz' &#1079;&#1073;&#1077;&#1088;&#1077;&#1078;&#1077;&#1085;&#1086; [81464/81464]

images/
images/stars1.png
images/snow2.png
images/snow1.png
images/plugin-elements.png
images/fireflies2.svg
images/fireflies1.svg
images/bubbles2.png
images/bubbles1.png
images/autumn2.png
images/autumn1.png
elements.c
elements.xml.in
Makefile
plugin.info
convert   : elements.xml.in -> build/elements.xml
bcop'ing  : build/elements.xml -> build/elements_options.h
bcop'ing  : build/elements.xml -> build/elements_options.c
schema    : build/elements.xml -> build/compiz-elements.schema
compiling : elements.c -> build/elements.loelements.c: In function &#8216;elementMove&#8217;:
elements.c:266: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:266: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:266: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:266: error: too few arguments to function &#8216;compLogMessage&#8217;
elements.c: In function &#8216;updateElementTextures&#8217;:
elements.c:843: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:843: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:843: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:847: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:847: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:847: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:889: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:889: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:889: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:893: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:893: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:893: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:936: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:936: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:936: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:940: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:940: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:940: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:983: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:983: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:983: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:987: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:987: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:987: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:1030: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:1030: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:1030: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:1034: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:1034: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:1034: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c: In function &#8216;elementsInitScreen&#8217;:
elements.c:1114: error: incompatible type for argument 2 of &#8216;compAddTimeout&#8217;
elements.c:1114: error: too many arguments to function &#8216;compAddTimeout&#8217;
elements.c: In function &#8216;elementsDisplayOptionChanged&#8217;:
elements.c:1418: error: incompatible type for argument 2 of &#8216;compAddTimeout&#8217;
elements.c:1418: error: too many arguments to function &#8216;compAddTimeout&#8217;
make: *** [build/elements.lo] &#1055;&#1086;&#1084;&#1080;&#1083;&#1082;&#1072; 1
compiling : elements.c -> build/elements.loelements.c: In function &#8216;elementMove&#8217;:
elements.c:266: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:266: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:266: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:266: error: too few arguments to function &#8216;compLogMessage&#8217;
elements.c: In function &#8216;updateElementTextures&#8217;:
elements.c:843: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:843: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:843: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:847: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:847: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:847: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:889: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:889: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:889: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:893: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:893: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:893: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:936: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:936: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:936: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:940: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:940: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:940: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:983: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:983: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:983: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:987: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:987: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:987: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:1030: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:1030: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:1030: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c:1034: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
elements.c:1034: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
elements.c:1034: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
elements.c: In function &#8216;elementsInitScreen&#8217;:
elements.c:1114: error: incompatible type for argument 2 of &#8216;compAddTimeout&#8217;
elements.c:1114: error: too many arguments to function &#8216;compAddTimeout&#8217;
elements.c: In function &#8216;elementsDisplayOptionChanged&#8217;:
elements.c:1418: error: incompatible type for argument 2 of &#8216;compAddTimeout&#8217;
elements.c:1418: error: too many arguments to function &#8216;compAddTimeout&#8217;
make: *** [build/elements.lo] &#1055;&#1086;&#1084;&#1080;&#1083;&#1082;&#1072; 1
anton@bilochka:~/download$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

what can you tell me about all those errors. Eventually I must have some dependencies unsatisfied?

compiz version 0.7.4

---

### Post by PatrickFisher on 2009-02-10
Check out post number 21.

Your problem is because of some changes to the API that the compiz developers insist on making which break everything.

If post 21 doesn't help, I need to know what version you have. run "compiz --version"

---

### Post by cyper on 2009-02-10
Once again: compiz --version
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
compiz 0.7.4

```

Maybe that's because of my loosy video - intel GMA950? ;)

---

### Post by alejobar on 2009-05-04
alejo@ubuntu-desktop:~$ cd Desktop
alejo@ubuntu-desktop:~/Desktop$ bash ./elementsinstall.sh
[sudo] password for alejo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-dev is already the newest version.
libxcomposite-dev is already the newest version.
libpng12-dev is already the newest version.
libsm-dev is already the newest version.
libxrandr-dev is already the newest version.
libxdamage-dev is already the newest version.
libxinerama-dev is already the newest version.
libstartup-notification0-dev is already the newest version.
libgl1-mesa-dev is already the newest version.
libtool is already the newest version.
libxslt1-dev is already the newest version.
xsltproc is already the newest version.
The following NEW packages will be installed:
  compiz-bcop
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/9596B of archives.
After this operation, 127kB of additional disk space will be used.
(Reading database ... 106029 files and directories currently installed.)
Unpacking compiz-bcop (from .../compiz-bcop_0.7.4-0ubuntu1_all.deb) ...
Setting up compiz-bcop (0.7.4-0ubuntu1) ...
mkdir: cannot create directory `/home/alejo/.elements': File exists
/home/alejo/.elements/elements.tar.gz: Permission denied
images/
images/stars1.png
images/snow2.png
images/snow1.png
images/plugin-elements.png
images/fireflies2.svg
images/fireflies1.svg
images/bubbles2.png
images/bubbles1.png
images/autumn2.png
images/autumn1.png
elements.c
tar: elements.c: Cannot open: File exists
elements.xml.in
tar: elements.xml.in: Cannot open: File exists
Makefile
tar: Makefile: Cannot open: File exists
plugin.info
tar: plugin.info: Cannot open: File exists
tar: Error exit delayed from previous errors
mkdir: cannot create directory `build': Permission denied
make: *** [build] Error 1
mkdir: cannot create directory `build': Permission denied
make: *** [build] Error 1
alejo@ubuntu-desktop:~/Desktop$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

I trying to install elements without luck in Hardy using compiz 0.7.4, any help please?

---

### Post by alejobar on 2009-05-04
Bump

---

### Post by Wise Ferret on 2009-06-09
Elements do not work for me on karmic. It is installable through compiz-fusion-plugins-unsupported from ubuntu repos, and it throws no compiz error message when enables. But pressing key combinations to start the display simply do nothing. I even made sure that the textures are set to real image files.

compiz --version: 0.8.2

---

### Post by pt123 on 2009-12-28
someone on this blog has created packages so the Elements plugin will work with Karmic

[http://ubuntuguide.net/enable-snow-on-ubuntu-desktop-using-compiz-fusion](http://ubuntuguide.net/enable-snow-on-ubuntu-desktop-using-compiz-fusion)

---

