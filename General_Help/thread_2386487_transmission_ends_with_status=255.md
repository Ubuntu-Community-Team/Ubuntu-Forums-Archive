---
title: "transmission ends with status=255"
date: 2018-03-06
forum: General Help
---

### Post by jgw on 2018-03-06
I have just spent a couple of hours trying to figure this out.  There are a lot of postings around on this one and they all seem to have different solutions or none at all.  I gave up and thought I would post this to see what I could find.  Here is what I did:

ran:              sudo apt-get autoremove transmission-daemon transmission-common transmission-cli transmission-gtk  --purge
then ran:      sudo apt-get install transmission-daemon transmission-common transmission-cli transmission-gtk

then I stopped transmission and edited the settings.json file at /var/lib/transmission-daemon/info and /var/lib/transmission-daemon/.config
After that I tried to restart transmission with: sudo service transmission-daemon restart and got:
Job for transmission-daemon.service failed because the control process exited with error code. See "systemctl status transmission-daemon.service" and "journalctl -xe" for details.
greg@movies:~$ sudo service transmission-daemon start
Job for transmission-daemon.service failed because the control process exited with error code. See "systemctl status transmission-daemon.service" and "journalctl -xe" for details.
greg@movies:~$ sudo systemctl status transmission-daemon.service
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2018-03-06 09:34:22 PST; 24s ago
  Process: 11609 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=255)
 Main PID: 11609 (code=exited, status=255)
failed to start

Then I:
greg@movies:~$ sudo systemctl status transmission-daemon.service
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2018-03-06 09:34:22 PST; 24s ago
  Process: 11609 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=255)
 Main PID: 11609 (code=exited, status=255)

Mar 06 09:34:22 movies systemd[1]: Starting Transmission BitTorrent Daemon...
Mar 06 09:34:22 movies transmission-daemon[11609]: [2018-03-06 09:34:22.664 PST] JSON parse failed in /var/lib
Mar 06 09:34:22 movies systemd[1]: transmission-daemon.service: Main process exited, code=exited, status=255/n
Mar 06 09:34:22 movies systemd[1]: Failed to start Transmission BitTorrent Daemon.
Mar 06 09:34:22 movies systemd[1]: transmission-daemon.service: Unit entered failed state.
Mar 06 09:34:22 movies systemd[1]: transmission-daemon.service: Failed with result 'exit-code'.

greg@movies:~$ journalctl -r
-- Logs begin at Sun 2018-03-04 14:08:45 PST, end at Tue 2018-03-06 09:35:38 PST. --
Mar 06 09:35:38 movies mono[14984]: [Error] DownloadedEpisodesImportService: Import failed, path does not exist

I also changed permissions to no avail  (basically put my user name in as group

Thoughts?

---

### Post by #&amp;thj^% on 2018-03-06
I knew we would be revisiting this issue, :)
I have no idea what you have done so far but some great suggestions found here by  talz1979 post #18: [https://ubuntuforums.org/showthread.php?t=2386355&p=13745863#post13745863](https://ubuntuforums.org/showthread.php?t=2386355&p=13745863#post13745863) 
Good Luck ;)
BTW If you have mucked around too much with the settings and configs via terminal or any application as root, you just might need a clean install of your OS. (Don't kill the messenger :( )

---

### Post by jgw on 2018-03-07
Thanks again!
I followed the link you suggested and found the following, followed the directions and, now, everything is running properly (thanks again!!):

 MarcosBL commented 21 hours ago
Just as 2 cents for others looking for help:

Create a file /etc/systemd/system/transmission-daemon.service.d/override.conf with this content:

[Service]
User=
Type=
Type=simple
User=debian-transmission
Group=debian-transmission

Then reload systemd config with systemctl daemon-reload

And finally start the service again with systemctl start transmission-daemon.service

After that transmission 2.93 works perfectly.

---

### Post by #&amp;thj^% on 2018-03-07
That's Great! Woot Woot! :D
Thanks for posting your solution "used". Very Helpful for those running the"** transmission-daemon**".
Cheers!

---

