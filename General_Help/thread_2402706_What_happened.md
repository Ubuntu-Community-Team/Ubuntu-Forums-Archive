---
title: "What happened?"
date: 2018-10-03
forum: General Help
---

### Post by sjm44 on 2018-10-03
I am totally new to the Forum and also to using Ubunto OS.  I was given an notebook computer with the Ubunto OS and it has worked fine until I experienced a problem with an on-line program using Chrome web browser.  It was recommended to update Chrome which I did and since then I cannot get on the internet.  When I try loading Chrome, nothing happens.  I see that there was another web browser on the computer called Chromiun so I tried to load it and the same thing happens.
I checked the wifi connection and it is very strong and all other devices in the house work fine.  It indicates with the wifi symbol that it is connected to the wifi.
The version of Ubunto the computer has is 14.04LTS. 

No one around town knows anything about it and cannot help.

Any help would be appreciated.

Thanks

---

### Post by SeijiSensei on 2018-10-03
Do you get an error like it not being able to identify the remote server by name?

Try connecting to [http://91.189.94.12/](http://91.189.94.12/).  Do you get the "We Are Canonical" page?  If so, the method for resolving names into addresses is broken.  If not, then the problem is more profound.

---

### Post by sjm44 on 2018-10-03
Thanks for the response.
I get no error messages, when I try to open Chrome and Chromium it indicates with the little circular icon that it is attempting to work.  Then it disappears and nothing happens.


the desktop opens fine and I can have access to that.

If I do not have an internet screen, where or how do I enter the http address you suggested?

Remember, you are working with a limited tech savvy person.  

Steve

---

### Post by monkeybrain20122 on 2018-10-03
Just to rule out internet connection problem can you connect with Firefox? By your description it seems that Chrome/Chromium just refuse to start. It is a different issue than not having connection.

Check [https://askubuntu.com/questions/488823/google-chrome-not-starting](https://askubuntu.com/questions/488823/google-chrome-not-starting)

---

### Post by yancek on 2018-10-03
Try running google-chrome from a terminal and see if there are any errors/messages.  On my system this is done with:  /opt/google/chrome/google-chrome.  Could check to see if that is where it is loxRWS on your system.

---

### Post by sjm44 on 2018-10-03
I hope it is apparent that I am using my desktop computer to communicate here.
I do not have Firefox loaded on the effected computer.
How do I try to start Chrome in terminal mode.  How do I get to the terminal mode in Ubunto?

Somewhere in loading the up to date Chrome I seem to remember seeing something about Chrome "running from a terminal".

Thanks again and hope I am not boring you.  

Steve

---

### Post by oldos2er on 2018-10-03
Ctrl-Alt-t should open a terminal, then type in google-chrome as yancek suggested.

---

### Post by sjm44 on 2018-10-04
Back again, had to get something done yesterday
I tried entering the google/chrome in the terminal mode and it says "no such file or directory"

---

### Post by oldos2er on 2018-10-04
Should be google-chrome, not google/chrome.

I'm a bit puzzled by "I do not have Firefox loaded on the effected computer." since Firefox has been the default browser on Ubuntu for years, including on 14.04.

---

### Post by sjm44 on 2018-10-04
I tried all different ways, with google-chrome and it still says the same thing.

---

### Post by sjm44 on 2018-10-04
I see in the downloads file directory there is a file called "google-chrome-stable_current_amd64(2).deb
When I double click this it brings up a page like it starting to load. Then another page appears, Ubuntu Software Center with a message that this program is run from a terminal.  It also says that the program is installed.

---

### Post by i7Fd-2sCB1 on 2018-10-04
Does this error appear with the vanilla Chrome browser from [https://www.google.com/chrome/](https://www.google.com/chrome/) ??? Download the up-to-date Chrome from the official site then double click the .deb to install it, it should have a popup which should then continue the setup. It may be a specific error with the chromium package but I want to see if you encounter it with the official Google's browser Chrome not chromium which is the open source build, Chrome is the proprietary build of Google's official browser thus not open source if I understand correctly.

---

### Post by sjm44 on 2018-10-04
ok, here is what the terminal screen shows

user2@shittop:-$ (it apprears that whoever had this computer before me did not like Ubuntu ;-} )

When I enter the [https://www.google.com/chrome/](https://www.google.com/chrome/) the response is No such file or directory

I must be doing something wrong.

---

### Post by i7Fd-2sCB1 on 2018-10-04
> **sjm44 said:**
> ok, here is what the terminal screen shows

user2@shittop:-$ (it apprears that whoever had this computer before me did not like Ubuntu ;-} )

When I enter the [https://www.google.com/chrome/](https://www.google.com/chrome/) the response is No such file or directory

I must be doing something wrong.

Did you install Ubuntu yourself or did someone else? Sounds to me like its a second hand computer. If it was installed and setup when the previous person had the said computer they may have altered some configurations to the main system have you considered a reset? A fresh install of Ubuntu on the device and start over but backing up your files before setting it up again? What does this command show?
```

history

```
That command should display what was done in the terminal is it possible showing it?

---

### Post by deadflowr on 2018-10-04
Try removing or moving the chrome profile,
in the terminal run
```
mv ~/.config/google-chrome ~/.config/google-chrome.old
```
see if that does anything.

Also let's see what is actually installed, (in terminal, still, run)
```
apt-cache policy google-chrome-stable
```
and perhaps a list of installed file related to chrome
```
dpkg -L google-chrome-stable
```

---

### Post by sjm44 on 2018-10-04
When I type in history, it only shows the last 3 commands I tried, nothing else

Yes it is a used computer and it apparently came with Windows installed and the previous owner does not like Windows.  He broke the screen off thinking it was a combination laptop and tablet.  Got mad and gave it to me.  I repaired the hinges and have been using it for a couple of years with no problem.  Then the problem Chrome was causing with one site and then the downloading the updated Chrome and here we are.
I only use it for traveling to check mail and a couple of other sites and I do not have any data on it that I could not replace easily.  
I had no problem with Ubuntu operating system so maybe a reset would be the way to go.  I don't know how to do it in Ubuntu.  

Thanks

---

### Post by deadflowr on 2018-10-04
>  I don't know how to do it in Ubuntu. 
Easy, backup and reinstall the system fresh.
Ubuntu doesn't have a restore point system like Windows, since reinstalling it is quick and fast.
And restoring your backups is simple. (Or simple if you don't overthink it)
Then post reinstall/backup restore you apply all system updates and then install the software you want
either through the Ubuntu Software store or apt/apt-get/synaptic/some other package management software program.

Ubuntu's default backup program backups up only your personal Home folder by default.
Dig around and you'll find many other backup program and maybe one that suits your needs better:
Reference here: [https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by sjm44 on 2018-10-04
OK when I enter the dpkg command a long string of things come up, to much enter here.. The first few lines are;
/.
/usr
/usr/share
/usr/share/appdata
/usr/share/appdata/google-chrome.appdata.xml

---

### Post by deadflowr on 2018-10-04
You can post all, use code tags
It should look like this:
```
/.
/usr
/usr/share
/usr/share/appdata
/usr/share/appdata/google-chrome.appdata.xml
/usr/share/doc
/usr/share/doc/google-chrome-stable
/usr/share/doc/google-chrome-stable/changelog.gz
/usr/share/menu
/usr/share/menu/google-chrome.menu
/usr/share/gnome-control-center
/usr/share/gnome-control-center/default-apps
/usr/share/gnome-control-center/default-apps/google-chrome.xml
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/google-chrome-stable.1.gz
/usr/share/applications
/usr/share/applications/google-chrome.desktop
/usr/bin
/opt
/opt/google
/opt/google/chrome
/opt/google/chrome/locales
/opt/google/chrome/locales/en-US.pak
/opt/google/chrome/locales/ja.pak
/opt/google/chrome/locales/id.pak
/opt/google/chrome/locales/ca.pak
/opt/google/chrome/locales/fi.pak
/opt/google/chrome/locales/es-419.pak
/opt/google/chrome/locales/ru.pak
/opt/google/chrome/locales/am.pak
/opt/google/chrome/locales/sk.pak
/opt/google/chrome/locales/vi.pak
/opt/google/chrome/locales/sl.pak
/opt/google/chrome/locales/fr.pak
/opt/google/chrome/locales/ko.pak
/opt/google/chrome/locales/da.pak
/opt/google/chrome/locales/nl.pak
/opt/google/chrome/locales/bg.pak
/opt/google/chrome/locales/en-GB.pak
/opt/google/chrome/locales/ta.pak
/opt/google/chrome/locales/kn.pak
/opt/google/chrome/locales/cs.pak
/opt/google/chrome/locales/th.pak
/opt/google/chrome/locales/nb.pak
/opt/google/chrome/locales/pt-BR.pak
/opt/google/chrome/locales/sv.pak
/opt/google/chrome/locales/gu.pak
/opt/google/chrome/locales/uk.pak
/opt/google/chrome/locales/mr.pak
/opt/google/chrome/locales/de.pak
/opt/google/chrome/locales/pt-PT.pak
/opt/google/chrome/locales/zh-CN.pak
/opt/google/chrome/locales/he.pak
/opt/google/chrome/locales/ro.pak
/opt/google/chrome/locales/hu.pak
/opt/google/chrome/locales/sr.pak
/opt/google/chrome/locales/el.pak
/opt/google/chrome/locales/sw.pak
/opt/google/chrome/locales/pl.pak
/opt/google/chrome/locales/es.pak
/opt/google/chrome/locales/hi.pak
/opt/google/chrome/locales/et.pak
/opt/google/chrome/locales/zh-TW.pak
/opt/google/chrome/locales/bn.pak
/opt/google/chrome/locales/it.pak
/opt/google/chrome/locales/hr.pak
/opt/google/chrome/locales/lt.pak
/opt/google/chrome/locales/lv.pak
/opt/google/chrome/locales/ms.pak
/opt/google/chrome/locales/tr.pak
/opt/google/chrome/locales/ar.pak
/opt/google/chrome/locales/te.pak
/opt/google/chrome/locales/ml.pak
/opt/google/chrome/locales/fa.pak
/opt/google/chrome/locales/fil.pak
/opt/google/chrome/product_logo_16.png
/opt/google/chrome/product_logo_128.png
/opt/google/chrome/xdg-mime
/opt/google/chrome/swiftshader
/opt/google/chrome/swiftshader/libGLESv2.so
/opt/google/chrome/swiftshader/libEGL.so
/opt/google/chrome/chrome_100_percent.pak
/opt/google/chrome/resources.pak
/opt/google/chrome/product_logo_64.png
/opt/google/chrome/v8_context_snapshot.bin
/opt/google/chrome/product_logo_32.png
/opt/google/chrome/cron
/opt/google/chrome/cron/google-chrome
/opt/google/chrome/natives_blob.bin
/opt/google/chrome/google-chrome
/opt/google/chrome/default_apps
/opt/google/chrome/default_apps/gmail.crx
/opt/google/chrome/default_apps/drive.crx
/opt/google/chrome/default_apps/docs.crx
/opt/google/chrome/default_apps/youtube.crx
/opt/google/chrome/default_apps/external_extensions.json
/opt/google/chrome/nacl_helper_bootstrap
/opt/google/chrome/MEIPreload
/opt/google/chrome/MEIPreload/preloaded_data.pb
/opt/google/chrome/MEIPreload/manifest.json
/opt/google/chrome/libwidevinecdm.so
/opt/google/chrome/product_logo_22.png
/opt/google/chrome/nacl_irt_x86_64.nexe
/opt/google/chrome/product_logo_24.png
/opt/google/chrome/icudtl.dat
/opt/google/chrome/chrome-sandbox
/opt/google/chrome/nacl_helper
/opt/google/chrome/product_logo_48.png
/opt/google/chrome/chrome
/opt/google/chrome/default-app-block
/opt/google/chrome/xdg-settings
/opt/google/chrome/product_logo_32.xpm
/opt/google/chrome/product_logo_256.png
/opt/google/chrome/chrome_200_percent.pak
/etc
/etc/cron.daily
/usr/share/man/man1/google-chrome.1.gz
/usr/bin/google-chrome-stable
/etc/cron.daily/google-chrome

```

---

### Post by sjm44 on 2018-10-04
do I enter the https: address in the terminal mode?

---

### Post by sjm44 on 2018-10-04
Yes, that string of lines is what it looks like.  Now what?

---

### Post by deadflowr on 2018-10-04
> [do I enter the https: address in the terminal mode?
You enter it into a browser address bar.
But is the issue really that browsers aren't opening at all?
that's what I'm gathering from what I've read.

It's not about making internet connections, it's the browser never actually opens.
Is the correct?

---

### Post by sjm44 on 2018-10-04
Well I went to the web and downloaded Ubuntu 16.04.5 on a USB drive figuring i should update the old version on the computer anyway.  To load it onto the computer I have to change the boot device to the USB drive.  Unfortunately to do this on the ASUS I have you have to update the BIOS.  To do this it appears I have to go on the internet and download the update to install it. 

Do you see where I am going?

I need to get the offending computer to be able to connect to the internet.  If I do this there is no reason to upgrade to a new version of Ubuntu.

So here I am back at the beginning.

Right now I am going upstairs and have supper and have a big glass of wine.

If anyone can offer a resolution I would greatly appreciate it.

Thanks to all so far.

---

