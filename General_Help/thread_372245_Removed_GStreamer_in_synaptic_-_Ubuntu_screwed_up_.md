---
title: "Removed GStreamer in synaptic - Ubuntu screwed up (freeze after login)!"
date: 2007-02-27
forum: General Help
---

### Post by xkrwlng on 2007-02-27
hey all

i've been running ubuntu on my machine for a few days now.  I've been having fun adding packages through synaptic, in order to get stuff like mp3, avi, and rmvb files to play on my media players.

anyway, earlier today I noticed that my headset wasn't playing any sound.  In the upper right corner, on the menu bar thing, there was the Volume icon, with that round red circle with a slash through it.  I double clicked on my Volume icon, and it gave me some error message about GStreamer or something like that.

Now, over the past few days, I think I installed a few of those additional GStreamer plugin libraries through synaptic.  Everything was working fine, I don't know why GStreamer broke or whatever.  But, thinking I must have installed a faulty Gstreamer plugin or something, I went into synaptic and Removed one or 2 of the Gstreamer plugins.

A few minutes ago, I powered up my computer the Ubuntu login screen came up.  I entered my user name, and my password, and the screen went to the sexy Gradient red background that Ubuntu shows when its loading everything up when you log in.  However, the center-aligned icons (that show whats being loaded after you try to log in) disappears, and Ubuntu gets stuck at the gradient Red background thing.

I must have accidentally removed the wrong GStreamer thing in Synaptic (a critical one, apparently).

How can I fix this? - How can I reinstall GStreamer if I can't login to do anything?
Ubuntu has a command-line recovery mode - what command would I need to enter to reinstall all necessary GStreamer files so I can get Ubuntu running again? (would it be an apt-get command?)

thanks for any help

---

### Post by magicfab on 2007-02-28
I am not sure how removing gstreamer would prevent you from loging in... but you can search for any gstreamer packages by using:
apt-cache search gstreamer --names-only

Use man apt-cache to find out more about apt-cache.

---

### Post by xkrwlng on 2007-02-28
> **magicfab said:**
> I am not sure how removing gstreamer would prevent you from loging in... but you can search for any gstreamer packages by using:
apt-cache search gstreamer --names-only

Use man apt-cache to find out more about apt-cache.
thanks, i followed those steps, and then did an "apt-get install" for several of the basic gstreamer packages that I think should have come enabled by default for Ubuntu.

no matter, still, whenever I try to login anymore (and am successful), ubuntu still goes to the Red-Gradient screen after i try to login, and doesn't do anything.  I can move the mouse around, but that's it.  There's nothing to click on, there's nothing to do.  Basically, the desktop for ubuntu just is non-existent.

I CAN login to an xterm command line window to do command line stuff, by clicking Options in the bottom left corner of the screen.  But that's the only functionality I am able to get from Ubuntu. :confused:

---

### Post by xkrwlng on 2007-03-14
were there any additional thoughts on how to fix this problem?

I can log in fine, but the second the login is successful, I go to the red-gradient screen (Ubuntu 6.06), and that's all Ubuntu does.  It has something to do with the absence of the Gstreamer packages, because Ubuntu broke after I uninstalled a gstreamer item in synaptic.

---

