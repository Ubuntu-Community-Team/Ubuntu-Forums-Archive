---
title: "Google Chrome (latest stable version) Causes Display/Unity to Crash on 14.10"
date: 2015-02-04
forum: General Help
---

### Post by gwinston99 on 2015-02-04
I have searched and cannot find anyone reporting my precise problem.

I run Ubuntu 14.10 on a not too old HP laptop - and Google Chrome is my browser of choice.  All was working well until (I think) a recent update.  Now whenever I run Google Chrome on websites with video (Youtube) and also on Google Inbox, the display crashes.

The Unity toolbar is gone, the status bar is gone and the browser flashes in and out with just the desktop wallpaper image.

Any suggestions as to how to troubleshoot this situation.

BTW - this does not happen with Firefox, but I do not want to switch from Chrome because I have it set up just the way I want it and use it at work and on my phone as well.

Thanks in advance for your assistance.

Gregg - Ubuntu User since Wharty

---

### Post by jgibson-oakg2 on 2015-02-24
I experience the same bug. I'm running Ubuntu 14.04 32-bit on an old Lenovo X61 laptop and Google Chrome, after it's been open for a couple of minutes, causes my screen to go extemely dark. Ususally I can adjust the screen brightness with Fn + Home/Fn + End, but after the crash, this feature doesn't work. I can restore the brightness of the screen by closing the laptop lid, which causes it to suspend, then waking it up. But when I wake it up, I find Unity has no app launcher, ctrl + Alt + t doesn't launch the terminal, and I can't do anything other than move the cursor and close Google Chrome. So I end up having to use the power butting to force the computer off.

I like Firefox but Chrome has the apps launcher and that's kind of important to me.

---

### Post by ventsislav-mladenov on 2015-03-05
Same bug here Chrome and Opera Developer breaks the Unity. On Chrome when I'm searching for extensions, on Opera when I start to login.

---

### Post by cesar-negrete on 2015-03-09
I had the same issue, and was driving me nuts to the point that I even didn't want to use this laptop anymore.
I use Chrome for Inbox and more recently for Whatsapp Web, it seems to crash Unity, Compiz, or the graphics driver, or I don't know.  the issue here seems to be with a bug in the DRI3 implementation for the Intel driver (at least in my case).

If you start chrome from the command line with the following (depending on the installed version), it should work fine:

LIBGL_DRI3_DISABLE=1 google-chrome-unstable

LIBGL_DRI3_DISABLE=1 google-chrome-stable

I assume the same goes for chromium

***** EDIT ******

**Nah, nevermind, I clicked on a file in Inbox and died again. I wonder which Ubuntu component is the culprit to search for the bug** :(

---

### Post by natalia4 on 2015-04-13
Hello guys,

I've been having this problem, and thought that installing Ubuntu from scratch would help, but it didn't.

It was really hard to find people with the same problem, so I thought I'd come back to tell you what solved the problem for me.

I have a Dell Inspiron 1525, latest released Ubuntu. What helped me was in Chrome to disable the option under System > Use hardware acceleration when available.

It opens a little slow, but it doesn't crash. In my case what happened was that my screen went black, and I had to do a hard restart.

Bad thing is that I didn't save where I got this information, but I found it somewhere. Try it! I was really happy it helped, I was really angry I couldn't use Inbox in Ubuntu.

If you read this, I'm really curious to know if it worked for you, let me know :)

---

### Post by chuck20 on 2015-04-17
I am also having the same problem.... But I hadn't figured out it was only Chrome until reading this. Running 14.10 on a Lenovo laptop. I'm going to try using firefox for awhile to see if it's in chrome on mine as well

---

### Post by One4All on 2015-04-19
Yes, this also WFM (worked for me, or Waffly Flying Monster?) - here
[https://answers.launchpad.net/ubuntu/+question/265485](https://answers.launchpad.net/ubuntu/+question/265485)

  specifically, this was a good workaround in my case
     "What helped me was in Chrome to disable the option under System > Use hardware acceleration when available."

---

