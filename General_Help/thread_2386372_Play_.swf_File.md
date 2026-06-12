---
title: "Play .swf File"
date: 2018-03-05
forum: General Help
---

### Post by zackarycw on 2018-03-05
I'm relatively new to Ubuntu and have tried everything to try and play some .swf files that I have. I installed the flash plugin by downloading the .tar.gz file from adobe's flash site and putting it in firefox's plugin folder.
```
sudo nautilus
```
is how I was able to write to it. I went to /usr/share/mime/packages and modified the freedesktop.org.xml such that "vnd.adobe.flash.movie" is now "x-shockwave-flash". I cannot seem to find GNU Gnash (or just gnash) in the Ubuntu Software Store.
I changed the .xml file by doing the following:
```
sudo su
cd /usr/share/mime/packages
cp freedesktop.org.xml freedesktop.org.xml.old
```
I modified this one by using VSCode.
```
update-mime-database /usr/share/mime/
```
After this I still can't seem to find a way to play my .swf files. I've been searching for a solution for about a week now and would appreciate any help.
~~Thanks!

---

### Post by tinylagarto on 2018-03-05
You probably should be able to open it from your browser. Of course you need the Flash plugin for Firefox. There is no need to install it from Adobe.

You can install it with this command from the terminal:

```
 sudo apt install flashplugin-installer
```

Then restart your browser. 

If you have Chrome installed you already have working Flash as it comes with its own Pepper Flash plugin.

---

### Post by zackarycw on 2018-03-05
I've already done this command in the terminal as well. It prompts to use sudo apt-get remove to remove it. I did uninstall and reinstall but nothing seems to have changed. Is there anything else that might make flash files not play?

---

### Post by zackarycw on 2018-03-05
Firefox DOES play flash files when it is ON THE WEB like from comdotgame.com etc. It just can't seem to play the .swf files downloaded on my computer.

---

### Post by #&amp;thj^% on 2018-03-05
Or you can install "swfdec-gnome" should work for most .swf files.
I haven't used this for a couple years now but give it whirl.
> This package is a transitional package for upgrading to Gnash
It can be safely removed when Gnash is installed

---

### Post by monkeybrain20122 on 2018-03-05
You can play .swf files in Firefox by doing the following(flash plugin has to be installed first of course)

In your home directory create a new document called .mime.types (note the "." in front, this is a hidden file). In it put only one line
```
application/x-shockwave-flash       swf swfl
``` (**Edited:** This is a lot cleaner than messing with freedesktop.org.xml )

Then logout and log back in (may not be necessary)

Next, you need to edit FF's config for it to play local .swf files. Open firefox, type about:config in the url, when the warning comes up click you accept the risks. Then in the search type plugins
locate the string 
> plugins.http_https_only
 click on value and change it to false.

Restart Firefox for it to take effect.

Now right click on your .swf file in Properties > Open with choose Firefox as the default. Now click on it an it would play in Firefox. 

**Edited:** Now setting plugins.http_https_only to be false means disabling a FF security feature, so do it at your own risk. You can mitigate it a bit by going to Tools > plugins and set flash's setting to "ask to activate" so you have to give it explicit permission to play a file.

---

### Post by zackarycw on 2018-03-06
OMG THIS WORKED. All I needed was the plugins.http_https_only thing toggled, other step didn't seem to do much. THANK YOU SO MUCH!!!!!!! This is my first time on this forum, is there a way I can set this issue to solved? THANK YOU!!

---

### Post by zackarycw on 2018-03-06
Use method described earlier in thread or configure freedesktop.org.xml accordingly then go to FF about:config and toggle plugins.http_https_only . Thank you [**[COLOR=#000000]monkeybrain20122[/COLOR]**]("https://ubuntuforums.org/member.php?u=1843403") and others for solution. (re-logging was not necessary here)

---

### Post by tinylagarto on 2018-03-06
> **zackarycw said:**
> This is my first time on this forum, is there a way I can set this issue to solved? THANK YOU!!

Edit the title in the first post of this thread.

---

### Post by dragonfly41 on 2018-03-06
Or read Thread Tools drop down menu at top right of this page.

---

### Post by oldos2er on 2018-03-06
> **ivanovnegro2 said:**
> Edit the title in the first post of this thread.

Easier to use Thread Tools,  just FYI.

---

### Post by tinylagarto on 2018-03-06
> **oldos2er said:**
> Easier to use Thread Tools,  just FYI.

Cool. Thanks. Did not know this exists.

---

