---
title: "Installing the light-weight web browser seamonkey"
date: 2015-06-04
forum: General Help
---

### Post by sudodus on 2015-06-04
**[SIZE=4]Installing the light-weight web browser seamonkey[/SIZE]**

I think seamonkey is a good light-weight browser, but the instructions  at the seamonkey web site to install it into linux are different from typical installations, so it would help to describe  how to do it, otherwise new users might have problems. More advanced  users might want a convenient method that is installing it for all users, not only  the own user. And above all, this script was made to create the nice  environment around seamonkey for ToriOS, to use it as the default for  several purposes. And I think it is worthwhile sharing it to be used  also in other light-weight distros.

I obtained the attached compressed script file ***install-seamonkey.gz*** from Israel Dahl, the developer of [ToriOS]("http://torios.net/").

Comments by Israel Dahl, who wrote this script:
> One thing that should be mentioned, is that Seamonkey is a **mail       program**, an **IRC program**, a** web browser** and a     simple **WYSIWYG web page editor**.
    
    So the script I made also generates desktop files for the mail, IRC     and a localized web browser script.
    This makes 3 extra desktop files, as the one that comes with     seamonkey is not localized.
    
    Also you should maybe link to:
[https://addons.mozilla.org/en-US/seamonkey/addon/gnomerunnergtk-revived/](https://addons.mozilla.org/en-US/seamonkey/addon/gnomerunnergtk-revived/)
    As this is the plugin to use the GTK theme, and makes Seamonkey much     more familiar looking (unless people liked Netscape Navigator...     Seamonkey still looks almost the same as it did in the 90s)
    
I looked at what LXLE was doing to see if I could get any help from Ronnie modifying Seamonkey, but I ended up just using the few modifications I liked.  LXLE also uses Seamonkey but they (Ronnie, really) modify it even further bringing in a lot of changes so it looks/acts like Chrome or Firefox.

We chose Seamonkey [for ToriOS] because I am a big fan of it for older computers (though Qupzilla is really nice too...), as it works well on most sites and has e-mail and irc included!  I advocated for it, because Midori is just not 'awesome' and looks terrible on small screens (the location bar hides!!). It is also in Puppy :-)

    Those are the only improvements I will add to your very good     thorough post!

The script ***install-seamonkey*** is used to make a full installation of Seamonkey. I verified today  (June 4, 2015) that it works in Lubuntu 14.04.2 LTS i386 (32-bit). It is tested by [v3.xx]("http://ubuntuforums.org/member.php?u=1937239") on Mate 15.10 daily build. See [post #9]("http://ubuntuforums.org/showthread.php?t=2281120&p=13298319#post13298319").

I think it will  work in other flavours of Ubuntu too, but I think the main targets are  Lubuntu, Ubuntu Mate, (maybe Xubuntu) and old computers with weak 32-bit processors and low amount of RAM.

[COLOR=#4b0082]***Notice that this installation makes seamonkey the default browser***. If that is not what you want, you should install it manually instead, for example according to[/COLOR] [post #2]("http://ubuntuforums.org/showthread.php?t=2281120&p=13298133#post13298133").[COLOR=#4b0082] The script is not tested for 64-bit kernels, and is not likely to work. ***See*** [/COLOR][post #2]("http://ubuntuforums.org/showthread.php?t=2281120&p=13298133#post13298133") [COLOR=#4b0082]***also for amd64 (64-bit) operating systems***.[/COLOR]

You can use the following md5sum file that is signed by me to verify that the download was correct, and the script reliable.
[SIZE=4]
1. Get the file install-seamonkey

[SIZE=3]1.1.1 Download the attached file [/SIZE][/SIZE][SIZE=3][I][B]install-seamonkey.gz
[/B][/I]
1.1.2 Expand to the script file [I][B]install-seamonkey
[/B][/I][/SIZE]
```
zcat install-seamonkey.gz > install-seamonkey
```
[SIZE=4]
[/SIZE][SIZE=4][SIZE=3]1.2 Download an updated version of file [/SIZE][/SIZE][SIZE=4][SIZE=3]***install-seamonkey*** directly from the developer[/SIZE][/SIZE]

Eric Bradshaw used the script and found some bugs. See [post #10]("http://ubuntuforums.org/showthread.php?t=2281120&p=13300873#post13300873"). This  made me understand that it is better to get the script directly from the  developer, because we can expect it to be developed and debugged.

[http://phillw.net/isos/torios/install-seamonkey](http://phillw.net/isos/torios/install-seamonkey)

The difference between the two scripts is small now (June 9, 2915), but it will increase with time.

```
diff install-seamonkey install-seamonkey0
170c170
< Comment[zh_TW]=Chat &#32842;&#22825;&#31243;&#24335;
---
> Comment[zh_TW]=X-Chat &#32842;&#22825;&#31243;&#24335;
172c172
< Exec=seamonkey -chat %u
---
> Exec=seamonkey -chat %U
```

We expect that the Icon lines for some desktop files should be changed after testing what is working.

[SIZE=4]2. Check that it is the correct file with this signed md5sum file[/SIZE]

Notice that this check is only for the version expanded from the attached file **install-seamonkey.gz**

```

-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

5491866c65fb844482bca6a7970116e7  install-seamonkey
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.11 (GNU/Linux)

iQEcBAEBAgAGBQJVcFDfAAoJEL1Dx0LrD8LIPzIIAM/xPe6Qo23b818OouX/IhST
aH3FYBKXn8GpAIr6Ma0yiu//+0poq+YZQ8spnGScYLw0YgpdmhOSmd/El+M2kk5d
UyuqC6Lw6zvY50ZqmlqXcwWgRlLqGZBBfrKnNURdY90Ncv5TM2nqJFj8qSqdCWoy
Jb0/yKW/B8jCW8RQZQjTDRFZZyCWimnhbqt9JA7xWKaZSQR5UM/jVGqAssACxZ8N
ftlrtsCghEE6GHyZ7AUY2FulAHCOirZP+iFAbmR48F/NZenFbz0YwR9ih1ifYFdd
rZL8ZBre1tz4YfeZqq4RBujP0uspMv7jzghbL1LpN5EBApABRF26DVDZR9lBQGE=
=gDrs
-----END PGP SIGNATURE-----

```

Copy and paste it into an editor, for example nano, and give it a name for example md5sum.txt.asc

```
nano md5sum.txt.asc
```

Save the file and test it.

```
gpg --keyserver hkp://pgp.mit.edu --recv-keys EB0FC2C8
gpg --verify md5sums.txt.asc
```

It should be clear that it is a 'Good signature from "Nio Sudden Wiklund (sudodus)"'. 

Then check the script file:

```
md5sum -c md5sums.txt.asc
```

It should state

```
install-seamonkey: OK
md5sum: WARNING: 14 lines are improperly formatted
```
(the gpg signature lines are not accepted by md5sum)

You can also inspect manually that the md5sum string matches

 ```
$ md5sum install-seamonkey
5491866c65fb844482bca6a7970116e7  install-seamonkey
```


[SIZE=4]3. In order to install into /usr you run the script with sudo[/SIZE]

```
sudo bash install-seamonkey
```

There will be menu items (as usual).

Details: The script will install

- the seamonkey directory into /opt/
- a link to the executable file into /usr/bin/
- two desktop files and an icon into /usr/share

```

sudo find / -name "*seamonkey*"
/usr/bin/seamonkey
/usr/share/applications/seamonkey.desktop
/usr/share/applications/seamonkey-mozilla-build.desktop
/usr/share/pixmaps/seamonkey-mozilla-build.png
/var/cache/apt/archives/seamonkey-mozilla-build_2.33.1-0ubuntu1_i386.deb
/var/lib/dpkg/info/seamonkey-mozilla-build.preinst
/var/lib/dpkg/info/seamonkey-mozilla-build.md5sums
/var/lib/dpkg/info/seamonkey-mozilla-build.list
/var/lib/dpkg/info/seamonkey-mozilla-build.postrm
/opt/seamonkey
/opt/seamonkey/chrome/icons/default/seamonkey.png
/opt/seamonkey/seamonkey-bin
/opt/seamonkey/seamonkey

ls -l /usr/bin/seamonkey
lrwxrwxrwx 1 root root 24 mar 26 03:42 /usr/bin/seamonkey -> /opt/seamonkey/seamonkey

```

[SIZE=4]
4. Enjoy light-weight browsing with seamonkey :smile:[/SIZE]

---

### Post by sudodus on 2015-06-04
[SIZE=4]Installation into the user's home directory
[/SIZE]
Seamonkey can also be installed into the own user's home directory (without using sudo) in an up to date (updated/dist-upgraded) installation of Lubuntu 14.04.2 LTS. This will not disturb the installation of other web browsers.

Install it like this:

[SIZE=4]1. Download a tarball from[/SIZE]

[http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)
or select locale manually from
[http://www.seamonkey-project.org/releases/#official](http://www.seamonkey-project.org/releases/#official)
The official releases contain code for 32-bit linux operating systems.

See attachment #1

 There are also the [Contributed builds (other platforms)]("http://www.seamonkey-project.org/releases/#contrib") ***if you want the 64-bit version***.
--- f t p : / / f t p .  mozilla.org/pub/mozilla.org/seamonkey/releases/2.33.1/contrib/seamonkey-2.33.1.en-US.linux-x86_64.tar.bz2  ---
Thanks for the tip at [post #5]("http://ubuntuforums.org/showthread.php?t=2281120&p=13298172#post13298172"), [vasa1]("http://ubuntuforums.org/member.php?u=449866").

[SIZE=4]2. Extract the content from the tarball[/SIZE]

It is easy with the archiver program ***file-roller***  in Lubuntu which starts by default. I made a local installation in the  user's home directory, but a more advanced installation, available for  all users, can be made according to the detailed description in the first post: [Installing the light-weight web browser seamonkey]("http://ubuntuforums.org/showthread.php?t=2281120")

See attachment #2

So now there is a directory **seamonkey** in my home directory.

```
tester@tester-SATELLITE-PRO-C850-19W:~$ ls ~/seamonkey/
application.ini             icons             libnssutil3.so    precomplete
blocklist.xml               isp               libplc4.so        removed-files
chrome                      libfreebl3.chk    libplds4.so       run-mozilla.sh
chrome.manifest             libfreebl3.so     libprldap60.so    seamonkey
components                  libldap60.so      libsmime3.so      seamonkey-bin
crashreporter               libldif60.so      libsoftokn3.chk   searchplugins
crashreporter.ini           libmozalloc.so    libsoftokn3.so    Throbber-small.gif
crashreporter-override.ini  libmozsqlite3.so  libssl3.so        updater
defaults                    libnspr4.so       libxul.so         updater.ini
dependentlibs.list          libnss3.so        license.txt       update-settings.ini
dictionaries                libnssckbi.so     omni.ja
distribution                libnssdbm3.chk    platform.ini
extensions                  libnssdbm3.so     plugin-container
tester@tester-SATELLITE-PRO-C850-19W:~$
```

[SIZE=4]3. Symbolic link or alias[/SIZE]

I created a symbolic link, that starts  seamonkey from a terminal window. This is not necessary, but may be  convenient for some people.

```

mkdir -p ~/bin
ln -s $HOME/seamonkey/seamonkey ~/bin

```

[COLOR=#696969]**~/bin** will be in **$PATH** after reboot,  so that links and executable files  in that directory will be found  directly (without explicit path). So it  is enough to type [/COLOR]     

```
seamonkey
``` 

 
(and launch it with the Enter  key) in a terminal window.

An alternative is to make an alias.

[SIZE=4]4. Desktop file[/SIZE]

I created a desktop file, that starts seamonkey from the desktop. (I  use the Swedish locale for Lubuntu, where 'Skrivbord' is used instead of  'Desktop').

```
$ cat ~/Skrivbord/seamonkey.desktop
```
```
[Desktop Entry]
Version=1.0
Categories=Application;System;
Type=Application
Name=seamonkey-local
Comment=Install system to mass storage device, typically USB pendrive
Exec=[COLOR=#0000cd]/home/tester[/COLOR]/seamonkey/seamonkey
Path=[COLOR=#0000cd]/home/tester[/COLOR]/
Icon=[COLOR=#0000cd]/home/tester[/COLOR]/seamonkey/chrome/icons/default/seamonkey.png
Terminal=false
StartupNotify=false
```

In the desktop file you change the user name **[COLOR=#0000cd]tester[/COLOR]** to your own user id, or to be completely correct, change [COLOR=#0000cd]**/home/tester**[/COLOR] to the output of ```
echo $HOME
```

[SIZE=4]5. Run seamonkey[/SIZE]

See attachment #3.

---

### Post by v3.xx on 2015-06-04
I like seamonkey.  And yes, installing can be painful through the site.

Later I'm going to give this a try in a vanilla Mate install, let you know what happens.

Good show :)

---

### Post by sudodus on 2015-06-04
I hope this tutorial will help some people. I'm looking forward to your results in a vanilla Mate install.

If you have tips to improve the tutorial, you are welcome :-)

---

### Post by vasa1 on 2015-06-04
Maybe you could mention the "contributed" builds --- f t p : / / f t p . mozilla.org/pub/mozilla.org/seamonkey/releases/2.33.1/contrib/seamonkey-2.33.1.en-US.linux-x86_64.tar.bz2 --- for those who want the 64-bit version.

---

### Post by sudodus on 2015-06-04
Yes, that is a good idea. Is there a reason why you entered those spaces in the ftp address? Should people not just click on it?

---

### Post by vasa1 on 2015-06-04
> **sudodus said:**
> Yes, that is a good idea. Is there a reason why you entered those spaces in the ftp address? Should people not just click on it?Well, some forums don't like links to downloads posted as such. I wasn't sure about the policy here.

---

### Post by sudodus on 2015-06-04
> **vasa1 said:**
> Well, some forums don't like links to downloads posted as such. I wasn't sure about the policy here.

I will look for some other suitable link (more indirect).

---

### Post by v3.xx on 2015-06-04
Ok, running Seamonkey using the install-seamonkey.gz (per post#1) on Mate 15.10 daily build.

A+ for being fast and painless :D  It installed in seconds, no hiccups and showed up in my menu.

I did go from zcat command, direct to sudo bash.

---

### Post by sudodus on 2015-06-09
On 06/08/2015 11:31 PM, Eric Bradshaw wrote:[INDENT]Israel,

I got your Mozilla SeaMonkey install script from
[http://ubuntuforums.org/showthread.php?t=2281120](http://ubuntuforums.org/showthread.php?t=2281120)

Great job! This really simplifies the install of SeaMonkey.

I've only installed on Lubuntu 14.04.2, but I've noticed somethings
which may (or may not) extend to other flavors:

I. Internet Sub-Menu

a. Chatzilla IRC

1. the shortcut has no icon
Couldn't find one on the system already, or on wikimedia

2. the shortcut actually opens the browser
Exec=seamonkey -chat %U
Should be
Exec=seamonkey -chat %u

b. Mail Client

1. the shortcut has no icon
Should be[?] Icon=/opt/seamonkey/chrome/icons/default/messengerWindow.png

c. Composer

1. shortcut missing completely.
Icon is likely the one at
/opt/seamonkey/chrome/icons/default/editorWindow.png

Eric
[/INDENT]

---

### Post by QDR06VV9 on 2015-06-17
> **sudodus said:**
> I hope this tutorial will help some people. I'm looking forward to your results in a vanilla Mate install.

If you have tips to improve the tutorial, you are welcome :-)
Hi sudodus just curious here, What the difference is between this howto to say this method.[http://linuxg.net/how-to-install-seamonkey-2-25-on-ubuntu-14-0413-1012-1012-04-linux-mint-161413-and-elementary-os-0-2/](http://linuxg.net/how-to-install-seamonkey-2-25-on-ubuntu-14-0413-1012-1012-04-linux-mint-161413-and-elementary-os-0-2/)
Is there better or more current builds there? I seem to always have the current build with above link.
Been using that approach since Raring I think, And on Mate since conception. 
Just Curious Kind Regards:grin:

---

### Post by sudodus on 2015-06-17
> **runrickus said:**
> Hi sudodus just curious here, What the difference is between this howto to say this method.[http://linuxg.net/how-to-install-seamonkey-2-25-on-ubuntu-14-0413-1012-1012-04-linux-mint-161413-and-elementary-os-0-2/](http://linuxg.net/how-to-install-seamonkey-2-25-on-ubuntu-14-0413-1012-1012-04-linux-mint-161413-and-elementary-os-0-2/)
Is there better or more current builds there? I seem to always have the current build with above link.
Been using that approach since Raring I think, And on Mate since conception. 
Just Curious Kind Regards:grin:

Both methods (described here and in your link) use the current (up to date) version of seamonkey ***via the same source***. The method in my post #1 adds some tweaks, that were selected and added by Israel Dahl. Posts #1 and 2 describe with some more details how to do the installation, which might help some users, but I suggest that you continue to install seamonkey the way you have done it all the time.

---

### Post by QDR06VV9 on 2015-06-17
> **sudodus said:**
> Both methods (described here and in your link) use the current (up to date) version of seamonkey ***via the same source***. The method in my post #1 adds some tweaks, that were selected and added by Israel Dahl. Posts #1 and 2 describe with some more details how to do the installation, which might help some users, but I suggest that you continue to install seamonkey the way you have done it all the time.
Thanks Very Clear! I did see the tweaks after the fact.
Again Thanks for the Explanation. I forgot to mention congrats on the bump to Moderator!(Well Deserved)
Kind Regards

---

### Post by sudodus on 2015-06-17
Thanks, runrickus :-)

---

### Post by Amos Moses on 2015-09-18
> **sudodus said:**
> [SIZE=4]Installation into the user's home directory [SIZE=4]4. Desktop file[/SIZE]  I created a desktop file, that starts seamonkey from the desktop. (I  use the Swedish locale for Lubuntu, where 'Skrivbord' is used instead of  'Desktop').  ```
$ cat ~/Skrivbord/seamonkey.desktop
``` ```
[Desktop Entry] Version=1.0 Categories=Application;System; Type=Application Name=seamonkey-local Comment=Install system to mass storage device, typically USB pendrive Exec=[COLOR=#0000cd]/home/tester[/COLOR]/seamonkey/seamonkey Path=[COLOR=#0000cd]/home/tester[/COLOR]/ Icon=[COLOR=#0000cd]/home/tester[/COLOR]/seamonkey/chrome/icons/default/seamonkey.png Terminal=false StartupNotify=false
```  In the desktop file you change the user name **[COLOR=#0000cd]tester[/COLOR]** to your own user id, or to be completely correct, change [COLOR=#0000cd]**/home/tester**[/COLOR] to the output of ```
echo $HOME
```  [SIZE=4]5. Run seamonkey[/SIZE]  See attachment #3.  I'm pretty new to tinkering with my computer, so I think I missed something here. When I tried:  ```
cat ~/Desktop/seamonkey.desktop
```  I got back a message that said there was "no such file or directory". Any tips on what I'm doing wrong?  I managed to get it installed all right and I can run it from the folder it's saved in, but I was hoping to make a desktop file to run it from. Thank you!

---

### Post by sudodus on 2015-09-19
Use a text editor (for example gedit, leafpad, mousepad, konsole). Enter the following content

```
[Desktop Entry]
Version=1.0
Categories=Application;System;
Type=Application
Name=seamonkey-local
Comment=Install system to mass storage device, typically USB pendrive
Exec=[COLOR=#0000cd]/home/tester[/COLOR]/seamonkey/seamonkey
Path=[COLOR=#0000cd]/home/tester[/COLOR]/
Icon=[COLOR=#0000cd]/home/tester[/COLOR]/seamonkey/chrome/icons/default/seamonkey.png
Terminal=false
StartupNotify=false
```

and save it to a file with the name **seamonkey.desktop** in your Desktop directory.

---

### Post by Amos Moses on 2015-09-25
Thanks so much! It worked perfectly.

---

### Post by ronniew on 2015-10-06
You can also simply add the Ubuntuzilla library to your repositories and install through a package manager of your choice.

[http://sourceforge.net/p/ubuntuzilla/wiki/Main_Page/#installation](http://sourceforge.net/p/ubuntuzilla/wiki/Main_Page/#installation)

---

### Post by vasa1 on 2015-11-18
I remember struggling with trying to install 32-bit Seamonkey on my 64-bit Lubuntu. I gave up and used an unofficial 64-bit version instead.

Someone on [Ask Ubuntu]("http://askubuntu.com/questions/698185/is-there-a-way-to-make-32-bit-mozilla-seamonkey-work-in-a-64-bit-xubuntu-14-04") recently posted a way to get a 32-bit install going on 64-bit Xubuntu 14.04. I don't use Seamonkey now but am posting this in case anyone is interested.

---

### Post by bapoumba on 2015-11-18
Threads merged :)

---

### Post by poorguy on 2015-11-20
my mistake.

---

### Post by vasa1 on 2015-11-20
> **poorguy said:**
> here is a very easy way to get the latest version.
it was so easy to do that i was even able to install it.
[URL="http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/s/seamonkey-mozilla-build/"]
http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/s/seamonkey-mozilla-build/[/URL]

See here: [http://ubuntuforums.org/showthread.php?t=2281120&p=13368951#post13368951](http://ubuntuforums.org/showthread.php?t=2281120&p=13368951#post13368951)

---

### Post by poorguy on 2015-11-20
> **vasa1 said:**
> See here: [http://ubuntuforums.org/showthread.php?t=2281120&p=13368951#post13368951](http://ubuntuforums.org/showthread.php?t=2281120&p=13368951#post13368951)


my mistake.

---

### Post by poorguy on 2015-11-21
ok this isn't an install question but it is about seamonkey.
what is the difference between seamonkey browser and firefoxfox browser as both are a mozilla product.

---

### Post by sudodus on 2015-11-21
I find a lot of links when I search the internet for **seamonkey firefox**, for example this link:

[Seamonkey review: Firefox&#8217;s lightweight hyper-functional cousin](http://www.linuxveda.com/2015/03/16/seamonkey-review-firefoxs-lightweight-hyper-functional-cousin/)

---

