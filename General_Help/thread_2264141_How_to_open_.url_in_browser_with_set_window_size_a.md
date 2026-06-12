---
title: "How to open .url in browser with set window size and no menu?"
date: 2015-02-05
forum: General Help
---

### Post by frogthroat on 2015-02-05
**Background, long version:** I have Kodi (ex-xbmc) running on my bedroom computer (OS irrelevant for this). I normally use an Android app to control it (also irrelevant for this), but sometimes I have something playing on the background while I work with my laptop. Laptop has Ubuntu 14.04.1. If I want to control the Kodi via the Ubuntu laptop I can go to [http://192.168.xxx.xxx:8080](http://192.168.xxx.xxx:8080) (the IP of the Kodi device) and get a nice remote control. Now, what I would like to do is create a desktop launcher that opens a browser (either Chrome or Firefox, doesn't matter) but it needs to:
1. Not have menus, scrollbars, or URL bar.
2. Open as certain window size. I estimate that it is something like 600x400px and the whole remote fits nicely inside. No window resize.
3. Not affect other instances of the browser, so if I open the browser normally it will be the normal size. I think this is simply done with users. Anyway, only the remote should open in certain window size from the desktop shortcut and others instances of the browser should not be affected. If that makes any sense.

I don't think Kiosk mode would be the correct one. I just want it to float there, extra, but tight size so I can continue to work on my laptop but when changing a TV show I don't need to get my Android device, but can simply switch to the new window. As a workaround I have it in a tab, but I don't like it. I tried to check man for Chrome and Firefox and search this, but could not find anything relevant. Also tried to search the net. Perhaps I just didn't use correct search terms.

**Short version:**
Ubuntu 14.04.1, desktop shortcut required.
Open local IP on browser, Chrome or Firefox.
Control the browser window size, no menus, no address bar, no resize.
Other instances of the browser should not be affected.

If there would be a command line options for either Chrome or Firefox how to open it like that it would be enough. But I just can't see any options like that.

---

### Post by dragonfly41 on 2015-02-05
I've found that Quickly (in Ubuntu Software Centre) is very easy to launch a popup as you describe.

For your app the command would be

quickly create ubuntu-html-app <appname>

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

Here is a useful tutorial

[https://www.youtube.com/watch?v=sO8hiPreNBg](https://www.youtube.com/watch?v=sO8hiPreNBg)

---

### Post by frogthroat on 2015-02-05
Wow! Just quickly checked the wiki (no pun intended), and it looks like even better solution than I was thinking. Thanks. Have to try it out tomorrow. (Late now, sleep needed.)

---

### Post by dragonfly41 on 2015-02-06
Just adding a few notes from my own notes ..

You may need to download additional templates from here ...
[https://launchpad.net/~apandada1/+archive/ubuntu/quickly-community-templates/+sourcepub/4278723/+listing-archive-extra](https://launchpad.net/~apandada1/+archive/ubuntu/quickly-community-templates/+sourcepub/4278723/+listing-archive-extra)

For HTML5 in a browser app (such as you describe) you will need ...

quickly-ubuntu-html-app-template

You might find some templates in Ubuntu Software Centre .. use Synaptic Package Manager to search "quickly"

e.g. sudo apt-get install  quickly-ubuntu-html-app-template

Then you just create an app using the default template and adapt it for your own needs

...

HTML5 tutorial
[http://wolfvollprecht.de/blog/tutorial-creating-an-ubuntu-application-with-html/](http://wolfvollprecht.de/blog/tutorial-creating-an-ubuntu-application-with-html/)

---

### Post by frogthroat on 2015-02-06
That html template will be most useful. I see there will be a learning curve for the application and it is a bit more than I was planning on doing, but I have no other project going at the moment so why not start reading about this. Thank you for your help. It will be more complicated and way more to read than I was originally planning on investing in this, but hopefully worth it. (Learning is never bad.) Wish me luck.

Thank you for your help.

---

