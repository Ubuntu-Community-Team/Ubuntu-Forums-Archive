---
title: "Firefox 3???"
date: 2008-06-18
forum: General Help
---

### Post by sponsoredwalk on 2008-06-18
Hi i am on ubuntu 7.10 and i always used firefox 2.0 but today i switched to my firefox 3.0 - 

"Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b3pre) Gecko/2008020507 Firefox/3.0b3pre"

 - that was always there lying pretty dormant until today, i am now wondering how to get movies and mp3's to play via the movie player plugin as it is perfect on firefox 2.0 and plays files fine but if i try to play anything on 3.0 i get asked to download the files instead. 

I am talking about the plug in that actually has a mini version of movie player that comes on the firefox screen when i open a movie or mp3 in a new tab, thanks.

---

### Post by badfish591 on 2008-06-18
in firefox go to tools->options.
and then in the options window click applications at the top and there you can pick how firefox handles different types of media, just find the type of file that you have been trying to open, click on it to highlight it, and then use the pulldown menu on the right to select how it handles that file(your looking for the totem movie player plug-in i believe).

---

### Post by Exsecrabilus on 2008-06-18
> **sponsoredwalk said:**
> Hi i am on ubuntu 7.10 and i always used firefox 2.0 but today i switched to my firefox 3.0 - 

"Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b3pre) Gecko/2008020507 Firefox/3.0b3pre"

 - that was always there lying pretty dormant until today, i am now wondering how to get movies and mp3's to play via the movie player plugin as it is perfect on firefox 2.0 and plays files fine but if i try to play anything on 3.0 i get asked to download the files instead. 

I am talking about the plug in that actually has a mini version of movie player that comes on the firefox screen when i open a movie or mp3 in a new tab, thanks.
Uhh, you know you're running Firefox 3 Beta 3?
You're six versions behind..... ^_^;;

---

### Post by sponsoredwalk on 2008-06-18
I found that menu under preferences and i have tried that but it doesn't change anything... perhaps it is preconfigured to be used only in firefox 2.0 and you have to switch it but i don't know how i would do anything like that?

---

### Post by sponsoredwalk on 2008-06-18
6 versions??? I didn't get any updates so i just assumed...
I haven't used it much. is there an easy way to update it, mabye via terminal?

---

### Post by Exsecrabilus on 2008-06-18
Watch [this topic](http://ubuntuforums.org/showthread.php?t=832407).

---

### Post by Happy_Man on 2008-06-18
Does Help --> Check for Updates not work?

---

### Post by aysiu on 2008-06-18
By what method did you install Firefox 3 on Ubuntu 7.10?

The answers to your questions depend on your answer to this question.

---

### Post by sponsoredwalk on 2008-06-20
Hi there is no check for updates in the help section of the firefox menu and i am pretty sure firefox 3 was in the menu the first time i installed the cd, i don't remember specifically picking it or anything...

---

### Post by Exsecrabilus on 2008-06-20
> **Happy_Man said:**
> Does Help --> Check for Updates not work?
Doesn't exist, as developers understand there are core updating centers in Linux.

---

### Post by Happy_Man on 2008-06-20
Ah, so you're using the distro's version? Well, then, you're going to have to wait. I think the current version is RC2 or something like that...if you're on Hardy. If you're on Gutsy, the latest version (as of when I left Gutsy behind) was Alpha 8 or something similar...

---

### Post by Exsecrabilus on 2008-06-20
If you enable *gutsy-backports*, I think it's Beta 4.

I'm running Hardy, and I have the final version. :)

---

### Post by sponsoredwalk on 2008-06-20
Ubuntu 7.10 - Gutsy... So the fact that i'm in beta means i cannot play movies via the movie player plugin. ok well i can use firefox 2.0 fine anyway i may enable backports. Cool thanks. :KS

---

### Post by aysiu on 2008-06-20
> **sponsoredwalk said:**
> Ubuntu 7.10 - Gutsy... So the fact that i'm in beta means i cannot play movies via the movie player plugin. ok well i can use firefox 2.0 fine anyway i may enable backports. Cool thanks. :KS
Why don't you tell us how you tried to install Firefox 3, and then we can tell you how to get it working with the plugins?

---

### Post by sponsoredwalk on 2008-06-20
> **Happy_Man said:**
> Ah, so you're using the distro's version?

I am using the firefox 3 web browser that was in my applications menu when i first installed ubuntu 7.10 in November,.

---

### Post by aysiu on 2008-06-20
> **sponsoredwalk said:**
> I am using the firefox 3 web browser that was in my applications menu when i first installed ubuntu 7.10 in November,.
That doesn't really make sense. Firefox 3 wasn't available for Ubuntu 7.10 in November. It's not even available for Ubuntu 7.10 now.

---

### Post by sponsoredwalk on 2008-06-20
When i first got 7.10 going i had 2 different firefox programs in my applications menu, firefox (2) and another firefox which is firefox 3 and it said either preview or beta beside it, now it just says firefox 3 web browser

---

### Post by aysiu on 2008-06-20
> **sponsoredwalk said:**
> When i first got 7.10 going i had 2 different firefox programs in my applications menu, firefox (2) and another firefox which is firefox 3 and it said either preview or beta beside it, now it just says firefox 3 web browser
So someone installed 7.10 for you and set up those two menu items? No stock installation of 7.10 is going to give you two versions of Firefox.

Well, let's see if we can get things working again.

Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal):

First, just in case you had some botched installation of Mozilla's Firefox, let's try to remove what might have been done badly. ```
rm -r ~/firefox
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
``` If you get messages about a certain directory not being removed because it doesn't exist, don't worry about it. 

Then, let's make sure the Ubuntu version of Firefox is installed: ```

sudo apt-get update
sudo apt-get install firefox
``` Let's back up your settings for Firefox, just in case. ```
cp -R ~/.mozilla ~/.mozilla.backup
``` Let's download Firefox 3.0 ```
wget -c http://ftp.plusline.de/mozilla/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2
``` Let's install Firefox 3.0 ```
sudo tar -jxvf firefox-3.0.tar.bz2 -C /opt
rm firefox-3.0.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` Now, let's try to launch Firefox 3.0 ```
firefox &
```

---

### Post by sponsoredwalk on 2008-06-21
> **aysiu said:**
> "So someone installed 7.10 for you and set up those two menu items? No stock installation of 7.10 is going to give you two versions of Firefox..." 

I just burned the 7.10 ISO onto a cd and installed it myself, in my gnome menu i found 'Firefox 3 Web Browser' and when i place my cursor over it a description saying - 'Firefox 3.0 Preview' - comes up, I was on my Xfe desktop yesterday and couldn't explain that that is what happens. thats the way it always has been. 

> **aysiu said:**
> "...If you get messages about a certain directory not being removed because it doesn't exist, don't worry about it...." 


I got the messages about that directory being removed and those actions changed nothing so i did the rest of the actions you displayed. i downloaded it and everything went fine. So this firefox 3 that i am on now has replaced my firefox 2 and when i try to play movies the files are correctly ascribed under - >edit >preferences >applications [i.e. some use xine plugins and some use mplayer plugins... ***NOTE*** [COLOR="Blue"]_this is very different from the other firefox as they only display movie player as an option under >edit >preferences >applications and then only a download option comes up when i try and open .wmv/.mpg/.avi files on web pages on this preview firefox 3.0_.][/COLOR] but if i try to open any of these types of files on my newly downloaded firefox it instantly shuts down.

_So to sum up_

**alpha)** *Why does my new and normal firefox 3 close when i try to open these types of files?*

**Beta)** [COLOR="Blue"]*In my preview firefox 3.0 how can i correct the setting so that they each use the specific plugin that applies to that files function?*[/COLOR]

---

### Post by aysiu on 2008-06-21
I'll take your word for it about the .isos containing Firefox 3, but I see a lot of 7.10 users here asking how to install Firefox 3, and I'm using eeeXubuntu (an Eee PC-optimized version of 7.10) and don't have Firefox 3, so just so you know... this is the first time I've heard of Firefox 3 being on 7.10.

As for the closing issue, maybe you have a corrupt profile or some weird extension that's acting buggy. Try ```
mv ~/.mozilla ~/.mozilla.old
firefox &
``` See if you still get the random closings.

---

### Post by sponsoredwalk on 2008-06-21
Now it works great! **_Thanks_ for the help,** did the last command you gave me reset firefox because all my addons and bookmarks (thank buddah i saved) are gone. 

**Alpha)** Is there a way to get my addons back though i can just sift through the site and get them again? 

**Beta)** Does anyone know if it was a plugin and what plugin it was *(if it was a plugin)* that caused it? 

**Gamma)** Is _swiftfox_ better than firefox, from what i've seen on blogs its faster but are there downsides making firefox 3 the best???

Yay:KS:KS:KS

---

### Post by aysiu on 2008-06-21
It renamed your settings folder. So all your bookmarks and add-ons are all in there, just not being used. I'd go ahead and import the bookmarks file, but the add-ons you might want to add on manually one at a time to see which one is screwing things up.

Sometimes the add-on itself isn't too bad, but there may be two add-ons that don't play nice with each other.

---

