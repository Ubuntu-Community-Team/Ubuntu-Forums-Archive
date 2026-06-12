---
title: "Dropbox segmentation fault after software upgrade gone bad"
date: 2014-01-09
forum: General Help
---

### Post by bjarte-3 on 2014-01-09
As loose as the title must be, here is the history.

Last week I set up a new machine with 13.10 (x64) to take over from my way too old 1U server also running 13.10 (x86) and had set up everything and transfered all the data and configurations I needed for a full replacement.

After all was completed I remembered I hadn't ran a proper apt-get update && apt-get upgrade since the initial install (via SSH mind you), so I figured I might as well do that and go to bed.

And here's the kicker: I had setup the machine with a static IP, but forgotten to reboot to ensure no DHCP would kick in. So during the upgrade DHCP did kick in or my static IP change got rolled back, in between all the dpkg configure lines causing me to have a dpkg configure state I could not complete (by any way obvious to me since my SSH session had disconnected due to the IP change).

I therefore thought it "smart" to just kill the dpkg session I couldn't complete and run it manually afterwards. And it did complete properly it would seem, but there's just one catch.

When I now try and start my command line based dropbox daemon, it crashes with a segmentation fault (core dumped) error. Dmesg points out that this happens in ld.2.17.so but I've replaced the file with no luck so far.

The strace of ~/dropbox-dist/dropboxd is at [http://rolland.nu/segfault.txt](http://rolland.nu/segfault.txt) if anyone could give me a few pointers on where to start looking other than what I've already tried.

For the time being, my other server acts as the dropbox server with the Dropbox folder mounted via cifs just to make sure everything is backed up at all times. But that's no ideal solution for me.

---

### Post by bjarte-3 on 2014-01-09
I figured I might as well throw in a few new libraries on the server, I could have removed some of them in mistake.


So I installed nautilus and all its fellow packages and that seem to have done the trick. Atleast the dropbox is running on the correct server again now :)

---

