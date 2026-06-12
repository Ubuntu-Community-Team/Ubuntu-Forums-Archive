---
title: "How do I install firefox from mozilla"
date: 2017-08-13
forum: General Help
---

### Post by l6griffin on 2017-08-13
I'm running firefox 54.0 and it is next to unuseable. The latest version is of firefox is 55.0 I've downloaded that. The instructions seem to be out of date and unuseable. Any help appreciated.

Larry

---

### Post by Autodave on 2017-08-13
If 54 is that bad, I doubt that 55 will be a whole lot better. What kind of problem(s) are you having? What are the specs of your machine? Do you know what video card is installed? Have you installed any drivers for the video card and if so, where did you get the driver(s) from?

---

### Post by cariboo on 2017-08-13
It's probably quite a bit easier to use a ppa to install the latest version of Firefox, plus it will update automagically when newer versions are released. See here:

[https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next](https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next)

on how to set it up.

---

### Post by l6griffin on 2017-08-13
I'm on an HP 2000 laptop, AMD 64 bit, AMD E1-1500 APU with Radeon(tm) HD Graphics × 2, Gallium 0.4 on AMD PALM (DRM 2.49.0 / 4.10.0-32-generic, LLVM 4.0.0).

I have not installed any drivers for the video. I installed 17.04 and it probably needs to be backed up, cleaned, and re-installed. The video has always been a problem. I did try and install a video driver but it didn't seem to help much. The screen doesn't seem to have been computed correctly the vertical height doesn't seem to be correct.

The problem is the screen dims randomly and it is not a problem in thunderbird but does exist in the updater. Now I'm also losing the ability to click. I can put the cursor on a button and click or right click don't work. I can go to launch pad and bring up TB no problem.

It maybe a month or two but I intend to buy a laptop with ubuntu already installed.

---

### Post by l6griffin on 2017-08-13
That seems to have worked, but I'll wait a bit, to mark as solved. I was on 54.0, 55.0 is on firefox web site (since 7/24, and the beta is 56.0, FYI

I'm also having a problem with thunderfbird and had installed it's Beta, which didn't solve the problem, and lost the task task bar i.e. File Edit, View, etc, etc. So i wasn't anxious to go Beta.

---

### Post by walts48 on 2017-08-14
> **l6griffin said:**
> That seems to have worked, but I'll wait a bit, to mark as solved. I was on 54.0, 55.0 is on firefox web site (since 7/24, and the beta is 56.0, FYI

I'm also having a problem with thunderfbird and had installed it's Beta, which didn't solve the problem, and lost the task task bar i.e. File Edit, View, etc, etc. So i wasn't anxious to go Beta.

Here is how I install Firefox from Mozilla.

Download the tarball to my ~/Apps folder
Right click and select Extract Here.
Launch it from a terminal window and Lock to Launcher.
Then I let it update from Mozilla. The updates are more current than from Ubuntu, and don't disable features like Multiprocess.

For your Thunderbird problem, right click in the Tab Bar and enable the Menu Bar.

---

### Post by l6griffin on 2017-08-14
Walt48, thanks the menu bar hint worked.

firefox and ubuntu are still not working right. I did find I could get the click working if I went to the launchpad bar and right clicked firefox icon and quit. firefox doesn't close but click works.

---

### Post by l6griffin on 2017-08-17
I didn't actually start this thread for my firefox problem but I thought I'd let you know that has been fixed. I received an update via updater Tues morn and again this morn and firefox is working as good as ever. Now if I could get an update for thunderbird I'be happy.

thanks all, Larry

---

### Post by walts48 on 2017-08-17
> **l6griffin said:**
> I didn't actually start this thread for my firefox problem but I thought I'd let you know that has been fixed. I received an update via updater Tues morn and again this morn and firefox is working as good as ever. Now if I could get an update for thunderbird I'be happy.

thanks all, Larry

Thunderbird 52.3.0 is out. :)

[https://www.mozilla.org/en-US/thunderbird/52.3.0/releasenotes/](https://www.mozilla.org/en-US/thunderbird/52.3.0/releasenotes/)

If installed through the Ubuntu repo (like my release version is) we have to wait on the maintainer.

If installed from Mozilla just click on Help > About Thunderbird.

---

