---
title: "Torrentflux issues"
date: 2007-04-01
forum: General Help
---

### Post by wounded on 2007-04-01
I was trying to set up Torrentflux on my server box but have run into a number of issues (Despite having set it up properly in the past).

First off, I tried to install it manually and that worked great except that I could not get the download path to be writable. I chmodded for hours, it would not work. I was trying to make them download to my second hard drive (That my user has all privileges to) but it kept giving me a red light on the Settings page in torrentflux. Searching the Torrentflux forums leads me to believe that this may have something to do with SELinux.... unfortunately no post over there ever talks about what that is (I have an idea after some googling though), much less how to actually deactivate it.

Then I decided to just install the torrentflux package from the repository. I copied the files from /usr/share/torrentflux to /var/www/flux and then edited the file in /etc/torrentflux with the mysql data... However, now I get "Path Not Valid" in the Settings page (As well as the directory nto writable described above) on the third and fourth settings (The one relating to bittornado..). The path wants a directory named "TF_BitTornado" in the flux folder but it is not there and a "locate TF_BitTornado" reveals nothing.

Any ideas? I don't mind starting over and reinstalling it manually or anything I just want to figure out how to get it to write to my second drive.

Thanks

---

### Post by detectiveinspekta on 2007-04-01
I have my downloads in my home directory /home/myself/torrents/ This puts individual folders for users in here.
I also did a:
```
chmod 777 -R /home/myself/torrents/
``` 
This sets the folder and everything inside it (if anything) to be read/write/execute by anyone.

I installed mine by grabbing the download. Installation was very easy. The TF_BitTornado folder on my machine is in /var/www/fluxtorrent/

---

### Post by detectiveinspekta on 2007-04-01
If you can restart everything (reinstall ubuntu) I'd do it. If you still don't know the innards of mysql then do it.
6.10 notes: When installing 6.10 make sure you select LAMP (I just pressed enter on LAMP, didn't acually install lamp, confusing interface). Download TF from the website and follow the instructions. Take note of your mysql username (normally root) and password.

I had problems with my router not correctly forwarding ports. Still have problems with the torrent going from good speeds to 0KB/s but I suspect its got to do with the connection restarting from which bittornado should be able to handle!

---

### Post by wounded on 2007-04-01
There is nothing wrong with the mysql settings. I copied the TF_BitTornado folder to the right place but I still cannot get it Torrentflux to write to my secondary drive. I changed the download path to a folder in my home directory and it works. I can just mv the files to my second drive after I'm done downloading and seeding but I'd much rather be able to download them directly to it. Any idea why I can't? chmod 777 gives no errors when I try it but the permissions don't change.

---

