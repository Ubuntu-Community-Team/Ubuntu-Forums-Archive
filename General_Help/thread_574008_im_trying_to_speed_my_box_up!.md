---
title: "im trying to speed my box up!"
date: 2007-10-12
forum: General Help
---

### Post by ninjaprawn on 2007-10-12
hi,

ive been lazy, and run ubuntu feisty fawn since it came out. But never actually done much in the way of tuning it.

im trying to get rid of tty 5-6. killing them just means they respawn. im guesing i need to comment out lines in a file? anyone know the file?

also, can i remove all tty except 1? with out my system having a heart attack? i have 2 xservers on 1 graphics card, does that use a 2nd tty??

thanks.

---

### Post by thirddeep on 2007-10-12
One have to wonder, exactly how much memory you will save killing ~4 terminals ?

Thd.

---

### Post by atlfalcons866 on 2007-10-12
the file system has a little to do with if your using EXT3. I use jfs and it is about 3 times faster

---

### Post by dabl on 2007-10-12
You may or may not be aware of this -- perhaps it could help you speed things up a bit:

[http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/)

:)

---

### Post by ninjaprawn on 2007-10-12
> **dabl said:**
> You may or may not be aware of this -- perhaps it could help you speed things up a bit:

[http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/)

:)

that was an awsome link! my box is massivly faster after following that!

ive bin using linux for a year now, still havent learnt how to do any of that stuff myself!

Thanks again!

---

### Post by kerry_s on 2007-10-12
> **dabl said:**
> You may or may not be aware of this -- perhaps it could help you speed things up a bit:

[http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/)

:)

good read. i switched to using active swap, it uses swap files and only when needed, then deletes them when there no longer being used. this way i have even more control of swap. the program is called "swapd" (sudo apt-get install swapd). i have 256ram, so i have mine's set to make swap at about 75% used.
my settings.

#/etc/swapd.conf
#apt-get install swapd
memlimit 85660
pause 300
swapsize 128000 
maxswaps 0

---

### Post by kerry_s on 2007-10-12
sorry, here's most of the settings i use, i cut out the debian specific sections.

```

#/boot/grub/menu.lst
vga=791 elevator=deadline 

#/etc/fstab
,noatime


#/etc/sysctl.conf
net/ipv4/icmp_echo_ignore_broadcasts=1
kernel.printk = 4 4 1 7
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1
net.ipv4.tcp_syncookies=1
net.ipv4.ip_forward=1
net/ipv4/icmp_ignore_bogus_error_responses = 1
net/ipv4/conf/all/accept_redirects = 0
net/ipv4/conf/all/send_redirects = 0
net/ipv4/conf/all/accept_source_route = 0
net/ipv4/conf/all/log_martians = 0
net/core/optmem_max = 65536
net/core/rmem_max = 8388608
net/core/rmem_default = 65536
net/core/wmem_max = 8388608
net/core/wmem_default = 65536
net/ipv4/tcp_rmem = 8192 65536 8388608
net/ipv4/tcp_wmem = 4096 65536 8388608
vm.overcommit_memory=1
vm.overcommit_ratio=75
vm.swappiness=0
vm.vfs_cache_pressure=0


#/etc/swapd.conf
#apt-get install swapd
memlimit 85660
pause 300
swapsize 128000 
maxswaps 0


#etc/rc.local
#apt-get install hdparm
hdparm -X68 -d1 -u0 -m16 -c1 -A1 -a1024 /dev/hda &



```

i'm looking into that "vm.vfs_cache_pressure=50" right now. :)

okay after, trying it i'm going with "vm.vfs_cache_pressure=0" for now

---

### Post by oldos2er on 2007-10-12
[http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

---

### Post by ninjaprawn on 2007-10-12
> **oldos2er said:**
> [http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

ta for that 1 aswell! any more?

---

### Post by ninjaprawn on 2007-10-12
somuch faster already! thanks for all that help anyway!

any ideas how to make firefox faster aswell?

thanks again.

---

### Post by jaybombalous on 2007-10-12
> **kerry_s said:**
> sorry, here's most of the settings i use, i cut out the debian specific sections.

```

#/boot/grub/menu.lst
vga=791 elevator=deadline 

#/etc/fstab
,noatime


#/etc/sysctl.conf
net/ipv4/icmp_echo_ignore_broadcasts=1
kernel.printk = 4 4 1 7
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1
net.ipv4.tcp_syncookies=1
net.ipv4.ip_forward=1
net/ipv4/icmp_ignore_bogus_error_responses = 1
net/ipv4/conf/all/accept_redirects = 0
net/ipv4/conf/all/send_redirects = 0
net/ipv4/conf/all/accept_source_route = 0
net/ipv4/conf/all/log_martians = 0
net/core/optmem_max = 65536
net/core/rmem_max = 8388608
net/core/rmem_default = 65536
net/core/wmem_max = 8388608
net/core/wmem_default = 65536
net/ipv4/tcp_rmem = 8192 65536 8388608
net/ipv4/tcp_wmem = 4096 65536 8388608
vm.overcommit_memory=1
vm.overcommit_ratio=75
vm.swappiness=0
vm.vfs_cache_pressure=0


#/etc/swapd.conf
#apt-get install swapd
memlimit 85660
pause 300
swapsize 128000 
maxswaps 0


#etc/rc.local
#apt-get install hdparm
hdparm -X68 -d1 -u0 -m16 -c1 -A1 -a1024 /dev/hda &



```

i'm looking into that "vm.vfs_cache_pressure=50" right now. :)

okay after, trying it i'm going with "vm.vfs_cache_pressure=0" for now


can u explain some of those settings???

---

### Post by kerry_s on 2007-10-12
> **ninjaprawn said:**
> somuch faster already! thanks for all that help anyway!

any ideas how to make firefox faster aswell?

thanks again.

my user.js

```

user_pref("network.http.max-connections", 48);
user_pref("network.http.max-connections-per-server", 32);
user_pref("network.http.max-persistent-connections-per-proxy", 20);
user_pref("network.http.max-persistent-connections-per-server", 16);
user_pref("network.http.pipelining", true);
user_pref("network.http.proxy.pipelining", true);
user_pref("network.http.pipelining.maxrequests", 8);
user_pref("nglayout.initialpaint.delay", 0);
user_pref("network.http.keep-alive.timeout", 30);
user_pref("network.http.request.max-start-delay", 4);
user_pref("network.http.connect.timeout", 30);
user_pref("network.dnsCacheExpiration", 60);
user_pref("network.dnsCacheEntries", 20);
user_pref("network.ftp.idleConnectionTimeout", 60);
user_pref("browser.cache.disk.capacity", 100000);
user_pref("browser.cache.disk_cache_ssl", true);
user_pref("browser.chrome.toolbar_tips", false);
user_pref("mousewheel.horizscroll.withnokey.action", 1);
user_pref("network.dns.disableIPv6", true);
user_pref("browser.link.open_newwindow", 3);


```

---

### Post by kerry_s on 2007-10-12
> **jaybombalous said:**
> can u explain some of those settings???

explain what? there tweaks, the "#" sections is where the go.

---

### Post by ninjaprawn on 2007-10-12
> **kerry_s said:**
> my user.js

```

user_pref("network.http.max-connections", 48);
user_pref("network.http.max-connections-per-server", 32);
user_pref("network.http.max-persistent-connections-per-proxy", 20);
user_pref("network.http.max-persistent-connections-per-server", 16);
user_pref("network.http.pipelining", true);
user_pref("network.http.proxy.pipelining", true);
user_pref("network.http.pipelining.maxrequests", 8);
user_pref("nglayout.initialpaint.delay", 0);
user_pref("network.http.keep-alive.timeout", 30);
user_pref("network.http.request.max-start-delay", 4);
user_pref("network.http.connect.timeout", 30);
user_pref("network.dnsCacheExpiration", 60);
user_pref("network.dnsCacheEntries", 20);
user_pref("network.ftp.idleConnectionTimeout", 60);
user_pref("browser.cache.disk.capacity", 100000);
user_pref("browser.cache.disk_cache_ssl", true);
user_pref("browser.chrome.toolbar_tips", false);
user_pref("mousewheel.horizscroll.withnokey.action", 1);
user_pref("network.dns.disableIPv6", true);
user_pref("browser.link.open_newwindow", 3);


```

sorry for being a complete noob, but what is the user.js, and where do i find it?

---

### Post by kerry_s on 2007-10-12
> **ninjaprawn said:**
> sorry for being a complete noob, but what is the user.js, and where do i find it?

you make it. it go's in your ~/.mozilla/firefox/xxxxxxxx.default/
reference: [http://www.mozilla.org/support/firefox/edit#user](http://www.mozilla.org/support/firefox/edit#user)

then restart firefox and all those settings will be applied. the manual way is using about: config.

i'm going to assume your using gnome.

**gedit ~/.mozilla/firefox/*.default/user.js**

then copy & paste those lines(left click drag to highlight & middle click to paste)

---

### Post by dabl on 2007-10-12
On this page:

[http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

There is a tip for dual core systems, to change the CONCURRENCY= value in etc/init.d/rc from "none" to "shell".  I just proved beyond doubt, through a total of 4 reboot cycles, that on my Core 2 Extreme rig, doing that disables my ethernet connection. And I can't fix it by doing anything with the network settings -- there is a "failure to parse XML back end" error when I try to "apply" the fix.

Isn't that odd?  I think I'm going to e-mail the author of the article and see if I can figure out what's up with that.

---

### Post by ninjaprawn on 2007-10-12
> **kerry_s said:**
> you make it. it go's in your ~/.mozilla/firefox/xxxxxxxx.default/
reference: [http://www.mozilla.org/support/firefox/edit#user](http://www.mozilla.org/support/firefox/edit#user)

then restart firefox and all those settings will be applied. the manual way is using about: config.

i'm going to assume your using gnome.

**gedit ~/.mozilla/firefox/*.default/user.js**

then copy & paste those lines(left click drag to highlight & middle click to paste)

ive found a firefox.js in /etc/firefox/pref

is that the same, or atleast the place i need to put the user.js??

---

### Post by DagMan on 2007-10-12
> **dabl said:**
> On this page:

[http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

There is a tip for dual core systems, to change the CONCURRENCY= value in etc/init.d/rc from "none" to "shell".  I just proved beyond doubt, through a total of 4 reboot cycles, that on my Core 2 Extreme rig, doing that disables my ethernet connection. And I can't fix it by doing anything with the network settings -- there is a "failure to parse XML back end" error when I try to "apply" the fix.

Isn't that odd?  I think I'm going to e-mail the author of the article and see if I can figure out what's up with that.

I had a problem when I enabled concurrent booting where hal was loading before dbus so I just had to put **sleep 3** at the begining of the hal script.  In my case it was that usually one comes up and then the other comes up directly after but with both cores handling processes, you run into situations were each one is handling a boot script at the same time and one may finish before something else that it needs has finished.  I don't know if that helps you or not, but try removing 'splash' from your grub or hit alt-f1 and see what is failing on boot, then edit it in /etc/init.d and tell it sleep for a few seconds before trying to load and maybe it will fix things.

---

### Post by kerry_s on 2007-10-12
> **ninjaprawn said:**
> ive found a firefox.js in /etc/firefox/pref

is that the same, or atleast the place i need to put the user.js??

no, you need to make it.
do this->

**gedit ~/.mozilla/firefox/*.default/user.js**

---

### Post by ninjaprawn on 2007-10-12
i never realised you could actually do that with the '~'!

ta!

---

### Post by kerry_s on 2007-10-12
> **ninjaprawn said:**
> i never realised you could actually do that with the '~'!

ta!

yes, the "~" means your home account. that's why you see it when you open a terminal. it's like a short cut instead of using the full path> /home/you/your-files shorts to ~/

also "*" is very useful, when you don't know what exactly you want. if you look in that file you'll see what i used it in place of> **nautilus ~/.mozilla/firefox**

---

### Post by skipbarker on 2007-10-12
> **dabl said:**
> You may or may not be aware of this -- perhaps it could help you speed things up a bit:

[http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/)

:)

Great Link! Huge difference on my machine.

---

### Post by ninjaprawn on 2007-10-12
thanks, im learning loads today!

1 thing tho, i made that file with the user settings in, and it broke my mouse kinda! so i went very drastic, checked my xorg.conf, reset the backup, no difference, my mouse side buttons were scrolling horizontally instead of browsing back and forward! then i deleted the user.js, still no difference, then i checked the about:config, and there was the culprit! the line;
mousewheel.horizscroll.withnokey.action
had been changed to 2 insted o 1!

couple a tweeks, and away we go!

that ~ is going to save me a lot of time

thanks!

---

### Post by kerry_s on 2007-10-12
> **ninjaprawn said:**
> thanks, im learning loads today!

1 thing tho, i made that file with the user settings in, and it broke my mouse kinda! so i went very drastic, checked my xorg.conf, reset the backup, no difference, my mouse side buttons were scrolling horizontally instead of browsing back and forward! then i deleted the user.js, still no difference, then i checked the about:config, and there was the culprit! the line;
mousewheel.horizscroll.withnokey.action
had been changed to 2 insted o 1!

couple a tweeks, and away we go!

that ~ is going to save me a lot of time

thanks!

that's my bag, i don't like the back & forward so i change it, it screws up my touchpad when i'm moving the mouse and hit the bottom. just remove those 2 lines from the user.js. 
user.js is like a overide to prefs.js so your settings get past there, you have to remove the lines in both places.
the way i have it set is to move the page left &right
SORRY!

---

### Post by ninjaprawn on 2007-10-13
easier than that! i just changed the 2 to a 1! fixed! if only all problems i came up against were that simple!

---

