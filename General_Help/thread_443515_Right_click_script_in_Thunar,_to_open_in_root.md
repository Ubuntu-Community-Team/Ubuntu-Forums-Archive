---
title: "Right click script in Thunar, to open in root?"
date: 2007-05-14
forum: General Help
---

### Post by crimesaucer on 2007-05-14
I would like to have this option in Thunar, is it possible?

This is in the wiki page: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_open_files_as_root_user_via_right_click](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_open_files_as_root_user_via_right_click) , but it's for nautilus:

 "How to open files as root user via right click"

```
gedit $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```

Insert the following lines into the new file

```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gksudo "gnome-open $uri" &
done

```

Save the edited file

```
chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```

```
Right click on file -> Scripts -> Open as root

```


....is there a similar way to be able to right click onto any script in my xubuntu's Thunar File System, and then be able to open it in root so that I can save changes?

---

### Post by crimesaucer on 2007-05-14
To edit a file, like my .conkyrc.....I usually have to click alt + F2 and enter gksudo thunar

I just wish that there was a way, that if I were already in my Thunar File System, and I felt like opening a certain file that usually needs to be opened in root to edit/save, that I could right click it, and open it in root from my drop down menu, instead of having to open gksudo thunar, and then having to search through my folder to get to the exact same file that I was already looking at in my regular Thunar.

---

### Post by aidanr on 2007-05-14
install libgnome2-0 and in thunar go edit -> configure custom actions and add the command 
gksudo gnome-open %f

if it's just config files though, i'd use
gksudo mousepad %f

---

### Post by kerry_s on 2007-05-14
pics->

---

### Post by crimesaucer on 2007-05-15
Thank you both, and kerry_s, thanks for the photos, I had no idea how easy that was. Everything works perfectly now.

Thanks again.

EDIT- I decided to post some screenshots for anyone else who might want the same function in Thunar.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-116.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-116-1.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-116-1.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-117.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-117-1.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-117-1.png)

---

### Post by kerry_s on 2007-05-15
my debian xfce4->

---

### Post by crimesaucer on 2007-05-15
> **kerry_s said:**
> my debian xfce4->

Hey kerry_s- Do you know of any other Custom Actions that I might want to make for Thunar to work even better?

I'm loving the the Root- open w/ mousepad Custom Action.

---

### Post by kerry_s on 2007-05-15
I just have a root-terminal. Also grab the thunar archive plugin, but use file-roller instead of xarchiver, xarchiver has been broken like forever. Other than that, i'll usually add things like "open-geany"(geany %f) if want nice color when working on html and executables. I also sometimes put my other players for my music, but i'm mostly vlc these days. Also scrot works better than the snapshot plugin.
whole screen= scrot %T.jpg
select & drag select= scrot -sb %T.jpg
wait 5= scrot -d 5 %T.jpg

If you got space, running you own dns cache helps-> [http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html](http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html)

Don't for get to fix the /etc/hosts file
127.0.0.1	localhost yourhostname
127.0.1.1	yourhostname

Also i notice you using alot of the xfce4 plugins, those tend to slow down load time, if that matters.
 
Have you added the tweaks to /etc/sysctl.conf ?

vm.swappiness=0
net.core.rmem_default = 524288 
net.core.rmem_max = 524288 
net.core.wmem_default = 524288 
net.core.wmem_max = 524288 
net.ipv4.tcp_wmem = 4096 87380 524288 
net.ipv4.tcp_rmem = 4096 87380 524288 
net.ipv4.tcp_mem = 524288 524288 524288 
net.ipv4.tcp_rfc1337 = 1 
net.ipv4.ip_no_pmtu_disc = 0 
net.ipv4.tcp_sack = 1 
net.ipv4.tcp_fack = 1 
net.ipv4.tcp_window_scaling = 1 
net.ipv4.tcp_timestamps = 1 
net.ipv4.tcp_ecn = 0 
net.ipv4.route.flush = 1



These tweak goes in /etc/rc.local->

echo 1000 > /proc/sys/dev/rtc/max-user-freq &
echo "base=0x98000000 size=0x8000000 type=write-combining" >| /proc/mtrr &


gksu mousepad /etc/modprob.d/bad_list
copy & paste->

alias net-pf-10 off


gksu mousepad /etc/environment
add

MOZ_DISABLE_PANGO="1"


I only installed this debian 2 days ago, so that's all i've done for now. This rest of the tweaks i've done has been for opera. I've got opera going way faster than firefox/iceweasel.

---

### Post by crimesaucer on 2007-05-15
Thank you for all of that good info. I haven't played around with my system that much beside graphically. I'm going to try to get my system faster now.

Thanks again.

---

### Post by BLTicklemonster on 2007-05-16
Sweet, I use thunar, and wondered about this.

---

### Post by crimesaucer on 2007-05-16
> **kerry_s said:**
> I just have a root-terminal. Also grab the thunar archive plugin, but use file-roller instead of xarchiver, xarchiver has been broken like forever. Other than that, i'll usually add things like "open-geany"(geany %f) if want nice color when working on html and executables. I also sometimes put my other players for my music, but i'm mostly vlc these days. Also scrot works better than the snapshot plugin.
whole screen= scrot %T.jpg
select & drag select= scrot -sb %T.jpg
wait 5= scrot -d 5 %T.jpg

If you got space, running you own dns cache helps-> [http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html](http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html)

Don't for get to fix the /etc/hosts file
127.0.0.1	localhost yourhostname
127.0.1.1	yourhostname

Also i notice you using alot of the xfce4 plugins, those tend to slow down load time, if that matters.
 
Have you added the tweaks to /etc/sysctl.conf ?

vm.swappiness=0
net.core.rmem_default = 524288 
net.core.rmem_max = 524288 
net.core.wmem_default = 524288 
net.core.wmem_max = 524288 
net.ipv4.tcp_wmem = 4096 87380 524288 
net.ipv4.tcp_rmem = 4096 87380 524288 
net.ipv4.tcp_mem = 524288 524288 524288 
net.ipv4.tcp_rfc1337 = 1 
net.ipv4.ip_no_pmtu_disc = 0 
net.ipv4.tcp_sack = 1 
net.ipv4.tcp_fack = 1 
net.ipv4.tcp_window_scaling = 1 
net.ipv4.tcp_timestamps = 1 
net.ipv4.tcp_ecn = 0 
net.ipv4.route.flush = 1



These tweak goes in /etc/rc.local->

echo 1000 > /proc/sys/dev/rtc/max-user-freq &
echo "base=0x98000000 size=0x8000000 type=write-combining" >| /proc/mtrr &


gksu mousepad /etc/modprob.d/bad_list
copy & paste->

alias net-pf-10 off


gksu mousepad /etc/environment
add

MOZ_DISABLE_PANGO="1"


I only installed this debian 2 days ago, so that's all i've done for now. This rest of the tweaks i've done has been for opera. I've got opera going way faster than firefox/iceweasel.

Well, things feel faster now, and they were already pretty quick with xubuntu.

I haven't done the dns cache yet, I'll read into it tomorrow, but I do have one question about the part for the /etc/rc.local->

Was I supposed to leave the exit = 0 part at the end? Like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 1024 > /proc/sys/dev/rtc/max-user-freq &
echo "base=0x98000000 size=0x8000000 type=write-combining" >| /proc/mtrr &

exit 0

```

besides that, I read into everything else and added them the correct way. I also read a cool part in a debian page for disabling the extra tty's that I don't use (2-6).

And your app, geany, looked really cool for writing html and other languages. 

So thanks again, and feel free to link me to any pages that you know that helping make my computer better.

---

### Post by kerry_s on 2007-05-16
Yes, you did it right. I forgot about the tty's, i have 2->6 disabled as well.
Also for the this->
echo 1024 > /proc/sys/dev/rtc/max-user-freq &
should be->
echo 1000 > /proc/sys/dev/rtc/max-user-freq &

This is a hz setting for resposiveness if set incorrectly it may cause apps to go unresponsive. It's a old school trick that, i stiil use.

I do have 1 more trick for firefox first start, it loads firefox into cache for faster startup from a reboot or if your one of those people who actually turn there computer off. It's a bit complicated, you would need to download a firefox.tgz from the site, it only works if the firefox is all in one folder, currently a firefox install is split to /etc/firefox, /usr/lib/firefox, /usr/shre/firefox, you just need /usr/lib/firefox.

So you would download firefox, unpack it, copy /usr/lib/mozilla-firefox/plugins to the new firefox. Change the old /usr/lib/firefox to firefox.old and copy the new one there, then add this to /etc/rc.local->

sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &

Replace the 3 "user" with your login name. Hope you can follow that.

---

### Post by crimesaucer on 2007-05-16
> **kerry_s said:**
> Yes, you did it right. I forgot about the tty's, i have 2->6 disabled as well.
Also for the this->
echo 1024 > /proc/sys/dev/rtc/max-user-freq &
should be->
echo 1000 > /proc/sys/dev/rtc/max-user-freq &

This is a hz setting for resposiveness if set incorrectly it may cause apps to go unresponsive. It's a old school trick that, i stiil use.


Yes, you were correct, My Exaile! would not play music until I deleted that part. Then after putting it it as echo 1000, everything worked good for Exaile!.

I do have a strange problem happening with my media player Xine-ui. It plays fine on one of my Beryl AiGLX workspace windows, but if I leave it playing on that workspace 1, and move to one of my other 4 workspaces, my cpu goes through the roof. My xorg jumps to like 90% plus, and then my Xine-ui gets an error message about dropped frames.


EDIT- well, I don't know what my problem is with my Xine-ui, I tried removing all of my new settings, and it worked perfectly for a moment. My xorg stayed at about 6.00 cpu % on my conky, and I had no cpu spike when I rotated to different cube workspaces with a Xine movie playing. Then I added one part, this part: MOZ_DISABLE_PANGO="1" and my cpu went through the roof again. So I removed that part, and my cpu is still through the roof (with all of the settings regualr) for the xorg, when playing a Xine movie on a different workspace, so I don't what the problem is. It used to mot be like that. 

I'm going to mess around with it for a while.

---

### Post by kerry_s on 2007-05-16
Sorry, i don't use beryl so i haven't tried any of those settings with beryl. Let me know what settings was the cause if you find it so i don't put it for the next person, thanks.

---

### Post by BLTicklemonster on 2007-05-16
> **aidanr said:**
> install libgnome2-0 and in thunar go edit -> configure custom actions and add the command 
gksudo gnome-open %f

if it's just config files though, i'd use
gksudo mousepad %f

Sweet!!! Thanks!

---

### Post by crimesaucer on 2007-05-17
> **kerry_s said:**
> Sorry, i don't use beryl so i haven't tried any of those settings with beryl. Let me know what settings was the cause if you find it so i don't put it for the next person, thanks.

I think it's just Beryl and Xine. I might of not noticed it before, since I never rotate to a different work space when a movie is playing.

To check if it was the new settings, I change all my settings back to normal, ran: sudo sysctl -p after I had changed my /etc/sysctl.conf back to normal. Then I rebooted and I still had the terrible cpu for xorg.

So, I "remove --purged" xine-ui, after a xine-check, and then tried out VLC and mplayer, and I had problems with them both. VLC would only work in xfwm4, not Beryl, and even when it sort of worked in Beryl, it would get the huge cpu for xorg when rotating to a different workspace. Plus Conky would mess with VLC's fullscreen display.

Mplayer wouldn't even work for some reason. So I reinstalled xine-ui, which works perfectly as long as I don't switch to a different cube face. 

And then I added that new code back into my /etc/sysctl.conf, and also fixed the /etc/rc.local-> with the correct echo 1000.

I didn't add the ' MOZ_DISABLE_PANGO="1" ' because I am happy with my fonts right now and I wasn't sure how it might change it, I'll read up on it but wasn't sure what to do. And as for this "alias net-pf-10 off" for ipv6, I wasn't sure if I needed to do that, I read mixed opinions and figured I would read up on it some more.


As for my Beryl acting funny with my movie players, I think it's from my recent settings....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screen-Berylsettings.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-53.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-1-5.png[/IMG]

I have it configured in a strange way, so that might be the problem with my movie players. I have my settings this way so my cube isn't a cube at all. When I use my "ctrl + alt + arrow", it instantly is on the next workspace with no cube effect at all. It's very fast. And I can just touch the edges with the mouse to rotate super fast to the next workspace, or I can move my mouse to the lower corners to move to the next workspace with the current opened app. Then if I mouse up to the right, I get the a choice of all apps on all 4 workspaces, or directly up gives me all the apps from one workspace. 

And if I feel like looking at my cube, I just ctrl + alt + click and move it manually to view my skydome and cube caps.

---

### Post by kerry_s on 2007-05-17
Maybe try starting a new thread and see if others are having funny problems with the players and beryl.

MOZ_DISABLE_PANGO="1" is not for fonts it's for firefox, the current firefox is built with cairo which is better speed wise, so instead of letting it choose which to use, it makes it use the faster 1.

"alias net-pf-10 off" is to disable ipv6 which is said to slow down the web browser, ipv6 is used on very few sites. disabling saves the browser from having to check what it should use as all sites will work with ipv4.

I condensed the explaination from what i've read.

---

### Post by crimesaucer on 2007-05-17
> **kerry_s said:**
> Maybe try starting a new thread and see if others are having funny problems with the players and beryl.

MOZ_DISABLE_PANGO="1" is not for fonts it's for firefox, the current firefox is built with cairo which is better speed wise, so instead of letting it choose which to use, it makes it use the faster 1.

"alias net-pf-10 off" is to disable ipv6 which is said to slow down the web browser, ipv6 is used on very few sites. disabling saves the browser from having to check what it should use as all sites will work with ipv4.

I condensed the explaination from what i've read.

Yeah, I'm not worried about the Beryl/Xine thing. My Beryl is set perfectly for how I like things, (fast). And xine-ui works perfect as long as I don't ctrl + alt + arrow to a different workspace.

I went ahead and configured those other two tips. I had read various views about ipv6, but I guess I should try this out and see if there is a difference on my own. And you cleared my question about Pango in your last post, and also in a different thread. I guess it's more necessary if you need it for a certain language's font.

Thanks for the all the help.

---

### Post by crimesaucer on 2007-05-17
HOLLY ****!!!!! I can not believe how fast my Firefox just got. Site's that usually load a bit slower like Xfce-Look.org just opened in a blink of the eye.

Even clicking on the Xfce-Look.org thumbnails that usually load slow, loaded the full size screenshots instantly.

I also opened deviantART so very fast.

Thanks again. I also recommend all of these settings. They were super easy to do, and really worked nicely.

---

### Post by kerry_s on 2007-05-17
That's great, sounds like you've gotten it were you want it to be.
I just remebered another one for firefox, i read somewere that if you move the cache to another drive or to /tmp it's suppose to help speed. I opted for /tmp as i usually don't have any other drives mounted.

You type about:config into the address bar to get to the settings.
scroll down to> browser.cache.disk.parent_directory
then just put the path to where you want your cache.

---

### Post by crimesaucer on 2007-05-17
I have these set to make my Firefox fast:

```
network.dns.disableIPv6 of the type boolean, set to true
nglayout.initialpaint.delay of the type integer, set it to 10
content.interrupt.parsing of the type boolean, set to true
content.max.tokenizing.time of the type integer, set it to 8
content.notify.backoffcount of the type integer, set it to -1
content.notify.interval of the type integer, set it to 2
content.notify.ontimer of the type boolean, set to true 
```

...I'll check your's out and add them.

---

### Post by kerry_s on 2007-05-18
mine are->

nglayout.compatibility.mode 2
nglayout.initialpaint.delay 0
content.maxtextrun 1000
content.notify.backoffcount 0


I don't use those other ones you have, they screw with responsiveness, makes you wait till the page is done loading before your click has a effect.

---

### Post by crimesaucer on 2007-05-18
Thank you, I'll change mine.

Should I try to fix my Direct memory access? I was reading about that.

---

### Post by kerry_s on 2007-05-18
> **crimesaucer said:**
> 
Should I try to fix my Direct memory access? I was reading about that.


Can you tell me more? I didn't see that problem.

---

### Post by crimesaucer on 2007-05-19
I found this page with all sorts of tips.

---

### Post by crimesaucer on 2007-05-19
> **kerry_s said:**
> mine are->

nglayout.compatibility.mode 2
nglayout.initialpaint.delay 0
content.maxtextrun 1000
content.notify.backoffcount 0


I don't use those other ones you have, they screw with responsiveness, makes you wait till the page is done loading before your click has a effect.

I ended up switching back to the settings on that debian page that I linked you to. My Firefox felt weird, I'm going to try it like this for a few days to compare.

---

### Post by kerry_s on 2007-05-19
> **crimesaucer said:**
> I ended up switching back to the settings on that debian page that I linked you to. My Firefox felt weird, I'm going to try it like this for a few days to compare.

Felt wierd? Loads to fast? :)
It's proably>
nglayout.compatibility.mode 2
and
content.maxtextrun 1000

I have mine set fast.

nglayout.compatibility.mode 2< is quirks-mode, it's like what IE use's to work past web page bugs.-> 
nglayout. compatibility. mode 	Integer 	Force a compatibility mode instead of autodetecting.
0 (default): Use supplied DTD
1: Standards compliance mode
2: Quirks mode
-> [http://en.wikipedia.org/wiki/Quirks_mode](http://en.wikipedia.org/wiki/Quirks_mode)
-> [http://kb.mozillazine.org/Category:Preferences](http://kb.mozillazine.org/Category:Preferences)

content.maxtextrun 1000< is how many words before it starts displaying, default for firefox is 8192-> [http://kb.mozillazine.org/Content.maxtextrun](http://kb.mozillazine.org/Content.maxtextrun)


Where's that link to the debian page your looking at?

---

### Post by crimesaucer on 2007-05-19
Thanks for the info, I'll read up on it, and try some other values.

---

