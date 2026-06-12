---
title: "Running Tor with 12.10"
date: 2012-10-21
forum: General Help
---

### Post by thatoneguywiththeface on 2012-10-21
Okay, so i'm adjusting to the learning curve of Ubuntu, but It seems that there's a common problem that new users seem to experience with running/installing TOR.

Alot of people seem to recieve the error message "Vidalia exited abnormally.  Exit code:127" when trying to run start-tor-browser from the bundle.  Sadly, i'm one of those people.  I've tried deleting every tor related file and re-downloading the bundle several times, and after that didn't work, i figured i'd turn to Terminal.

I've tried using the PPA provided by this website:
[http://www.upubuntu.com/2012/10/install-tor-browser-bundle-v2239-1-from.html](http://www.upubuntu.com/2012/10/install-tor-browser-bundle-v2239-1-from.html)

but the thing is this website has 2 other PPA's as well claiming to work.

[http://www.upubuntu.com/2012/10/how-to-configure-your-computer-to-use.html](http://www.upubuntu.com/2012/10/how-to-configure-your-computer-to-use.html)

[http://www.upubuntu.com/2012/08/install-tor-browser-bundle-from-ppa-on.html](http://www.upubuntu.com/2012/08/install-tor-browser-bundle-from-ppa-on.html)

They don't.


Can someone please help?

---

### Post by speme on 2012-10-30
I got the other notice:> Vidalia was unable to start Tor. Check your settings to ensure the correct name and location of your Tor executable is specified.

I just install vidalia with command "apt-get install vidalia".

In the command line. I type"vidalia" and got the message

> (<unknown>:2813): IBUS-WARNING **: Unable to load /var/lib/dbus/machine-id: Failed to open file '/var/lib/dbus/machine-id': Permission denied

(<unknown>:2813): GVFS-RemoteVolumeMonitor-WARNING **: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': Permission denied"

I has been join the "debian-tor" group.

---

### Post by zombifier25 on 2012-10-30
The error usually happens when Tor is already running, and Vidalia either needs to start Tor by itself under your account, or be given permission to control the existing Tor. Run this command to check
```
ps ax | grep tor
```
Check the output and see if there is "tor" (and just "tor").

Try purging everything related to Tor and manually download the browser bundle from [Tor Project's page](https://www.torproject.org/), run it and see if it works.

---

### Post by jimmac49 on 2012-10-30
First of all Google TOR, then choose the one that says Anonymity Online, the choose **Tor Browser**, select your architecture ie, 32 or 64, down load then extract to wherever you have downloaded it to, then RUN, you do not install TOR you run it, thats all there is to it.

I am running Ubuntu 12.10 on a 16Gb flash drive and it works for me.

Luck

---

### Post by MasterNetra on 2012-11-06
> **jimmac49 said:**
> First of all Google TOR, then choose the one that says Anonymity Online, the choose **Tor Browser**, select your architecture ie, 32 or 64, down load then extract to wherever you have downloaded it to, then RUN, you do not install TOR you run it, thats all there is to it.

I am running Ubuntu 12.10 on a 16Gb flash drive and it works for me.

Luck

Good thought, trying to run vidalia and keep getting

"Vidalia was unable to save your Advanced settings.
ControlSocket path doesn't exist."

(And surely enough the Control Sokcet file isn't there, a fail from the installer?)

Its looking like install is more hassle then its worth I guess.

---

### Post by zombifier25 on 2012-11-07
You are running what Vidalia? The installed one or the one started by the start_tor_browser.sh (may not be exact name) script found in the bundle?

---

