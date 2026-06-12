---
title: "Compile compiz-fusion from git [UPDATED] (NEW SCRIPT)"
date: 2008-05-04
forum: General Help
---

### Post by Martje_001 on 2008-05-04
[COLOR="Red"]**!! This is installing the latest compiz-fusion which might be unstable !!**[/COLOR]
[COLOR="Red"]**!! After installing, run compiz with fusion-icon (in application-menu) !!**[/COLOR]
[COLOR="DarkOrange"]!! If this script doesn't work for you, try [this]("http://telperion.wordpress.com/2008/03/10/compizfusion-makefusion9-script-per-compilazione/") ([original page]("http://telperion.wordpress.com/2008/04/02/compizfusion-makefusion9-aggiornamento//")) !!
[/COLOR]

The script is not yet stable, please help testing..
**To get and run compiz-git:**
```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
./compiz-git install
```
That's it!

More info here:
[http://mbastiaan.nl/compizgit.php](http://mbastiaan.nl/compizgit.php)

Edit: If you don't know *what* you're doing, don't use it...

---

### Post by Zorael on 2008-05-04
You misspelled the filename, both here and on that website. Might want to correct that. :>

```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newe**_w_**st.tar.gz
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
```

edit: Also, where's the Kubuntu Hardy option? I imagine there's not a whole lot of difference, though.

---

### Post by Martje_001 on 2008-05-04
:oops: Corrected :oops:

There is.. Kubuntu Hardy comes with KDE4 if I'm not mistaking.. but I'm working at that!

---

### Post by Zorael on 2008-05-04
There are two version of Kubuntu Hardy, one normal with KDE 3.5.9 (current stable) and one Kubuntu "Remix" version with KDE 4.0.

Most non-bleeding edge Kubuntulings agree that KDE4 is an uncomplete work in progress, so I think it's best to assume that most are still running KDE3. :>

---

### Post by Martje_001 on 2008-05-04
I'm downloading both now, to test everything. I think tomorrow there's Kubuntu hardy support ;)

---

### Post by 565Customz on 2008-05-04
yeah umm....this definatly made all my title bars disapeer and all my windows are up high and i cant drag them back down...cuz they have to title bar...? wtf lol

---

### Post by Fireblend on 2008-05-04
So how would I go around deleting the old compiz-git from the original thread so I can install this one?

I'm guessing a simple apt-get remove won't be enough :p

---

### Post by Martje_001 on 2008-05-04
> **565Customz said:**
> yeah umm....this definatly made all my title bars disapeer and all my windows are up high and i cant drag them back down...cuz they have to title bar...? wtf lol
Activate 'Decoration' in CompizConfig Settings Manager and run fusion-icon.

---

### Post by Martje_001 on 2008-05-04
> **Fireblend said:**
> So how would I go around deleting the old compiz-git from the original thread so I can install this one?

I'm guessing a simple apt-get remove won't be enough :p
haha, no:
```
sudo compiz-git --uninstall
sudo apt-get remove compiz-git
sudo mv /etc/apt/sources.list /etc/apt/sources.list1
sudo apt-get update
sudo cp /etc/apt/sources.list1 /etc/apt/sources.list
sudo apt-get update
```
and follow the instructions here ;)

Edit:
btw, Fireblend, you've got a beautiful desktop!

---

### Post by Fireblend on 2008-05-04
> **Martje_001 said:**
> haha, no:
```
sudo compiz-git --uninstall
sudo apt-get remove compiz-git
sudo mv /etc/apt/sources.list /etc/apt/sources.list1
sudo apt-get update
sudo cp /etc/apt/sources.list1 /etc/apt/sources.list
sudo apt-get update
```
and follow the instructions here ;)

Edit:
btw, Fireblend, you've got a beautiful desktop!

Thanks, gonna try that now. Oh and the one in my signature is a really outdated version from last christmas. [This is my current desktop]("http://i30.tinypic.com/2hhgcqo.png") :D which I love even more. Actually I'll update the signature now :p

---

### Post by Martje_001 on 2008-05-04
Do you think so? I like the one from last christmas better ;)

---

### Post by Fireblend on 2008-05-04
> **Martje_001 said:**
> Do you think so? I like the one from last christmas better ;)

Dark themes are not really my thing either, but this one looked way too cool to pass up :D Also, the script worked perfectly; if I find anything worth reporting I'll let you know; thanks!

---

### Post by Lacrimstein on 2008-05-04
Installing this practically destroyed my compiz on Hardy ><.
Compiz-git wouldn't start at all, and when I removed it and reinstalled normal compiz, I couldn't enable window decorations - metacity or emerald. Emerald wouldn't even start, stating libemerald0.so is unaccessable. And plugins in CCSM lost all of their icons. Still looking for a solution.

---

### Post by Martje_001 on 2008-05-05
Remove compiz from synaptic:
```
sudo apt-get remove libcompiz* compiz* compiz compizconfig-backend-gconf compizconfig-backend-kconfig libdecoration0 compizconfig-settings-manager python-compizconfig emerald
```
Remove all left behind trash:
```
sudo rm -rf /etc/compiz* > /dev/null 2>&1
sudo rm -rf /etc/xdg/compiz* > /dev/null 2>&1
sudo rm -rf /home/*/.compiz* > /dev/null 2>&1
sudo rm -rf /home/*/.gconf/apps/compiz* > /dev/null 2>&1
sudo rm -rf /root/.compiz* > /dev/null 2>&1
sudo rm -rf /usr/bin/compiz* > /dev/null 2>&1
sudo rm -rf /usr/bin/bcop > /dev/null 2>&1
sudo rm -rf /usr/bin/ccsm > /dev/null 2>&1
sudo rm -rf /usr/bin/emerald* > /dev/null 2>&1
sudo rm -rf /usr/bin/fusion-icon > /dev/null 2>&1
sudo rm -rf /usr/bin/gtk-window-decorator > /dev/null 2>&1
sudo rm -rf /usr/etc/compiz* > /dev/null 2>&1
sudo rm -rf /usr/etc/gconf/schemas/compiz* > /dev/null 2>&1
sudo rm -rf /usr/include/compiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/compiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/emerald* > /dev/null 2>&1
sudo rm -rf /usr/lib/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/lib/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/lib/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/compiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/emerald* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/lib/pkgconfig/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/share/compiz* > /dev/null 2>&1
sudo rm -rf /usr/share/bcop* > /dev/null 2>&1
sudo rm -rf /usr/share/ccsm* > /dev/null 2>&1
sudo rm -rf /usr/share/emerald* > /dev/null 2>&1
sudo rm -rf /usr/share/pkgconfig/bcop.pc > /dev/null 2>&1
sudo rm -rf /usr/local/bin/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/bin/bcop > /dev/null 2>&1
sudo rm -rf /usr/local/bin/ccsm > /dev/null 2>&1
sudo rm -rf /usr/local/bin/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/bin/fusion-icon > /dev/null 2>&1
sudo rm -rf /usr/local/bin/gtk-window-decorator > /dev/null 2>&1
sudo rm -rf /usr/local/etc/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/etc/gconf/schemas/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/include/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/libcompiz* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/libdecoration* > /dev/null 2>&1
sudo rm -rf /usr/local/lib/pkgconfig/libemerald* > /dev/null 2>&1
sudo rm -rf /usr/local/share/compiz* > /dev/null 2>&1
sudo rm -rf /usr/local/share/bcop* > /dev/null 2>&1
sudo rm -rf /usr/local/share/ccsm* > /dev/null 2>&1
sudo rm -rf /usr/local/share/emerald* > /dev/null 2>&1
sudo rm -rf /usr/local/share/pkgconfig/bcop.pc > /dev/null 2>&1
sudo rm /usr/local/share/locale/*/LC_MESSAGES/*compiz*.mo > /dev/null 2>&1
sudo rm /usr/share/locale-langpack/*/LC_MESSAGES/compiz* > /dev/null 2>&1
sudo rm /usr/lib/window-manager-settings/libcompiz.so > /dev/null 2>&1
sudo rm /usr/lib/window-manager-settings/libcompiz.a > /dev/null 2>&1
sudo rm /usr/lib/window-manager-settings/libcompiz.la > /dev/null 2>&1
sudo rm /usr/local/lib/python2.5/site-packages/compiz* > /dev/null 2>&1
```
Remove compiz-git:
```
sudo apt-get remove compiz-git
sudo mv /etc/apt/sources.list /etc/apt/sources.list1
sudo apt-get update
sudo cp /etc/apt/sources.list1 /etc/apt/sources.list
sudo apt-get update
```

Install compiz either with my script or with synaptic. Make sure you enable 'decorations' in CompizConfig Settings Manager!

---

### Post by Martje_001 on 2008-05-05
> **Lacrimstein said:**
> Emerald wouldn't even start, stating libemerald0.so is unaccessable. 
Download my script and do
```
./compiz-git patch
```
Edit: Newest compiz-git should do this automatically.

---

### Post by pingpongboss on 2008-05-05
Hey Martje is there a changelog for your new script version?

---

### Post by Martje_001 on 2008-05-05
hey pingpongboss, glad to see you back ;)

You mean from the previous version? No there isn't because it is a complete rewrite. But, I keep a changelog from this one:
```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
cat changelog
```

---

### Post by pingpongboss on 2008-05-05
> **Martje_001 said:**
> hey pingpongboss, glad to see you back ;)

You mean from the previous version? No there isn't because it is a complete rewrite. But, I keep a changelog from this one:
```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
cat changelog
```

gotcha. I'll definitely check it out later. How does your script handle plugins that are not included by default in your script? For example if I want to compile/install the Dodge plugin from git everytime I update compiz using your script. ([http://gitweb.compiz-fusion.org/?p=users/rcxdude/dodge;a=summary](http://gitweb.compiz-fusion.org/?p=users/rcxdude/dodge;a=summary))
I haven't tried it out yet but from skimming over the source, it seems like it's something you might want to look at in the future. :)

---

### Post by Martje_001 on 2008-05-05
Well, it does not remove the plugin.. it just doesn't updates it (if that's what you mean). But, do you want the dodge plugin? I can try to add it.

Edit: Dodge plugin added ;)

---

### Post by Het Irv on 2008-05-05
Okay, sorry about the wait, I had a busier weekend than expected,
about the new script....uhhhh
```
hetirv@hetirv-desktop:~$ wget http://www.xs4all.nl/wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
--14:34:12--  http://www.xs4all.nl/wget
           => `wget'
Resolving www.xs4all.nl... 194.109.6.92
Connecting to www.xs4all.nl|194.109.6.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:34:12 ERROR 404: Not Found.

--14:34:12--  http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
           => `compiz-git-newest.tar.gz'
Connecting to www.xs4all.nl|194.109.6.92|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,122 (5.0K) [application/x-tar]

100%[====================================>] 5,122         --.--K/s             

14:34:13 (43.52 KB/s) - `compiz-git-newest.tar.gz' saved [5122/5122]


FINISHED --14:34:13--
Downloaded: 5,122 bytes in 1 files
hetirv@hetirv-desktop:~$ tar xzf compiz-git-newest.tar.gz
hetirv@hetirv-desktop:~$ cd compiz-git
hetirv@hetirv-desktop:~/compiz-git$ ./compiz-git install
You're not root. Is it ok to use sudo command? (yes/no): yes

Currently this script supports:

1) Debian Sid (gnome)
2) Debian Sid (kde)
3) Debian Lenny (gnome)
4) Debian Lenny (kde)
5) Ubuntu Gutsy (gnome)
6) Kubuntu Gutsy (kde)
7) Ubuntu Hardy (gnome)

Please pick a distribution (number): 7    

Found 1 repo, autoselecting 'annongit.opencompositing.org'.

Save settings? (yes/no): y
Save settings? (yes/no): y
Save settings? (yes/no): y
Save settings? (yes/no): y
Save settings? (yes/no): y
Save settings? (yes/no): 

```

I am thinking that Save settings should only come up once. Do you know what has happened?  I am thinking that when It asked me if I should be root, it should have asked for a password and when it gets here It wouldn't bug out like this.  

I am gonna try again with sudo just to see if it works.

EDIT: or it could be that you have to spell out 'Yes' instead of using 'y':oops:.  Might I suggest an error message saying something here.

---

### Post by Zorael on 2008-05-05
Kubuntu Hardy added yet? :>

---

### Post by Martje_001 on 2008-05-05
> **Het Irv said:**
> EDIT: or it could be that you have to spell out 'Yes' instead of using 'y':oops:.  Might I suggest an error message saying something here.
You have to typ 'yes' indeed.. :rolleyes:;)

> Kubuntu Hardy added yet? :>  
Don't be impatient! :P
It's more work than I expected..

---

### Post by Het Irv on 2008-05-05
I cannot get emerald to work ```
(emerald-theme-manager:10438): Gtk-WARNING **: You must override the default 'drag_data_received' handler on GtkTreeView when using models that don't support the GtkTreeDragDest interface and enabling drag-and-drop. The simplest way to do this is to connect to 'drag_data_received' and call g_signal_stop_emission_by_name() in your signal handler to prevent the default handler from running. Look at the source code for the default handler in gtktreeview.c to get an idea what your handler should do. (gtktreeview.c is in the GTK source code.) If you're using GTK from a language other than C, there may be a more natural way to override default handlers, e.g. via derivation.
```

This appers in the terminal if I double click on a theme.  This is being run on a testing partition, so there isn't much installed on here. Any ideas?

Also I cannot get any more than two desktops
```
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

---

### Post by Het Irv on 2008-05-05
Looking at your script, it think many of the problems that I am experienceing seem to be bugs with compiz, not your script.  Is there a way that you could install version 0.7.4 of the ccsm instead of 0.7.5. 0.7.4 is the lastest version that has been released for general use.  I think most of the problems that I have seen in the hour I have been playing with it are caused by Compiz itself and is no fault of your own (unless you are a dev for Compiz).

---

### Post by jryprt on 2008-05-05
Hi is there a way to completely remove your script & all it downloaded , compiz does not work now  I cannot get Advanced Desktop Effects Settings anymore now its stays as compizconfig setting manager. I would like to go back to what I had. 
Thank you Jerry

---

### Post by jylertones on 2008-05-05
When I try to install compiz using the script, I get the following output. It says that it is downloading the folders but then it can't find them.

```
Configuration-file says to use sudo, following.

Distribution specified in configurationfile, following.

Found 1 repo, autoselecting 'annongit.opencompositing.org'.

No settings changed, skipping question.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcompizconfig0 for regex 'libcompiz*'
Note, selecting libcompizconfig-backend-gconf for regex 'libcompiz*'
Note, selecting libcompizconfig0-dev for regex 'libcompiz*'
Note, selecting libcompizconfig-backend-kconfig for regex 'libcompiz*'
E: Couldn't find package compiz-git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  autoconf autotools-dev curl libdigest-sha1-perl liberror-perl libgail-dev 
  libgnutlsxx13 libkadm55 libkrb5-dev libltdl3-dev liblzo1 liblzo2-dev 
  libpixman-1-dev libpthread-stubs0 libpthread-stubs0-dev libxcb-xlib0-dev 
  libxcb1-dev libxml2-dev m4 orbit2 python-all python-dev python2.4 
  python2.4-dev python2.4-minimal python2.5-dev 
The following NEW packages will be installed:
  autoconf automake autotools-dev build-essential comerr-dev curl diffstat 
  enscript g++ g++-4.2 gawk git-core hspell intltool libacl1-dev 
  libart-2.0-dev libasound2-dev libaspell-dev libatk1.0-dev libattr1-dev 
  libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev 
  libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libbz2-dev 
  libcairo2-dev libcroco3-dev libcupsys2-dev libdbus-1-dev 
  libdbus-glib-1-dev libdigest-sha1-perl liberror-perl libesd0-dev 
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libfuse-dev libgail-dev 
  libgconf2-dev libgcrypt11-dev libgl1-mesa-dev libglade2-dev 
  libglib2.0-dev libglu1-mesa-dev libgnome-desktop-dev libgnome-keyring-dev 
  libgnome-window-settings-dev libgnome2-dev libgnomecanvas2-dev 
  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 
  libgpg-error-dev libgsf-1-dev libgtk2.0-dev libice-dev libidl-dev 
  libidn11-dev libjasper-dev libjpeg62-dev libkadm55 libkrb5-dev 
  liblcms1-dev libltdl3-dev liblua50 liblua50-dev liblualib50 
  liblualib50-dev liblzo-dev liblzo1 liblzo2-dev libmetacity-dev libmng-dev 
  libnotify-dev libogg-dev libopencdk10-dev libopenexr-dev liborbit2-dev 
  libpango1.0-dev libpcre3-dev libpcrecpp0 libpixman-1-dev libpng12-dev 
  libpopt-dev libpthread-stubs0 libpthread-stubs0-dev librsvg2-dev 
  libsasl2-dev libselinux1-dev libsepol1-dev libsm-dev libssl-dev 
  libstartup-notification0-dev libstdc++6-4.2-dev libtasn1-3-dev 
  libtiff4-dev libtiffxx0c2 libtool libvorbis-dev libwnck-dev libx11-dev 
  libx11-xcb-dev libxau-dev libxcb-xlib0-dev libxcb1-dev libxcomposite-dev 
  libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev 
  libxft-dev libxi-dev libxinerama-dev libxml2-dev libxmu-dev 
  libxmu-headers libxrandr-dev libxrender-dev libxres-dev libxslt1-dev 
  libxss-dev libxt-dev lua50 m4 mesa-common-dev orbit2 poster psutils 
  python-all python-all-dev python-dev python-pyrex python2.4 python2.4-dev 
  python2.4-minimal python2.5-dev quilt x11proto-composite-dev 
  x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-gl-dev 
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev 
  x11proto-resource-dev x11proto-scrnsaver-dev x11proto-xext-dev 
  x11proto-xinerama-dev xtrans-dev 
0 packages upgraded, 156 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/44.4MB of archives. After unpacking 157MB will be used.
Writing extended state information... Done
Extracting templates from packages: 100%
dpkg: parse error, in file `/var/lib/dpkg/available' near line 389 package `libnjb5':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 389 package `libnjb5':
 missing version
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             

Pulling compiz from git... done!
Pulling ccsm from git... done!
Pulling compizconfig-python from git... done!
Pulling libcompizconfig from git... done!
Pulling emerald from git... done!
Pulling emerald-themes from git... done!
Pulling i18n from git... done!
Pulling bcop from git... done!
Pulling compiz-manager from git... done!
Pulling plugins-extra from git... done!
Pulling loginout from git... done!
Pulling plugins-main from git... done!
Pulling plugins-unsupported from git... done!
Pulling wallpaper from git... done!
Pulling photowheel from git... done!
Pulling workspacenames from git... done!
Pulling atlantis2 from git... done!
Pulling snowglobe from git... done!
Pulling screensaver from git... done!
Pulling freewins from git... done!
Pulling anaglyph from git... done!
Pulling fusion-icon from git... done!
Pulling compizconfig-backend-gconf from git... done!
./compiz-git: line 168: cd: compiz: No such file or directory
Compiz
./compiz-git: line 170: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: bcop: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: libcompizconfig: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: compizconfig-python: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: compizconfig-backend-gconf: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: emerald: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: emerald-themes: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: i18n: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: plugins-extra: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: plugins-main: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: plugins-unsupported: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: anaglyph: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: atlantis2: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: freewins: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: loginout: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: photowheel: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: screensaver: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: snowglobe: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: wallpaper: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: workspacenames: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 209: cd: fusion-icon: No such file or directory
python: can't open file './setup.py': [Errno 2] No such file or directory
python: can't open file './setup.py': [Errno 2] No such file or directory
./compiz-git: line 215: cd: ccsm: No such file or directory
python: can't open file './setup.py': [Errno 2] No such file or directory
python: can't open file './setup.py': [Errno 2] No such file or directory

```

---

### Post by pingpongboss on 2008-05-06
> **jylertones said:**
> When I try to install compiz using the script, I get the following output. It says that it is downloading the folders but then it can't find them.

```
Configuration-file says to use sudo, following.

Distribution specified in configurationfile, following.

Found 1 repo, autoselecting 'annongit.opencompositing.org'.

No settings changed, skipping question.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcompizconfig0 for regex 'libcompiz*'
Note, selecting libcompizconfig-backend-gconf for regex 'libcompiz*'
Note, selecting libcompizconfig0-dev for regex 'libcompiz*'
Note, selecting libcompizconfig-backend-kconfig for regex 'libcompiz*'
E: Couldn't find package compiz-git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  autoconf autotools-dev curl libdigest-sha1-perl liberror-perl libgail-dev 
  libgnutlsxx13 libkadm55 libkrb5-dev libltdl3-dev liblzo1 liblzo2-dev 
  libpixman-1-dev libpthread-stubs0 libpthread-stubs0-dev libxcb-xlib0-dev 
  libxcb1-dev libxml2-dev m4 orbit2 python-all python-dev python2.4 
  python2.4-dev python2.4-minimal python2.5-dev 
The following NEW packages will be installed:
  autoconf automake autotools-dev build-essential comerr-dev curl diffstat 
  enscript g++ g++-4.2 gawk git-core hspell intltool libacl1-dev 
  libart-2.0-dev libasound2-dev libaspell-dev libatk1.0-dev libattr1-dev 
  libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev 
  libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libbz2-dev 
  libcairo2-dev libcroco3-dev libcupsys2-dev libdbus-1-dev 
  libdbus-glib-1-dev libdigest-sha1-perl liberror-perl libesd0-dev 
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libfuse-dev libgail-dev 
  libgconf2-dev libgcrypt11-dev libgl1-mesa-dev libglade2-dev 
  libglib2.0-dev libglu1-mesa-dev libgnome-desktop-dev libgnome-keyring-dev 
  libgnome-window-settings-dev libgnome2-dev libgnomecanvas2-dev 
  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 
  libgpg-error-dev libgsf-1-dev libgtk2.0-dev libice-dev libidl-dev 
  libidn11-dev libjasper-dev libjpeg62-dev libkadm55 libkrb5-dev 
  liblcms1-dev libltdl3-dev liblua50 liblua50-dev liblualib50 
  liblualib50-dev liblzo-dev liblzo1 liblzo2-dev libmetacity-dev libmng-dev 
  libnotify-dev libogg-dev libopencdk10-dev libopenexr-dev liborbit2-dev 
  libpango1.0-dev libpcre3-dev libpcrecpp0 libpixman-1-dev libpng12-dev 
  libpopt-dev libpthread-stubs0 libpthread-stubs0-dev librsvg2-dev 
  libsasl2-dev libselinux1-dev libsepol1-dev libsm-dev libssl-dev 
  libstartup-notification0-dev libstdc++6-4.2-dev libtasn1-3-dev 
  libtiff4-dev libtiffxx0c2 libtool libvorbis-dev libwnck-dev libx11-dev 
  libx11-xcb-dev libxau-dev libxcb-xlib0-dev libxcb1-dev libxcomposite-dev 
  libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev 
  libxft-dev libxi-dev libxinerama-dev libxml2-dev libxmu-dev 
  libxmu-headers libxrandr-dev libxrender-dev libxres-dev libxslt1-dev 
  libxss-dev libxt-dev lua50 m4 mesa-common-dev orbit2 poster psutils 
  python-all python-all-dev python-dev python-pyrex python2.4 python2.4-dev 
  python2.4-minimal python2.5-dev quilt x11proto-composite-dev 
  x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-gl-dev 
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev 
  x11proto-resource-dev x11proto-scrnsaver-dev x11proto-xext-dev 
  x11proto-xinerama-dev xtrans-dev 
0 packages upgraded, 156 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/44.4MB of archives. After unpacking 157MB will be used.
Writing extended state information... Done
Extracting templates from packages: 100%
dpkg: parse error, in file `/var/lib/dpkg/available' near line 389 package `libnjb5':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 389 package `libnjb5':
 missing version
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             

Pulling compiz from git... done!
Pulling ccsm from git... done!
Pulling compizconfig-python from git... done!
Pulling libcompizconfig from git... done!
Pulling emerald from git... done!
Pulling emerald-themes from git... done!
Pulling i18n from git... done!
Pulling bcop from git... done!
Pulling compiz-manager from git... done!
Pulling plugins-extra from git... done!
Pulling loginout from git... done!
Pulling plugins-main from git... done!
Pulling plugins-unsupported from git... done!
Pulling wallpaper from git... done!
Pulling photowheel from git... done!
Pulling workspacenames from git... done!
Pulling atlantis2 from git... done!
Pulling snowglobe from git... done!
Pulling screensaver from git... done!
Pulling freewins from git... done!
Pulling anaglyph from git... done!
Pulling fusion-icon from git... done!
Pulling compizconfig-backend-gconf from git... done!
./compiz-git: line 168: cd: compiz: No such file or directory
Compiz
./compiz-git: line 170: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: bcop: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: libcompizconfig: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: compizconfig-python: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: compizconfig-backend-gconf: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: emerald: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: emerald-themes: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: i18n: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: plugins-extra: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: plugins-main: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 193: cd: plugins-unsupported: No such file or directory
./compiz-git: line 194: ./autogen.sh: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: anaglyph: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: atlantis2: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: freewins: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: loginout: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: photowheel: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: screensaver: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: snowglobe: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: wallpaper: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 202: cd: workspacenames: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./compiz-git: line 209: cd: fusion-icon: No such file or directory
python: can't open file './setup.py': [Errno 2] No such file or directory
python: can't open file './setup.py': [Errno 2] No such file or directory
./compiz-git: line 215: cd: ccsm: No such file or directory
python: can't open file './setup.py': [Errno 2] No such file or directory
python: can't open file './setup.py': [Errno 2] No such file or directory

```

The folders are found in ```
~/.compiz-git
```

---

### Post by pingpongboss on 2008-05-06
Hi Martje a few things:
First of all the script worked :P But a few questions below


Is the script downloading from master or noxcb-master?

Will it tell you if files are updated? Or will it only say "Pulling xxxxx from git... " [COLOR="DarkRed"]Edit: Looks like what you're doing is, everytime we use your script, it deletes every source folder, then git clone them again. This is less efficient than detecting the folders, cd into them, then do a git pull to update. However this way would be harder since you'd have to write code to detect whether or not the user has already initiated a git repository for each folder.[/COLOR]

Why is python2.4 needed? version 2.5 works when compiling compiz, and using your script the first time with v2.4 gave an error message.

There is no longer a final message telling new users what to do after they have installed using your script. Having "Please run fusion-icon" or something like you had before would be nice.

Also, the widget layer plugin is no longer working for some reason. It might be because the Italian script incorporated it while yours didn't. I'll look into that a bit further.
[COLOR="DarkRed"]Edit: It seems that Widget Layer should be included in PluginsExtra, so I don't know why it's not working right with your script.  [/COLOR]```
compiz (core) - Error: Couldn't load plugin 'widget'
```
[COLOR="DarkRed"]Edit2: Installing widget from git (git-clone git://anongit.compiz-fusion.org/fusion/plugins/widget) makes it work again. Still, this should not happen.
[/COLOR]
[COLOR="DarkRed"]Edit3: In your script line 133, ```
rm -rf anaglyph atlantis2 bcop ccsm compiz compizconfig-python compiz-manager emerald emerald-themes freewins i18n libcompizconfig loginout photowheel plugins-extra plugins-main plugins-unsupported screensaver snowglobe wallpaper wiimote wiitrack workspacenames libcompizconfig compizconfig-backend-gconf compizconfig-backend-kconfig fusion-icon
``` should have dodge at the end. Other wise it fails to remove&redownload the folder.
[/COLOR]
For those people who lose their window borders after running fusion-icon, try this: Right click the icon in the notification zone, and select quit. Run fusion-icon again from the terminal. If you see something like ```
*** glibc detected *** compiz: corrupted double-linked list: 0x0000000000b98200 ***
``` then run  killall -9 compiz and retry fusion-icon.

---

### Post by jryprt on 2008-05-06
> **jryprt said:**
> Hi is there a way to completely remove your script & all it downloaded , compiz does not work now  I cannot get Advanced Desktop Effects Settings anymore now its stays as compizconfig setting manager. I would like to go back to what I had. 
Thank you Jerry
Does anyone know how?
I tried 
cd compiz-git
./compiz-git uninstall
cd ..
rm -r compiz-git

did not work

---

### Post by t0n1 on 2008-05-06
Sadly, the wallpaper plugin is still not functioning.
This is a plugin to have a different wallpaper on each workspace, when used with desktop wall. I have read on the compiz forums that making it work would require patching nautilus.
I wish there was an easier way.

---

### Post by pingpongboss on 2008-05-06
> **jryprt said:**
> Does anyone know how?
I tried 
cd compiz-git
./compiz-git uninstall
cd ..
rm -r compiz-git

did not work

not entirely sure, but you may try this:

cd into ~/.compiz-git

cd into every folder and do a **sudo make uninstall**
This only works if the script didn't already delete all the source folders.

---

### Post by Martje_001 on 2008-05-07
> **jryprt said:**
> Does anyone know how?
I tried 
cd compiz-git
./compiz-git uninstall
cd ..
rm -r compiz-git

did not work
You need to install compiz again with Synaptic. Search for 'compiz' and install it, plus plugins-main, plugins-extra.

---

### Post by Martje_001 on 2008-05-07
> **pingpongboss said:**
> not entirely sure, but you may try this:

cd into ~/.compiz-git

cd into every folder and do a **sudo make uninstall**
This only works if the script didn't already delete all the source folders.
That can be easily done by:
```
for i in `ls`; do
cd $i
sudo make uninstall
cd ..
done
```

---

### Post by Martje_001 on 2008-05-07
> **pingpongboss said:**
> Is the script downloading from master or noxcb-master?
As far as I know, master.

> **pingpongboss said:**
> Will it tell you if files are updated? Or will it only say "Pulling xxxxx from git... " [COLOR="DarkRed"]Edit: Looks like what you're doing is, everytime we use your script, it deletes every source folder, then git clone them again. This is less efficient than detecting the folders, cd into them, then do a git pull to update. However this way would be harder since you'd have to write code to detect whether or not the user has already initiated a git repository for each folder.[/COLOR]
I know, but what are the commands for updating? I couldn't find them :/ :(

> Why is python2.4 needed? version 2.5 works when compiling compiz, and using your script the first time with v2.4 gave an error message.

Err.. 2.5 gets also installed.. (python-all-dev, python-all)

> There is no longer a final message telling new users what to do after they have installed using your script. Having "Please run fusion-icon" or something like you had before would be nice.
Fixing that.

> Also, the widget layer plugin is no longer working for some reason. 

...

[COLOR="DarkRed"]Edit2: Installing widget from git (git-clone git://anongit.compiz-fusion.org/fusion/plugins/widget) makes it work again. Still, this should not happen.
[/COLOR]
Fixing that too.

> [COLOR="DarkRed"]Edit3: In your script line 133, ```
rm -rf anaglyph atlantis2 bcop ccsm compiz compizconfig-python compiz-manager emerald emerald-themes freewins i18n libcompizconfig loginout photowheel plugins-extra plugins-main plugins-unsupported screensaver snowglobe wallpaper wiimote wiitrack workspacenames libcompizconfig compizconfig-backend-gconf compizconfig-backend-kconfig fusion-icon
``` should have dodge at the end. Other wise it fails to remove&redownload the folder.
[/COLOR]
A dodge at the end means 'remove this folder', and this should not happen.

Edit: Aaagh.. my English is very bad again.. I thought you meant a dot (.)... sorry :P
Fixing!

```
For those people who lose their window borders after running fusion-icon, try this: Right click the icon in the notification zone, and select quit. Run fusion-icon again from the terminal. If you see something like [CODE]*** glibc detected *** compiz: corrupted double-linked list: 0x0000000000b98200 ***
``` then run  killall -9 compiz and retry fusion-icon.[/QUOTE][/CODE]
Also try enabling decoration in ccsm.


pingpongboss, I thank you very very much for your help!

---

### Post by Martje_001 on 2008-05-07
*Added update function
*Fixed bug stopping compiz-git from pulling from git
*Fixed widget bug
*Message after installation added

Update compiz-fusion with:
```
./compiz-fusion update
```

---

### Post by Simpe on 2008-05-07
Hi, when I'm trying to install this it's like the terminal i going into a loop, an then never finishes the installation?

Any suggestions? Do I need to uninstall old versions of compiz-fusion, and if I do, then how do i do it?

Simon

---

### Post by Zorael on 2008-05-07
Where's my Screensaver plugin? *hint!*

Also Kubuntu Hardy! *jab!*

---

### Post by Het Irv on 2008-05-07
> **Martje_001 said:**
> *Added update function
*Fixed bug stopping compiz-git from pulling from git
*Fixed widget bug
*Message after installation added

Update compiz-fusion with:
```
./compiz-fusion update
```
Do we have to download a new script to get the update function?  
Or maybe I just didn't do it right.

---

### Post by Martje_001 on 2008-05-08
> **Simpe said:**
> Hi, when I'm trying to install this it's like the terminal i going into a loop, an then never finishes the installation?
Can you give an example? Output?

> Where's my Screensaver plugin? *hint!*

Also Kubuntu Hardy! *jab!*
Fixing those..

> Do we have to download a new script to get the update function? 
Or maybe I just didn't do it right. 
Yes, you have to download it.

---

### Post by Simpe on 2008-05-08
[QUOTE=Martje_001;4908744]Can you give an example? Output?


I think i have fixed it myself,

thanks anyway..

---

### Post by wudsta on 2008-05-08
This pretty much shafted my install... I am trying to uninstall using the scripts mentioned in the post but I cannot get it to work. I want to uninstall and return to my previous Compiz installation.

---

### Post by Martje_001 on 2008-05-08
> **wudsta said:**
> This pretty much shafted my install... I am trying to uninstall using the scripts mentioned in the post but I cannot get it to work. I want to uninstall and return to my previous Compiz installation.
Don't say I didn't warn you..

```
cd compiz-git
./compiz-git uninstall
sudo apt-get install compiz
```

---

### Post by Zorael on 2008-05-08
If it won't install compiz, you may have to dpkg --purge any packages it complains about.
```
Blahblah can't install compizconfig-settings-manager, something something keeping old settings
Something something python something else
**zorael@sunspire:~$ sudo dpkg --purge compizconfig-settings-manager**
Removing compizconfig-settings-manager...
zorael@sunspire:~$ sudo aptitude install compizconfig-settings-manager
Installing compizconfig-settings-manager...
```

---

### Post by Het Irv on 2008-05-08
I have the new script, and I am having some problems.
Visually, the ccsm looks the same as the one that I am using on my stable partition, but it is acting totally different.  In the general options I cannot change the horizontal desktop size to four, any other number, yes, four no.

I don't use the scale plug-in, but if I start the ccsm though command line while the scale plug-in is enabled I get this:
```
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

This doesn't seem to be any fault of you script, but bugs in Compiz itself.  Where should I take these questions?

---

### Post by Martje_001 on 2008-05-08
You may want to try it here:
[http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

---

### Post by Zorael on 2008-05-08
New script works great, love the update argument.

The current build fixes my Nvidia redraw corruption, so I'm beside myself with joy~

---

### Post by pingpongboss on 2008-05-08
> **Het Irv said:**
> I have the new script, and I am having some problems.
Visually, the ccsm looks the same as the one that I am using on my stable partition, but it is acting totally different.  In the general options I cannot change the horizontal desktop size to four, any other number, yes, four no.

I don't use the scale plug-in, but if I start the ccsm though command line while the scale plug-in is enabled I get this:
```
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

This doesn't seem to be any fault of you script, but bugs in Compiz itself.  Where should I take these questions?

You should not use the GCONF backend. Go into ccsm, go to Preferences in the lower left-hand site, then for backend choose Flat-file. GCONF has alot of problems.

---

### Post by Het Irv on 2008-05-08
Can anyone else set their Horizontal Virtual Desktop Size to Four?

Changing to Flat File fixed that problem... but now middle clicking to rotate cube isn't working

---

### Post by pingpongboss on 2008-05-08
Martje, thanks for listening to my recommendations! A few more things:

When I'm updating compiz, I like to see what files get changed from the git pull. It just gives me an idea of what is being changed, or what new things are being added, etc. **It'd be nice if you had an option in your script to not stop all verbose messages** or something. Same thing for compiling/installing - **it'd be nice to hide compilation messages and only display errors and warnings.**


I updated using your script, and it seems like you are selectively building the components that are updated (cause the update is so fast and there is little output). Meaning if compiz updates but ccsm doesnt, then only compiz will be rebuilt.** Is that what you are doing? Are you sure doing it this way won't break anything?** My previous experience tells me that rebuilding some parts of compiz and not others will break the other parts. Maybe you could look into this.

Another idea: When the user already has the source folders in ~/.compiz-git, it means they already used your script using **./compiz-git install**. How about, the next time they run ./compiz-git install, you detect that they already have the source code, and offer to do an **update** instead?

---

### Post by pingpongboss on 2008-05-08
> **Het Irv said:**
> Can anyone else set their Horizontal Virtual Desktop Size to Four?

Changing to Flat File fixed that problem... but now middle clicking to rotate cube isn't working

I've found out that sometimes, randomly, the Viewport Switcher plugin doesn't work. I can't middle click desktop, or use scroll wheel on desktop to change sides of the cube. It's not this script writer's problem, AFAIK. make sure you have the viewport switcher plugin enabled in the first place.

---

### Post by Genius314 on 2008-05-08
So how exactly do I upgrade? Do I just do the install again?

Also, I've gotten a few problems... not sure whether its the script not installing correctly, or if its just Compiz-Git...
1. Shelf and Widget Layer don't work. They automatically disable themselves.
2. Cube Caps appears in the list, which shouldn't happen (should it?), since its been fused with the other cube effects.
3. Cube Atlantis... is much different from the last time I tried it. Is this 1 or 2? Seems less customizable, but looks better, so I'm not sure...
4. Cube Reflection and Deformation... The reflection works, but the cube won't turn into a sphere or cylinder. (It worked a while ago, then it stopped...)
5. Wallpaper didn't install... is it supposed to?

---

### Post by t0n1 on 2008-05-08
I have run into a small problem with this script.
Namely, how can the changes be reverted. I tried
```
cd compiz-git
./compiz-git uninstall

```
After that, I have reinstalled compiz through synaptic.
But! When I try to run compiz from the terminal, I get:
```

The program 'compiz' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-core
bash: compiz: command not found

```
Any help will be greatly appreciated.

---

### Post by pingpongboss on 2008-05-08
> **t0n1 said:**
> I have run into a small problem with this script.
Namely, how can the changes be reverted. I tried
```
cd compiz-git
./compiz-git uninstall

```
After that, I have reinstalled compiz through synaptic.
But! When I try to run compiz from the terminal, I get:
```

The program 'compiz' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-core
bash: compiz: command not found

```
Any help will be greatly appreciated.

Sorry if this sounds stupid, but did you install compiz-core? You didn't make it clear how you "reinstalled compiz through synaptic"

---

### Post by SomeGuyDude on 2008-05-08
Quick Q: do I have to uninstall everything I currently have to use this?

---

### Post by t0n1 on 2008-05-09
> **pingpongboss said:**
> Sorry if this sounds stupid, but did you install compiz-core? You didn't make it clear how you "reinstalled compiz through synaptic"

Yes, I have reinstalled all the packages associated with compiz: compiz-core, compiz settings manager, emerald, etc.

---

### Post by Martje_001 on 2008-05-09
> **SomeGuyDude said:**
> Quick Q: do I have to uninstall everything I currently have to use this?
The script will do this for you.

```

Also, I've gotten a few problems... not sure whether its the script not installing correctly, or if its just Compiz-Git...
1. Shelf and Widget Layer don't work. They automatically disable themselves.
2. Cube Caps appears in the list, which shouldn't happen (should it?), since its been fused with the other cube effects.
3. Cube Atlantis... is much different from the last time I tried it. Is this 1 or 2? Seems less customizable, but looks better, so I'm not sure...
4. Cube Reflection and Deformation... The reflection works, but the cube won't turn into a sphere or cylinder. (It worked a while ago, then it stopped...)
5. Wallpaper didn't install... is it supposed to? 
```
1. Bug, please report
2. It should if I'm correct..
3. 2
4. Have you tried [this](http://img401.imageshack.us/img401/51/schermafdrukps1.png)?
5. It should.. is it in ~/.compiz-git?

---

### Post by Martje_001 on 2008-05-09
> **t0n1 said:**
> Yes, I have reinstalled all the packages associated with compiz: compiz-core, compiz settings manager, emerald, etc.
Can you give the ouput of:
```
ls /usr/bin | grep compiz
ls /usr/local/bin | grep compiz
```
?

Also: try to reinstall again (with synaptic).

---

### Post by Martje_001 on 2008-05-09
> **pingpongboss said:**
> Martje, thanks for listening to my recommendations! A few more things:
You're welcome

> When I'm updating compiz, I like to see what files get changed from the git pull. It just gives me an idea of what is being changed, or what new things are being added, etc. **It'd be nice if you had an option in your script to not stop all verbose messages** or something. Same thing for compiling/installing - **it'd be nice to hide compilation messages and only display errors and warnings.**

Working on it!

> I updated using your script, and it seems like you are selectively building the components that are updated (cause the update is so fast and there is little output). Meaning if compiz updates but ccsm doesnt, then only compiz will be rebuilt.** Is that what you are doing? Are you sure doing it this way won't break anything?** My previous experience tells me that rebuilding some parts of compiz and not others will break the other parts. Maybe you could look into this.
I've never experienced that sort of problem, but I'll look into it!

> Another idea: When the user already has the source folders in ~/.compiz-git, it means they already used your script using **./compiz-git install**. How about, the next time they run ./compiz-git install, you detect that they already have the source code, and offer to do an **update** instead?
Offer, yes. But not forcing them to. I will look at it.

---

### Post by jfg69 on 2008-05-09
Martje_001
thanks very much for that script, it seems to have worked quite well on my install of Ultimate Edition 1.8x64. Is the cylinder cube/ sphere plug in installed, I didnt see it and was wondering if it is hiding someplace or could be added to your script.

Thanks again!
jfg69

---

### Post by Martje_001 on 2008-05-09
It is called 'cube reflection and deformation' in CompizConfig Settings Manager.

---

### Post by jfg69 on 2008-05-09
> **Martje_001 said:**
> It is called 'cube reflection and deformation' in CompizConfig Settings Manager.

I have the cube reflection, but it wont stay checked. There is no mention of deformation. I guess something went wrong on the compile?


```

jerry@jerry-desktop:~$ ls /usr/bin | grep compiz
compiz
compiz-decorator
compiz.real
jerry@jerry-desktop:~$ ls /usr/local/bin | grep compiz
compiz
jerry@jerry-desktop:~$ 

```

---

### Post by Zorael on 2008-05-09
My plugin is named "Cube Reflection and Deformation", but then I don't have any Photowheel plugin as displayed in your screenie so I'm likely running an older/newer build.

---

### Post by redserpent7 on 2008-05-09
Is there a way to download the git package and install it offline, the installation keeps failing:

Pulling widget from git... failed!

please help....

---

### Post by jfg69 on 2008-05-09
I should probably mention that I'm using a x64 version of HH (Ultimate Edition 1.8x64)

---

### Post by Zorael on 2008-05-09
> **redserpent7 said:**
> Is there a way to download the git package and install it offline, the installation keeps failing:

Pulling widget from git... failed!

please help....
Could something be wrong with your Internet connection? I just completely removed and reinstalled with the script, and it worked without errors.


> **jfg69 said:**
> I should probably mention that I'm using a x64 version of HH (Ultimate Edition 1.8x64)
As mentioned above, I just reinstalled and the plugin is there, called "Cube Reflection and Deformation". Are you, by any chance, using an old build?

---

### Post by jfg69 on 2008-05-09
> As mentioned above, I just reinstalled and the plugin is there, called "Cube Reflection and Deformation". Are you, by any chance, using an old build?

I'm not sure, I'll have to look later, I gotta head out to work. How do I check?

---

### Post by Zorael on 2008-05-09
> **jfg69 said:**
> I'm not sure, I'll have to look later, I gotta head out to work. How do I check?
Huh, I'm not sure. It'd be easy if it was installed with a package.

Entering this lets you know *when* you installed it, at least.
```
zorael@sunspire:~$ ls -l /usr/local/bin/compiz
-rwxr-xr-x 1 root root 1096967 2008-05-09 19:22 /usr/local/bin/compiz
```

---

### Post by Martje_001 on 2008-05-09
> **jfg69 said:**
> I have the cube reflection, but it wont stay checked. There is no mention of deformation. I guess something went wrong on the compile?


```

jerry@jerry-desktop:~$ ls /usr/bin | grep compiz
compiz
compiz-decorator
compiz.real
jerry@jerry-desktop:~$ ls /usr/local/bin | grep compiz
compiz
jerry@jerry-desktop:~$ 

```
That means you have 2 versions of compiz-fusion installed. One from my script and one from synaptic.. please remove compiz with synaptic and use my script again.

---

### Post by Genius314 on 2008-05-09
> **Martje_001 said:**
> 
```

Also, I've gotten a few problems... not sure whether its the script not installing correctly, or if its just Compiz-Git...
1. Shelf and Widget Layer don't work. They automatically disable themselves.
2. Cube Caps appears in the list, which shouldn't happen (should it?), since its been fused with the other cube effects.
3. Cube Atlantis... is much different from the last time I tried it. Is this 1 or 2? Seems less customizable, but looks better, so I'm not sure...
4. Cube Reflection and Deformation... The reflection works, but the cube won't turn into a sphere or cylinder. (It worked a while ago, then it stopped...)
5. Wallpaper didn't install... is it supposed to? 
```
1. Bug, please report
2. It should if I'm correct..
3. 2
4. Have you tried [this](http://img401.imageshack.us/img401/51/schermafdrukps1.png)?
5. It should.. is it in ~/.compiz-git?

4. Yeah, I tried that. Nothing.
5. The folder is there, but there's no wallpaper plugin in CCSM... EDIT: Actually, I'm seeing a lot of plugins in that folder that aren't in CCSM, like Screensaver, Snowglobe, Freewins, Workspace Names, Dodge...

Thanks.

---

### Post by redserpent7 on 2008-05-09
> Originally Posted by redserpent7 View Post
Is there a way to download the git package and install it offline, the installation keeps failing:

Pulling widget from git... failed!

please help....
Could something be wrong with your Internet connection? I just completely removed and reinstalled with the script, and it worked without errors.


actually I don't have any internet flaws, my connection is solid, yes its only 512Kbps but it works and as I was checking the system monitor while downloading, the download rate was a stable 50KBps so I don't think its an internet problem, moreover all other packages downloaded just fine, compiz, emerald, ..., only the widgets are not downloading. I mean its like they just don't exist anymore, I don't have a waiting period, as the installer reaches the pulling widgets from git... it immediately terminates with a failed!!!.

So if there isn't a way to download git as a whole package then extract it offline, is there a way to exclude widgets from the download. I don't really need widgets as I use gdesklets and they work fine for me...

---

### Post by ibuclaw on 2008-05-09
Not sure if someone has already reported this...
Mine compiled fine and runs fine.

But I can only access the new plugins when I run "fusion-icon" as root...
How to I enable them for normal users?

Regards
Iain

---

### Post by Martje_001 on 2008-05-10
Yes.. I'm working on that. Some plugins get installed in ~/.compiz so only root can acces them, because they're in /root.

> So if there isn't a way to download git as a whole package then extract it offline, is there a way to exclude widgets from the download. I don't really need widgets as I use gdesklets and they work fine for me...
Try:
```
rm -rf ~/.compiz-git/widget
```

> 
5. The folder is there, but there's no wallpaper plugin in CCSM... EDIT: Actually, I'm seeing a lot of plugins in that folder that aren't in CCSM, like Screensaver, Snowglobe, Freewins, Workspace Names, Dodge...

same problem as above

---

### Post by Martje_001 on 2008-05-10
```
*Some plugins didn't install themselves systemwide. Fixed by adding 'BUILD_GLOBAL = true' to 'plugin.info'
*Fixed bug in 'widget' plugin
```
Please try the newest version.

---

### Post by Zorael on 2008-05-10
> **Martje_001 said:**
> ```
*Some plugins didn't install themselves systemwide. Fixed by adding 'BUILD_GLOBAL = true' to 'plugin.info'
*Fixed bug in 'widget' plugin
```
Please try the newest version.
Is there a script command to make it upgrade itself, or need I redownload the .tar.gz?

---

### Post by jfg69 on 2008-05-10
> **Martje_001 said:**
> That means you have 2 versions of compiz-fusion installed. One from my script and one from synaptic.. please remove compiz with synaptic and use my script again.

I uninstalled all compiz via the commands you have posted at the beginning of this thread. All seemed to go well upon re-installation using your script, until this point:

```

checking for COMPIZ... configure: error: Package requirements (x11-xcb          xcomposite               xfixes                  xdamage                 xrandr                  xinerama                ice                     sm             libxml-2.0               libxslt                 libstartup-notification-1.0 >= 0.7) were not met:

No package 'x11-xcb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Failed: Executing ./autogen.sh --enable-librsvg --disable-kconfig --disable-kde --disable-kde4


```

I'm not seeing x11-xcb in synaptic..

Incidentally, trying this on my gutsy install before I try it on my hardy.
Where do I go from here?

---

### Post by pingpongboss on 2008-05-11
> **jfg69 said:**
> I uninstalled all compiz via the commands you have posted at the beginning of this thread. All seemed to go well upon re-installation using your script, until this point:

```

checking for COMPIZ... configure: error: Package requirements (x11-xcb          xcomposite               xfixes                  xdamage                 xrandr                  xinerama                ice                     sm             libxml-2.0               libxslt                 libstartup-notification-1.0 >= 0.7) were not met:

No package 'x11-xcb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Failed: Executing ./autogen.sh --enable-librsvg --disable-kconfig --disable-kde --disable-kde4


```

I'm not seeing x11-xcb in synaptic..

Incidentally, trying this on my gutsy install before I try it on my hardy.
Where do I go from here?

x11-xcb is only available in the Hardy repos.

---

### Post by enyckma on 2008-05-11
hi to you all!
i've just installed compiz-git but nothing is changed in my ccsm!
is the same compiz fusion that i had befor installing compiz-git! 
any ideeas to resolve this problem?

P.S. excuze my english!!!

---

### Post by pingpongboss on 2008-05-11
> **enyckma said:**
> hi to you all!
i've just installed compiz-git but nothing is changed in my ccsm!
is the same compiz fusion that i had befor installing compiz-git! 
any ideeas to resolve this problem?

P.S. excuze my english!!!

If you had compiz from the Hardy repository at first, then you should see the new plugin "Cube Reflection and Deformation".

Make sure you restart/reload compiz with fusion-icon.

---

### Post by jfg69 on 2008-05-11
> **pingpongboss said:**
> x11-xcb is only available in the Hardy repos.
Thanks, I pretty much gave up on the gutsy install as I wont really be staying with it anyway. Did manage to get it working (minus the widgets) on HH tho.. Thanks!

jfg69

---

### Post by enyckma on 2008-05-11
> **pingpongboss said:**
> If you had compiz from the Hardy repository at first, then you should see the new plugin "Cube Reflection and Deformation".

Make sure you restart/reload compiz with fusion-icon.

"Cube Reflection and Deformation" is missing from the both ccsm (c-g & c-f), in fact there is no diference between them!!! the only diference is that are not the same option enabled.

---

### Post by castironpants on 2008-05-11
I can't even get the script to work. When I try it, I get this:

> jeremy@box:~/Sources/compiz-git$ ./compiz-git installConfiguration-file says to use sudo, following.

Distribution specified in configurationfile, following.

Found 1 repo, autoselecting 'annongit.opencompositing.org'.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcompizconfig0 for regex 'libcompiz*'
Note, selecting libcompizconfig-backend-gconf for regex 'libcompiz*'
Note, selecting libcompizconfig0-dev for regex 'libcompiz*'
Note, selecting libcompizconfig-backend-kconfig for regex 'libcompiz*'
E: Couldn't find package libcompiz*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

Pulling compiz from git... 


And then it just sort of stops. The same thing happens when I try to use any other git command, or svn for that matter. What's going on?

---

### Post by SomeGuyDude on 2008-05-11
> **castironpants said:**
> I can't even get the script to work. When I try it, I get this:



And then it just sort of stops. The same thing happens when I try to use any other git command, or svn for that matter. What's going on?

Same. Only with compiz-git instead of libcompiz.

---

### Post by Sponzenbroekske on 2008-05-11
How long does the script take, cuz I let it run for like half an hour and it still wasn't finished so I stopped it myself.?

---

### Post by pingpongboss on 2008-05-11
> **Sponzenbroekske said:**
> How long does the script take, cuz I let it run for like half an hour and it still wasn't finished so I stopped it myself.?

Depends on how fast your computer is. Shouldn't take half an hour though. If the CPU is being used by gcc or whatever the compiler is, then the script is still running. Or, it might just take forever to download the source files cause you're on dialup or something?

---

### Post by Cygoku on 2008-05-11
I am under Ubuntu Hardy Heron 32bit, iff I use this script, will it work good?  Is really going to update my sweet little Compiz to latest git version?

What's git anyway?  

Cygoku

---

### Post by pingpongboss on 2008-05-11
> **Cygoku said:**
> I am under Ubuntu Hardy Heron 32bit, iff I use this script, will it work good?  Is really going to update my sweet little Compiz to latest git version?

What's git anyway?  

Cygoku

Git is basically a super up-to-date version of the program. Has all the new features, but may be buggy.

This script is hit-or-miss. It worked for most people but not for some others. There are other scripts to try if this one doesn't work out. I'd say go ahead and try it.

---

### Post by seriey_x2 on 2008-05-12
This script worked for me. However, cube cap plugin was not installed.
Also, I cannot enable splash plugin. When I try to enable splash plugin, what I got is 

[INDENT]failed to load image :compizcap.png
failed to load image :fusioncap.png[/INDENT]

So, how can I install cube cap? and get splash plugin work

---

### Post by crislosi on 2008-05-12
Hi, I'm trying to make a deb package about all plugins but cubeaddon plugin doesn't work, i obtain many errors when i write the make instruction. Can you tell me where i can downlo0ad this plugin fine, please?
Thank you

---

### Post by Het Irv on 2008-05-12
[http://gitweb.compiz-fusion.org/](http://gitweb.compiz-fusion.org/)

Once you make the debs, will there be a repo that can update them?  All of these packages are beta quality and are being updated regularly

---

### Post by crislosi on 2008-05-13
It doesn' t work, i obtain all these errors:

```
convert   : cubeaddon.xml.in -> build/cubeaddon.xml
bcop'ing  : build/cubeaddon.xml -> build/cubeaddon_options.h
bcop'ing  : build/cubeaddon.xml -> build/cubeaddon_options.c
schema    : build/cubeaddon.xml -> build/compiz-cubeaddon.schema
compiling : cubeaddon.c -> build/cubeaddon.locubeaddon.c:77: error: expected specifier-qualifier-list before ‘CubeShouldPaintViewportProc’
cubeaddon.c: En la función ‘cubeaddonChangeCap’:
cubeaddon.c:238: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘topCap’
cubeaddon.c:238: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘bottomCap’
cubeaddon.c: En la función ‘cubeaddonTopImagesChanged’:
cubeaddon.c:270: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘topCap’
cubeaddon.c:271: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘topCap’
cubeaddon.c: En la función ‘cubeaddonBottomImagesChanged’:
cubeaddon.c:285: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘bottomCap’
cubeaddon.c:286: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘bottomCap’
cubeaddon.c: En la función ‘cubeaddonCheckOrientation’:
cubeaddon.c:464: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘reflection’
cubeaddon.c: En la función ‘cubeaddonGetRotation’:
cubeaddon.c:483: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘reflection’
cubeaddon.c:485: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘vRot’
cubeaddon.c:489: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘vRot’
cubeaddon.c: En la función ‘cubeaddonClearTargetOutput’:
cubeaddon.c:500: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘reflection’
cubeaddon.c:504: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘backVRotate’
cubeaddon.c:507: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘reflection’
cubeaddon.c: En la función ‘cubeaddonShouldPaintViewport’:
cubeaddon.c:523: error: ‘CubeScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:523: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:524: error: ‘CubeScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:526: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:526: error: ‘CubeScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:526: error: ‘CubeScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:531: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:560: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c: En la función ‘cubeaddonPaintCap’:
cubeaddon.c:632: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘topCap’
cubeaddon.c:638: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘bottomCap’
cubeaddon.c:650: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:659: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:659: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillNorm’
cubeaddon.c:702: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillIdx’
cubeaddon.c:766: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillIdx’
cubeaddon.c:770: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘topCap’
cubeaddon.c: En la función ‘cubeaddonPaintTop’:
cubeaddon.c:802: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘paintTop’
cubeaddon.c:804: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘paintTop’
cubeaddon.c: En la función ‘cubeaddonPaintBottom’:
cubeaddon.c:831: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘paintBottom’
cubeaddon.c:833: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘paintBottom’
cubeaddon.c: En la función ‘cubeaddonAddWindowGeometry’:
cubeaddon.c:856: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:907: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘tmpRegion’
cubeaddon.c:909: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘tmpRegion’
cubeaddon.c:912: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘tmpRegion’
cubeaddon.c:924: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘nTmpBox’
cubeaddon.c:926: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘tmpBox’
cubeaddon.c:926: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘tmpBox’
cubeaddon.c:927: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘tmpBox’
cubeaddon.c:929: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘nTmpBox’
cubeaddon.c:933: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘tmpBox’
cubeaddon.c:981: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c:982: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c:984: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c:985: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c:1028: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1072: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1073: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c: En la función ‘cubeaddonDrawWindow’:
cubeaddon.c:1102: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c: En la función ‘cubeaddonDrawWindowTexture’:
cubeaddon.c:1138: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1152: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormSize’
cubeaddon.c:1154: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c:1154: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c:1156: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c:1158: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormSize’
cubeaddon.c:1161: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormSize’
cubeaddon.c:1181: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c:1182: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c:1184: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c:1185: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c:1219: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c:1219: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1220: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c:1220: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1221: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c:1225: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c:1225: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1226: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c:1226: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1227: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c:1234: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c: En la función ‘cubeaddonPaintTransformedOutput’:
cubeaddon.c:1271: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘wasDeformed’
cubeaddon.c:1276: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1280: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1298: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1305: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1307: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capDistance’
cubeaddon.c:1313: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1313: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capDeform’
cubeaddon.c:1313: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capDistance’
cubeaddon.c:1314: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capDeformType’
cubeaddon.c:1324: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1325: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1326: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1327: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillNorm’
cubeaddon.c:1328: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillNorm’
cubeaddon.c:1329: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillNorm’
cubeaddon.c:1337: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1341: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1347: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillNorm’
cubeaddon.c:1358: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1359: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1359: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1360: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1361: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillNorm’
cubeaddon.c:1362: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillNorm’
cubeaddon.c:1363: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillNorm’
cubeaddon.c:1376: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1378: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1380: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1387: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillNorm’
cubeaddon.c:1397: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capDeform’
cubeaddon.c:1397: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1398: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capDistance’
cubeaddon.c:1399: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capDeformType’
cubeaddon.c:1402: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘first’
cubeaddon.c:1404: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘first’
cubeaddon.c:1405: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘reflection’
cubeaddon.c:1437: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘backVRotate’
cubeaddon.c:1459: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1460: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1461: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1462: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1482: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1496: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1504: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1504: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1505: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1510: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1515: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1525: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘zTrans’
cubeaddon.c:1528: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘zTrans’
cubeaddon.c:1531: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘zTrans’
cubeaddon.c:1535: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1538: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1540: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1541: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘zTrans’
cubeaddon.c:1543: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘vRot’
cubeaddon.c:1545: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘backVRotate’
cubeaddon.c:1545: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘vRot’
cubeaddon.c:1549: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1549: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1550: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFill’
cubeaddon.c:1554: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1567: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘vRot’
cubeaddon.c:1570: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘zTrans’
cubeaddon.c:1574: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘zTrans’
cubeaddon.c:1597: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘vRot’
cubeaddon.c:1601: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘vRot’
cubeaddon.c:1601: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘vRot’
cubeaddon.c:1663: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘reflection’
cubeaddon.c:1668: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1669: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘zTrans’
cubeaddon.c:1670: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1673: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1673: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘zTrans’
cubeaddon.c: En la función ‘cubeaddonPaintOutput’:
cubeaddon.c:1693: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c:1694: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘first’
cubeaddon.c:1696: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c: En la función ‘cubeaddonDonePaintScreen’:
cubeaddon.c:1710: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘first’
cubeaddon.c:1711: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1712: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘zTrans’
cubeaddon.c:1714: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘wasDeformed’
cubeaddon.c:1714: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1716: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1719: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c: En la función ‘cubeaddonInitScreen’:
cubeaddon.c:1797: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘reflection’
cubeaddon.c:1798: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘first’
cubeaddon.c:1799: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘last’
cubeaddon.c:1800: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘yTrans’
cubeaddon.c:1801: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘zTrans’
cubeaddon.c:1802: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘tmpRegion’
cubeaddon.c:1803: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘deform’
cubeaddon.c:1804: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capDeform’
cubeaddon.c:1806: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormals’
cubeaddon.c:1807: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘winNormSize’
cubeaddon.c:1809: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘tmpBox’
cubeaddon.c:1810: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘nTmpBox’
cubeaddon.c:1812: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘capFillIdx’
cubeaddon.c:1825: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘topCap’
cubeaddon.c:1826: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘bottomCap’
cubeaddon.c:1828: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘topCap’
cubeaddon.c:1829: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘bottomCap’
cubeaddon.c:1855: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:1855: error: ‘CubeScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:1855: error: ‘CubeScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:1856: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘paintTop’
cubeaddon.c:1857: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘paintBottom’
cubeaddon.c: En la función ‘cubeaddonFiniScreen’:
cubeaddon.c:1869: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘tmpRegion’
cubeaddon.c:1881: error: ‘CubeScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:1881: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘shouldPaintViewport’
cubeaddon.c:1882: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘paintTop’
cubeaddon.c:1883: error: ‘CubeaddonScreen’ no tiene un miembro llamado ‘paintBottom’
make: *** [build/cubeaddon.lo] Error 1
tobal@tobal:~/compiz/cubeaddon$ 


```

I don't have repository, only i'll be able a link for download deb packages for hardy heron.

---

### Post by 5735guy on 2008-05-14
This is great work thankyou and works faultlessly on Hardy:):)

However it will not install on Gutsy after I have selected the No.5 option:confused:( Any ideas please:confused:

---

### Post by Zorael on 2008-05-14
Once more requesting Kubuntu Hardy option! ;>

Don't think I'll let you rest or anything. Not allowed. This "sleep" you've heard so much about is just propaganda.

---

### Post by .:PiXi²:. on 2008-05-14
Just a quick question, can anyone tell me why the title bars of my windows disappear when using Compiz as window manager?
When using Metacity, it all works perfect.
Thanks in advance!

---

### Post by Fenris_rising on 2008-05-14
in the compiz setup window tick 'decoration' took me a while to realise
what was going on myself. Any chance of a 'users' guide to explian what does what and how? i know some of its obvious but it took me 3 days to get the cylinder screensaver going :)

---

### Post by Zorael on 2008-05-14
Basically, Metacity is a **window manager**. It keeps track of which window has focus so keypresses can be sent there, enable you to move windows, etc. It is also a **window decorator** and draws titlebars and borders on windows.

Metacity is the default in Gnome, and KWin is the default in KDE. I don't know the name of the Xfce one.

Compiz is a **window compositioner** and adds OpenGL rendering, making all those fancy effects possible. It is also a **window manager**, but it is not a **window decoratior**. Without one you won't get window borders, which means you must run one on the side. Enabling the window decorations plugin makes compiz load one upon start of it.

The compiz crew maintains three different window compositioners, **gtk-window-decorator**, **kde-window-decorator** and **emerald**. gtk-window-decorator support Gnome's themes, so enabling Compiz with that decorator will just give you GL effects with the same looks as earlier. The same goes with kde-window-decorator but with KDE themes. Emerald, on the other hand, has its own themes and its own theme manager, so if you enable emerald as your decorator you'll (by default) suddenly get a red window theme.

Emerald is the most advanced of those three, with support for fancy transparency and other effects. kde-window-decorator is, in my experience, buggy and prone to crashing. I can't speak for gtk-window-decorator.

---

### Post by melenor on 2008-05-14
I installed this on my computer but i didn't get the new plugin for the sphere. that they released a little while ago. what happened i followed the code in the first post.

---

### Post by Martje_001 on 2008-05-15
> **melenor said:**
> I installed this on my computer but i didn't get the new plugin for the sphere. that they released a little while ago. what happened i followed the code in the first post.
It's in ccsm. It's called 'Cube Reflection and Deformation'.

---

### Post by zeld on 2008-05-15
hi guys... i've installed compiz-git, and it's all ok...but when i try to start compiz with compiz --replace i get this error:

compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

anyone can help me?

---

### Post by mozdef on 2008-05-15
thanks...it works perfectly on my fresh hardy installation although it did take a while.

---

### Post by EnigMattic on 2008-05-15
IMHO the first post should be modified to note the pre-existing compiz-fusion installations should be removed before using the script and maybe list which packages need to be taken out.

---

### Post by techno-mole on 2008-05-16
okay, ive tried this new version of installing compiz, and ive tried the latest version of the italian script, and on both occassions all went well, but the cylinder plugin wasnt installed with either method ?
is it not being included in compiz anymore ?
or does it need to installed after the main installed (eg - as an extra)

cheers.

---

### Post by talisfang on 2008-05-16
Window decoration is not working after i installed the new version. Previous version was perfect. Where can I download the previous one?

---

### Post by techno-mole on 2008-05-16
have you enabled the window decorations in ccsm ? ive had this a few times after installing compiz, if that option isnt set it does display the title bars etc etc
right click on the fusion icon, select "settings manager" and then look for " window decorations " make sure its enabled (if it isnt)

if you have already done all this, im not sure what else to try, apart from re-installing or finding another method

cheers

---

### Post by Het Irv on 2008-05-16
> **Martje_001 said:**
> It's in ccsm. It's called 'Cube Reflection and Deformation'.


Techno-mole, there's your sphere plug-in^^^

---

### Post by techno-mole on 2008-05-16
i know where it should have been, but after the installation there was no cube add on plugin, i checked through everything and it wasnt there, in the end i went and installed it myself from the gitweb site, then i compiled it myself, and now i have it (where it should be under ccsm, cube reflection and deformation)

like i said i have no idea why that plugin wasnt installed, least it was easy enough to solve.
cheers

---

### Post by Het Irv on 2008-05-16
Oh, okay.  It sounded like you were looking for the wrong plugin at first. Sorry 'bout that.

---

### Post by techno-mole on 2008-05-17
no worries, it just seemed strange that the cube add on wasnt installed with the main install ?
dont you just love technology :) (no matter how much agro i get from my pc i keep coming back for more)
anyway all sorted now, installed it manually and it works, so thats good enough for me.
cheers

---

### Post by talisfang on 2008-05-17
in ccsm windows decoration is checked. but i cant see the decoration that is behind the window. when it is unchecked i cant see the panel above the window.(close, minimize, etc). It was working great in the previous script i downloaded from here.

---

### Post by NovruzeliH on 2008-05-17
Man i just downloaded it im going to try it now :D

---

### Post by CC_machine on 2008-05-17
Kubuntu Hardy still missing.
come on, its just Ubuntu Hardy with KDE. can i mod the script or SOMETHING??

i've been looking around for ways to install it, this looked SO CLOSE - but no, you all messed it up. cheers. why doesnt a compiz-fusion-plugins-unsupported .deb package for compiz 7.4 exist already? 0.0

---

### Post by Ub1476 on 2008-05-17
Any back traces by using compiz git? Like icons missing in ccsm and worse fps (had those issues on previous script)?

I'm using nVidia 7900gs on Hardy Gnome 64-bit. 

Thanks for your work anyway!:)

---

### Post by Martje_001 on 2008-05-17
> **CC_machine said:**
> but no, you all messed it up. cheers.
Arrogant $%!#.. you shouldn't be using this in the first place. AND YES, you can edit the script, you've got the source already! $#*$!

to all others: I can't get it working ok in Kubuntu Hardy :(, anyone who gives me the hint for the right dependencies?

---

### Post by Martje_001 on 2008-05-17
> **Ub1476 said:**
> Any back traces by using compiz git? Like icons missing in ccsm and worse fps (had those issues on previous script)?

I'm using nVidia 7900gs on Hardy Gnome 64-bit. 

Thanks for your work anyway!:)
I've heard nobody complain since the new script ;)

---

### Post by Ub1476 on 2008-05-17
Do I have to remove Compiz before running script? Cause I didn't do that now and nothing has changed (even though script completed sucessfully).

---

### Post by EnigMattic on 2008-05-17
Anyone know how to ensure 'fusion-icon' starts before my screenlets? I added it to 'Sessions' and now I have to 'Reload Window Manager' every time I boot to get the Screenlets to render properly :-(

---

### Post by Martje_001 on 2008-05-18
Maby you should make a script:
```
#!/bin/bash
fusion-icon &
sleep 5
screenletsd
```
make it executable (with chmod +x) and add it to sessions.

---

### Post by CC_machine on 2008-05-18
forget my previous post, alcohol == bad.

anyway got it to install on Kubuntu 8.04 by installing ubuntu-desktop and then running with the ubuntu hardy option. probably a bad idea, but I did remove everything compiz related first (in synaptic).

I notice the following plugins do not activate: (i check the box and a second later they uncheck again)
- Show Mouse
- Group and Tabbed Windows  (>___<)
- Splash

other bugs:
-Expo with Curve deformation has a much lower framerate than before (stock 8.04 compiz).

are these bugs in the current GIT version or occured because I ran the script on Kubuntu? should i use the Kubuntu Gutsy option instead?

thanks for the script guys, everything else working grand :KS

---

### Post by 22flames on 2008-05-18
Hey don't you think you could actually put this in a bash.sh file so that all the people that are new to Ubuntu could find it more accessible this is just a question..

---

### Post by Martje_001 on 2008-05-18
> **22flames said:**
> Hey don't you think you could actually put this in a bash.sh file so that all the people that are new to Ubuntu could find it more accessible this is just a question..
No:
1. New Ubuntu users shouldn't use this
2. Instructions are clear on the first page
3. The script exists out of 8 files.

I don't mean to be rude or anything, but this is just the way I see it. I hope you can see it too ;)

> forget my previous post, alcohol == bad.
Apologize accepted, and yes it is. :)

I think those are problems with Kubuntu. I will try (again) to write an updated version with support for Kubuntu Hardy, in the next weekend.

---

### Post by 22flames on 2008-05-18
okay i see i i was just suggesting i mean its not to difficult anyway is it :) thanks btw i like it how does the rotating window effect work thought...

---

### Post by janz84 on 2008-05-18
OK I got it working... you have to uninstall all compiz entries with synaptic, and then use the removal commands on page 2 of the guide before running the install on page 1.... wish it was a little more consolidated

---

### Post by stueau on 2008-05-19
someone mentioned that this shouldn't be tried by anyone relatively new to ubuntu.... guess I read that a little late. I just get too damn excited by eye-candy!

Anyway, ran the script, all went well except that new options were not available on the settings manager. Read some posts to try to fix it, but decided to try to get rid of it. Ran the following from the link in the thread starter:
```

cd compiz-git
./compiz-git uninstall
cd ..
rm -r compiz-git

```

But original compiz didn't work. However, didn't panic and thought that simply reinstalling compiz would work. Didn't.

I've tried a couple of times: removed compiz (+ all instances of 'compiz') using synaptic then tried to reinstall:
```

scott@scott-laptop:~$ sudo apt-get install compiz
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-gnome compiz-plugins
Suggested packages:
  nvidia-glx
The following NEW packages will be installed
  compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-gnome compiz-plugins
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4318kB of archives.
After this operation, 20.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package compiz-core.
(Reading database ... 127483 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_1%3a0.7.4-0ubuntu6_amd64.deb) ...
Selecting previously deselected package compiz-fusion-plugins-extra.
Unpacking compiz-fusion-plugins-extra (from .../compiz-fusion-plugins-extra_0.7.4-0ubuntu1_amd64.deb) ...
Selecting previously deselected package compiz-fusion-plugins-main.
Unpacking compiz-fusion-plugins-main (from .../compiz-fusion-plugins-main_0.7.4-0ubuntu5_amd64.deb) ...
Selecting previously deselected package compiz-plugins.
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.7.4-0ubuntu6_amd64.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.7.4-0ubuntu6_amd64.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_1%3a0.7.4-0ubuntu6_all.deb) ...
Setting up compiz-core (1:0.7.4-0ubuntu6) ...
Setting up compiz-fusion-plugins-extra (0.7.4-0ubuntu1) ...

Setting up compiz-fusion-plugins-main (0.7.4-0ubuntu5) ...

Setting up compiz-plugins (1:0.7.4-0ubuntu6) ...
Setting up compiz-gnome (1:0.7.4-0ubuntu6) ...

Setting up compiz (1:0.7.4-0ubuntu6) ...
scott@scott-laptop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-compizconfig
The following NEW packages will be installed
  compizconfig-settings-manager python-compizconfig
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/644kB of archives.
After this operation, 4178kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package python-compizconfig.
(Reading database ... 127886 files and directories currently installed.)
Unpacking python-compizconfig (from .../python-compizconfig_0.7.4-0ubuntu1_amd64.deb) ...
Selecting previously deselected package compizconfig-settings-manager.
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.7.4-0ubuntu2_all.deb) ...
Setting up python-compizconfig (0.7.4-0ubuntu1) ...
Setting up compizconfig-settings-manager (0.7.4-0ubuntu2) ...

```
There's nothing there that I can see would mean it doesn't work, but alas no luck.

System > Preferences has no 'Advanced desktop settings' and I cannot select any desktop effects from System > Preferences > Appearence > Visual Effects.

Any pointers? I miss my cube!

Thanks.



EDIT: thought I'd run compiz in the terminal and post the output:
```

scott@scott-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5975 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.
Segmentation fault

```

That can't be good.

---

### Post by janz84 on 2008-05-19
looks like you need to enable your nvidia card before installing then do what I said in the post above yours ;)

---

### Post by stueau on 2008-05-19
> **janz84 said:**
> looks like you need to enable your nvidia card before installing then do what I said in the post above yours ;)

I don't have an nvidia card. I'm running ATI accelerated graphics. I did try disabling the restricted driver, rebooting, then reeabling it again. No luck.

Also tried purging the compiz install as mentioned in the thread, but get the very weird responce:
```

scott@scott-laptop:~$ sudo apt-get purge compiz* libcompiz*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-git-newest.tar.gz
scott@scott-laptop:~$ 

```


EDIT: compiz is now working, or appears to be. However, ccsm still will not appears, even when "installed". I can run ccsm from terminal or by using 'Alt+F2', but options have no effect. Really just want to get rid of compiz and start again, but am stuck with the issue above!

---

### Post by Martje_001 on 2008-05-19
> **stueau said:**
> ```

scott@scott-laptop:~$ sudo apt-get purge compiz* libcompiz*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-git-newest.tar.gz
scott@scott-laptop:~$ 

```
Very very strange apt mensions compiz-git.. try this:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.1
sudo apt-get update
sudo mv /etc/apt/sources.list.1 /etc/apt/sources.list
sudo apt-get update
```
Any succes now?

---

### Post by Zorael on 2008-05-19
[FONT="Courier New"]apt-get[/FONT] does not accept [FONT="Courier New"]purge[/FONT] as an operation.
```
scott@scott-laptop:~$ sudo apt-get purge compiz* libcompiz*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-git-newest.tar.gz
```
It interpreted [FONT="Courier New"]compiz*[/FONT] as the file [FONT="Courier New"]compiz-git-newest.tar.gz[/FONT] that was in the current directory.

You want to do [FONT="Courier New"]autoremove **--purge**[/FONT] or use another package manager. Like so:
```
$ sudo apt-get autoremove --purge compiz* libcompiz* emerald* libemerald*
$ sudo dpkg --purge compizconfig-settings-manager
```
```
$ sudo aptitude purge ~ncompiz ~nemerald
$ sudo dpkg --purge compizconfig-settings-manager
```
The [FONT="Courier New"]dpkg --purge[/FONT] line has proven necessary for me every time, but that might be related to my system.

*Then* reinstall. Purge [FONT="Courier New"]compiz-gnome[/FONT] and add [FONT="Courier New"]compiz-kde[/FONT] if you use KDE.
```
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

---

### Post by stueau on 2008-05-20
> **Zorael said:**
> [FONT="Courier New"]apt-get[/FONT] does not accept [FONT="Courier New"]purge[/FONT] as an operation.
```
scott@scott-laptop:~$ sudo apt-get purge compiz* libcompiz*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-git-newest.tar.gz
```
It interpreted [FONT="Courier New"]compiz*[/FONT] as the file [FONT="Courier New"]compiz-git-newest.tar.gz[/FONT] that was in the current directory.

You want to do [FONT="Courier New"]autoremove **--purge**[/FONT] or use another package manager. Like so:
```
$ sudo apt-get autoremove --purge compiz* libcompiz* emerald* libemerald*
$ sudo dpkg --purge compizconfig-settings-manager
```
```
$ sudo aptitude purge ~ncompiz ~nemerald
$ sudo dpkg --purge compizconfig-settings-manager
```
The [FONT="Courier New"]dpkg --purge[/FONT] line has proven necessary for me every time, but that might be related to my system.

*Then* reinstall. Purge [FONT="Courier New"]compiz-gnome[/FONT] and add [FONT="Courier New"]compiz-kde[/FONT] if you use KDE.
```
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

Yeah... still get the same error, which is VERY weird. Anyway, tried for a few hours, got nowhere, so reinstalled the whole system. May have been overkill, but it was guaranteed to work!

I think I'll wait for a stable release through the repos to upgrade, no matter how much I want the rounded cube thing!

Thanks for the help guys

---

### Post by Nudgeworth on 2008-05-20
After entering your script I was told I didn't have X11-XCB. 
 I'm running gutsy, how can I get this package?

---

### Post by bouta on 2008-05-20
when will this plugin be official ? and will it be updated thru the repos ?

---

### Post by Martje_001 on 2008-05-21
> **Nudgeworth said:**
> After entering your script I was told I didn't have X11-XCB. 
 I'm running gutsy, how can I get this package?
See [this]("http://forum.compiz-fusion.org/showthread.php?t=3152").

> when will this plugin be official ? and will it be updated thru the repos ? 
1. Never
2. Never

It installs compiz from git, and that's bleeding edge software. This will never come to the ubuntu repo's.

---

### Post by Zorael on 2008-05-21
That said, a newer Compiz version may at some point become available through the backports repositories, if development reaches a "stable" state, and a petition to add it to the repo is sent to and accepted by the backports team.

When grabbing it from git you cannot, should not, must not *expect* it to Just Work. If it does, yay. If it doesn't, it's not the fault of the script's author, and in no way do any of us owe you an obligation to miraculously fix it. *<eyes certain post in this thread>*

There aren't (m)any forseeable ways that this can mess up your system to a non-restorable state; you'd just need to enter the right commands. And finding out which ones is the fun part, ye?

---

### Post by bouta on 2008-05-21
i installed compiz-git ..i guess so since, when i go to the advanced desktop settings..its name is changed to compiz config settings ..i want to know where is the plugin to make my desktop a sphere ?

---

### Post by Martje_001 on 2008-05-21
Please search this thread before asking questions. It's called
> Cube Reflection and Deformation

---

### Post by muschen on 2008-05-22
Okay so, I just installed it, but it seemed to mess a bit so I decided to get rid of it again, following your in structions on page 13. But now, Emerald doesn't start up, Compiz does show up, but all the pictures are gone, and my I can't change the theme colours anymore (I've got stuck with this really ugly wine-red).

Any suggestions? :(

---

### Post by 00arthuryu on 2008-05-22
```

Configuration-file says to use sudo, following.

Distribution specified in configurationfile, following.

Found 1 repo, autoselecting 'annongit.opencompositing.org'.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcompizconfig0 for regex &#8216;libcompiz*&#8217;
Note, selecting libcompizconfig-backend-gconf for regex &#8216;libcompiz*&#8217;
Note, selecting libcompizconfig0-dev for regex &#8216;libcompiz*&#8217;
Note, selecting libcompizconfig-backend-kconfig for regex &#8216;libcompiz*&#8217;
E: Couldn't find package compiz-git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      

Pulling compiz from git... 

```

It says it can't find compiz-git is that normal?
It just stalls at pulling compiz from git..
no internet activity and it doesn't do anything :(

I think i've missed out something or forgot something really silly lol
Thanks for creating a script :D
but could anyone help?

---

### Post by Zorael on 2008-05-23
> **muschen said:**
> Okay so, I just installed it, but it seemed to mess a bit so I decided to get rid of it again, following your in structions on page 13. But now, Emerald doesn't start up, Compiz does show up, but all the pictures are gone, and my I can't change the theme colours anymore (I've got stuck with this really ugly wine-red).

Any suggestions? :(
If you're getting the wine-red theme, that usually means Emerald is running. :>

---

### Post by melenor on 2008-05-23
is there any way just to add this to the repos? to make updateing and getting them easier?

---

### Post by Martje_001 on 2008-05-23
I'll try to setup a repository a.s.a.p.

---

### Post by chapterthree on 2008-05-24
I followed the instructions in [post 14](http://ubuntuforums.org/showpost.php?p=4884809&postcount=14) first to remove compiz (which maybe should go in the first post), then followed the installation instructions in the first post, and everything went very smoothly.  I have been having much better success with compiz after installing this latest version.  :) Thanks, and I look forward to seeing this migrate into a repo.

---

### Post by Martje_001 on 2008-05-25
If you want to use the repository please add these lines to your */etc/apt/sources.list* and update your sources list by either doing *sudo apt-get update* in a terminal or by clicking *refresh* in Synaptic:

**deb [http://194.109.6.92/~mgj1/ubuntu-repo/](http://194.109.6.92/~mgj1/ubuntu-repo/) stable main**

This will also give you access to the unstable versions of sabnzbd. Please test the repo, if it works, I'll put it on the front page.

---

### Post by BoredOutOfMyMind on 2008-05-26
> **chapterthree said:**
> I followed the instructions in [post 14](http://ubuntuforums.org/showpost.php?p=4884809&postcount=14) [COLOR="Magenta"][SIZE="3"]first to remove compiz (which maybe should go in the first post), then followed the installation instructions in the first post[/SIZE][/COLOR], and everything went very smoothly.  I have been having much better success with compiz after installing this latest version.  :) Thanks, and I look forward to seeing this migrate into a repo.


THERE is a usuable idea!

---

### Post by melenor on 2008-05-26
> **Martje_001 said:**
> If you want to use the repository please add these lines to your */etc/apt/sources.list* and update your sources list by either doing *sudo apt-get update* in a terminal or by clicking *refresh* in Synaptic:

**deb [http://194.109.6.92/~mgj1/ubuntu-repo/](http://194.109.6.92/~mgj1/ubuntu-repo/) stable main**

This will also give you access to the unstable versions of sabnzbd. Please test the repo, if it works, I'll put it on the front page.

I already had Compiz-Fusion installed so that might be why it doesn't work, but i tried it and no upgrade and no plugins like the other way in a little bit i will try to do a complete uninstall then install.

---

### Post by BoredOutOfMyMind on 2008-05-26
> **melenor said:**
> I already had Compiz-Fusion installed so that might be why it doesn't work, but i tried it and no upgrade and no plugins like the other way in a little bit i will try to do a complete uninstall then install.

That worked for me. 

:)

---

### Post by melenor on 2008-05-26
did you get the cube deform? to make it look like a cylinder?

---

### Post by Fenris_rising on 2008-05-28
just a small query. i have removed compiz using the synaptic. also used the remove strings on here to make sure my system is clean ready for the new compiz in this thread. now i still have the icons 'compiz fusion icon' in the system menu. and emerald and ccsm are still in the preferences menu. is this correct or have i not cleared them of the system properly? im running 8.04.

---

### Post by Martje_001 on 2008-05-28
I'm working on that, it shouldn't be a problem.

---

### Post by pingpongboss on 2008-05-28
oh yea, to anyone who's having trouble getting the newly installed compiz to work, try this:

turn off Metacity's compositing manager.
open "gconf-editor"
navigate to apps, metacity, general
uncheck compositing_manager

---

### Post by Fenris_rising on 2008-05-29
hi all
well i had a bit of bother (usb memsticks wouldnt mount suddenly) so i ended up doing a full reinstall of HH. so ive got a fresh install and this compiz is the only one now present on my machine yaaaaaaaay! any way just one small question.....wheres the screensaver option gone??? great compiz though. 

!!!!!!!forget i asked, its re-appeared ?!?!?!?! 

+1

---

### Post by boyce1 on 2008-05-30
the script went really well :) thanks, working perfect except when i rebooted, my settings were reset. not a huge problem, but i can't seem to get back all the functions with my mouse, such as scrolling to change windows, and holding middle button to enable cube.


any help would be appreciated.

---

### Post by Martje_001 on 2008-05-31
*[31-05-08] Added Italian translation (Thank you Nello)
*[31-05-08] Added Brazilian Portugese translation (Thank you SantAnna)
*[31-05-08] Moved functions to seperate folder (code clean-up)

Script should be updated through the repo, or redownloading compiz-git-newest.tar.gz.

Planning to make an option to install awn from git, what do you think?

---

### Post by bmwman on 2008-05-31
I've installed this script on multiple machines so far and it always works great. The last one I did was on my desktop PC. Everything works but the Wobbly windows doesnt work. I also have Window decoration checked. I really like the wobbly windows plugin and it would be great to make it work. Is there a way to reinstall just that or I need to run the whole script again. I'm afraid it's gonna break if reinstall twice? I'm not sure if the update feature works either.

---

### Post by Gourgi on 2008-05-31
Martje_001 could you make your compiz-git_0.1-2_i386.deb  to be amd64 compatible ?
all you have to do is replace 
```
Architecture: i386
```
to 
```
Architecture: all 
```
in your control file.
unless there is a reason you don't do that:confused:

oh, by the way,  here are the greek locales (attachment)
i know my translation may not be perfect but it's better than nothing

---

### Post by Martje_001 on 2008-06-01
> **Gourgi said:**
> Martje_001 could you make your compiz-git_0.1-2_i386.deb  to be amd64 compatible ?
all you have to do is replace 
```
Architecture: i386
```
to 
```
Architecture: all 
```
in your control file.
I typed 'any' *oops*.

I will add your translation tomorrow. Thanks!

---

### Post by Gourgi on 2008-06-01
[http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Architecture](http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Architecture)


i really can't see the difference , try both and will see :D

---

### Post by stldirty on 2008-06-01
ok this script has been running for awhile now and i can't tell if its looping or not.    it this normal?

---

### Post by stldirty on 2008-06-01
nvm i got it installed.  i can't seem to figure out how to use the screesaver plugin tho.  any help would be appreciated.

---

### Post by Gourgi on 2008-06-01
> **stldirty said:**
> nvm i got it installed.  i can't seem to figure out how to use the screesaver plugin tho.  any help would be appreciated.

open compiz settings manager (ccsm) go: 
screensaver -- > bindings --> initiate (keyboard) and set it to 
```
<Super>F3
```
that should give you a preview of the screensaver.


note that this plugin is supposed to replace the gnome-screensaver ,although in my pc it is not always become active, 
so it's eyecandy but very buggy :(

i wish i helped 
you can find more at [www.compiz-fusion.org](www.compiz-fusion.org) 
look at wiki + forums there ;)

---

### Post by stldirty on 2008-06-01
> **Gourgi said:**
> open compiz settings manager (ccsm) go: 
screensaver -- > bindings --> initiate (keyboard) and set it to 
```
<Super>F3
```
that should give you a preview of the screensaver.


note that this plugin is supposed to replace the gnome-screensaver ,although in my pc it is not always become active, 
so it's eyecandy but very buggy :(

i wish i helped 
you can find more at [www.compiz-fusion.org](www.compiz-fusion.org) 
look at wiki + forums there ;)
oh i'm sorry i meant wallpaper lol.  i can't get different wallpapers on different desktops.  the screensaver does "kinda" work.  when the floating windows start the desktop goes black. for some reason i remember being able to still see my desktop while this plugin was working. and for somereason my show desktop plugin won't allow me to check it anymore :(

grrrr

---

### Post by Martje_001 on 2008-06-02
If you activate the wallpaper plugin and do 'killall nautilus' do you see different wallpapers?

---

### Post by iamjfarrell on 2008-06-02
is there any way that I can uninstall this and get my compiz back running properly? my compiz is completely screwed up now and i cant get it back to normal.

---

### Post by Martje_001 on 2008-06-02
Search the thread please...

---

### Post by stldirty on 2008-06-02
> **Martje_001 said:**
> If you activate the wallpaper plugin and do 'killall nautilus' do you see different wallpapers?
nope

---

### Post by Martje_001 on 2008-06-02
In a terminal do:

```
gconf-editor /apps/nautilus/preferences
```
and disable 'show desktop'.

---

### Post by iamjfarrell on 2008-06-02
Alright.. I dont know what happened but it works really good now! Oh well. I guess I did something right!

---

### Post by Martje_001 on 2008-06-03
That's good! I was just going to point you at page 2, post 2 ;)

---

### Post by azizzle on 2008-06-03
I installed on a fresh version of Hardy, and everything works great, except when I try to change the desktop size to 4 to have a cube, the slider just slides back to 2. I've been tinkering with the other settings, but I can't find out why this is happening. Any ideas?

---

### Post by Het Irv on 2008-06-03
Under your Prefrences try changeing the backend to something eles. That helped me when that helped me.

---

### Post by azizzle on 2008-06-03
k ill try it when i get off work, thanks

---

### Post by iOli on 2008-06-05
Hi
I installed it and i wanna uninstall it now because the cube reflection doesn't work and this programm made my computer slow! 

How can i uninstall it? Please Quick :D

Thx:)

---

### Post by Gourgi on 2008-06-05
> **iOli said:**
> Hi
I installed it and i wanna uninstall it now because the cube reflection doesn't work and this programm made my computer slow! 

How can i uninstall it? Please Quick :D

Thx:)
did you try this ?
```
./compiz-git uninstall
```

---

### Post by iOli on 2008-06-05
> **Gourgi said:**
> did you try this ?
```
./compiz-git uninstall
```
No i havent tried it..
After i did that, can i install the normal version?
EDIT: It didn't work. it said ./compiz-git is a directory..
HELP

---

### Post by Gourgi on 2008-06-06
> **iOli said:**
> No i havent tried it..
After i did that, can i install the normal version?
EDIT: It didn't work. it said ./compiz-git is a directory..
HELP
follow this steps
```

wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
chmod u+x compiz-git
./compiz-git uninstall

```

after that you can install normal version

---

### Post by stldirty on 2008-06-07
> **Martje_001 said:**
> In a terminal do:

```
gconf-editor /apps/nautilus/preferences
```
and disable 'show desktop'.
ok that worked.  but now i can't get the taskbar to be transparent lol.

looks like i'm going to have to compromise...

---

### Post by funnypanks on 2008-06-07
this thing didnt really help me so i got rid of it but i liked the emerald themes that came with it, is there a way to just get the emerald themes?

---

### Post by Fenris_rising on 2008-06-07
hi all

im having a few problems with this. compiz forgets any settings i apply after shutdown or reboot. if i try and set extras i lose title bars of windows with emerald or GTK (decoration is enabled and emerald is present) and cube packs up. 6 weeks ago when i first installed 8.04 all was well. i have had to reinstall a few times as i screwed things up but up till now everything has been fine. also i cant get the animated windows effects any more. i have done everything as far as i can see. uninstalling the original compiz, full clean down afterwards and then followed the guide here to reinstall the new vrsion. can anyone shed light on this situation?
ATI drivers are enabled, version 2.1.7412 release. my card is a radeon x300.
i have tried the latest drivers but they were why i had to reinstall a couple of times.

---

### Post by Gourgi on 2008-06-07
> **Fenris_rising said:**
> hi all

im having a few problems with this. compiz forgets any settings i apply after shutdown or reboot. in ccsm go to preferences and use flat-file configuration as backend, maybe this helps

---

### Post by Gourgi on 2008-06-07
> **funnypanks said:**
> this thing didnt really help me so i got rid of it but i liked the emerald themes that came with it, is there a way to just get the emerald themes?
download this 
[http://gitweb.compiz-fusion.org/?p=fusion/decorators/emerald-themes;a=snapshot;h=4211335dd3edd7b87fb8a0b72fb332e0c8cbe48d;sf=tgz](http://gitweb.compiz-fusion.org/?p=fusion/decorators/emerald-themes;a=snapshot;h=4211335dd3edd7b87fb8a0b72fb332e0c8cbe48d;sf=tgz)

---

### Post by Martje_001 on 2008-06-08
> **stldirty said:**
> ok that worked.  but now i can't get the taskbar to be transparent lol.

looks like i'm going to have to compromise...
Oh yeah, forgot to mention that. Gnome-panel uses fake-transparency. You have to use AWN or any other dock that supports composite-transparency.

---

### Post by Het Irv on 2008-06-09
> **stldirty said:**
> ok that worked.  but now i can't get the taskbar to be transparent lol.

looks like i'm going to have to compromise...

The other thing you could do is make a Transparent picture roughly the size of your Panel and use that image as the background image.  I did that so that i could make part of my Panel Tansparent and part Opaque.  I have a picture in my album here on the Forums.

---

### Post by iOli on 2008-06-09
> **Gourgi said:**
> follow this steps
```

wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
chmod u+x compiz-git
./compiz-git uninstall

```

after that you can install normal version

Ok now I uninstalled it, but when i go under system, preferences and then compiz config settings manager and than click on it, nothing happens.
Help again? :D
Thx

---

### Post by Gourgi on 2008-06-09
> **iOli said:**
> Ok now I uninstalled it, but when i go under system, preferences and then compiz config settings manager and than click on it, nothing happens.
Help again? :D
Thx
you have to reinstall compiz from synaptic or via cli :
```

sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main emerald  fusion-icon simple-ccsm emerald-themes

```

---

### Post by stldirty on 2008-06-10
ok i want to give this another try but i don't want to run into the same problem.  i NEED the show desktop plugin to work properly but with this installed i wasn't able to enable it.  is there any reason why this could have been happening?

---

### Post by maxfact on 2008-06-10
Can I also try your script on ubuntu feisty?

if I add this voice
```
ubuntu-feisty
```
in this point of the script
```
case $chosen_distro in
		1) chosen_distro_t=debian-sid-gnome; de=gnome; break;;
		2) chosen_distro_t=debian-sid-kde; de=kde; break ;;
		3) chosen_distro_t=debian-lenny-gnome; de=gnome; break ;;
		4) chosen_distro_t=debian-sid-kde; de=kde; break ;;
		5) chosen_distro_t=ubuntu-gutsy; de=gnome; break ;;
		6) chosen_distro_t=kubuntu-gutsy; de=kde; break ;;
		7) chosen_distro_t=ubuntu-hardy; de=gnome; break ;;
```
and this voice
```
ubuntu-feisty) $pri aptitude -y install $ubuntu_feisty_dep;;
```
in this point
```
# Installing dependencies
	case $chosen_distro_t in
		debian-sid-gnome) $pri aptitude -y install $debian_sid_gnome_dep;;
		debian-sid-kde) $pri aptitude -y install $debian_sid_kde_dep;;
		debian-lenny-gnome) $pri aptitude -y install $debian_lenny_gnome_dep;;
		debian-sid-kde) $pri aptitude -y install $debian_lenny_kde_dep;;
		ubuntu-gutsy) $pri aptitude -y install $ubuntu_gutsy_dep;;
		kubuntu-gutsy) $pri aptitude -y install $kubuntu_gutsy_dep;;
		ubuntu-hardy) $pri aptitude -y install $ubuntu_hardy_dep;;
```

do you believe that can work?

---

### Post by Martje_001 on 2008-06-10
No, it won't. You have to add all the dependencies to the dependencies file.

---

### Post by maxfact on 2008-06-11
> **Martje_001 said:**
> No, it won't. You have to add all the dependencies to the dependencies file.
but I am for now a headstrong person
I have only a problem packet x11-xcb where I find it on ubuntu feisty

I have looked for on synaptic 
I have added the libxcb-devs but nothing

---

### Post by Martje_001 on 2008-06-11
[http://forum.compiz-fusion.org/showthread.php?t=3152](http://forum.compiz-fusion.org/showthread.php?t=3152)

---

### Post by stldirty on 2008-06-11
> **Martje_001 said:**
> [http://forum.compiz-fusion.org/showthread.php?t=3152](http://forum.compiz-fusion.org/showthread.php?t=3152)

update.  i fixed my problems wit the show desktop plugin by reinstalling the plugin from a git repository. thanks again for the great script.

---

### Post by giannis12a on 2008-06-11
Very nice plugins, but in my case broken my system and i reinstalled all from beginning. use it with careful.

---

### Post by sdowney717 on 2008-06-11
no windows decorations. And it is 'checked' in ccsm
And I did restart fusion-icon
metacity --replace will put it back to metacity with window decorations.

I do get this error, anyone know what to do?

gtk-window-decorator: symbol lookup error: gtk-window-decorator: 
undefined symbol: decor_blend_border_picture

ok, I fixed it by going into ccsm and do a reset back to default values.
open up another terminal and type emerald --replace to get the emerald themes running.


```

scott@scott-desktop:~/compiz-git$ fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
 * No GLX_EXT_texture_from_pixmap with direct rendering context
 ... present with indirect rendering, exporting: LIBGL_ALWAYS_INDIRECT=1
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
gtk-window-decorator: symbol lookup error: gtk-window-decorator: undefined symbol: decor_blend_border_picture
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Setting Update "command"
Setting Update "initiate_key"
Setting Update "clear_key"
Setting Update "bg_brightness"



```

---

### Post by sdowney717 on 2008-06-12
I have compiz fusion icon starting automatically, nice little icon to control compiz.
So I dont have to type in terminal fusion-icon or emerald --replace

[http://neoaddict.wordpress.com/2007/11/03/getting-fusion-icon/](http://neoaddict.wordpress.com/2007/11/03/getting-fusion-icon/)
I followed this, not sure if have to do this to get those files.
Then I setup fusion-icon in sessions to start at bootup.
system-preferences-sessions
add a startup program
point it to fusion-icon created following above commands in url.
reboot and it shows up, running compiz, emerald and the fusion icon.

---

### Post by TheeMahn2003 on 2008-06-15
I have been re-writing this script to include additional animations, [helix]("http://www.youtube.com/watch?v=fz1id8P-4AA"), [maze]("http://www.youtube.com/watch?v=KZBbWfUYwPw") & other plugins, it also builds using a GUI (zenity).  I have written it to take advantage of multiple cores if available, cuts my build time to 1/3 (quad core).  Below is the code I am currently using, it is incomplete, it will also have a auto update routine (currently not used)...

```
#!/bin/bash
SCRIPT_VERSION=1.00
pri="sudo"
#detect and fully utilize the processor(s)
CORES=1
CORES=$(cat /proc/cpuinfo | grep processor | wc -l)

##Check for zenity
if [ ! -e "/usr/bin/zenity" ]; then
	gksudo apt-get install -y zenity
fi

update() {
 wget -O /tmp/fusion.sh http://repoubuntusoftware.info/upgrades/fusion.sh >/dev/null 2>&1
 REMOTE_VERSION=`grep SCRIPT_VERSION /tmp/fusion.sh |head -n1 |sed 's/.*=//'`
 if [ "$REMOTE_VERSION" != "$SCRIPT_VERSION" ]; then
  if [[ -n $DIALOG ]]
  then
   dialog --yesno "Newer version of Compiz Fusion Builder has been found\n\nDo you wish to install it?" 0 0
   DIALOG_EXIT_CODE=$?
   if [[ $DIALOG_EXIT_CODE = 0 ]]
   then
    cp /tmp/fusion.sh $0
    echo "Compiz Fusion Builder script has been updated to v $REMOTE_VERSION"
    echo "Please re-run the script"
    zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png --info --text='Newer version of script detected '$REMOTE_VERSION'.  It has been upgraded please re-run script.' --title="Compiz Fusion Builder";
    exit
   fi
  else
   cp /tmp/fusion.sh $0
   echo "Newer version detected: $REMOTE_VERSION"
   zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png --info --text='Newer version of script detected '$REMOTE_VERSION'.  It has been upgraded please re-run script.' --title="Compiz Fusion Builder";
   exit
  fi
 fi
 rm /tmp/fusion.sh 2>/dev/null
}




#Prompt user
custom="$(zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png  --width=250 --height=220 --title "Compiz Fusion Builder" --text "Which do you wish to do?" --list --radiolist --column "Direction" --column "Distro" true 'Install' false 'Update' false 'Uninstall')";

cd `echo ${0%/*}`
# Including some functions
function check_op
{
	if [ "$?" = "1" ] ; then
		echo Failed: $1
		exit 1
	fi
}

function get_git
{
	echo -n "$get_git1" `basename $1` "$get_git2"
	git clone "$repo""$1" > /dev/null 2>&1
	if [ "$?" = "1" ] ; then
		echo "$failed"
		exit 1
	fi
	if [ "$?" = "0" ] ; then
		echo "$done"
	fi
}

function pull_git
{
	if [ -d "$1" ] ; then
		echo -n "Updating $1... "
		cd "$1"
		git pull > .status-compiz-git 2>&1
		if [ "$?" = "1" ] ; then
			echo "$failed"
			rm .status-compiz-git
			exit 1
		fi
		if [ "`cat .status-compiz-git | grep -o 'Already up-to-date.'`" = "Already up-to-date." ] ; then
			echo up-to-date!
			#update="$update$1 "
		else
			echo "$done"
			update="$update$1 "
		fi
		cd ..
	fi
}

# Import previous settings and redirect all output (including error messages) to /dev/null
source ~/.compiz-git/config > /dev/null 2>&1

# Import dependencies
source dependencies
check_op "Importing dependencies"

# Import a language
source locales/$LANG > /dev/null 2>&1
if [ "$?" = "1" ] ; then
	source locales/en_US.UTF-8
fi

# Check if we're running this as normal user or as root
touch /usr/share/check-root.$tlt > /dev/null 2>&1
if [ -w /usr/share/check-root.$tlt ] ; then
	rm /usr/share/check-root.$tlt
	pri=""
else
	while true; do
		if [ "$not_root_t" = "$no" ] ; then
			echo "$config_run_root"
			exit
		fi
		if [ "$not_root_t" = "$yes" ] ; then
			echo "$config_sudo"
			echo ""
			break
		fi
		echo -n "$not_root"
		read not_root_t
		if [ "$not_root_t" = "$yes" ] ; then
			echo ""
			settings_changed="1"
			break
		fi
		if [ "$not_root_t" = "$no" ] ; then
			echo "Please run this script as root."
			settings_changed="1"
			exit
		fi
	done
	pri="sudo"
fi

# Creating workdirectory
mkdir ~/.compiz-git > /dev/null 2>&1

# Choose a distribution
while true; do
	if [ "$chosen_distro" = "" ] ; then
		echo "$supported_distros"
		echo ""
		echo -n "$pick_supported_distros"
		read chosen_distro
	else

		echo "$dis_specified"
	fi
	case $chosen_distro in
		1) chosen_distro_t=debian-sid-gnome; de=gnome; break;;
		2) chosen_distro_t=debian-sid-kde; de=kde; break ;;
		3) chosen_distro_t=debian-lenny-gnome; de=gnome; break ;;
		4) chosen_distro_t=debian-sid-kde; de=kde; break ;;
		5) chosen_distro_t=ubuntu-gutsy; de=gnome; break ;;
		6) chosen_distro_t=kubuntu-gutsy; de=kde; break ;;
		7) chosen_distro_t=ubuntu-hardy; de=gnome; break ;;
	esac
done

# Choose reprosity
echo ""
echo "$repo_t"
echo ""
repo=git://anongit.compiz-fusion.org/

# Save settings as defaults
echo not_root_t=$not_root_t > ~/.compiz-git/config
echo chosen_distro=$chosen_distro >> ~/.compiz-git/config
echo repo=$repo >> ~/.compiz-git/config

if [ "$custom" = "Install" ] ; then
	# Removing conflicting packages
	$pri apt-get -y remove $all_distro_conflicts

	# Installing dependencies
	case $chosen_distro_t in
		debian-sid-gnome) $pri aptitude -y install $debian_sid_gnome_dep;;
		debian-sid-kde) $pri aptitude -y install $debian_sid_kde_dep;;
		debian-lenny-gnome) $pri aptitude -y install $debian_lenny_gnome_dep;;
		debian-sid-kde) $pri aptitude -y install $debian_lenny_kde_dep;;
		ubuntu-gutsy) $pri aptitude -y install $ubuntu_gutsy_dep;;
		kubuntu-gutsy) $pri aptitude -y install $kubuntu_gutsy_dep;;
		ubuntu-hardy) $pri aptitude -y install $ubuntu_hardy_dep;;
	esac

	# Pulling latest data from git
	cd ~/.compiz-git
	echo ""
	rm -rf anaglyph atlantis2 bcop ccsm compiz compizconfig-python compiz-manager emerald emerald-themes freewins i18n libcompizconfig loginout photowheel plugins-extra plugins-main plugins-unsupported screensaver snowglobe wallpaper wiimote wiitrack workspacenames libcompizconfig compizconfig-backend-gconf compizconfig-backend-kconfig fusion-icon dodge widget
	get_git compiz
	get_git fusion/compizconfig/ccsm
	get_git fusion/compizconfig/compizconfig-python
	get_git fusion/compizconfig/libcompizconfig
	get_git fusion/decorators/emerald
	get_git fusion/decorators/emerald-themes
	get_git fusion/i18n
	get_git fusion/libraries/bcop
	get_git fusion/misc/compiz-manager
	get_git fusion/plugins-extra
	get_git fusion/plugins/loginout
	get_git fusion/plugins-main
	get_git fusion/plugins-unsupported
	get_git fusion/plugins/wallpaper
	get_git users/b0le/photowheel
	get_git fusion/plugins/widget
	#get_git users/klange/wiitrack
	#get_git users/smspillaz/wiimote
	get_git users/maniac/workspacenames
	get_git users/metastability/atlantis2
	get_git users/metastability/snowglobe
	get_git users/pafy/screensaver
	get_git users/warlock/freewins
	get_git users/wodor/anaglyph
	get_git users/crdlb/fusion-icon
	get_git users/rcxdude/dodge

	if [ "$de" = "gnome" ] ; then
		get_git fusion/compizconfig/compizconfig-backend-gconf
	fi
	if [ "$de" = "kde" ] ; then
		get_git fusion/compizconfig/compizconfig-backend-kconfig
	fi

	# Install compiz (need special threatment)
	if [ "$de" = "gnome" ] ; then
		cd compiz
		./autogen.sh --enable-librsvg --disable-kconfig --disable-kde --disable-kde4
		check_op "Executing ./autogen.sh --enable-librsvg --disable-kconfig --disable-kde --disable-kde4"
		make -j$CORES | zenity --progress --pulsate --auto-close --width=500 --title="Compiling Compiz for Gnome";
		check_op "Make failed (compiz)"
		$pri make install
		check_op "Make install failed (compiz)"
		cd ..
	fi
	if [ "$de" = "kde" ] ; then
		cd compiz
		./autogen.sh --enable-librsvg --disable-gconf --disable-gtk --disable-metacity --disable-gnome
		check_op "Executing ./autogen.sh --enable-librsvg --disable-gconf --disable-gtk --disable-metacity --disable-gnome"
		make - j$CORES | zenity --progress --pulsate --auto-close --width=500 --title="Compiling Compiz for KDE";
		check_op "Make failed (compiz)"
		$pri make install
		check_op "Make install failed (compiz)"
		cd ..
	fi

	if [ "$de" = "gnome" ] ; then
		backend=compizconfig-backend-gconf
	fi
	if [ "$de" = "kde" ] ; then
		backend=compizconfig-backend-kconfig
	fi

	# Install with ./autogen.sh
	for i in `echo bcop libcompizconfig compizconfig-python $backend emerald emerald-themes i18n plugins-extra plugins-main plugins-unsupported`; do
		cd $i
		./autogen.sh
		check_op "Executing autogen.sh ($i)"
		make -j$CORES | zenity --progress --pulsate --auto-close --width=500 --title="Compiling $i plugin"; 
		check_op "Executing make ($i)"
		$pri make install
		check_op "Executing make install ($i)"
		cd ..
	done

	# Install with only makefiles
	for i in `echo anaglyph atlantis2 freewins widget loginout photowheel screensaver snowglobe wallpaper workspacenames dodge`; do
		cd $i
		echo 'BUILD_GLOBAL = true' >> plugin.info
		make -j$CORES | zenity --progress --pulsate --auto-close --width=500 --title="Compiling $i plugin"; 
		$pri make install
		cd ..
	done

	# Install fusion-icon
	cd fusion-icon
	python ./setup.py build
	$pri python ./setup.py install | zenity --progress --pulsate --auto-close --width=500 --title="Compiling Fusion-Icon";
	cd ..

	# Install CompizConfig Settings Manager
	cd ccsm
	python ./setup.py build
	$pri python ./setup.py install | zenity --progress --pulsate --auto-close --width=500 --title="Compiling CompizConfig Settings Manager";
	cd ..

	$pri ln -s /usr/local/lib/libcompizconfig.so.0.0.0 /usr/lib/libcompizconfig.so.0
	$pri ln -s /usr/local/lib/libemeraldengine.so.0.0.0 /usr/lib/libemeraldengine.so.0
	$pri ln -s /usr/local/lib/libdecoration.so.0.0.0 /usr/lib/libdecoration.so.0

	#Compile additional Plugins
	#Grab & extract plugins
	#download animations plugin
	wget http://repoubuntusoftware.info/scripts/animation.tar.gz 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading \2/' | zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png --width=600 --height=100 --progress --auto-close --title="Downloading Animations Plugins..."
	tar xfv animation.tar.gz
	#Maze plugin
	wget http://repoubuntusoftware.info/scripts/maze.tar.gz 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading \2/' | zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png --width=600 --height=100 --progress --auto-close --title="Downloading Maze Plugin..."
	tar xfv maze.tar.gz
	#static plugin
	wget http://repoubuntusoftware.info/scripts/compiz-plugins-static-0.0+git20080514.tar.gz 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading \2/' | zenity --window-icon=/usr/share/ultimate/ubuntu_ico.png --width=600 --height=100 --progress --auto-close --title="Downloading Static Plugin..."
	tar xfv compiz-plugins-static-0.0+git20080514.tar.gz
	for i in `ls -d */` ; do
		echo "Compiling $i";
		cd $i ; 
		make -j$CORES install | zenity --progress --pulsate --auto-close --width=500 --title="Compiling $i plugin"; 
		make clean ;
		cd .. ;
	done

	clear

	echo "$install_ready"

	exit 0
fi

if [ "$1" = "uninstall" ] ; then
	$pri rm -rf /etc/compiz* > /dev/null 2>&1
	$pri rm -rf /etc/xdg/compiz* > /dev/null 2>&1
	$pri rm -rf /home/*/.compiz* > /dev/null 2>&1
	$pri rm -rf /home/*/.gconf/apps/compiz* > /dev/null 2>&1
	$pri rm -rf /root/.compiz* > /dev/null 2>&1
	$pri rm -rf /usr/bin/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/bin/bcop > /dev/null 2>&1
	$pri rm -rf /usr/bin/ccsm > /dev/null 2>&1
	$pri rm -rf /usr/bin/emerald* > /dev/null 2>&1
	$pri rm -rf /usr/bin/fusion-icon > /dev/null 2>&1
	$pri rm -rf /usr/bin/gtk-window-decorator > /dev/null 2>&1
	$pri rm -rf /usr/etc/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/etc/gconf/schemas/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/include/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/lib/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/lib/emerald* > /dev/null 2>&1
	$pri rm -rf /usr/lib/libcompiz* > /dev/null 2>&1
	$pri rm -rf /usr/lib/libdecoration* > /dev/null 2>&1
	$pri rm -rf /usr/lib/libemerald* > /dev/null 2>&1
	$pri rm -rf /usr/lib/libcompiz* > /dev/null 2>&1
	$pri rm -rf /usr/lib/pkgconfig/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/lib/pkgconfig/emerald* > /dev/null 2>&1
	$pri rm -rf /usr/lib/pkgconfig/libcompiz* > /dev/null 2>&1
	$pri rm -rf /usr/lib/pkgconfig/libdecoration* > /dev/null 2>&1
	$pri rm -rf /usr/lib/pkgconfig/libemerald* > /dev/null 2>&1
	$pri rm -rf /usr/share/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/share/bcop* > /dev/null 2>&1
	$pri rm -rf /usr/share/ccsm* > /dev/null 2>&1
	$pri rm -rf /usr/share/emerald* > /dev/null 2>&1
	$pri rm -rf /usr/share/pkgconfig/bcop.pc > /dev/null 2>&1
	$pri rm -rf /usr/local/bin/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/local/bin/bcop > /dev/null 2>&1
	$pri rm -rf /usr/local/bin/ccsm > /dev/null 2>&1
	$pri rm -rf /usr/local/bin/emerald* > /dev/null 2>&1
	$pri rm -rf /usr/local/bin/fusion-icon > /dev/null 2>&1
	$pri rm -rf /usr/local/bin/gtk-window-decorator > /dev/null 2>&1
	$pri rm -rf /usr/local/etc/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/local/etc/gconf/schemas/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/local/include/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/local/lib/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/local/lib/emerald* > /dev/null 2>&1
	$pri rm -rf /usr/local/lib/libcompiz* > /dev/null 2>&1
	$pri rm -rf /usr/local/lib/libdecoration* > /dev/null 2>&1
	$pri rm -rf /usr/local/lib/libemerald* > /dev/null 2>&1
	$pri rm -rf /usr/local/lib/pkgconfig/emerald* > /dev/null 2>&1
	$pri rm -rf /usr/local/lib/pkgconfig/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/local/lib/pkgconfig/libcompiz* > /dev/null 2>&1
	$pri rm -rf /usr/local/lib/pkgconfig/libdecoration* > /dev/null 2>&1
	$pri rm -rf /usr/local/lib/pkgconfig/libemerald* > /dev/null 2>&1
	$pri rm -rf /usr/local/share/compiz* > /dev/null 2>&1
	$pri rm -rf /usr/local/share/bcop* > /dev/null 2>&1
	$pri rm -rf /usr/local/share/ccsm* > /dev/null 2>&1
	$pri rm -rf /usr/local/share/emerald* > /dev/null 2>&1
	$pri rm -rf /usr/local/share/pkgconfig/bcop.pc > /dev/null 2>&1
	$pri rm /usr/local/share/locale/*/LC_MESSAGES/*compiz*.mo > /dev/null 2>&1
	$pri rm /usr/share/locale-langpack/*/LC_MESSAGES/compiz* > /dev/null 2>&1
	$pri rm /usr/lib/window-manager-settings/libcompiz.so > /dev/null 2>&1
	$pri rm /usr/lib/window-manager-settings/libcompiz.a > /dev/null 2>&1
	$pri rm /usr/lib/window-manager-settings/libcompiz.la > /dev/null 2>&1
	$pri rm /usr/local/lib/python2.5/site-packages/compiz* > /dev/null 2>&1
	exit 0
fi

if [ "$1" = "update" ] ; then
	cd ~/.compiz-git
	for i in `ls`; do
		pull_git "$i"
	done

	for i in $update; do
		if [ "$i" = "$compiz" ] ; then
			if [ "$de" = "gnome" ] ; then
				cd compiz
				make clean
				./autogen.sh --enable-librsvg --disable-kconfig --disable-kde --disable-kde4
				make -j$CORES
				$pri make install
				cd ..
			fi
			if [ "$de" = "kde" ] ; then
				cd compiz
				make clean
				echo Compiz
				./autogen.sh --enable-librsvg --disable-gconf --disable-gtk --disable-metacity --disable-gnome
				make -j$CORES
				$pri make install
				cd ..
			fi

			if [ "$de" = "gnome" ] ; then
				backend=compizconfig-backend-gconf
			fi
			if [ "$de" = "kde" ] ; then
				backend=compizconfig-backend-kconfig
			fi
		fi
		if [ "$i" = "`echo bcop libcompizconfig compizconfig-python $backend emerald emerald-themes i18n plugins-extra plugins-main plugins-unsupported | grep -o $i`" ]; then
			cd $i
			make clean
			./autogen.sh
			make -j$CORES
			$pri make install
			cd ..
		fi
		if [ "$i" = "`echo anaglyph atlantis2 freewins widget loginout photowheel screensaver snowglobe wallpaper workspacenames dodge | grep -o $i`" ]; then
			cd $i
			make clean
			make -j$CORES
			$pri make install
			cd ..
		fi
		if [ "$i" = "fusion-icon" ] ; then
			cd fusion-icon
			python ./setup.py build
			$pri python ./setup.py install
			cd ..
		fi
		if [ "$i" = "ccsm" ] ; then
			cd ccsm
			python ./setup.py build
			$pri python ./setup.py install
			cd ..
		fi		
	done
	exit 0
fi

echo "$error1"
```

It is incomplete, I had it working 100% when I tested the update routine it overwrote my work.  Won't Happen again.  ;)

TheeMahn

---

### Post by easybake on 2008-06-16
How are you supposed to run that. I did a gedit compizfusionbuilder.sh in terminal. Pasted the code. made it executable. tried to run it in terminal with 'sh compizfusionbuilder.sh but I keep getting the code.

```
easybake@easybake-desktop:~$ sh compizfusionbuilder.sh
cd: 45: can't cd to compizfusionbuilder.sh
compizfusionbuilder.sh: 47: function: not found
compizfusionbuilder.sh: 55: function: not found
basename: missing operand
Try `basename --help' for more information.

```

any help?

---

### Post by Martje_001 on 2008-06-16
easybake: It is supposed to be run with BASH. So either
```
chmod +x script.sh
./script.sh
```
or
```
bash script.sh
```
should do the trick.

TheeMahn2003: Going to test it now, do  you mind if I pack it in my compiz-git-newest.tar.gz? Of course I'll give you credits!

Edit: It doesn't run that well. It still needs my script.. I can help you if you want, please pm / mail me.

---

### Post by chrisruls00 on 2008-06-16
Do you know if this will be updated for Kubuntu Hardy?

---

### Post by Martje_001 on 2008-06-16
If someone passed me the dependencies to build, ok. To be honest; I'm to lazy to:

1. Install Kubuntu
2. Check dependencies
3. Remove Kubuntu

Maby this weekend then..

---

### Post by SteveNorman on 2008-06-16
sorry,,noob here,,

How do I get the cube to rotate now? Not sure If things are running good yet.

ls /usr/bin | grep compiz
lists nothing

 ls /usr/local/bin | grep compiz
lists "compiz"

-I did all the sudo remove steps as well as checking things compiz related for complete removal in synaptic package manager.
-I have the proper driver for my nvidia 8800 series card. Then I ran the script from post one. 
-did fusion-icon

I did I think I just am not setting compiz manager correctly. Whenever I close ccsm it seems to uncheck what I checked.

---

### Post by TheeMahn2003 on 2008-06-17
> **Martje_001 said:**
> easybake: It is supposed to be run with BASH. So either
```
chmod +x script.sh
./script.sh
```
or
```
bash script.sh
```
should do the trick.

TheeMahn2003: Going to test it now, do  you mind if I pack it in my compiz-git-newest.tar.gz? Of course I'll give you credits!

Edit: It doesn't run that well. It still needs my script.. I can help you if you want, please pm / mail me.

Its not done yet, yes it uses what you have written for distro dependencies,  I am getting closer it now asks which distro you are running by a gui, I was thinking of doing a
```
DISTRO=(cat /etc/lsb-release | grep DISTRIB_ID)
```

and doing the same for the release, but I am unsure if debian etc. has the same layout.

It will get much, much better.

Thanks for checking it out.  Using it to compile in the latest & greatest into UE Gamers ;)

Thanks,

TheeMahn

---

### Post by Fenris_rising on 2008-06-17
hi all

ive just reinstalled this compiz. ive had a bit of a do wit the OS and had to do a full reinstall. any way i have as before followed the instructions to the letter. all the fancy effects work no problem. BUT! im using emerald as the decorator and inexplicably i dont have any frames to my windows it is selected in ccsm. ive checked what i think i need to check but i cant see anything wrong. the selected frame is wombat but non of the options in emerald show. any one got a clue whats up? if i change to GTK deco' i get the standard window decoration no problem. slight change GTK decorator doesnt give me window borders anymore either!!!

---

### Post by rated_emman on 2008-06-18
HI GUYS! before i try to install this, i have the advanced desktop settings with desktop cubes wobbly windows and stuff.. when i installed this, those are all gone WAHHHHH! :(

how do i put it back? when i go to system>perf>... there's none saying advanced desktop settings like before with the desktop cubes and everything! :( helpp plzzz..
im using hardy heron 8.04... plzz how do i put it back? :-s


thanks

---

### Post by YaroMan86 on 2008-06-18
> **rated_emman said:**
> HI GUYS! before i try to install this, i have the advanced desktop settings with desktop cubes wobbly windows and stuff.. when i installed this, those are all gone WAHHHHH! :(

how do i put it back? when i go to system>perf>... there's none saying advanced desktop settings like before with the desktop cubes and everything! :( helpp plzzz..
im using hardy heron 8.04... plzz how do i put it back? :-s


thanks

First, you'll need to find a way to uninstall the GIT'd Compiz Fusion (I'm not sure how to do this, since I have had no problems with it.)

Once that is done, go into Synaptic and search for Compiz and install that along with the package compizconfig-settingsmanager.

Could easily be installed through the terminal this way:

```

sudo apt-get install compiz python-compizconfig

```

I know of no way to recover your settings for it, but it usually isn't too difficult to recreate settings manually.

---

### Post by rated_emman on 2008-06-18
> **YaroMan86 said:**
> First, you'll need to find a way to uninstall the GIT'd Compiz Fusion (I'm not sure how to do this, since I have had no problems with it.)

Once that is done, go into Synaptic and search for Compiz and install that along with the package compizconfig-settingsmanager.

Could easily be installed through the terminal this way:

```

sudo apt-get install compiz python-compizconfig

```

I know of no way to recover your settings for it, but it usually isn't too difficult to recreate settings manually.


anybody? PLZ? anybody knows how to uninstall GIT'd Compiz Fusion?

thanks so much for the code YAROMAN86

i just wanna get it go back to normal :(

---

### Post by bmwman on 2008-06-18
Try sudo ./compiz-git uninstall

---

### Post by rated_emman on 2008-06-18
> **bmwman said:**
> Try sudo ./compiz-git uninstall

i tried and i get this:

```
emman@emmanuel-laptop:~$ sudo ./compiz-git uninstall
[sudo] password for emman: 
sudo: ./compiz-git: command not found

```

plzz anybody??? :(

---

### Post by Fenris_rising on 2008-06-18
not sure what i ticked in the end (damn) but i must have done something right as everything is running as it should. and after several on/offs of the PC it appears its remembering all the settings hurrah!

---

### Post by rated_emman on 2008-06-18
when i try that, i get this: 

```
emman@emmanuel-laptop:~$ sudo ./compiz-git uninstall
[sudo] password for emman: 
sudo: ./compiz-git: command not found

```

plzzz i just want my desktop effect settings back :(

---

### Post by SteveNorman on 2008-06-18
the first couple of pages in this thread have removal instructions.

---

### Post by Het Irv on 2008-06-18
> **SteveNorman said:**
> sorry,,noob here,,

How do I get the cube to rotate now? Not sure If things are running good yet.

ls /usr/bin | grep compiz
lists nothing

 ls /usr/local/bin | grep compiz
lists "compiz"

-I did all the sudo remove steps as well as checking things compiz related for complete removal in synaptic package manager.
-I have the proper driver for my nvidia 8800 series card. Then I ran the script from post one. 
-did fusion-icon

I did I think I just am not setting compiz manager correctly. Whenever I close ccsm it seems to uncheck what I checked.

Did you enable Cube rotation?  Some genius decided that it should be a separate plugin that doesn't come on by default when you turn on the Cube Plugin.

---

### Post by SteveNorman on 2008-06-18
Yeah,,I clicked it,,disabled wall,, made horizontal desktops = 4,,

actually not many of the effects work for me. No wobbly windows, rain or most of my animations. Thats what made me think something else may need to be done.

I have a good vid card and the latest driver. I am in the process of removing git and am going to try and reload from synaptic. With synaptic compiz not all the effects worked either. Cube, water, fire and animations did tho.

I may have some software conflicts from trying to put in some plugins awhile ago. I think Im just to ignorant at this stage of my linux use to do this sort of thing. Fun trying tho.

---

### Post by Gourgi on 2008-06-18
> **rated_emman said:**
> when i try that, i get this: 

```
emman@emmanuel-laptop:~$ sudo ./compiz-git uninstall
[sudo] password for emman: 
sudo: ./compiz-git: command not found

```

plzzz i just want my desktop effect settings back :(

```

wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
sudo ./compiz-git uninstall

```

---

### Post by paul.roberts20 on 2008-06-19
Worked fine for me.

Just a note for people thinking about trying it, make sure to uninstall all compiz stuff through synaptic first and set fusion-icon to start up on login afterward (use sessions)

---

### Post by Zorael on 2008-06-19
Arr, where's me Kubuntu 8.04 support? >:>

---

### Post by Exsecrabilus on 2008-06-20
Does this install Stackswitch?

---

### Post by portach king on 2008-06-20
As far as I can tell Exsecrabilus, not yet.

---

### Post by niiiick on 2008-06-21
```
checking pkg-config is at least version 0.9.0... yes
checking for COMPIZ... configure: error: Package requirements (x11-xcb          xcomposite               xfixes                  xdamage                 xrandr                  xinerama                ice                     sm             libxml-2.0               libxslt                 libstartup-notification-1.0 >= 0.7) were not met:

No package 'x11-xcb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Failed: Executing ./autogen.sh --enable-librsvg --disable-kconfig --disable-kde --disable-kde4
```

not seeing x11-xcb, and failing on autogen.sh.  what can i do?

tried uninstalling this and installing from synaptic and still doesn't work cuz of this:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found
```
ideally i'd like to get the GIT install working.

---

### Post by Victormd on 2008-06-21
Beautiful! After the installation, everything worked fine... but... ccsm won't commit the changes on some of the plugins I've added, i.e., cube reflection and deformation. Everyting else is working fine. However, when I load the Compiz Fusion Icon and Reload Window Manager, then it applies the changes and everything works fine. Is this something that I'm going to have to do everytime (or setup under sessions to do so) or is there another workaround for this. The reason I'm asking is because this is the first time I've depended on the Compiz Fusion Icon to get things to work and I'm not convinced that it is a must...

I'm sorry if this was already addressed but I only read up to page 8 or 9 of the thread... :redface:

---

### Post by dracule on 2008-06-21
I get this as an output:

```
 * Detected Session: gnome
 * Searching for installed applications...
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
    from util import env
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 421, in <module>
    decorators = CompizDecorators(_installed)
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 228, in __init__
    self.command = context.Plugins['decoration'].Display['command']

```

but it wont run...



OK now i got it to run. but no window decorations! o my! (decorations are enabled in the settings. but for somereason NO plugins are working. nothing. no wobbly windows or anything.


EDIT: Ok, now i got them to work... but i cant move windows. When i right click the bottom and select it, it does nothing. and when i click up at the top bar decoratoin (which finally appeared) it does nohting (but the buttons work to close it and stuff). I also tried it with the emerald window decorator, but no go.

---

### Post by Victormd on 2008-06-21
Those issues can be fixed by right clicking on the fusion icon then "Reload Window Manager". This is my biggest concern. Everytime I restart, I have to do this otherwise it's a mess.

---

### Post by dracule on 2008-06-21
> **Victormd said:**
> Those issues can be fixed by right clicking on the fusion icon then "Reload Window Manager". This is my biggest concern. Everytime I restart, I have to do this otherwise it's a mess.

that didnt work. my title bar is still unresponsive. so know when i need to move a window i have to go into expo. kinda bad.

Also, i can double click the title bar, and it will roll up. the minimize, maximize and close buttons all work. it is just that i cannot move a window...

lol, had to enable plug ins for moving windows...

---

### Post by Victormd on 2008-06-21
try holding the ALT key while trying to drag (normally you can click anywhere in the window to do this) and that should do the trick... :)

---

### Post by tad1073 on 2008-06-21
I am having one problem, I can not get only 4 desktops. I can get 1, 2, 3, 5, 6, 7, etc. but not 4.

---

### Post by Exsecrabilus on 2008-06-21
> **tad1073 said:**
> I am having one problem, I can not get only 4 desktops. I can get 1, 2, 3, 5, 6, 7, etc. but not 4.
I know, right? Me too!

I settled for three, looks really cool.

---

### Post by Victormd on 2008-06-21
You mean under the General Options>Desktop size settings of the ccsm?

---

### Post by Het Irv on 2008-06-21
Try going under Prefrences and changing the backend  That seems to help with the desktop problem

---

### Post by Exsecrabilus on 2008-06-21
> **Het Irv said:**
> Try going under Prefrences and changing the backend  That seems to help with the desktop problem
Can you further explain how to do that?

---

### Post by Martje_001 on 2008-06-22
> **Exsecrabilus said:**
> Can you further explain how to do that?
CCSM --> Preferences --> Backend (change to Flat file)

@niiiick: [http://forum.compiz-fusion.org/showthread.php?t=3152](http://forum.compiz-fusion.org/showthread.php?t=3152)

---

### Post by dakun on 2008-06-26
does is require the xkb to compile it?(i dont remember the exact name)
i tried compiling the ones from the compiz fusion gits but they needed a package that didnt exist on the repos and needed a whole bunch of other stuff to be compiled.

oh and for those who got annoyed as i did when compiling for what seems hours, heres where you can find 0.7.6 "packages"

[https://launchpad.net/~compiz/+archive](https://launchpad.net/~compiz/+archive)

just follow what it says it needs, if theres no 7.6 version of it then the 7.4 will do. remember to get the compiz-dev package as well or else you cant compile the 7.6 plugins

---

### Post by chikko on 2008-07-06
:bump:
any progress (if is anyone working on that..) altering the script so it fits Kubuntu hasty as well..? :(

---

### Post by 5735guy on 2008-07-19
package x11-xcb not found

Anyone having trouble running this script on Gutsy,here is a script that does work
[http://ubuntuforums.org/showthread.php?t=643485](http://ubuntuforums.org/showthread.php?t=643485)
It works on Feisty as well:):):guitar::):)

---

### Post by Smatt454 on 2008-07-21
So how's the kubuntu hardy support coming?

---

### Post by Zorael on 2008-07-23
The compiz-git script from the current tar.gz archive does not have executable properties.

```
$ ls -l compiz-git
-rw-r--r-- 1 zorael zorael 11363 2008-07-13 19:18 compiz-git
```

---

### Post by ehabareda on 2008-07-24
I'm trying to install the script and when I did I had the following:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=78765&stc=1&d=1216895172[/IMG]


the message : permission denied ...Even when I used sudo :confused:

---

### Post by Smatt454 on 2008-07-29
> **ehabareda said:**
> I'm trying to install the script and when I did I had the following:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=78765&stc=1&d=1216895172[/IMG]


the message : permission denied ...Even when I used sudo :confused:

```

chmod a+x ./compiz-git

```
you have to make the script executable before running it XD

---

### Post by Smatt454 on 2008-07-29
> **Exsecrabilus said:**
> I know, right? Me too!

I settled for three, looks really cool.

If you are talking about your desktop cube, you have to change the horizontal and vertical size in your general settings. you may have to change the horizontal back and forth. (in my experience, i set my horizontal size to 4, i had 3 desktops, then set it to 3, then back to 4 and i had the cube)

---

### Post by ehabreda on 2008-08-02
**[COLOR="Blue"]I'm sorry but I still have problems with it...please see the attachment.[/COLOR]**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=79832&stc=1&d=1217661815[/IMG]

---

### Post by Martje_001 on 2008-08-02
Do a
```
rm -r ~/.compiz-git
```
and try again.

---

### Post by castironpants on 2008-08-05
Ok, I'm having a little problem. I used the script to install compiz, and it's worked beautifully, but in the last week or so it updates plugins-main EVERY TIME I run the update script. It's like the same update, and I don't think it's taking effect. What gives?

---

### Post by Martje_001 on 2008-08-05
Try to uninstall everything and install it again. Maby it's a problem with git's cache.

---

### Post by castironpants on 2008-08-07
I did and it worked, but now it's doing it again. I might switch to another script.

---

### Post by jiggygent on 2008-08-09
Well.. it seems this hosed my compiz.. My title bar for all my windows are gone. Upon boot up, I do have my desktop cube working, but if I execute the compiz fusion icon, my cube dies and so does multiple desktops with it. I searched the thread for people experiencing the same symptoms and attempted the recommended fixes thus far.  Activating Window Decoration didn't help for my title bar problem.. neither did reloading the Window Manager.  I also tried running ./compiz-fusion update to see if any bug fixes might have resolved this, but any time i try and run that command I get the following:

su ./compizfusion update
Unknown id: ./compiz-fusion

or if I just try it without su, I get:
bash: ./compiz-fusion: No such file or directory

Any suggestions to try and resolve this?  Or should I just uninstall/reinstall at this point?

---

### Post by Martje_001 on 2008-08-09
There may be a bug in GIT, be patient if so.

What's the ouput of:
```
gtk-window-decorator --replace
```
?

---

### Post by jiggygent on 2008-08-09
Am I suppose to type that in a certain directory?  When I just open up a terminal window and type gtk-window-decorator --replace  I just get a response saying command not found.

---

### Post by fred.warren on 2008-08-10
I hacked on the script a little bit. It now works to install Compiz-Fusion from git for Kubuntu Hardy. This would be for the KDE3 version.

---

### Post by Martje_001 on 2008-08-10
> **jiggygent said:**
> Am I suppose to type that in a certain directory?  When I just open up a terminal window and type gtk-window-decorator --replace  I just get a response saying command not found.
What's the ouput of these:
```
ls /usr/bin | grep gtk
ls /usr/local/bin | grep gtk
```
?

> **fred.warren said:**
> I hacked on the script a little bit. It now works to install Compiz-Fusion from git for Kubuntu Hardy. This would be for the KDE3 version.
You forgot the update the locales. Done now, and uploaded to xs4all. Thank you!

---

### Post by jiggygent on 2008-08-10
> What's the ouput of these:
Code:

ls /usr/bin | grep gtk
ls /usr/local/bin | grep gtk

?

Never mind.. I just uninstalled everything regarding compiz and then added the following to my repositories:

[http://ppa.launchpad.net/compiz/unbuntu](http://ppa.launchpad.net/compiz/unbuntu) hardy

After that, I went through the install via Synaptic Package Manger and it all installed smoothly..  The only thing I noticed was that I didn't have all my workspaces available to me, but I did a little digging and found that If I went to the general tab in my ccsm that I was able to add 4 workspaces by augmenting the horizontal virtual size to 4.  Still playing with it a bit, but for the most part.. it's stable.  Now I'm just trying to figure out how to get it to run on startup instead of me having to go to the compiz-fusion icon and then reload the Window Manager...

---

### Post by 5735guy on 2008-08-29
Ubuntu Hardy. Here is a super quick way to get all the latest plug-ins for the default Hardy Compiz Fusion

[http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/](http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/)

It upgrades from Compiz Fusion 0.7.4 to Compiz Fusion 0.7.6 without running a huge script.

ENJOY :guitar::guitar::guitar:

---

### Post by bmwman on 2008-08-29
> **5735guy said:**
> Ubuntu Hardy. Here is a super quick way to get all the latest plug-ins for the default Hardy Compiz Fusion

[http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/](http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/)

It upgrades from Compiz Fusion 0.7.4 to Compiz Fusion 0.7.6 without running a huge script.

ENJOY :guitar::guitar::guitar:

Has anyone tried that yet?

---

### Post by 5735guy on 2008-08-29
I have applied it on 3 seperate Hardy installations and it works flawlessly :):):)

---

### Post by Caseyjp on 2008-08-29
> **bmwman said:**
> Has anyone tried that yet?

Worked perfectly over here as well.

---

### Post by Zorael on 2008-08-29
I downloaded the script just now (didn't add the repo) and tried to install the Kubuntu Hardy (kde3) flavor. A minute or two into the compilation it spouts the following and ends.
```
checking for COMPIZ... configure: error: Package requirements ("compiz") were not met:

No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Failed: Executing autogen.sh (libcompizconfig)
```
What should I do?

---

### Post by Zorael on 2008-08-30
Update: installing the Gnome flavor worked so there's something amiss with the Kubuntu Hardy-specific code.

/torch, /pitchfork :>

---

### Post by wingnux on 2008-09-06
I get this error when I try to run "fusion-icon", any help?

> wingnux@wingnux-desktop ~ $ fusion-icon 
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
    from util import env
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
    import os, compizconfig, ConfigParser, time
ImportError: /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions


And more:

> wingnux@wingnux-desktop ~ $ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

---

### Post by wingnux on 2008-09-06
Ok, I don't know how nor why but they work now...

---

### Post by Vishal Agarwal on 2008-09-15
I have installed the compiz. Now I want to get the desktop background like 
[Effect- I]("http://ayozone.org/wp-content/gallery/screenshots-september-2008/08092008.png")
and this
[Effect-II]("http://ayozone.org/wp-content/gallery/screenshots-september-2008/31082008.png")

I want to see the information like top command showing into the terminal. i.e CPU utilization, Threads running, etc and HDD utilisation and the below Tash bar like that.

Thanks for help in advance.

---

### Post by liyanricaoqiyue1314 on 2008-09-15
[size=2]Nude-calendar 1177, human and Shouzu the third "Battle of Lawson," Lawson barriers on the ground before the start of the Gap. [Runescape Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)This is a historic campaign, the campaign is "human beast seven years of war" in the first three major campaigns, the history of bare-called "people's car used to launch the war." [Runescape Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)Because, the bare-three million migrant workers has made in a month-20,000 warships, and timely expansion to the navy,[Runescape Powerleveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) so that mankind has made the absolute superiority in the sea, with both sides of the back to. And the barren Shouzufengru the mainland until the 37th of the people of God the outbreak of war. [runescape shop](http://www.runescape-shop.com/)And it is precisely because of this campaign, the first time in the bare-war history, referred to the "Portland Ruo-yun," the name, many historians experts to the expansion of the war of special significance. Some people even said that, if not the war, as there will be a great hero was inspired by, of course, will be impossible for a human return to the mainland seven glorious history. [age of conan power leveling](http://www.aoc-power-leveling.org)Moreover, we said to this great man, in this war also made a bit of good results? [Runescape Gold Farm](http://www.runescape-shop.com/runescape-gold-farm/runescape-gold-farm.php)Portland Ruo-yun from Lawson on the Fort Fangyanwangqu, with both sides of the narrow ground to beat the Shouzu row over the army. [aoc power leveling](http://www.aoc-power-leveling.org)A tall face of ferocious ethnic people Zhengning the claws, but the body is more moderate and flexible people who foot, body, wrapped in a layer of black scales in the long tentacles of the Long Tuzhuo ethnic people. Of course, the master control of the air wing wizard and although their number less, but also with the team in the final, when prone radio ready siege of human soldiers guarding the wall. [/size][size=2][buy age of conan power leveling](http://www.aoc-power-leveling.org)Mankind's troops began to open Lawson barriers, 200,000 of the green collar Tieqi, hidden in two wings of the Tieqi second only to God bow of the 50,000 camp bow riders, and are in the final of the 300,000 Yazhen infantry. [buy aoc power leveling](http://www.aoc-power-leveling.org)Interval between the two sides about two kilometers distance from each other to see the other side of the bright banner of omnipresent there shaking. Ma Si Ming and the anger of the arms occasionally break out the [Runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)sound of the collision, but the two sides is almost non-soldiers heard voices, the silence before the war that is reinforced by the kind of Qishixiongxiong Fengyuyulai. [Runescape Mini Game](http://www.runescape-shop.com/rs-mini-game/runescape-mini-game.php)The weather has also Laicourenao this time, to beat the dark clouds gradually from the [Rs Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) floating over the horizon, live coverage of the original is also clear skies, Yuan Yidian gradually so that the soldiers almost clear of each other's faces, the temperature suddenly dropped. So many people and irritable, even more tense over the past fainted. [Rs Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)Line-up finish. Last night talk election effort a silvery white armor, general Pigua&#24471;&#19981;skin to stay one point, struggling carrying a spear, at the moment Lawson body trembling from the Fort-Ruo-yun, although aware that this time only The first student, is not played with, but on the battlefield or Sheyu powerful Shaqi, the lack of tension in the Tuiruan body. [/size]

---

### Post by slinkey1981 on 2008-09-20
@Vishal Agarwal - a lot of that stuff is from Screenlets, I don't know the names of the ones used in the screenshot, but you can always google "linux screenlet" and look around at what is available.

PS: I am really digging the weather screenlet in that screenshot.

---

### Post by mx92 on 2008-10-04
Excuse me. I've a problem after the installation of compiz-git.
At the end of script it tells me to write "fusion-icon" to run the program but when I write it on the terminal, I've this output:
```
root@mauro:~/compiz-git# fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
    from util import env
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
    import os, compizconfig, ConfigParser, time
ImportError: /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions
root@mauro:~/compiz-git# 
```
Please can you help me? Thanks.

Ps. Sorry for my bad english.

---

### Post by Martje_001 on 2008-10-04
This is probably due a bug. Please try again next week to see if the bug is gone!

---

### Post by uBeer on 2008-10-07
Fusion-icon doesn't work for me right now, but you can run compiz by running compiz-manager from terminal.

And it runs smooth!! For the first time in a year no more stuttering and slow response! Too bad ccsm is broken for me as well, so no tweaks...
Last week I bought a big screen and managed to set up dual-screen with my old screen and it certainly looks good and works really well!

EDIT: darn, found out that it wasn't faster because of compiz, but because just before I rebooted my system I messed around in nvidia-settings and set the OpenGL rendering quality on performance. Make a BIG difference in performance, but not so much in quality, so: I still like it!!

2nd EDIT: by magic fusion-icon and ccsm are working.... No idea as to why they work now... could be system updates

---

### Post by celticbhoy on 2008-10-07
I have a problem after updating to the new script. It defaults to emerald, and my system wont run emerald. How can I change this without running fusion-icon, ie what is the name and location of the config file, so that I can edit it manually to sort this small prob.

---

### Post by thobbs on 2008-11-04
I have looked around the internet and can't find anything? But is there a Ibex Ubuntu version of this amazing script?

cheers!

---

### Post by Martje_001 on 2008-11-04
Soon soon, I'm busy with it!

---

### Post by detroit/zero on 2008-11-17
> **slinkey1981 said:**
> @Vishal Agarwal - a lot of that stuff is from Screenlets, I don't know the names of the ones used in the screenshot, but you can always google "linux screenlet" and look around at what is available.

PS: I am really digging the weather screenlet in that screenshot.
With the exception of that crazy clock (which I want to find and use), those displays are Conky.

---

### Post by jazzperm on 2009-01-27
Great script! Thanx!!

I have a question. When I enable 3d windows or cube reflection. Then I can see my desktop cube with the flying windows screensaver. Is it possible to enable these functions and that I wont see the desktop cube during the screensaver??

---

