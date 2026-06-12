---
title: "Firefox freezes frequently"
date: 2023-08-18
forum: General Help
---

### Post by satimis on 2023-08-18
Hi all,

Ubuntu 22.04 

Firefox freezes frequently.  It has happened for a week.  I have "uninstall/install/reinstall" it on repo several times, including deleting its old folder.  But problem remains for unknown cause.

I just leave it there withouot running and now I'm only start Google Chrome.

Could any folk shed me some light how to fix the problem?  Thanks in advance.

Regards

---

### Post by VMC on 2023-08-18
Does it freeze or just refresh keeps spinning. does refresh key work? I have a similar issue.

---

### Post by Impavidus on 2023-08-18
Have you tried disabling extensions? I've had a similar issue for the past week (Firefox from the PPA) and it appeared to be related to the NoScript extension.

---

### Post by satimis on 2023-08-18
> **VMC said:**
> Does it freeze or just refresh keeps spinning. does refresh key work? I have a similar issue.
Hi,

OS - Ubuntu 22.04 desktop
RAM - 32G onboard

Problem occurred as follow;

Start PC -> Start Ubuntu -> Start Firefox

Its screen freezes -> after a while turning to a dark screen -> After another while, it turns back to Firefox screen again but still freezing.

I have to hard-reboot the PC

Start Ubuntu again -> Start Firefox

This time Firefox works but it freezes again after working sometimes.

I have encountered this problem for a week.  Now I'm only running Google Chrome.

Regards

---

### Post by satimis on 2023-08-18
> **Impavidus said:**
> Have you tried disabling extensions? I've had a similar issue for the past week (Firefox from the PPA) and it appeared to be related to the NoScript extension.
Hi,

Please advise which extenesion?  How to disable it?  Thanks

Regards

---

### Post by #&amp;thj^% on 2023-08-18
> **satimis said:**
> Hi,

Please advise which extenesion?  How to disable it?  Thanks

Regards

It would be hard for us to tell which is the bad one or multiple, but start here:
```
about:addons
```
Disable all at first, then add one at time to see if this is really your problem.

---

### Post by satimis on 2023-08-18
> **1fallen said:**
> It would be hard for us to tell which is the bad one or multiple, but start here:
```
about:addons
```
Disable all at first, then add one at time to see if this is really your problem.
Whether you meant "firefox-addons ?

$ ls /usr/lib/ | grep firefox-addons
no output

Please advise where to run your code?  Thanks

Regards

---

### Post by tea for one on 2023-08-18
> Please advise where to run your code? Thanks
The address bar in Firefox

---

### Post by satimis on 2023-08-18
> **tea for one said:**
> The address bar in Firefox
Thanks for your advice.

Unfortunately starting Firefox freezes Ubuntu 22.04

I have tried 3 times

Regards

---

### Post by #&amp;thj^% on 2023-08-18
satimis what firefox are you using, snap or deb?
```
apt policy firefox
firefox:
  Installed: 116.0.3+build2-0ubuntu0.23.04.1~mt1
  Candidate: 116.0.3+build2-0ubuntu0.23.04.1~mt1
  Version table:
     1:1snap1-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu lunar/main amd64 Packages
 *** 116.0.3+build2-0ubuntu0.23.04.1~mt1 501
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Dennis N on 2023-08-18
Find your add-ons:
Firefox Menu >Tools > Add-Ons and Themes > Extensions
There are switches to enable/disable each of these.
As suggested, disable them all and see if your problem still appears. Reactivate one by one and check again.

Also check,
Firefox Menu > Tools > Add-Ons and Themes > Plugins

What type of Firefox? Snap? Flatpak? PPA? Other?

---

### Post by satimis on 2023-08-18
> **1fallen said:**
> satimis what firefox are you using, snap or deb?
```
apt policy firefox
firefox:
  Installed: 116.0.3+build2-0ubuntu0.23.04.1~mt1
  Candidate: 116.0.3+build2-0ubuntu0.23.04.1~mt1
  Version table:
     1:1snap1-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu lunar/main amd64 Packages
 *** 116.0.3+build2-0ubuntu0.23.04.1~mt1 501
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status

```

Hi,

I install firefox on repo

$ apt policy firefox```

firefox:
  Installed: 1:1snap1-0ubuntu2
  Candidate: 1:1snap1-0ubuntu2
  Version table:
 *** 1:1snap1-0ubuntu2 500
        500 http://hk.mirrors.thegigabit.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

I suppose it is snap version

Regards

---

### Post by tea for one on 2023-08-18
> **satimis said:**
> 
Its screen freezes -> after a while turning to a dark screen -> After another while, it turns back to Firefox screen again but still freezing.
I have to hard-reboot the PC
If you have to hard-reboot your PC, you may have incurred file-system damage.
Have you run fsck from a live session to check?

---

### Post by satimis on 2023-08-18
> **Dennis N said:**
> Find your add-ons:
Firefox Menu >Tools > Add-Ons and Themes > Extensions
There are switches to enable/disable each of these.
As suggested, disable them all and see if your problem still appears. Reactivate one by one and check again.

Also check,
Firefox Menu > Tools > Add-Ons and Themes > Plugins

What type of Firefox? Snap? Flatpak? PPA? Other?
Hi,

Thanks for your advice.

My problem here is unable to start Firefox.  It freezes the PC

I installed firefox on repo

Regards

---

### Post by satimis on 2023-08-18
> **tea for one said:**
> If you have to hard-reboot your PC, you may have incurred file-system damage.
Have you run fsck from a live session to check?
No.

The PC is working without problem but not to start Firefox.  It freezes the PC

Regards

---

### Post by tea for one on 2023-08-18
You can also try Firefox Troubleshoot Mode
[https://support.mozilla.org/en-US/kb/diagnose-firefox-issues-using-troubleshoot-mode](https://support.mozilla.org/en-US/kb/diagnose-firefox-issues-using-troubleshoot-mode)
Extensions and customisations will be temporarily disabled.

---

### Post by #&amp;thj^% on 2023-08-18
> **satimis said:**
> Hi,

Thanks for your advice.

My problem here is unable to start Firefox.  It freezes the PC

I installed firefox on repo

Regards
This sometimes renews an apps bugs,quirks, and gremlins.
```
sudo apt install --reinstall firefox
```
EDIT: Disregard my post your using a damn snap....:(

---

### Post by satimis on 2023-08-18
> **1fallen said:**
> This sometimes renews an apps bugs,quirks, and gremlins.
```
sudo apt install --reinstall firefox
```
Thanks for your advice.

I have done it 3 times but still having same problem.

On google search I found postings re "Firefox keeps freezing".  I just follows them not to use it.

Regards

---

### Post by #&amp;thj^% on 2023-08-18
I prefer Firefox my self, but yes it is not a Snap either.
I have a rule (seriously) no Snaps Allowed period....
I can show you how to get rid of the snap version of firefox, and go back to the .deb if you want.

---

### Post by deadflowr on 2023-08-18
>  I have "uninstall/install/reinstall" it on repo several times, including deleting its old folder.
What folder are you deleting?

---

### Post by satimis on 2023-08-18
> **deadflowr said:**
> What folder are you deleting?
If I remember correct

~/snap/firefox/common/.mozilla/firefox/

Regards

---

### Post by deadflowr on 2023-08-18
I wonder if it's an issue with hardware acceleration.

---

### Post by ajgreeny on 2023-08-18
Just as a test of an alternative way to run firefox download the archive direct from Mozilla [https://www.mozilla.org/en-GB/firefox/download/thanks/](https://www.mozilla.org/en-GB/firefox/download/thanks/)
Extract it temporarily to your Downloads folder where it will make a folder named firefox.
In that folder is an executable file also named firefox which if double clicked will open an instance of firefox browser which will make use of your current hidden .mozilla folder in your home.

If that version also crashes it points to a problem of some sort in your firefox profile so rename that hidden .mozilla folder as .mozilla-backup and start firefox again using that same executable file.
Any better?

If that also crashes I am not sure where we go from here but it must be something possibly related to your hardware or software and other respondents have made many other suggestions that have not helped yet so we keep trying!

---

### Post by satimis on 2023-08-18
> **ajgreeny said:**
> Just as a test of an alternative way to run firefox download the archive direct from Mozilla [https://www.mozilla.org/en-GB/firefox/download/thanks/](https://www.mozilla.org/en-GB/firefox/download/thanks/)
Extract it temporarily to your Downloads folder where it will make a folder named firefox.
In that folder is an executable file also named firefox which if double clicked will open an instance of firefox browser which will make use of your current hidden .mozilla folder in your home.

If that version also crashes it points to a problem of some sort in your firefox profile so rename that hidden .mozilla folder as .mozilla-backup and start firefox again using that same executable file.
Any better?

If that also crashes I am not sure where we go from here but it must be something possibly related to your hardware or software and other respondents have made many other suggestions that have not helped yet so we keep trying!
Thanks for your advice.

Following your steps I install Firefox -> start running it for about 15 min. -> it freezes again
I have to restart the PC by pressing Ctrl+Alt+Del

I have no idea whether it is hardware issue.  This PC (AMD 8-core Ryzen 5, RAM 32G) has been running for more than 5 years without problem up-to-now.  I'll test Firefox on Ubuntu 22.04 VM on this PC later to make sure not an OS problem

If it is the hardware issue I just build a new AMD Ryzen 7/Rysen 9, 64G RAM PC.  I haven't build new PC for 5 years.

I'll come back later

Regards

---

### Post by satimis on 2023-08-19
Hi all,

Further to my posting #24 above

Just test Firefox on a spare PC
AMD 8-core CPU
32G RAM onboard

Firefox still freezes occasionally.  After a while, without doing anything on it (but working on Google Chrome), it works again.

It is very strange.  I don't think that there will be hardware problem on 2 PCs?

Regards

---

### Post by ajgreeny on 2023-08-19
Did you use a new profile for Firefox on both machines as I suggested in post #23?

---

### Post by satimis on 2023-08-19
> **ajgreeny said:**
> Did you use a new profile for Firefox on both machines as I suggested in post #23?
No.  I'll test the new profile on the spare PC later.

I tested the Firefox installed on repo on my spare PC.  It proved that the firefox installed on repo freezing from time to time on both my daily working PC as well as my spare PC.

I'll report my test result afterwards.  Thanks

Regards

---

### Post by satimis on 2023-08-19
Hi ajgreeny,

Tried again.

Steps performed as follows:-

On Terminal
$ type firefox```

firefox is /usr/bin/firefox

```
Firefox was installed using apt not using snap

Steps
1)
$ sudo apt-get purge firefox

2)
delete .mozilla/firefox/ directory
$ rm -rf ~/.mozilla/firefox/

3)
Delete .macromedia/ and .adobe directories in home directory
$ rm -rf ~/.macromedia/
$ rm -rf ~/.adobe/

4)
Remove Preferences and User Profiles
$ sudo rm -rf /etc/firefox/

5)
Restart PC
sudo reboot

Again on Terminal run;
$ apt policy firefox```

firefox:
  Installed: (none)
  Candidate: 1:1snap1-0ubuntu2
  Version table:
     1:1snap1-0ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```
Firefox is not installed

6)
$ type firefox```

firefox is /snap/bin/firefox

```

Firefox was installed on snap.  There are 2 (two) firefox running on this spare PC which is very strange to me.

7)
Uninstall Firefox which was installed via snap
$ sudo snap remove firefox```

firefox removed

```

Reboot PC again
$ sudo reboot

Install firefox as per your advice on post #23

Firefox still freezes but taking longer time, about 45 min.  I have to logout and relogin Ubuntu 22.04 to get it started again

Regards

---

### Post by #&amp;thj^% on 2023-08-19
Post #28 is a good start, i would also remove:
```

 /usr/lib/firefox/ 
/usr/lib/firefox-addons/ 
```

The later holds your addons ie:
```
ls /usr/lib/firefox-addons/
distribution  extensions  plugins

```
I just don't know about snaps though.

---

### Post by ajgreeny on 2023-08-19
Unfortunately you did not follow my suggestions in post #23 so I am not sure where you have currently got to.

My suggestion was to download the .tar.gz archive which is not what you seem to have done originally, though I think you have now done so. You may need to remove the profile that was created when you run the snap that you installed from the repos just in case that is the treason for your problem, though I can not see why it should. 
Doing so will ensure you at least have a completely fresh, clean start, and unless you have added a PPA for firefox and changed the apt priority for the version you want to install, do not run the ***sudo apt install firefox*** command or you will again get the snap version. See [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) for details.

I know very little about the Firefox snap as I've never used it, having immediately started using the .tar.gz archive, and totally removed the complete snap infrastructure from all my computers; snaps simply do not suit my way of working or my current old hardware.

---

### Post by satimis on 2023-08-20
> **ajgreeny said:**
> Unfortunately you did not follow my suggestions in post #23 so I am not sure where you have currently got to.

- snip - 
Tried again.  Installed Firefox from firefox-116.0.3.tar.bz2 as advised.

Start Firefox on its folder.

Working about 15 min. Firefox still freezes but without dark screen popup.  Waiting a while it works again.  But freezing repeats and I have to wait again.

Regards

---

### Post by simonsaysthis on 2023-08-22
> **satimis said:**
> Thanks for your advice.

Unfortunately starting Firefox freezes Ubuntu 22.04

I have tried 3 times

Regards

I have the same problem on a fresh installation. Starting FF can lead to a total system freeze with screen being partially black.

---

### Post by VMC on 2023-08-22
Search for relevant errors: ```
journalctl -p 3 -xb
```

---

### Post by satimis on 2023-08-22
> **VMC said:**
> Search for relevant errors: ```
journalctl -p 3 -xb
```
$ journalctl -p 3 -xb > output.txt

output.txt is attached here.

Regards

---

### Post by VMC on 2023-08-22
Nothing relevant seen.
Open Firefox using terminal, then when freezes, check the opened terminal for messages.

---

### Post by satimis on 2023-08-22
> **VMC said:**
> Nothing relevant seen.
Open Firefox using terminal, then when freezes, check the opened terminal for messages.
Hi,

Thanks for your advice.

I'm now running the Firefox installed on "firefox-116.0.3.tar.bz2" as advised by 'ajgreeny' on post #23 above, on my spare/standby PC.  It seems quite stable, except freezing occasionally but without dark screen popup.  After waiting a while it works again.

I'm not starting it on Terminal.  On the folder where the package was extracted I just right-click "firefox" --> Run , to start it.  Where shall I check?  Thanks

Regards

---

### Post by ajgreeny on 2023-08-23
Assuming it is in the **Downloads** folder of your home which is where you say it is start it using terminal with command ```
cd Downloads/firefox && firefox
```
A new window of firefox should appear and if that freezes there may be useful information shown in terminal.

---

### Post by satimis on 2023-08-23
> **ajgreeny said:**
> Assuming it is in the **Downloads** folder of your home which is where you say it is start it using terminal with command ```
cd Downloads/firefox && firefox
```
A new window of firefox should appear and if that freezes there may be useful information shown in terminal.
I start firefox with following steps;

-> File Manager -> Downloads -> Firefox (folder manually created by me) -> firefox (folder created automatically during extraction) -> right-click firefox -> Run (click)

During freezing no new window popup.  Click items on firefox window with mouse pointer no response.  It freezes a while then firefox works again.  Ubuntu 22.04 desktop is still working, not freezing.

Edit:
On firefox folder (automatically created on extraction)
Also I can right-click firefox-bin -> Run 
to start  firefox

Regards

---

### Post by ajgreeny on 2023-08-23
Ok, you created a folder Downloads/Firefox so the command I mentioned in my last post will have to be changed to ```
cd Downloads/Firefox/firefox && firefox
```
This will take account of that extra manually created folder.

---

### Post by satimis on 2023-08-23
> **ajgreeny said:**
> Ok, you created a folder Downloads/Firefox so the command I mentioned in my last post will have to be changed to ```
cd Downloads/Firefox/firefox && firefox
```
This will take account of that extra manually created folder.
$ cd Downloads/Firefox/firefox && firefox```

Command 'firefox' not found, but can be installed with:
sudo snap install firefox  # version 116.0.3-2, or
sudo apt  install firefox  # version 1:1snap1-0ubuntu2
See 'snap info firefox' for additional versions.

```
Regards

---

### Post by satimis on 2023-08-24
Hi ajgreeny,

Standby/Spare PC
==============
Now I can start firefox of firefox-116.0.3.tar.bz2 package on Terminal with following steps:-

$ cd Downloads/Firefox/firefox/
$ sudo chmod +x ./firefox-bin
$ ./firefox-bin

In these 2 days this firefox seems quite stable only freezing once.  I logout/relogin Ubuntu and restarted it.

If this time firefox freezes again I'll check the Terminal and report the output here.

Regards

---

### Post by frank-w on 2023-12-01
In my case apparmor was rootcause

[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2044304](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2044304)

---

