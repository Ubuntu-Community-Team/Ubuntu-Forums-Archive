---
title: "Terrible font rendering of monospaced fonts in browsers."
date: 2013-04-21
forum: General Help
---

### Post by Darknote on 2013-04-21
**EDIT: **Installed lsb-core and it fixed the terrible fontrendering in ubuntu.
```

sudo apt-get install lsb-core

```
Then move the ~/.fonts.conf file to ~/.config/fontconfig/fonts.conf

**Original post:**
Is there something I can do to fix font rendering of monospaced fonts in the browsers.
This seems to be a system wide problem because the fonts are the same whether it be in Firefox, Google Chrome, or Opera.

**The problem describes as following:**

When I navigate to a webpage like github.com, og jsfiddle.net, the monospaced font displayed in the text input area renders terribly. I have got anti-aliasing turned on.
Basically, the font renders like if we were back in the 90s in a Windows console except the fonts are really thin and look like a bad variant of the ugly Microsoft Consolas font.

When I navigate to these pages, or similar pages using other systems, f.ex. Fedora or even Windows the font is much nicer, leaner and stronger which makes it easier to see and to read.

I have done some tweaking to my system to increase performance. Followed this guide: [http://ubuntuarena.wordpress.com/2012/12/26/11-tips-to-speed-up-computers-running-ubuntu-12-1012-04linux-mint-13-maya/](http://ubuntuarena.wordpress.com/2012/12/26/11-tips-to-speed-up-computers-running-ubuntu-12-1012-04linux-mint-13-maya/)
And I installed Gnome Shell and Cinnamon and switched from lightdm to gdm window manager. This is due to the fact that Unity was performing badly on my machine and I simply don't like it. And after my tweaks and installing Cinnamon the performance went sky high.

Anyone?

Thank you.

---

### Post by ajgreeny on 2013-04-21
Do you happen to run any KDE applications and have the kde system-settings package installed?

If you do, and have used system-settings and made changes to the Fonts tab of that, there will be a hidden **.fonts** file in your home.  Remove that and fonts in your gnome desktop my return to normal.

If you don't have the system-settings package then simply ignore this post; I thought it worth posting, however, as I had what sounds like the same problem on my Xubuntu system, and what I suggest above put things back to normal again.

---

### Post by Darknote on 2013-04-23
@ajgreeny

I don't have any KDE apps installed and I don't remember when this problem occurred. I just remember installing Cinnamon Desktop via the Cinnamon PPA and doing some awesome tweaks to improve the performance and then suddenly I noticed the bad font rendering. Whether it had happened before the installation of Cinnamon, or the tweaking of my OS I can't really tell since I wasn't observing it.

It fixed itself after I installed the [lsb-core]("https://launchpad.net/ubuntu/quantal/+package/lsb-core") package ```
sudo apt-get install lsb-core
```

Then a new .fonts.conf file was living under my home/ folder so I moved it under ~/.config/fontconfig/fonts.config .

Now my PC shines!

---

### Post by ajgreeny on 2013-04-24
Thanks for the interesting update.

Even though it came from a different source, I wonder if the .fonts.conf file does the same thing when made by lsb-core instead of the kde system-settings, and makes the rendering go awry for some reason.

Glad you got it fixed!

---

