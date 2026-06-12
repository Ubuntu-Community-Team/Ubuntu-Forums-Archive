---
title: "trying to install transmission"
date: 2021-08-15
forum: General Help
---

### Post by jgw on 2021-08-15
I have been trying to install transmission and failing for the most part.  My problem is that i think I have now installed two versions.  One works and one doesn't.  I tried to delete the first and keep the second but that didn't work.  I think its still there but with problems.  When I do a check I get:
[B]   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Sun 2021-08-15 14:12:23 PDT; 31min ago
    Process: 28352 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=1/FAILUR>
   Main PID: 28352 (code=exited, status=1/FAILURE)

Aug 15 14:12:23 movies systemd[1]: Starting Transmission BitTorrent Daemon...
Aug 15 14:12:23 movies transmission-daemon[28352]: [2021-08-15 14:12:23.058] transmission-daemon Error>
Aug 15 14:12:23 movies systemd[1]: transmission-daemon.service: Main process exited, code=exited, stat>
Aug 15 14:12:23 movies systemd[1]: transmission-daemon.service: Failed with result 'exit-code'.
Aug 15 14:12:23 movies systemd[1]: Failed to start Transmission BitTorrent Daemon.
[/B]

I also went to ubuntu software deleted transmission and installed transmission remote.  Not sure I also installed son other gtk transmission stuff in my search.  all in all I think I need to delete the entire bunch (all I can find) and then start over with some directions as to installing transmission which I can watch in my browser.  

Thank you.................

---

### Post by monkeybrain20122 on 2021-08-15
Isn't transmission already installed by default? I remember having to remove it on each new Ubuntu install (I use qbittorrent, which is a lot more featurful)

Here I checked the software store (Ubuntu 20.04) I see two versions of transmission, one is from the apt repo, another a flatpak. There is possibly a third, snap version. I don't know since I have purged all snaps but flatpak would have to be enabled by user, so I assume you have installed both the apt version and the snap.

So remove both of them and then reinstall one version. 
To remove the apt version

```
sudo apt purge  transmission-gtk && sudo autoremove
```

For the snap

```
sudo snap remove transmission
```

---

### Post by jgw on 2021-08-15
Thank you for the reply!

I will make a run at it.  I currently have three transmission folders in my home directory:
transmission
transmission-daemon
transmission-remote-gtk

Each one, for instance, has a json file attached.  I have yet to get any of them to appear in my browser.  Wish me luckl!

---

### Post by monkeybrain20122 on 2021-08-15
Remove all those three folders, they store your settings. Get rid of them to start with a new slate.

---

### Post by jgw on 2021-08-17
I just checked my machine (after I did as you said)  I then went to my computer root and searched my entire computer for "transmission".  there are a LOG of transmissions.  There are literally hundreds of them.  Here are some samples (there are multiples of everything):
file:///etc/rc2.d/S01transmission-daemon
file:///usr/share/transmission
file:///etc/default/transmission-daemon
file:///etc/apt/trusted.gpg.d/transmissionbt-ubuntu-ppa.gpg
file:///usr/share/applications/io.github.TransmissionRemoteGtk.desktop
file:///usr/share/man/man1/transmission-edit.1.gz
file:///usr/share/man/man1/transmission-show.1.gz
file:///usr/share/man/man1/transmission-create.1.gz

My thought is to delete every one of them but thought I should ask somebody who knows first.  I always have thought that the purge command would remove them all - guess not......

Thank you for the reply!

---

### Post by monkeybrain20122 on 2021-08-17
Or you can re-install it and then purge it. Don't do it manually.

---

### Post by jgw on 2021-08-20
I completely removed transmission and transmission-gtk.  I want to install transmission remote.  I tried once and failed.  Its all now removed but I need help on installation for a transmission I can see in my browser and I don't want to use snap.  Is there a link that has instructions and works?  The last one I had installed transmission and transmission-gtk but it wouldn't appear in my browser.

---

### Post by jgw on 2021-08-23
ok, here is what I have done so far.  I removed any and all transmissions.  I then went to ubuntu software.  There were two transmissions, plain transmission and transmission remote.  I installed transmission and then started it up.  It has a bunch of stuff to also put it on to the browser but everything I have tried has failed on that one.  Apparently one is supposed to tell transmission the address to send the browser connection to.  This is odd.  The address, 127.0.0.1:9091, is clearly in settings.json and also in the remote section of transaction settings in the gui.  Anyway, I have 2 Transmission in .config and also transmission_remote_gtk  both have .json files in them.  I am not sure where the remote_gtk came from but its there now.  

When I tell the gui to connect by pressing "open web client" it takes me to my browser (127.0.0.1:9091) and tells me "403: Forbidden".

I also have a transmission.gtk which is running and am not sure but I think I started 'transmission' and that's what started.

There is also stuff about a transmission daemon which doesn't exist and there are indications that I should also install transmission_remote (which I can do from ubuntu software).

I am writing this in the hope that somebody can tell me where to go from here.

Thank you............

---

### Post by monkeybrain20122 on 2021-08-23
Just use a different torrent app. There are many better ones like deluge or qbittorrent. I have no idea what "browser" you are talking about.

---

### Post by ActionParsnip on 2021-08-23
What is the output of
```

apt-cache policy transmission

```
Thanks

---

### Post by monkeybrain20122 on 2021-08-23
Transmission is installed by default for all flavours of *buntu so I have no idea why you have to install it yourself.

---

### Post by ajgreeny on 2021-08-23
I will not get into any arguments about which torrent client is the best to use, though I have used transmission for any torrent downloads I have made, and it always works brilliantly for me.

I am, however, completely baffled as to why you felt you needed to uninstall transmission in the first place, and do not understand your query about watching transmission in your (web?) browser.

I hope you can give us more details about what and why you are trying to do this.

---

### Post by jgw on 2021-08-24
I uninstalled transmission because I cleverly started installing them because I misread something, I think.  When I did that I had three installed and a genuine mess so I completely removed them from my system and started over.  That's when I installed transmission from the ubuntu software.  I then checked on my transmission and was told that transmission-gtk was version 3.something.  So, right now I have both transmission and transmission-gtk installed.  I then went to the transmission gui/preferences and clicked the open web client and got 403: Forbidden  So then I searched on that one which told me I had a problem with rcp settings.  I have changed those several times and failed each time.  Below is what it looks like now:

```
    
    "rpc-authentication-required": false,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-host-whitelist": "",
    "rpc-host-whitelist-enabled": true,
    "rpc-password": "{37e19d2b176c0095e64811e42c43f8006be9a099WmHq22VE",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "",
    "rpc-whitelist": "127.0.0.1:9091",
    "rpc-whitelist-enabled": true,
 
```

and this is where I am stuck

---

### Post by jgw on 2021-08-25
Thanks for the replies!

I was messing with transmission, the one I got from ubuntu software, and got it to run.  Had to change something in settings.json  I would explain but I don't remember what I did (my memory is shot)  The transmission I downloaded was just plain "transmission" and NOT transmission-remote.  Transmission is now on my browser and opening upon boot although not completely and I have to goto the tab and hit return.  I will work on that one too.  My open command, on boot is "tranmission-gtk"  that's it!

If I remember I will post it here.  I do know that it had to do with the 403 error and that I found the answer on the internet.

In the meantime I am gong to mark this one as solved.

---

