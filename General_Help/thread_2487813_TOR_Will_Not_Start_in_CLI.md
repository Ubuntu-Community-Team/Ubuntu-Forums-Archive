---
title: "TOR Will Not Start in CLI"
date: 2023-06-15
forum: General Help
---

### Post by shane_faulkinbury2 on 2023-06-15
I installed TOR from the TOR web page and it worked the first night, but today it will not start from the gui nor will it start from the CLI.

So, I reinstalled it using the package I got from the TOR website.  I went to the Download folder, extracted it and the ran it in CLI.  This is what I get.

```
torbrowser-launcherTor Browser Launcher
By Micah Lee, licensed under MIT
version 0.3.3
https://github.com/micahflee/torbrowser-launcher
Creating GnuPG homedir /root/.local/share/torbrowser/gnupg_homedir
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
Downloading Tor Browser for the first time.
Downloading https://aus1.torproject.org/torbrowser/update_3/release/Linux_x86_64-gcc3/x/en-US
Latest version: 12.0.7
Downloading https://dist.torproject.org/torbrowser/12.0.7/tor-browser-linux64-12.0.7_ALL.tar.xz.asc
Downloading https://dist.torproject.org/torbrowser/12.0.7/tor-browser-linux64-12.0.7_ALL.tar.xz
Verifying Signature
Refreshing local keyring...
pub   rsa4096 2014-12-15 [C] [expires: 2025-07-21]
      EF6E286DDA85EA2A4BA7DE684E2C6E8793298290
uid           [ unknown] Tor Browser Developers (signing key) <torbrowser@torproject.org>
sub   rsa4096 2021-09-17 [S] [expires: 2023-09-17]


Extracting tor-browser-linux64-12.0.7_ALL.tar.xz
Running /root/.local/share/torbrowser/tbb/x86_64/tor-browser_ALL/start-tor-browser.desktop
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/torbrowser_launcher/launcher.py", line 442, in success
    self.run_task()
  File "/usr/lib/python3/dist-packages/torbrowser_launcher/launcher.py", line 301, in run_task
    self.run()
  File "/usr/lib/python3/dist-packages/torbrowser_launcher/launcher.py", line 477, in run
    if not self.check_min_version():
  File "/usr/lib/python3/dist-packages/torbrowser_launcher/launcher.py", line 465, in check_min_version
    for line in open(self.common.paths["tbb"]["changelog"], "rb").readlines():
FileNotFoundError: [Errno 2] No such file or directory: '/root/.local/share/torbrowser/tbb/x86_64/tor-browser_ALL/Browser/TorBrowser/Docs/ChangeLog.txt'



```

Please help me fix this.

Oh, this is what I get when started the gui.  The "Installing" stays on for 15 minutes before I cancel.

---

### Post by shane_faulkinbury2 on 2023-06-15
No help?

---

### Post by Rubi1200 on 2023-06-16
Is there a reason you chose to do it this way and not via the official repositories?

```
sudo apt install torbrowser-launcher
```

---

### Post by andrew.46 on 2023-06-16
It may have no bearing on your issue but are you running the installation in a full root environment? Interesting to see the results if you install as an ordinary user with sudo...

---

### Post by shane_faulkinbury2 on 2023-06-16
This morning I'm trying to install it using the 'Tor Browser Launcher Settings' installed from Flatpak.  If that doesn't work again i will try the terminal.

---

### Post by shane_faulkinbury2 on 2023-06-16
No go on either.

```
sudo apt install torbrowser-launcher[sudo] password for shane: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
torbrowser-launcher is already the newest version (0.3.3-6ubuntu1.22.04.1).
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

---

### Post by Rubi1200 on 2023-06-16
Go to menu >> Internet and you should see 2 options: Tor Browser and Tor Browser Settings.

Open Tor Browser Settings and you need to install it for the first time. I suppose leave the mirror as whatever default for your location.

Let me know if it works now.

---

### Post by shane_faulkinbury2 on 2023-06-16
Menu where?  It says installing and it looks like it completes, but the installing icon never stops.  I leave it up for about an hour before cancelling it.

---

### Post by Rubi1200 on 2023-06-16
You can search Tor under applications and should see something like this [https://prnt.sc/fXphw_ohAF3O](https://prnt.sc/fXphw_ohAF3O)

I tested the process and keep running into the same problem. I don't know if this is a repository issue or something else.

Sorry I wasn't able to help more. Hopefully, somebody else might have some ideas.

---

### Post by #&amp;thj^% on 2023-06-16
> **shane_faulkinbury2 said:**
> This morning I'm trying to install it using the 'Tor Browser Launcher Settings' installed from Flatpak.  If that doesn't work again i will try the terminal.

If you still have the Flatpak installed please run and capture the output and paste back to view:
```
flatpak run com.github.micahflee.torbrowser-launcher
```

---

### Post by shane_faulkinbury2 on 2023-06-16
```
flatpak run com.github.micahflee.torbrowser-launchererror: app/com.github.micahflee.torbrowser-launcher/x86_64/master not installed



```

---

### Post by shane_faulkinbury2 on 2023-06-16
Opened Flatpak, looked at installed apps and opened Tor.

---

### Post by #&amp;thj^% on 2023-06-16
If you removed it via, (flatpak remove "torbrowser") then that's the expected result.
So did you remove the flatpak version?
```
 flatpak list
Name                    Application ID                               Version  Branch      Installation
Tor Browser Launcher    com.github.micahflee.torbrowser-launcher     0.3.6    stable      system

```
And just so we are working toghether here please try:
```
 sudo apt install flatpak
flatpak install flathub com.github.micahflee.torbrowser-launcher -y
flatpak run com.github.micahflee.torbrowser-launcher
```
A successful outcome will look just like this:
```
flatpak run com.github.micahflee.torbrowser-launcher
Tor Browser Launcher
By Micah Lee, licensed under MIT
version 0.3.6
https://github.com/micahflee/torbrowser-launcher
Launching Tor Browser.
Running /home/me/.var/app/com.github.micahflee.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/start-tor-browser.desktop
Launching './Browser/start-tor-browser --detach'...

```

---

### Post by shane_faulkinbury2 on 2023-06-16
Cool, it worked.  It installed, I fired it up and got stuck here.  It told me to bridge.  Any ideas?  Oh, I'm on a VPN.

---

### Post by jet-bundle on 2023-06-16
Around a month ago I had a problem installing Tor. It turned out that there was a problem with the [COLOR=#ff0000]common.py[/COLOR] file, which lives in [COLOR=#ff0000]/usr/lib/python3/dist-packages/torbrowser_launcher/[/COLOR] . I found a modified version of the file at [[COLOR=#ff0000]https://github.com/micahflee/torbrowser-launcher/blob/main/torbrowser_launcher/common.py[/COLOR]]("https://github.com/micahflee/torbrowser-launcher/blob/main/torbrowser_launcher/common.py") and using that to replace the existing file fixed my problem. Perhaps that might help with yours?

---

### Post by #&amp;thj^% on 2023-06-16
> **shane_faulkinbury2 said:**
> Cool, it worked.  It installed, I fired it up and got stuck here.  It told me to bridge.  Any ideas?  Oh, I'm on a VPN.
Stop your VPN first get a good start, close Tor, now Stop your VPN, and now relaunch torbrowser.
After that you should be good to go.

---

### Post by shane_faulkinbury2 on 2023-06-16
[h=1][COLOR=#424242][COLOR=#000000]1fallen,  [/COLOR][/COLOR][SIZE=2][COLOR=#424242]I was able to connect and then I turned my VPN on and couldn't go to an url.   Is there anything I can change in TOR settings or should I just split tunnel TOR.   The funny thing is that TOR has always worked with my VPN on earlier distributions.[/COLOR][/SIZE][/h]

---

### Post by #&amp;thj^% on 2023-06-16
I have 3 VPN's all work with torbrowser, what is the VPN provider your using.
I use NordVPN AirVPN CLI only those two are wiregaurd protocols or my homespun VPN.
Also check your firewall to allow torbrowser. And there is thier Forum Area: [https://forum.torproject.net/](https://forum.torproject.net/)
I am curious how it would work with a bridge though, again this shouldn't be necessary.

---

### Post by shane_faulkinbury2 on 2023-06-16
Oldfred, I have no idea what happened, but I went out, came home, fired TOR up and it's working now.  I'll let you know tomorrow if it's still good to go.  It's 9:20 PM here now.

---

### Post by shane_faulkinbury2 on 2023-06-18
Sorry, I got busy.  All is good to go guys and thank you all.

---

