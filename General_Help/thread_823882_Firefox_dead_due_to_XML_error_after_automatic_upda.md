---
title: "Firefox dead due to XML error after automatic update"
date: 2008-06-09
forum: General Help
---

### Post by Syg on 2008-06-09
About 10-30 minutes ago, Ubuntu's system update asked me to install new versions of the firefox, firefox-3.0, etc packages. I did so, and I waited it for it to download and install. Afterwards, I started up Firefox and all I got was this:

```
XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 242, Column 5:
    <key                          key="&fullZoomReduceCmd.commandkey2;"  command="cmd_fullZoomReduce"  modifiers="accel"/>
----^
```

I would investigate file myself (I have a (very) little experience with Firefox's inner-workings), but I'm not certain where the files are installed or how much damage I could do trying to fix it.

Any help or assistance fixing the problem would be greatly appreciated.

EDIT: Might be useful to note that I've tried reinstalling the packages.

---

### Post by y-lee on 2008-06-09
Hmm I am not sure

one thing you can try tho is to deleting FF's Cache


Open nautilus and click view and then show hidden folders. Now navigate to 

```
/home/username/.mozilla/firefox/xxxmm.default/Cache
```

Where username is your user name and xxx is a seemingly random string of characters. Now delete everything in the Cache directory.

Note I am using FF2 so your directory name may be a bit different and I am also assuming you have only the default firefox profile.

Now start FF and see if it works.

---

### Post by jimv on 2008-06-09
Also, you could try this:

```
sudo apt-get remove --purge firefox-3.0
sudo rm -r /usr/lib/firefox-3.0/chrome
sudo apt-get install firefox-3.0
```

---

### Post by y-lee on 2008-06-09
jimv advice should work if mine doesn't, assuming FF was installed thru the repos and not compiled. But purging firefox will lose all your add ons and themes and custimizations, for me that would be a hassle to fix back.

It might also be a problem with your profile and or add ons. to test this try

```
firefox -P
```

and create a new profile. If this works something is wrong with your old profile.

---

### Post by Syg on 2008-06-09
Would purging also remove my bookmarks, etc? If so, how would I save them before hand?

---

### Post by y-lee on 2008-06-09
> **Syg said:**
> Would purging also remove my bookmarks, etc? If so, how would I save them before hand?

Yeah I think it would.

In your firefox directory i mentioned above look for the file bookmarks.html copy it somewhere and then try to move it back or import it after you reinstall.

---

### Post by Syg on 2008-06-09
The purge seemed to work, but 'download statusbar' is still in my addons window, and doesn't work (and I can't install it again). None of my bookmarks/profile was lost in the purge, however.

---

### Post by y-lee on 2008-06-09
> The purge seemed to work, but 'download statusbar' is still in my addons window, and doesn't work (and I can't install it again). None of my bookmarks/profile was lost in the purge, however.

Cool!
It will not let you uninstall the download statusbar add on?

---

