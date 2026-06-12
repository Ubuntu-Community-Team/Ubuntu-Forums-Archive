---
title: "Magnet links"
date: 2013-05-08
forum: General Help
---

### Post by Bro0kLyNz on 2013-05-08
(Using 13.04)
I uninstalled transmission..
and now I can't get my magnet links to open with Vuze. I've looked around, the only fix I find isn't working for me.

the fix: gconf-editor > desktop/gnome/url-handlers/magnet > vuze/azureus is set to own magnets. Looks like this:
Command: azureus "%s"
enabled; true
terminal; false.

I'm using chromium, but it's the same for firefox. I click on the magnet link and nothing happens. Torrents work fine though.

If you need more information let me know I'll post it. pls help :(

---

### Post by papibe on 2013-05-08
Hi Bro0kLyNz.

The most common situation is that you get a magnet link from a website,  you click it, and you want a bittorrent client to be open. Is that what you are looking for?

If so, it has to do more with the browser itself than with the desktop (Unity, Gnome, etc).

For instance, in Firefox:
```
Edit -> Preferences -> Applications -> Content Type -> magnet
```
If you have a magnet content type, set it to azureus.

Let us know how it goes.
Regards.

---

### Post by Bro0kLyNz on 2013-05-08
There is no "magnet" option under content type in firefox. and there is nothing at all under chromium's handlers. :(

---

### Post by papibe on 2013-05-08
Open this url in Firefox:
```
about:config
```
Right click to create a new Boolean. Name it:
```
network.protocol-handler.expose.magnet
```
set its value to false, and restart Firefox.

Next time you click a magnet link, it should ask you what to do, so you can choose Azures.

Let us know how it goes.
Regards.

---

### Post by Bro0kLyNz on 2013-05-09
This worked for Firefox! Thanks!
I still need to do it on Chromium (I don't use Firefox much) know how? :)


EDIT:
nvm, chromium is crashing. Firefox it is :)

---

### Post by papibe on 2013-05-09
:) Glad it's working for you!

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Regards.

---

### Post by colin.p on 2013-05-09
I have had this issue for years and, frankly, I got tired of trying to get it to work. What I do is right click on the magnet link and copy it, then open it with whatever torrent program I use at the time. Currently, I use Deluge and that is how I open magnet links. Works everytime, no matter what version of linux, whatever browser, and whatever torrent program.

---

### Post by Bro0kLyNz on 2013-05-15
> **colin.p said:**
> I have had this issue for years and, frankly, I got tired of trying to get it to work. What I do is right click on the magnet link and copy it, then open it with whatever torrent program I use at the time. Currently, I use Deluge and that is how I open magnet links. Works everytime, no matter what version of linux, whatever browser, and whatever torrent program.
I'm lazy. One click start ftw :P





*marked as solved.

---

### Post by Mariane on 2014-01-26
It worked for me with Firefox but not with Seamonkey. 
2 pitfalls I fel into:
I right-clicked the Azureus icon to see where Azureus was and I told Firefox to open the magnet with /usr/share/applications/azureus.desktop
Wrong one, I needed to associate magnets with /usr/bin/azureus
I closed the Firefox window before the magnet associated with /usr/bin/azureus had completely downloaded the torrent, and the download failed. 
I started again, and it's now functioning properly. 

Anyone knows why these magnet links? And what they are?

---

### Post by Michael_Ramsey on 2014-05-04
> **Mariane said:**
> It worked for me with Firefox but not with Seamonkey. 
2 pitfalls I fel into:
I right-clicked the Azureus icon to see where Azureus was and I told Firefox to open the magnet with /usr/share/applications/azureus.desktop
Wrong one, I needed to associate magnets with /usr/bin/azureus
I closed the Firefox window before the magnet associated with /usr/bin/azureus had completely downloaded the torrent, and the download failed. 
I started again, and it's now functioning properly. 

Anyone knows why these magnet links? And what they are?

Thank you thank you thank you!!!

I've tried a 100 times to make azureus.desktop to work with 0 success... /usr/bin/azureus worked perfectly.

Thanks again


Edit, magnet links are so that there is no actual file sitting on a server that could possibly get the server owner locked up.

---

