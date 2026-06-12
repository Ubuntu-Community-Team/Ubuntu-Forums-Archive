---
title: "firefox meltdown"
date: 2006-07-02
forum: General Help
---

### Post by anubix on 2006-07-02
ok, so i upgraded ubuntu to 6.06
after which firefox started giving me grief:
flash objects that worked before the upgrade no longer did, plugins weren't installed, etc.
so after trying to re-install the plugins, to no avail, i used apt-get to remove firefox, then reinstall it.  after the reinstall whenever i tried to run firefox, i would get an error "unable to initiate child class" or some such nonsense.
i downloaded a tarbal from getfirefox.com "firefox-1.2.0.4.tar.gz" which i am able to extract a "firefox" directory from, then run the "firefox" script to be able to post this thread.
my question is this:
how can i use apt-get to give me a working firefox, or how can i install this tarbal so that i get icons in the application menu, and back in the tray.

pz

---

### Post by nanotube on 2006-07-02
well, don't know what exactly is the problem with your "default" firefox. have you tried moving your old profile out of the way (should be in ~/.mozilla), and trying to start it again?

if that fails, just leave it installed, but then use the install script from here [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)
to install the latest official mozilla version of firefox. that will put it in and transparently substitude the official mozilla version instead of the ubuntu version, when you use your menu items or shortcuts, etc. then you should be able to run firefox...

---

### Post by anubix on 2006-07-02
for clarity this is the error i'm getting

[IMG]http://i46.photobucket.com/albums/f141/sadie42/Screenshot.png[/IMG]

---

### Post by anubix on 2006-07-02
OK, so i got new firefox in...
BUT i can't get realplayer plugin to work... ideas?
also, there is an ifilm i put on my myspace... [http://www.ifilm.com/ifilmdetail/2685784?htv=12](http://www.ifilm.com/ifilmdetail/2685784?htv=12) now when i try and watch it (using that link) i have to choose "quicktime, windows media player, or realplayer"... realplayer 10 is already in my applications menu, but when i select it for ifilm, i get the "install missing plugins" thing, and when i installed it (again) still the same result.  I embedded this on my myspace, and when i try and watch it there, i get "flashplayer 8 is required to view this" i have flashplayer 7 installed and working.....
how can i make realplayer work?

---

### Post by nanotube on 2006-07-03
[QUOTE=anubix]OK, so i got new firefox in...
BUT i can't get realplayer plugin to work... ideas?
also, there is an ifilm i put on my myspace... [http://www.ifilm.com/ifilmdetail/2685784?htv=12](http://www.ifilm.com/ifilmdetail/2685784?htv=12) now when i try and watch it (using that link) i have to choose "quicktime, windows media player, or realplayer"... realplayer 10 is already in my applications menu, but when i select it for ifilm, i get the "install missing plugins" thing, and when i installed it (again) still the same result.  I embedded this on my myspace, and when i try and watch it there, i get "flashplayer 8 is required to view this" i have flashplayer 7 installed and working.....
how can i make realplayer work?[/QUOTE]
i dont know about realplayer 10, but if you install the mplayer firefox plugin (package mplayer-firefox, or something like that), it will be able to play just about anything, including realplayer stuff. once it is installed, you just have to link the plugin from your ubuntu firefox directory (/usr/lib/firefox/plugins), to your "new" firefox plugins directory in /opt/firefox/plugins
so... try that. :)

---

### Post by anubix on 2006-07-03
ok, first the only package i can find is "mozilla-mplayer" and what the proper syntax to link the directories together?

---

### Post by nanotube on 2006-07-03
[QUOTE=anubix]ok, first the only package i can find is "mozilla-mplayer" and what the proper syntax to link the directories together?[/QUOTE]
mozilla-mplayer sounds like the right package
after you install it, run command
```
sudo ln -s -f /usr/lib/firefox/plugins/* /opt/firefox/plugins/
```
to place links to all the plugins into your new firefox plugins dir.

---

