---
title: "Reinstalled Firefox but now get a missing profile message."
date: 2022-10-12
forum: General Help
---

### Post by Nosphky on 2022-10-12
I made a fresh UbuntuStudio installation in September - moving from XFCE to KDE Plasma. All worked fine and I got things on the desktop to my liking but then suddenly this morning, my desktop wouldn't boot. I remember yesterday I had a load of updates including new low-latency kernel/headers etc and I was surprised that there wasn't any invitation to reboot after the updates. I don't know whether the failure to boot today was linked with those updates but I thought the easiest recovery was just to boot off the live usb stick and reinstall.

The reinstall went well and I started on getting things back to 'my normal' but in so doing, I accidently deleted Firefox. I reinstalled it using the Muon Package manager (listed as a a transitional package to firefox snap) but now when I try to run Firefox, it just puts up an error message "Your Firefox profile cannot be loaded. It may be missing or inaccessible." Then clicking the ok button just makes it quit.

How can I reconnect Firefox with my profile or just get it to make a new profile?  Or is there a better way of installing Firefox as a snap? Or even a suggestion how to install another browser without having a working browser?

---

### Post by TheFu on 2022-10-12
There are lots of web browsers. None of them need a browser to be installed, just a working internet connection.

I use different browsers for different needs, configured in different ways, based on the risks.

In 22.04, firefox and chromium browsers as provided by Canonical are deployed as snap packages.  This has some pros and a bunch of negatives.  I'll leave it to you to go find and read the 20 threads in these forums which go in depth about snap package issues and why power users generally dislike them.  Reading through the issues will probably find some that apply to you along with the work-arounds.  Sadly, the Snap development has decided NOT to fix many issues, because it is working as they think it should, though on any other software, it would be SEV-1 critical bug when the application crashes without a clear reason displayed to the user.

There are ways to install firefox outside the default snap package. Other websites have written articles on doing just that, which you can find.
In 20.04, the chromium-browser was converted to a snap package.  Because it wasn't the default, few people noticed or complained.  I noticed, since I use chromium as my "danger-close" browser inside a firejail with a profile that allows no access to any local storage. I'm not able to use the snap version since then, but had to figure out ways to use it differently which aren't non-expert friendly. Sorry.

There is the "Brave" browser and lynx and dillo as well, but those are stripped down and useful for stripped down websites only. Neither support javascript of any sort, which is great for security. Web developers hate when people visit their websites and don't have javascript enabled.  Without javascript, most of their tracking efforts fail.

I've been avoiding 22.04 for a number of reasons. More mandated snap packages is 1, but not the only.  I may end up changing distros due to the mandated snap packages.  Non-Ubuntu dristros don't require snaps be used.  Just sayin'.

Oh, if you've been using 'sudo' with GUI programs over the years, it is possible that the settings directories have the wrong owner that would remain if you don't do a full-wipe install and format the location that /home uses.  A fix for that specific issue that will do NO harm at all is:
```
sudo chown -R $USER $HOME
```
Copy that exact line and paste it into a terminal.  Logout and login again (shouldn't need to reboot).  It might fix things, but I'm not confident it will.  It shouldn't harm anything, regardless.

---

### Post by col48 on 2022-10-12
Something here should help, although I think this predates the era of snap.

[https://support.mozilla.org/en-US/kb/how-run-firefox-when-profile-missing-inaccessible]("https://support.mozilla.org/en-US/kb/how-run-firefox-when-profile-missing-inaccessible")

---

### Post by Nosphky on 2022-10-12
Thanks for the responses. I think I'm with you 'The Fu' on snap.  And 'col48' the article you referenced provided me with a clue. I used 'firefox -P' at the command line to open the profile manager and create a new profile. That process showed me where the profiles live under snap:  ~/snap/firefox/common/.mozilla/firefox/ .  

I now have Firefox working via the snap and now I'll use it the way I did when I made my fresh installation of UbuntuStudio 22.04 last month. That is to use the snap version to download and install Chrome (which I use just for some specialised extensions), then to delete the Firefox snap version and use Chrome to download Firefox from Mozilla - picking up my old profile from Ubuntustudio 20.04 and earlier. That worked fine until my machine failed to boot this morning.

---

### Post by Frogs Hair on 2022-10-12
I notice your thread is marked solved and if not these commands will the extended support release of Firefox. It is not the latest, but fully functional and no snap package. If solved please post your solution so others may benefit.  
 
```
sudo add-apt-repository ppa:mozillateam/ppa
```
```
sudo apt update
```
```
sudo apt install firefox-esr
```

to remove the Firefox snap:
```
sudo snap remove firefox
```

---

### Post by TheFu on 2022-10-12
> **Nosphky said:**
> Thanks for the responses. I think I'm with you 'The Fu' on snap.  And 'col48' the article you referenced provided me with a clue. I used 'firefox -P' at the command line to open the profile manager and create a new profile. That process showed me where the profiles live under snap:  ~/snap/firefox/common/.mozilla/firefox/ .  

I now have Firefox working via the snap and now I'll use it the way I did when I made my fresh installation of UbuntuStudio 22.04 last month. That is to use the snap version to download and install Chrome (which I use just for some specialised extensions), then to delete the Firefox snap version and use Chrome to download Firefox from Mozilla - picking up my old profile from Ubuntustudio 20.04 and earlier. That worked fine until my machine failed to boot this morning.

This sounds like an excellent plan.  I'll probably NOT use Chrome (installing tracking software from the largest internet tracking company in the world doesn't fit my needs), but with De-google'd chromium and ESR firefox when/if move to 22.04 for my daily use desktop, does need some real consideration.  I still have some 18.04 servers to move to 20.04, so those have priority for now.  I do a leap-frog upgrade process between 2 physical systems and I'm still having the newest 20.04 system settling down. Still need to get 1 more nice-to-have thing working on it before I can move the other physical system up. I have lots of moving parts here with lots of servers on different physical subnets connected to different physical NICs getting passed through to VMs.

Anyway, I like your plan. I'd been avoiding the upgrade because I didn't have a good plan - actually was planning to have an 18.04 container running older versions of firefox and chrome as my fallback plan. Now I know I won't need this. Thanks!

---

### Post by kurt18947 on 2022-10-12
I did an in-place upgrade from 20.04 to 22.04. I don't usually do that but figured I'd live dangerously. I could re-install with little difficulty. Every thing went well and I did get a warning about Firefox becoming a snap app. That went well except the cursor became a shape I'd never seen before. I couldn't find a solution so removed snap firefox then installed flatpak Firefox. I had previously installed LibreOffice and Zoom as flatpaks with no issues I was aware of. Libreoffice snap wouldn't open files off USB flash drives. Libreoffice flatpak had no limitations and the flatpaks seem to update as expected. It's nice that the various packaging schemes appear to coexist peacefully.

---

