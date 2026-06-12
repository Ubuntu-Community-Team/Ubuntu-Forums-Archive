---
title: "RSSOwl internal browser problems"
date: 2005-05-15
forum: General Help
---

### Post by royg1234 on 2005-05-15
Hey.  Just recently installed RSSOwl as per the Starter Guide, and the internal browser doesn't work, so I see html tags in the preview pane and there's no formatting whatsoever.

I did the guide verbatim, then did it for 1.1.1, both with the latest firefox build.  Neither has a working internal browser.

/usr/bin/runRSSOwl.sh

```

export MOZILLA_FIVE_HOME=/usr/lib/mozilla-firefox
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:${MOZILLA_FIVE_HOME}:${LD_LIBRARY_PATH}
cd /opt/rssowl_linux_1_1_1_bin/
./run.sh

``` 

/usr/share/applications/RSSOwl.desktop

```

[Desktop Entry]
Name=RSSOwl
Comment=RSSOwl
Exec=runRSSOwl.sh
Icon=/opt/rssowl_linux_1_1_1_bin/rssowl.xpm
Terminal=false
Type=Application
Categories=Application;Network;

```

This seems works fine in Windows, btw, albeit w/ Internet Explorer <--  [-X 

Thanks in advance!

---

### Post by royg1234 on 2005-05-21
fix:

[COLOR=DarkGreen] Tools > Preferences > View [/COLOR]

then under "[COLOR=DarkGreen]Misc[/COLOR]", check "[COLOR=DarkGreen]View Newstext in Browser[/COLOR]"

This isn't set as default, though it should be.  I think it is in the Windows version.

---

