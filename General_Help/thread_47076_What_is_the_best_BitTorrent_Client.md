---
title: "What is the best BitTorrent Client?"
date: 2005-07-07
forum: General Help
---

### Post by JumpyLINUX on 2005-07-07
What do you think is the best BitTorrent Client for (K)ubuntu?
Do you have a screenshot of it?

And could you give me installation instructions because I am new to Linux.

---

### Post by tnilsson on 2005-07-07
[QUOTE=JumpyLINUX]What do you think is the best BitTorrent Client for (K)ubuntu?
Do you have a screenshot of it?

And could you give me installation instructions because I am new to Linux.[/QUOTE]
 One of the most user friendly Bittorrent clients is Azureus. I have used for a couple of years.
I use it when I share Ubuntu distributions.

[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

---

### Post by JumpyLINUX on 2005-07-07
Does anyone else have a favorite?

---

### Post by lothar_m on 2005-07-07
I generally use the original bittorrent client because i prefer using the cli. it&#347; much more flexible and allows much more control.

If you really need the gui the azureus is a  fine alternative.

---

### Post by brian g on 2005-07-07
[QUOTE=lothar_m]I generally use the original bittorrent client because i prefer using the cli. it&#347; much more flexible and allows much more control.[/QUOTE]i've had no luck installing bittorrent-4.1.2.linux_i686-2_all.deb and getting it to work.

any idea what i might be doing wrong?

---

### Post by bored2k on 2005-07-07
[QUOTE=brian g]i've had no luck installing bittorrent-4.1.2.linux_i686-2_all.deb and getting it to work.

any idea what i might be doing wrong?[/QUOTE]
 Download teh source package. Extract, then double click or run btdownloadgui.py

---

### Post by brian g on 2005-07-07
[QUOTE=bored2k]Download teh source package. Extract, then double click or run btdownloadgui.py[/QUOTE]it asks me if i want to edit, run in terminal, or just Run.
I clicked RUN and it dosen't do anything else after that.

---

### Post by bored2k on 2005-07-07
[QUOTE=brian g]it asks me if i want to edit, run in terminal, or just Run.
I clicked RUN and it dosen't do anything else after that.[/QUOTE]
 In a terminal type python btdownloadgui.py
BTW, it SHOULD load when you click run. I usually drag the file to the panel so it creates a launcher.

---

### Post by Lowe on 2005-07-07
Double clicking and selecting run, works for me. check the permissons on the file, if there wrong a quick chmod +x will do wonders. ;)

Quick note: Stay away from azureus, for some reason it kills firefox, i reported the bug and they told me it was a windows problem, yet im using linux, funny eh? What i mean by killing firefox is, if you have azureus running webpages seem to refuse to load, i have to keep clicking about 20 times before it finally loads the webpags. It is a bug, i know for a fact it's not a problem on my side, it happens on every computer and distro i've tried.

They refuse to fix it, because it's a windows problem with max connections, yet i don't even have windows installed on any of my computers, i even told them this and i was ignored and for some reason i can't find my bug ticket anywhere. So screw them.

---

### Post by brian g on 2005-07-07
[QUOTE=bored2k]In a terminal type python btdownloadgui.py
BTW, it SHOULD load when you click run. I usually drag the file to the panel so it creates a launcher.[/QUOTE]
$ python btdownloadgui.py
python: can't open file 'btdownloadgui.py': [Errno 2] No such file or directory

even after cd to /usr/bin where btdownloadgui.py is> check the permissons on the file,-rwxr-xr-x

---

### Post by NeoSNightmarE on 2005-07-07
I would say that my favorite one is Azureus. However, I've been using the default one that comes with Ubuntu....the Gnome BT program because it's pretty simple to use and I've been doing a million things at once. 

And good luck with getting that .deb to work. They covered everything I can think of so I can't add anything to that.

---

### Post by bored2k on 2005-07-07
usr bin ? Just extract the file and double click on it (SOURCE pkg)

---

### Post by brian g on 2005-07-07
[QUOTE=bored2k]usr bin ? Just extract the file and double click on it (SOURCE pkg)[/QUOTE]

..

[QUOTE=brian g]it asks me if i want to edit, run in terminal, or just Run.
I clicked RUN and it dosen't do anything else after that.[/QUOTE]

---

### Post by lothar_m on 2005-07-07
[QUOTE=brian g]i've had no luck installing bittorrent-4.1.2.linux_i686-2_all.deb and getting it to work.

any idea what i might be doing wrong?[/QUOTE]



Hi brian

this is the command i use

```

btdownloadheadless.py --save_in /directory_where_the_downloaded_file_should_be_savd /path_of_torrent_file/Name_of_torrent_file.torrent

```

this command will begin the client in background. It will not provide with information about the download.

However, if you want to see the stats for the download just use btdownload.py instead of btdownloadheadless.py in the above example.

hope this helps.

---

### Post by rwabel on 2005-07-07
opera has now bittorrent integrated. very nice!

---

### Post by MechR on 2005-07-09
[QUOTE=Lowe]Quick note: Stay away from azureus, for some reason it kills firefox, i reported the bug and they told me it was a windows problem, yet im using linux, funny eh? What i mean by killing firefox is, if you have azureus running webpages seem to refuse to load, i have to keep clicking about 20 times before it finally loads the webpags. It is a bug, i know for a fact it's not a problem on my side, it happens on every computer and distro i've tried.

They refuse to fix it, because it's a windows problem with max connections, yet i don't even have windows installed on any of my computers, i even told them this and i was ignored and for some reason i can't find my bug ticket anywhere. So screw them.[/QUOTE]Do you limit your upload speed?  When I let my BT client max out without limit, it starts interfering with my browsing.

---

### Post by bored2k on 2005-07-09
[QUOTE=MechR]Do you limit your upload speed?  When I let my BT client max out without limit, it starts interfering with my browsing.[/QUOTE]
 Indeed. Everyone knows your UL limit should not be higher than 85% of your real UL capabilities. It's on azureus website, bt official's, btornado's, it's everywhere, so don't blame the most  advanced BT client this side of Mars (/msg to the original poster, Lowe).

---

