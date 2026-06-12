---
title: "Pidgin - Plugin Settings"
date: 2008-01-28
forum: General Help
---

### Post by danny_ on 2008-01-28
I've noticed a problem I didn't experience prior to 7.10 which is what I currently run on. Apparently, Pidgin fails to save the plugins I've enabled into it's settings when I exit it. I reload Pidgin, and none of the plugins that I enabled aren't enabled anymore and I have to go through and re-enable them.

Is anyone else having this problem? I've reinstalled Pidgin a couple of times, but it's still a no go.

Thanks.
[I]
Ubunbu 7.10 x86, Kernel 2.6.22-14-generic, Xfce 4.4.2, Pidgin 2.3.1[/I]

---

### Post by Helios38 on 2008-01-28
you may want to open the debug window while changing settings, it may reveal what the problem is.

but it sounds like something isnt saving right.

---

### Post by y-lee on 2008-01-28
Others have been having this problem, see [URL="http://ubuntuforums.org/showthread.php?t=609122&highlight=pidgin+plugins"] 
pidgin plugins never saved! [/URL]

it seems Ubuntu Gutsy shipped a broken **/etc/purple/prefs.xml** for a while which caused this problem. See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/144122") for information on the problem and how to fix it. 

From what i gather one can open and edit  the file **prefs.xml**  found at **/etc/purple/** and fix the problem. I'm running Dapper and things are set up differently for me. This file probably has root  permissions so to edit it you need to open it by using

 ```
gksudo nautilus
```

Be sure pidgin is closed first and now open the file in gedit. search for **stringlist** and change to **pathlist** and close gedit.

you may have to also edit the file prefs.xml found in your home directory at **/home/username/.purple**.  Replace **username** with your own user name. Just open this file gedit and change **stringlist** to **pathlist** in it, do this as a normal user not a super user.

**EDIT**  you may wish to back up these files before you edit them. It would be the smart thing to do.

---

### Post by danny_ on 2008-01-28
Thanks for the help. I checked the debug menu and got this message:

**(13:09:06) prefs: purple_prefs_set_path_list: /pidgin/plugins/loaded not a path list pref**

after Googling I found a related post - [http://ubuntuforums.org/showthread.php?t=563828](http://ubuntuforums.org/showthread.php?t=563828)

I will try the second solution posted by y-lee and see how things go.

---

### Post by y-lee on 2008-01-28
> after Googling I found a related post - [http://ubuntuforums.org/showthread.php?t=563828](http://ubuntuforums.org/showthread.php?t=563828)


What I suggest above is the same as suggested in the thread you just posted, except I describe in more detail how to do that. Except they also recommend removing **docklet.so** from both **prefs.xml** files. They sound like they know what they are talking about so ya might want to do that also :)

---

### Post by danny_ on 2008-01-29
The issue has been **resolved**. Thanks, again.

Now another issue I'm having is witth the Guifications plugin, I've attached a screen cap of it. Basically the text is small as all hell. I've tried changing the font size in the Pidgin GTK+ Theme Control plugin and saving it but it doesn't appear to help any.

---

### Post by y-lee on 2008-01-29
Let's see danny_, I didn't have that plugin installed then I ran into a minor problem installing it. (I have Pidgin 2.3.1 installed in a nonstandard location and an older version of Pidgin installed where it is supposed to be...been meaning to fix that but I'm lazy...not even sure how or why I did that)

Anyway I managed to get it working in Pidgin 2.3.1. Maybe its a problem with the Guifications plugins themes. Have you tried changing them. Click **Tools** in **Pidgin** and then **Plugins** select **Guifications 2.16** and then click **Configure Plugin**. Now click on the **Themes** tab and see which theme it is using. try changing it to another. You might have to hit refresh after you do it.

btw this is just a guess. :confused: Let us know if this works or not. If you don't have Guifacations version 2.16 consider updating :)

---

### Post by danny_ on 2008-01-29
> **y-lee said:**
> Anyway I managed to get it working in Pidgin 2.3.1. Maybe its a problem with the Guifications plugins themes. Have you tried changing them. Click **Tools** in **Pidgin** and then **Plugins** select **Guifications 2.16** and then click **Configure Plugin**. Now click on the **Themes** tab and see which theme it is using. try changing it to another. You might have to hit refresh after you do it.

btw this is just a guess. :confused: Let us know if this works or not. If you don't have Guifacations version 2.16 consider updating :)

I have 2.14 installed which I obtained from [www.getdeb.net](www.getdeb.net) I haven't found a deb for 2.16+?

**Update**
After Googling the issue, I found this trac ticket - [http://plugins.guifications.org/trac/ticket/159](http://plugins.guifications.org/trac/ticket/159)

I read over all that was posted, and tried to resolve the issue with making a copy of the mini-theme and changing the font size on all of the dialogs from the (default) 12pt to 14pt and it seems to have fixed the issue.

---

### Post by y-lee on 2008-01-29
> i read over all that was posted, and tried to resolve the issue with making a copy of the mini-theme and changing the font size on all of the dialogs from the (default) 12pt to 14pt and it seems to have fixed the issue.

I'm glad :popcorn:

> I have 2.14 installed which I obtained from [www.getdeb.net](www.getdeb.net) I haven't found a deb for 2.16+?

I compiled mine, it was very easy to do. It compiled like something is supposed to  :) The only thing is it got compiled to my old Pidgin not my new one. So I had to do it again and use

```
PKG_CONFIG_PATH=/usr/lib/pkgconfig ./configure --prefix=/usr
``` 

instead of just 

```
./configure
```

If you wish to install the newest plugin and need help let us know. Me or someone else would be glad to help ya. In a nutshell provided you are in the **pidgin-guifications-2.16** directory (ie after you have downloaded the file and "unzipped" it)  the 3 commands below should be all ya have to do

```
./configure 
make
sudo make install
```

It might help to uninstall the old first and of course be sure Pidgin is closed.

---

### Post by danny_ on 2008-01-29
> **y-lee said:**
> I compiled mine, it was very easy to do. It compiled like something is supposed to  :) The only thing is it got compiled to my old Pidgin not my new one. So I had to do it again and use

```
PKG_CONFIG_PATH=/usr/lib/pkgconfig ./configure --prefix=/usr
``` 

instead of just 

```
./configure
```

I downloaded 2.16, extracted it, and used the commands you specified above and I get this...

```
checking for PIDGIN... configure: error: Package requirements (pidgin purple) were not met:

No package 'pidgin' found
No package 'purple' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PIDGIN_CFLAGS
and PIDGIN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by y-lee on 2008-01-29
How did you install Pidgin? I think you are missing the pidgin-dev package. Try

```
sudo apt-get install pidgin-dev
```

Now try again and see what happens.

---

### Post by danny_ on 2008-01-29
> **y-lee said:**
> How did you install Pidgin? I think you are missing the pidgin-dev package. Try

```
sudo apt-get install pidgin-dev
```

Now try again and see what happens.

Oi! I should have thought of that. It always gets me when the problem is always something simple yet over looked. I should have guessed it from experience debugging scripts and just general programming.

All went well, however I now get this message after executing the make command.

```
/usr/bin/ld: cannot find -lpurple
collect2: ld returned 1 exit status
make[2]: *** [guifications.la] Error 1
make[2]: Leaving directory `/home/danny/Documents/pidgin-guifications-2.16/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/danny/Documents/pidgin-guifications-2.16'
make: *** [all] Error 2
```

---

### Post by y-lee on 2008-01-29
Sorry, it was easy to compile and make for me :confused: Again how did you install Pidgin? This might help find the problem and also what version of Pidgin do you have?

---

### Post by danny_ on 2008-01-29
No worries, I installed the latest version of Pidgin from a deb package ([http://getdeb.net/release.php?id=1867](http://getdeb.net/release.php?id=1867))

---

### Post by y-lee on 2008-01-29
I also found:

> hello, guifications compile needs expat-dev, dbus-dev, libxml-dev, but ./configure does not check the presence of this dependencies. 


Open Synaptic and search for dbus and install the dev packages. 
Do the same for libexpat1, and libxml-dev. If these packages are not already installed. 

I'm sorry I run Dapper or I'd tell ya the exact file names.

Now try.

EDIT

Might be easier to


```
apt-get build-dep pidgin
```


I'm new to linux and ubuntu and still learning. lol

---

### Post by y-lee on 2008-01-29
> **danny_ said:**
> No worries, I installed the latest version of Pidgin from a deb package ([http://getdeb.net/release.php?id=1867](http://getdeb.net/release.php?id=1867))

Hmm sometimes installing third party debs can cause you problems later on. **It is always safer to get stuff from the repos or compile yourself.**

Tho of course I've been known to do  the same :popcorn:

---

### Post by danny_ on 2008-01-29
> **y-lee said:**
> Hmm sometimes installing third party debs can cause you problems later on. **It is always safer to get stuff from the repos or compile yourself.**

Tho of course I've been known to do  the same :popcorn:

Agreed. I checked the deps, and they were installed except for one so I installed it and I still get the same problem. I'm thinking of just sticking with the version thats on the repos 2.14 I think it was until it's updated there.

Thanks again for the assistance, quick replys, and courteousness.

---

### Post by y-lee on 2008-01-29
no problem :)

---

### Post by leetrum on 2008-02-19
Danny:

Check your /usr/lib for libpurple.so ; there is a good change it is a broken symbolic link to an old version of libpurple.so.X.X.X; simply delete it and re-link it against the current version and you should be good to go.

---

