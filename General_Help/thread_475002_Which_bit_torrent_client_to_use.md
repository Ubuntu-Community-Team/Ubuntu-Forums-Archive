---
title: "Which bit torrent client to use?"
date: 2007-06-15
forum: General Help
---

### Post by crthomas on 2007-06-15
I have used Azureus for a long time, and was happy with it until today.  I have tried using the webui html plugin, but couldn't get it to work.  For a long time, I was using VNC to control it, but I decided to play around with php today, so I created a php script to parse the Azureus_Stats.xml file.  Now that I have that working, I want to start/stop/remove torrents from the same script.  The problem is that I can't remember the name of the plugin that will let me control azureus from the command line.

That lead me to the idea of using a command line based one, but I have a somewhat intricate setup, and I don't know which ones will support all that I want it to do.

Right now, I have Azureus set up to monitor a directory and automatically download new torrents that are added to the directory.  Then, when it is finished, it moves it to a new place.  Finally, I want it to output an xml stat file, at least somewhat similar to the one Azureus does.

So, all that being said...does anyone know the name of the extension that will let me control azureus from the command line?  If not, which program will let me do everything I am already doing with azureus, and can control from the command line?

---

### Post by wconstantine on 2007-06-15
rTorrent is the best cli based torrent client in my opinion. You can ssh to it instead if you want to use a similar feature as a web ui.

It supports most of the features you talked about. Although I don't think it has the feature to move finished downloads to a specific directory yet. It'll come I'm sure, or it's just me whom has missed it. Lemme know if you prove me wrong.

Here's an example of a rTorrent config:
[http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest](http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest)

Chill out.

---

### Post by crthomas on 2007-06-29
I don't know if the post was deleted, but I got an automated email saying there was an update to the forums.  The email contained the post, and there was a link to a list.  I don't have the email anymore, so I can't put the link back up, but there was a great suggestion on the list.  It is called TorrentFlux.  It is a php/mysql front end for bittornado (I think).  It doesn't have an option to move files upon completion of download, but it does damn near everything else.

---

### Post by MCSE_Crossover on 2007-06-29
By far the best two are "ktorrent" for KDE and "Deluge" for Gnome. Check 'em out! Azureus is too clunky with java.

---

### Post by MCSE_Crossover on 2007-06-29
Oh...sorry. Should have read better. Didn't realize you were looking for strong command line support. But, if you are looking for GUI apps, check the two I mentioned! :)

---

### Post by theonlyalterego on 2007-06-29
rtorrent is awesome, I just started using it over SSH and was pointed to this HOW-TO:
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)
That's helps a lot, with a brief overview and a lot of details.

Edit: also checkout using rtorrent and screen together to keep it running in the background

---

