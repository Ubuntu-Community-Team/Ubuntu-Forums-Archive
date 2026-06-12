---
title: "is there a way to clear cache automatically on leaving opera-beta?"
date: 2015-09-26
forum: General Help
---

### Post by shantiq on 2015-09-26
i cannot see any as yet having googled till blue in da face

Best trick i have arrived at this far is this >>[ATTACH=CONFIG]264668[/ATTACH]

but that is still manual need to remember to do it on leaving or starting ....   is there a better way ...    an automatic way to set this?

Thanx



PS [humour corner]  clearing cash automatically on leaving The Opera would be easier ...   maybe

---

### Post by QDR06VV9 on 2015-09-26
[FONT=Helvetica]Opera stores visited pages both in memory and on disk, so they will be available after a restart. To change the cache settings, go to [/FONT][FONT=Helvetica]Settings > Preferences > Advanced > History[/FONT][FONT=Helvetica] and choose from the following options in the Disk Cache section:[/FONT]Empty cache on exit	Check Empty on exit.
Regards

---

### Post by shantiq on 2015-09-26
thanx R i should have said it was for opera-beta not repo opero :] ;  i do not see any of these on my version of opera-beta  maybe the regular has those settings   [i installed this version to have access to 360° videos on YT as earlier versions do not]
so no [COLOR=#000000][FONT=Helvetica]Preferences > Advanced > History there at all

[/FONT][/COLOR] opera-beta --version
32.0.1948.19


see here [ATTACH=CONFIG]264669[/ATTACH]

---

### Post by CantankRus on 2015-09-26
Use private browsing.
If you want to use extensions, enable them in private mode.

You can edit your application launcher to open a private window on left click.
Copy the launcher to your local settings...
```
cp /usr/share/applications/opera-beta.desktop ~/.local/share/applications
```

Edit the local launcher to open private windows...
```
gedit ~/.local/share/applications/opera-beta.desktop
```

Edit the exec line to read...
```
Exec=opera-beta --private %U
```

You may have to remove and re-add your opera-beta launcher to the unity launcher for change to take effect.

---

### Post by howefield on 2015-09-26
> **shantiq said:**
> thanx R but these i believe might be the instructions for Windows not for Ubuntu

Nah, it is just a copy/paste from the wrong help page for your version.

There is no native option to automatically clear your cache on exit, you either need to Ctrl+Shift+Del and clear manually, use private browsing, or install an extension which will clear on exit.

---

### Post by shantiq on 2015-09-27
thanx guys for further input

howefield    yes that is just for the default version it seems

CantankRus [ace name :] surely a private window will not keep my history/passwords/autofill etc the only thing i want removed is the cache so it loads up in crisper fashion not be so cumbersome [older machine] i do not want to remove other "memories" merely the cache  ....   hmmm   maybe there is a way to customize private window   then i could indeed edit my launcher [easier for me here as on LXDE]


[B]Edit


[/B]so in the launcher i tried

```
Exec=opera-beta && rm -rf  ~/.cache/opera-beta
```   but that does not do it

although rm -rf ~/.cache/opera-beta evidently clears the cache on its own

Now something here i clearly do not understand about the launcher command ;   does it not like the && ?  ha it seems it only commands software not added requests

There must be a way to combine both commands in the launcher which will work?   any ideas?

[B]Edit2

[/B]ok ran opera-beta --help   and you get that info

```
Opera 32.0.1948.19 betaFeatures available through command-line switches:
    --with-feature:accessible_panes [Enabled by default: false]
    --with-feature:addons-detailed-errors [Enabled by default: false]
    --with-feature:autoupdate-notifications [Enabled by default: false]
    --with-feature:bundle-downloads [Enabled by default: false]
    --with-feature:bundle-history [Enabled by default: true]
    --with-feature:default-browser-prompt-in-start-page [Enabled by default: true]
    --with-feature:disable-npapi [Enabled by default: false]
    --with-feature:drag-and-drop-downloads [Enabled by default: true]
    --with-feature:encrypted-media-extensions [Enabled by default: true]
    --with-feature:extended-feature-stats [Enabled by default: false]
    --with-feature:extended-lazy-session-loading [Enabled by default: false]
    --with-feature:extension-content-verification [Enabled by default: false]
    --with-feature:extension-desktop-capture-api [Enabled by default: false]
    --with-feature:forced-default-browser-prompt [Enabled by default: false]
    --with-feature:hidpi-speed-dial-tiles [Enabled by default: false]
    --with-feature:hi-resolution-thumbnails [Enabled by default: false]
    --with-feature:intel-realsense-support [Enabled by default: false]
    --with-feature:invalidations-webui [Enabled by default: false]
    --with-feature:linux-libnotify-toasts [Enabled by default: false]
    --with-feature:mac-toolbar-redesign [Enabled by default: true]
    --with-feature:npapi-removal-notification [Enabled by default: false]
    --with-feature:other-speed-dials-cleaner [Enabled by default: false]
    --with-feature:enable-platform-accelerated-video-decoding [Enabled by default: false]
    --with-feature:proprietary-codecs-support-for-web-audio-api [Enabled by default: false]
    --with-feature:restore-contenteditables-state [Enabled by default: true]
    --with-feature:share-button-visibility [Enabled by default: false]
    --with-feature:show-domain-when-entering-fullscreen [Enabled by default: true]
    --with-feature:standalone-discover-page [Enabled by default: true]
    --with-feature:startup-improvements [Enabled by default: true]
    --with-feature:metrics-versioning [Enabled by default: true]
    --with-feature:sync-history [Enabled by default: true]
    --with-feature:sync-passwords [Enabled by default: true]
    --with-feature:tab-hibernation [Enabled by default: false]
    --with-feature:tools-custom-controls-style [Enabled by default: true]
    --with-feature:trees-in-bookmarks [Enabled by default: true]
    --with-feature:use-turbo2 [Enabled by default: false]
    --with-feature:use-turbo2-video-compression [Enabled by default: false]
    --with-feature:vibrancy-in-window-frame [Enabled by default: false]
    --with-feature:video-theme [Enabled by default: true]
    --with-feature:warn-for-unknown-root [Enabled by default: false]
    --with-feature:bookmark-thumbnails-direct-upload [Enabled by default: true]
    --with-feature:surf-easy-promotion [Enabled by default: true]
```

so there must be a way to concoct a launcher command with the --with-feature:    just a case of knowing which one to remove the cache on leaving

also asked for help on Opera forums :]

---

### Post by howefield on 2015-09-27
> **shantiq said:**
> ... the only thing i want removed is the cache so it loads up in crisper fashion not be so cumbersome [older machine] i do not want to remove other "memories" merely the cache  ....

Install [Download Chrome Extension]("https://addons.opera.com/en/extensions/details/download-chrome-extension-9/?display=en"), then install [Click&Clean]("https://chrome.google.com/webstore/detail/clickclean/ghgabhipcejejjmhhchfonmamedcbeod") extension. Seems to work pretty well giving decent control over what and when is cleaned.

---

### Post by shantiq on 2015-09-27
ok howefield seems to do the job will monitor it   thanx for tip   [i usually try and avoid extensions as slow-down always a possibility but we'll see]

i set it thus for my aims here  >>  

[ATTACH=CONFIG]264685[/ATTACH]

---

### Post by uninvolved on 2015-09-27
I've not seen this feature since they upgraded to using Chromium as their base. I've been an Opera user since the days when you had to pay for it. You mentioned that you wanted to avoid extensions but I've played with this one and it's rather light as it only does something when you tell it to. So, for what it's worth, there's this extension:
[https://addons.opera.com/en/extensions/details/close-clean/?display=en](https://addons.opera.com/en/extensions/details/close-clean/?display=en)

There may be some other extensions on the Chrome store and those will *generally* work just fine with Opera - there's even an extension to easy add Chrome extensions from the page - convoluted but easy enough nonetheless. But, as you said, you generally try to avoid them.

---

### Post by shantiq on 2015-09-27
thanx uninvolved   just seen your post looks good too  ...  will use click and clean for a while 
amzing what is available when you ask around :]    thanx to 
PS if opera forum shows up a route with --with-feature: to add to launcher will report

**edit**
hmmm only problem is click and clean and close all and clean do not work in the beta >>
so back to square one :]

[ATTACH=CONFIG]264690[/ATTACH]

---

### Post by uninvolved on 2015-09-27
It's strange, I'd completely missed howefield's reply. Anyhow, I've found that putting feature requests into the beta forum seems to be the best way to get noticed.

[http://forums.opera.com/categories/en-opera-beta-and-opera-developer](http://forums.opera.com/categories/en-opera-beta-and-opera-developer)

I'd asked to be able to sync more content (i'm constantly switching computers and distros) and it was implemented about a month later. They've not yet added the ability to sync extensions, however.

---

### Post by CantankRus on 2015-09-30
Try [**_[COLOR="#B22222"]History Eraser[/COLOR]_**]("https://addons.opera.com/en-gb/extensions/details/history-eraser/?display=en")
I use it to periodically start afresh.
You can choose what to erase and set it up to close Opera after cleaning so you can just use the
extension icon to clean and close Opera.

---

