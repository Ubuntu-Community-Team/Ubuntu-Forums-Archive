---
title: "Blocking ads in apps"
date: 2024-05-07
forum: General Help
---

### Post by schwim-dandy on 2024-05-07
Hi there everyone,

On my windows machine, I use Adguard to route Spotify traffic through which works to block ads.  I can't, however, seem to find a similar application that works the same for my linux installs.  Could someone point out what I could use to block ad traffic in non-browsers on the OS?

Thanks for your time!

---

### Post by #&amp;thj^% on 2024-05-07
For spotify: [https://github.com/Nuzair46/SpotX-Linux](https://github.com/Nuzair46/SpotX-Linux)

I use a VPN that handles the rest.

---

### Post by schwim-dandy on 2024-05-07
Thanks very much for that, unfortunately it results in a completely blank UI in Spotify after install (.deb version of Spotify, hiding podcasts enabled).  Running the uninstall did not restore the application so removal of Spotify was necessary.

Seems to be a current issue.  Perhaps Spotify application has changed something in the last year after the last X update.

[https://github.com/Nuzair46/SpotX-Linux/issues/49](https://github.com/Nuzair46/SpotX-Linux/issues/49)

---

### Post by #&amp;thj^% on 2024-05-07
I'm using a Flatpak version for spotify, with no issues, (See Screenshot)

Also there are some optional arguments that can be used>>Optional Install Arguments:
```

-c Clear app cache -- use if UI-related patches aren't working
-e Experimental features -- enables experimental features
-E Exclude feature -- disables specified feature(s) [currently disabled]
-f Force patch -- forces re-patching if backup detected
-h Hide podcasts, episodes and audiobooks on home screen
-o Old UI -- skips forced 'new UI' patch
-P Path directory -- manually set Spotify directory if not found in PATH
-p Premium subscription setup -- use if premium subscriber
```

Use any combination of flags.
The following example clears app cache, adds experimental features and uses the new UI (if supported):
```

bash <(curl -sSL https://raw.githubusercontent.com/SpotX-CLI/SpotX-Linux/main/install.sh) -cesed
```

---

### Post by schwim-dandy on 2024-05-07
Flatpak can't find the spotify client.

> Error: Error  pulling from repo: While pulling app/com.spotify.Client/x86_64/stable  from remote flathub: Opening content object  2d60843887c1ead209184c44b63cc9fa530d84ae7256eacd5f653ff5b6eb27e6:  Opening content object  2d60843887c1ead209184c44b63cc9fa530d84ae7256eacd5f653ff5b6eb27e6:  Couldn't find file object  '2d60843887c1ead209184c44b63cc9fa530d84ae7256eacd5f653ff5b6eb27e6'
error:  Failed to install com.spotify.Client: Error pulling from repo: While  pulling app/com.spotify.Client/x86_64/stable from remote flathub:  Opening content object  2d60843887c1ead209184c44b63cc9fa530d84ae7256eacd5f653ff5b6eb27e6:  Opening content object  2d60843887c1ead209184c44b63cc9fa530d84ae7256eacd5f653ff5b6eb27e6:  Couldn't find file object  '2d60843887c1ead209184c44b63cc9fa530d84ae7256eacd5f653ff5b6eb27e6'



Power of linux and all that.  I'll try again later and use the Windows client since it just works in that environment for me.

---

### Post by #&amp;thj^% on 2024-05-07
Hmm is flatpak installed?
```
flatpak list | grep com.spotify.Client
Spotify	com.spotify.Client	1.2.31.1205.g4d59ad7c	stable	flathub	system

```

---

### Post by tennen2 on 2024-05-07
> **schwim-dandy said:**
> Thanks very much for that, unfortunately it results in a completely blank UI in Spotify after install (.deb version of Spotify, hiding podcasts enabled).  Running the uninstall did not restore the application so removal of Spotify was necessary.

Seems to be a current issue.  Perhaps Spotify application has changed something in the last year after the last X update.


Try out the alternative repo listed in the issue. The main contributor moved to that repo to continue work. 

It is shame AdGuard does not make Linux client. AdGuard DNS filtering is alternative maybe.

---

### Post by schwim-dandy on 2024-05-07
Ah that worked fantastic!  Thanks for pointing out the repo!

---

### Post by schwim-dandy on 2024-05-07
I do and waiting a few hours resolved the issue.  Everything I could find about that type of error said just to wait a while for the servers where the app data resides to sort themselves out.

---

### Post by #&amp;thj^% on 2024-05-07
Ahh Good Job! And that's interesting you had to wait.
Any Who Enjoy :)

---

