---
title: "Flash Plugin Reverts to Old Version [Resolved]"
date: 2007-03-07
forum: General Help
---

### Post by Alev on 2007-03-07
I'm kinda dumbfounded by this.  I installed the Flash 9 plug in using the script you can download from Adobe's site ([http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)).
 It was pretty easy.  The first time I launch Firefox after installing it, it runs with version 9.  When I close the browser and open it again, it switches back to version 7.  I've done the install a few times and same thing happens.  I'm using [http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/) to check what version of the plugin the browser is using.  I'll try to be detailed, so I hope I don't bore you too much.

If I go to about:plugins, there are two entries for Shockwave Flash, both exactly the same except they are for different versions:

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31

As far as I can tell all the script installs is the files flashplayer.xpt and libflashplayer.so.  I looked these up in my system, and I found them in
/usr/lib/firefox/plugins
/usr/lib/mozilla/plugins

This seems normal to me.  I also found them in /var/cache/flashplugin-nonfree/
flashplayer.xpt in the two above folders are links that point to a copy in /var/cache/flashplugin-nonfree/
I tried changing manually the two files in this folder for the two updated ones, but that didn't seem to do anything.

The installer updated the libflashplayer.so in /usr/lib/firefox/plugins (I checked the Date Modified times), and in /usr/lib/mozilla/plugins there's a link that points to it.

So that's it.  I imagine this'll end up being something super simple that I didn't realize.  Any suggestions appreciated.

---

### Post by aysiu on 2007-03-07
Instead of using the script, can you try this? The first two steps remove all your old Flash player installations, just in case.
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Redeyes_Gambit on 2007-03-07
Have you checked your home folder? I had this EXACT same issue and it took me forever to find the answer. Turns out there was a hidden folder in my home directory that had an old firefox plugin directory/version 7 flash plugin.

---

### Post by Alev on 2007-03-08
Thanks Redeyes_Gambit, that solved it.
By the way aysiu, I think that site recommends pretty much what I had done, except I didn't think to get rid of the old flash first.

---

### Post by Redeyes_Gambit on 2007-03-08
No problem :) . Trust me, that was quite the puzzle to me for quite some time. Glad I could help. :)

---

### Post by RIchard James13 on 2007-12-14
Hi I was having trouble with Firefox always loading up flash 7. I would install 9 and it would work for one session and then when I restarted Firefox it would be using the 7 version.

/home/richard/.mozilla/firefox/pluginreg.dat

refers to both
/usr/lib/flashplugin-nonfree/libflashplayer.so
and
/home/richard/.mozilla/plugins/libflashplayer.so

So I had a look at the second one and it was the 7 plugin. So every time I quit Firefox it was taking my local flash7 over the global flash9. 

Deleting the
/home/richard/.mozilla/plugins/libflashplayer.so
file got rid of my problems

Now I can play more advanced pointless flash games :)

---

### Post by tomjennings on 2007-12-22
I had all of the problems mentioned above, on three systems -- two of which were complete wipes/reinstalls of 7.10. And I know it's not me -- I just purchased a laptop from ZAreason, it came with ubuntu 7.10 installed, and flash9 didn't work there either! :-)

I got it to work finally but I'm not happy with it.... see below.

This is on my new laptop, 7.10 just installed...

tomic@ubuntu:~$ uname -a
Linux ubuntu 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux



When installing flashplugin-nonfree, I also get an error not mentioned, after

$ killall firefox-bin
$ apt-get purge flashplugin-nonfree
$ apt-get install flashplugin-nonfree
...
10:44:33 (1.10 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz

Unbelievable!



What finally worked for me was purging everything, including my .mozilla directory. There was also a .macromedia folder in my home, I just rm -r'd that.


find / | egrep flash and deleted every instance.

$ cd ~
$ mv .mozilla was.mozilla
$ sudo apt-get purge flashplugin-nonfree
$ sudo apt-get purge firefox
$ sudo apt-get install firefox

Still couldn't install flashplugin-nonfree; same MD5 error. So I went to a flash9 site, got the "need flash" warning; clicked; downloaded the .tar.gz file from adobe.

In a terminal, untarred it etc. 

$ sudo ./install_flash_plugin   ## or whatever it's called; I deleted it already...

The installer asks the usual questions, and when it prompts for the install path (default provided was /usr/lib/mozilla I think)  NOTHING WORKS. I'm su'd to root, it should be able to write anywhere. So what's it want?

I retried, this time WITHOUT sudo: at the install path question the default was .mozilla/plugins -- hit RETURN and no further complaints.

Ran firefox, went to flash site, IT WORKED. Browsed around. Quit firefox. IT WORKED SECOND TIME.

I then quit firefox, manually moved my old bookmarks file back from the saved was.mozilla, but decided to start with empty history and cookies files, and not restore those. Still got 'em though in case I change my mind.



My conclusion is that mozilla/firefox is a very messy program that does not clean up after itself (old versions, etc) and that the Adobe linux installer is total crap. I hate adobe.

---

