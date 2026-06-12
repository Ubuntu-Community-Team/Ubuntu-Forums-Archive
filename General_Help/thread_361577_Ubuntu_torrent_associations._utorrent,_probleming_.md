---
title: "Ubuntu torrent associations. utorrent, probleming opening torrents."
date: 2007-02-14
forum: General Help
---

### Post by jseiser on 2007-02-14
i have utorrent installed, wine running it, my ports forwarded on my router, and when i go to download the torrent file (one, it says its saving to the desktop, i cant figure out how to change that, but the file never actually shows up on the desktop.)  when i hit open from the download manager, or sometimes it just tries to open automatically and says /tmp/name of torrent.torrent could not be opened because the associated file application does not exist. change the association in your preferences.  i tried ststem/preferences/preferred application but that only gives me the option to change the terminal, and browser.  I want to be able to download the torrent and have utorrent open it automaticly.  If this isnt possible i would atleast be able to download the torrent file to a folder somewhere and then just open it from my computer with utorrent.

Im on ubuntu 6.10, installed utorrent from the guides on here.  any help would be appreciated.

---

### Post by Andy_D on 2007-02-14
You can change the program a filetype opens with by right clicking on a file of that type and clicking properties (you will need a .torrent file downloaded to do this, advice on this given later). On the screen that pops up there is a tab labeled open with. On this tab you can select (or most likely add and then select) the application you wish to open that type of file with by default.

Your downloading issues are also fairly simple to resolve, I assume you use firefox? To change the default download location you go to edit > preferences then on the main tab you are able to select the directory to download to by default or you have the option to choose each time. I believe the reason you are not seeing the torrents you download on your desktop is that you are actually selecting the open option rather than save in the firefox download dialog, as when opening a file firefox saves a temporary copy to the /temp directory just as you mentioned. As you do not have an application, in this case utorrent, associated with .torrent files firefox will not be able to open the file.

Changing your file association for .torrent files and making sure you select save rather than open will enable you to successfully download and use .torrent files...assuming utorrent works of course ;) 

Good luck.

---

### Post by jseiser on 2007-02-14
ah thanks for a reply!  I actually got utorrent to open the torrents from the tmp directory and work (well works once, when i minimize utorrent it wont mazimize fully, but it continues to work)  The site im on is a private site and the link to the torrent files are seen as something.php so i cant just save the link to my desktop, but I think i pretty much have this problem solved.  now if utorrent would actually stay working :)

---

