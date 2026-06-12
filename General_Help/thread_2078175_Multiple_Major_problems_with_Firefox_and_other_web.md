---
title: "Multiple Major problems with Firefox and other web browsers"
date: 2012-10-30
forum: General Help
---

### Post by MelissaCutler on 2012-10-30
Hi,

I have recently installed Ubuntu (I think it's 12.4) on a new laptop.  At first seemed to work, and I spend some time installing all the software I needed, and getting things setup right.  I installed several addons for Firefox.

One day Firefox started to crash.  This would happen instantly on starting it - making it impossible to access the web.  The error message gave me the option of resetting Firefox to default settings - removing addons.  I tried this, but it didn't help.

I thought that this had been caused by a buggy update, so I did nothing, hoping that the problem would be fixed by another update within a week or so.  It has been more than a week now.

I tried down-loading Chromium, and encountered similar problems with that.  (These problems were not caused by an update, but were present from installation.  The symptoms were the same as Firefox.  It would crash, instantly on start up, for no apparent reason.)

I tried to uninstall and re-install Firefox.  It uninstalled no problem (I used to Software Centre) but I could not re-install it (The error message said "download failed, check your internet connection") note that I have tried this several times, with different internet connections, and with restarts between attempts.  I have also successfully installed another program between failed attempts at re-installing Firefox.

Current situation:

Firefox is not installed.  Chromium appears to be working today.  I don't know why it has started to work.  Perhaps the problem with Chromium was always inconsistent, rather than predictable.  Perhaps it will work from now on, perhaps it will not.  I do not know.

Even so I would prefer to also have Firefox, as I make extensive use of addons such as Zortero, and others.  Firefox is the browser that I am familiar with.

Fortunately this is not an urgent problem.  I also have a Windows 7 partition on the machine, with a working installation of Firefox, Zotero, and LibreOffice, which will allow me to continue working.

Thank you in advance for you assistance,

Melissa

When answering please bear in mind that, though I have some experience of Linux, I do not "understand" the operating system.  If you assume I have more back ground knowledge that is actually the case it is likely that things will become very confusing and frustrating for me.  Thank you again, Melissa

---

### Post by netwo on 2012-10-30
You should give up a try to Google Chrome , way more stable! 
I can also suggest you to reinstall Firefox and all his plugin with Ubuntu Software Manager.

---

### Post by jerrrys on 2012-10-30
If you maximum stability, stick with LTS.

 [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by howefield on 2012-10-30
Might be worth using a fresh Firefox profile (delete or rename your ~/.mozilla folder) and then install your add-ons one at a time, using the browser for a bit of time between each to try to isolate the issue.

You could also try starting the browser from a terminal, this may give a clue as to what is failing which you can post back here if needs be.

```
firefox &
```

---

### Post by MelissaCutler on 2012-10-30
> **netwo said:**
> You should give up a try to Google Chrome , way more stable! 
I can also suggest you to reinstall Firefox and all his plugin with Ubuntu Software Manager.

Thank you, but this is confusing.

What is Ubuntu Software Manager?  Is this the same thing as the Software Centre?  Like I said, I have uninstalled Firefox, and attempted to reinstall in the Software Centre, but there is an error.  If says it is unable to download the package, even though I can install other packages no problem.

Like I said, I have installed Chromium, and this is giving me some web browsing ability, but it crashes sometimes.  Is Chrome related, or something separate?  I can't find anything called Chrome in the software centre.  Does Chrome have have a plugin similar to Zotero?

---

### Post by MelissaCutler on 2012-10-30
> **jerrrys said:**
> If you maximum stability, stick with LTS.

 [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Thank you, but my understanding is that 12.04 is a long term support version.  I have checked, and I am definitely running Ubuntu 12.04.

---

### Post by MelissaCutler on 2012-10-30
> **howefield said:**
> Might be worth using a fresh Firefox profile (delete or rename your ~/.mozilla folder) and then install your add-ons one at a time, using the browser for a bit of time between each to try to isolate the issue.

You could also try starting the browser from a terminal, this may give a clue as to what is failing which you can post back here if needs be.

```
firefox &
```

Thank you, but how should I get Firefox back on the machine?

Firefox is gone now, and when I attempt to install it using the software centre I get an error message saying it cannot download.  I can still install other packages in the software centre, it's just Firefox that give this problem.

---

### Post by howefield on 2012-10-30
Go to your home folder and press Ctrl + H to reveal the hidden folders, scroll down and look for one called .mozilla then rename it.

Then open a terminal and type the following threee commands one at a time, typing in your password if requested.

```
sudo apt-get clean
``` 
```
sudo apt-get update
```
```
sudo apt-get install firefox
```

If you get an error, post it here.

---

### Post by jerrrys on 2012-10-30
> **MelissaCutler said:**
> Thank you, but my understanding is that 12.04 is a long term support version.  I have checked, and I am definitely running Ubuntu 12.04.

My mistake, I somehow read 12.10 into your post.

---

### Post by MelissaCutler on 2012-10-30
> **howefield said:**
> Go to your home folder and press Ctrl + H to reveal the hidden folders, scroll down and look for one called .mozilla then rename it.

Then open a terminal and type the following threee commands one at a time, typing in your password if requested.

```
sudo apt-get clean
``` 
```
sudo apt-get update
```
```
sudo apt-get install firefox
```

If you get an error, post it here.

Thank you, that has re-installed Firefox on the system, and it seems to be allowing me to do basic web browsing.  I've just tried going to the Menu "Tools", then "addons" and it crashes abruptly, bringing up the Mozilla Crash report.

Thank you so much for your help.

Melissa

---

### Post by howefield on 2012-10-30
Not sure what to suggest, if it is reproducible you could try starting Firefox from terminal, and leave the terminal window open.

If it crashes you may get some useful output in the terminal.

```
firefox
```

---

### Post by MelissaCutler on 2012-11-03
> **howefield said:**
> Not sure what to suggest, if it is reproducible you could try starting Firefox from terminal, and leave the terminal window open.

If it crashes you may get some useful output in the terminal.

```
firefox
```


I've tried that, and there was no output in the terminal.

Going to Tools -> add-ons
Reproducibly causes a crash.  It also crashes randomly, at unpredictable times.

---

### Post by MelissaCutler on 2013-01-09
Can anyone help me with this?

It's a major problem, as Firefox usually crashes within a few minutes browsing.  My Ubuntu installation is not much use like this, so I'm considering switching to another distro over it.  I really don't want to do that.

---

### Post by MelissaCutler on 2013-02-12
I think I've sorted it out now, by removing flash player.

---

### Post by kurt18947 on 2013-02-12
> **MelissaCutler said:**
> I think I've sorted it out now, by removing flash player.

Good ol' Adobe.  Unfortunately,  there won't be any flash updates for Firefox beyond security fixes.  Google Chrome (not found in the repositories) uses  something called 'pepper' with flash.   That's why some people have installed Chrome; they need the latest and greatest flash player, often for online games.

There might be one other thing you could try if you're so inclined.  Create a new user in Ubuntu.  Assuming you're using Unity or Gnome-shell, press the 'super'(windows) key and type "user".  You should find an app to create and delete users.  This must be done from an account with SUDO (administrator or root) privileges.  Log out then log into the newly created account.  Does Firefox misbehave there too?   What this exercise accomplishes is bypassing any account specific settings that may be causing Firefox "indigestion".  If there's no improvement, just delete the newly created account.

---

