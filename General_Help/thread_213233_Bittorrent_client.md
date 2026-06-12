---
title: "Bittorrent client"
date: 2006-07-11
forum: General Help
---

### Post by Unknowndeepness on 2006-07-11
Hello there. Im in the look for a good torrentclient, and i cant find anything good (even though the only ones i found is azureus and ktorrent).

What i want is something that can run by itself, preferly completly without the X-server running. I want to be able to add torrents from a remote computer (mabie put the torrentfiles in a folder (via ftp), or ssh, or something), and then it will download to some folder, and then it will seed automaticly.

You know anything good?

---

### Post by mogelhead on 2006-07-11
I have a server which I use without X. When I download stuff to it with bittorrent i use screen and the official commandline client (from bittorrent.com).

This is how I do it:
[LIST]
[*]Connect to my server with SSH.
[*]Download the torrent file to the server 
```
wget http://server.com/file.torrent
```
[*]Start bittorrent with a new screen session
```
screen -S the_file btdownloadcurses file.torrent
```
[*]Then I detatch the screen session with Ctrl+A+D. Now I can logout from the server.
[/LIST]

Later, when I wanto check the download status:
[LIST][*]Connect to server
[*]List all screen sessions with ```
screen -list
```
[*]Resume the correct session with ```
screen -r the_file
```
[*]If it is finished I press q to quit, otherwise I detatch the session again.[/LIST]

Possible improvements:

This is many steps involved. I think there is a command to start downloading using all bittorrent files in a particular directory (btlaunchmanycurses). Using that and maybe some cron job (scheduler) you might automate this process so that you can upload bittorrent files to your server with ssh or ftp, and then have them start downloading automatically.

---

### Post by Unknowndeepness on 2006-07-11
Ah, thanQ.
But wont this _just_ download, and not seed anything later on?

---

### Post by mogelhead on 2006-07-11
When all the contents of the torrent is downloaded, it will start seeding. It will continue seeding untill you stop it.

---

### Post by Unknowndeepness on 2006-07-11
So ill start a screensession with one screen per torrent, and then i can just like.. rename each screen for each torrent, and just connect to the screen whenever i want to check it?

---

### Post by mogelhead on 2006-07-11
Correct!

---

### Post by Unknowndeepness on 2006-07-11
Since were on it, is it possible to download TO some other folder?

---

### Post by mogelhead on 2006-07-11
I'm not sure, and currently cannot test how it works.

But the man page of bittorrent client says something about a saveas paramter:  "--saveas filename
    store the downloaded file to filename, instead of querying user (gui) or using the filename stored in the torrent info file"

Not sure if the parameter also handles directories.

---

