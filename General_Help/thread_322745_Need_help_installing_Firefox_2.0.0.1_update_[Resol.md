---
title: "Need help installing Firefox 2.0.0.1 update [Resolved]"
date: 2006-12-20
forum: General Help
---

### Post by FuturePilot on 2006-12-20
Can someone help me install the Firefox 2.0.0.1 update? I'm not exactly sure how to do it.

---

### Post by canadianwriterman on 2006-12-20
I believe that Firefox 2.0.0.1 is a security update. In which case, it will be updated automatically, likely in the next few days. You just have to wait and watch for the update icon. It's worth waiting to avoid the hassle.

---

### Post by FuturePilot on 2006-12-20
But the check for updates is disabled. Will I stii get the update icon?

---

### Post by iamhugeinjapan on 2006-12-20
Firefox security updates are handled by Ubuntu's update manager, that's why the option is greyed out.

---

### Post by canadianwriterman on 2006-12-20
The updates are not done through Firefox itself. They are pushed to you by Ubuntu through the Update Manager. The update icon will appear on the top panel on the right side, beside the date/time. I'm assuming that you are using Edgy with the default Firefox 2.0?

---

### Post by FuturePilot on 2006-12-20
Oh, ok. I thought you were talking about the update manager. I'm using Dapper 6.06

---

### Post by canadianwriterman on 2006-12-21
Do you have Firefox 2.0 on Dapper right now? If so, how did you get it? If it was through the Dapper backports, then I think it will still update automatically. If you downloaded and install 2.0 from the Mozilla Web site yourself, then the Firefox update checkbox should be highlighted.

Failing both of those, you can always download 2.0.0.1 from Mozilla and install it yourself. I see that the download is a tar file. After you untar it, there should be a readme file that describes how to install.

---

### Post by FuturePilot on 2006-12-21
I installed it by using [this]("http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html")
The readme didn't help very much. It just took me to the page to download Firefox
The weird thing is, is that Synaptic still thinks I have 1.5.0.8:confused:

---

### Post by canadianwriterman on 2006-12-21
If Synaptic thinks you have 1.5, then 1.5 is probably still installed somewhere on your system. When you followed the guide for installing 2.0, Synaptic probably didn't pick it up. You could use the same guide, just replace all references to 2.0 in the command lines with 2.0.0.1.

---

### Post by FuturePilot on 2006-12-21
I tried that, but it said no file exists.

---

### Post by canadianwriterman on 2006-12-21
Yes, you're probably right. Try downloading the file from Mozilla and installing it:

[http://www.mozilla.com/en-US/firefox/]("http://www.mozilla.com/en-US/firefox/")

---

### Post by FuturePilot on 2006-12-21
Ok, the reason it didn't work before was because I forgot to change one of the 2.0 to 2.0.0.1:oops:  I have it installed now but Synaptic still says I have 1.5.0.8

---

### Post by canadianwriterman on 2006-12-21
Glad you're all set with 2.0.0.1. Don't worry about Synaptic. It's not picking up your 2.0.0.1 install because the install was done manually without using Synaptic.

---

### Post by FuturePilot on 2006-12-21
Thanks for your help!:D  Does this mean though that I'll have to manually install updates for Firefox from now on?

---

### Post by towsonu2003 on 2006-12-21
See [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) section 1.5 (updating from 2.0 to a later version).

I have Dapper 6.06 and I use this method:
> 
Backup your profile with:
```
cp -R ~/.mozilla ~/.mozilla.backup.20x
```
close Firefox and give your user (yourself) file ownership: ```
sudo chown -R ${USER}:${USER} /opt/firefox
``` Start Firefox normally and update (Help -> Check for updates...) Once the update is completed, close Firefox and then restore ownership to root: ```
sudo chown -R root:root /opt/firefox
``` Do **_NOT_** browse other sites while firefox has these elevated permissions, that is without changing back the ownership of /opt/firefox over to root. Such a practice is ***_[COLOR="DarkRed"][SIZE="4"]not safe[/SIZE][/COLOR]_***.

This assumes that you installed firefox to /opt/firefox as indicated in that howto. 

hmm, well, I just noticed that I forgot to backup my profile this time, oops ;)

---

### Post by matchstich on 2006-12-21
i got 2.0 thru the psychocats site. not sure how to go about getting the upgrade.
thanks

---

### Post by towsonu2003 on 2006-12-21
the script and the other poster's [link]("http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html") use the same place[1] to install the new firefox as the wiki page.  

check it with
```

ls -ls /opt/
``` will have this section: ```
drwxr-xr-x 13 root root 4096 2006-12-21 00:16 firefox
```, in which case, you can use the way provided above and in the wiki. 

I usually try not to use scripts so that I'll be forced to learn what's going in where :)

[1] the relevant part of psychocats script
```

echo -e "\nExtracting the downloaded Firefox archive\n"
sudo tar -C **/opt** -xzf firefox-$VERSION.tar.gz

echo -e "\nRemoving installation file(s) to free up disk space\n"
rm -f firefox-$VERSION.tar.gz firefox-$VERSION.tar.gz.asc

echo -e "\nLinking plugins\n"
sudo mv /opt/firefox/plugins /opt/firefox/plugins_`date -Iseconds`
sudo ln -s -f $PLUGINPATH /opt/firefox/plugins

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s -f /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s -f **/opt/firefox**/firefox /usr/bin/mozilla-firefox

```

---

### Post by matchstich on 2006-12-21
ok, i got the same thing yu show. but, being a noob here, where is the wiki, i tried the  way shown here

[http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html](http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html)

i have the tarball from mozilla on my desktop and changed th line from 2.0 to 2.0.0.1 , but it said that nothing was found.
thanks

---

### Post by towsonu2003 on 2006-12-21
> **matchstich said:**
> ok, i got the same thing yu show. but, being a noob here, where is the wiki
check out my post number 15 above (link: [http://ubuntuforums.org/showpost.php?p=1913510&postcount=15](http://ubuntuforums.org/showpost.php?p=1913510&postcount=15) )

> 
i have the tarball from mozilla on my desktop and changed th line from 2.0 to 2.0.0.1 , but it said that nothing was found.
which line? never mind, the wiki should fix your problem :)

if you get errors, pls don't forget to copy paste everything you get here

---

### Post by matchstich on 2006-12-21
ok, but you said that runs it as root, that is why i didn't do that.  how do i change it back from root? 
thanks

---

### Post by towsonu2003 on 2006-12-21
> **matchstich said:**
> ok, but you said that runs it as root, that is why i didn't do that.  how do i change it back from root? 
thanks

if I understand you correctly[1], the way I do (posted above) doesn't run it as root. instead, you change the folder ownerships (the first chown command) so the files belong to you, launch firefox as yourself and let it update, and then change back the file ownerships (second chown command) back to root. 

if you forget to do the second chown command and let the files in /opt/firefox be owned by yourself, that's not safe. 

[1] if I misunderstood, can you give quotes of what you're refrring to? :mrgreen:

---

### Post by matchstich on 2006-12-21
ok, my apology's to y'all, i got it installed. my mistook was putting in " en-us"  when i had to do   "en-US "
going on 3 days with 2 hours of sleep. 
but,  the up date feature is still  greyed out.

thanks for the help.

i am keeping that page bookmarked in case ff updates again.

---

### Post by towsonu2003 on 2006-12-21
> **matchstich said:**
> 
but,  the up date feature is still  greyed out.


I'm assuming (from the start of this thread) that you're using Dapper. 

When you chown the /opt/firefox (i.e. change folder and file permissions so that their owner is you) directory and launch firefox, the option will be back to normal. as usual, just to remind, don't forget to change back the file ownerships (second chown command) back to root.

> going on 3 days with 2 hours of sleep
ouch - come back and read the thread once more when you had time to sleep eheh :mrgreen: :p 

PS. be careful, when you're tired but still play around with sudo, it's dangerous ;)

---

### Post by FuturePilot on 2006-12-21
> **towsonu2003 said:**
> PS. be careful, when you're tired but still play around with sudo, it's dangerous ;)
Got that right lol:p  Is there a way to update through Synaptic or at least make it realize I have the latest version?

---

### Post by towsonu2003 on 2006-12-21
> **FuturePilot said:**
> Got that right lol:p  Is there a way to update through Synaptic or at least make it realize I have the latest version?

nope, sorry.

---

### Post by asnd16 on 2006-12-21
OK ok ok ok sos how are we able to install this? ](*,)

---

### Post by matchstich on 2006-12-21
[http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html](http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html)

go there and do what it say buy put in 2.0.0.1 instead of 2.0 and if you want american english change the  part about en-GB to en-US, it worked for me and i was dead tired when i  did it. thanks
now to see if i can get help on how to get a sane patch where it belongs.

---

### Post by keithpeter on 2006-12-22
> **towsonu2003 said:**
> See [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) section 1.5 (updating from 2.0 to a later version).

I have Dapper 6.06 and I use this method:

hmm, well, I just noticed that I forgot to backup my profile this time, oops ;)

Is this idea of enabling software updates from within Firefox going to work with Swiftfox or am I going to have to a re-install manually?

CHeers

---

### Post by bkj1 on 2006-12-22
Generally, you can install any application through Synaptic from the Ubuntu repositories. These sections will only describe those installations that require some non-standard action to get them installed and working (most often due to them not being present in the repositories).
Install Official Mozilla Build of Firefox

Firefox updates for Ubuntu releases usually come a few days after the official security patches are released. You can either wait, and in the meantime be susceptible to those security holes, or install the official mozilla release instead. Lucky for us, it is quite simple to do. This page on the Ubuntu wiki spills the beans on how to get the new firefox going.

As an alternative to following the wiki instructions, you can use this script that will automatically download and install the newest firefox for you. I created it in collaboration with Aysiu, who helped with testing, ideas, and motivation. It automatically detects the newest firefox release, allows you to make a choice of language for firefox, verifies the gpg signature, and installs the new firefox in /opt/firefox. Here are the steps to take to use this script:

    * Download the script to your desktop
    * Open a terminal (how?)
    * Enter these commands: 

cd Desktop
chmod +x installnewfirefox.sh
./installnewfirefox.sh

And, if no errors occur, your new firefox is ready for use!

A few little tricks:

    * If middle click on tab to close it does not work, you can enable it by pointing Firefox to "about:config" and set middleclick.contentloadURL to false. Voila, middle click to close works again.
    * To enable the autoscroll (where you middle click and a little arrow-graphic appears and you can scroll just by moving the mouse), go to "about:config" and set general.autoScroll to true.
    * To automatically select the entire contents of the URL bar when you click there, open "about:config" and set browser.urlbar.clickSelectsAll to true. I find this a helpful usability improvement. 

all of this was directly ripped from here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles)
This script only works on Breezy, Dapper, or Edgy.

---

### Post by treris on 2006-12-22
I used that script first to update to firefox 2.0 under dapper and then to go to firefox 2.0.0.1 
worked like a charm!
only thing I had to do was manually add the jre plugin to the plugin directory in /opt/firefox that was about it and it's been awesome ever since

Thanks for all the work bkj1 and Aysiu!!!

---

### Post by towsonu2003 on 2006-12-22
> **keithpeter said:**
> Is this idea of enabling software updates from within Firefox going to work with Swiftfox or am I going to have to a re-install manually?

CHeers

I think swiftfox does not allow anyone to get incremental updates. (i.e. no)

---

### Post by FuturePilot on 2006-12-22
> **bkj1 said:**
> 

Firefox updates for Ubuntu releases usually come a few days after the official security patches are released. You can either wait, and in the meantime be susceptible to those security holes,.
But then why have I still not recieved an update to 2.0? I keep getting ones for 1.5

---

