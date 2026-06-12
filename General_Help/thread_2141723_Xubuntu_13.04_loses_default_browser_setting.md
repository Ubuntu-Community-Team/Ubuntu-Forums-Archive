---
title: "Xubuntu 13.04 loses default browser setting"
date: 2013-05-03
forum: General Help
---

### Post by VideoRoy on 2013-05-03
I just switched to Xubuntu 13.04 and really like the experience on my older HP Mini Netbook.

One annoying problem I am having is that every once in a while Xubuntu will forget it has a default browser.  To be clear it is not setting the wrong the default browser it does not know that any default browser was previously set.

I use Chrome but still have Firefox installed.  I rarely use FF and may eventually uninstall but I always have a backup browser installed for the cases when pages will not render correctly or some other quirk.

When Xubuntu forgets it has a default browser, I can go into Settings -->Preferred Applications and the browser setting is blank.  I can launch Chrome and it said it is not the default browser and if I launch Firefox it also says it is not the default browser.

This does not happen all the time or after every reboot but just often enough to be annoying.

Any ideas or suggestions of places to check is appreciated.

---

### Post by pqwoerituytrueiwoq on 2013-05-03
are you sure you did not click yes on a "XXX is not your default browser..." message
i have not had any issue with it on 13.04
using chromium and firefox, i have a custom script set as the default browser

---

### Post by VideoRoy on 2013-05-03
> **pqwoerituytrueiwoq said:**
> are you sure you did not click yes on a "XXX is not your default browser..." message
i have not had any issue with it on 13.04
using chromium and firefox, i have a custom script set as the default browser

Thanks for the reply.

No, I do not think I have even seen that particular message.  I am fairly confident it actually has nothing to do with the browser settings at this point but something within xubuntu itself.

One clue I have now is that it might be related to the widget on the panel dock where you go set which browser is the default so it launches that one.  Similar to the Music player and Email client.  When I first installed it did not seem to "stick" and I ended up removing the dock panel for other reasons as well.  I am now using cario dock but I was going to go find that browser widget in the menu and see what it thinks the browser is if any.

One other clue is that I notice that the Settings --> Preferred Applications setting for default browser can get out of sync with actual default browser.  During troubleshooting I had changed default browser there in Settings but then launch Firefox as a test and set it to default.  The Settings still said Chrome even though it was Firefox.

Not a horrible problem just annoying.

---

### Post by VideoRoy on 2013-05-03
Now I have completely messed it up.

The problem does stem from the Web Browser Helper or whatever it is called.  I launched it and set Chrome as default in that application box.  Then when Chrome launches it says it it not the default so I set it there.  Then I go to Settings and it says no application set, so I set it there.

Now I launch Chrome and it says it is not default so I set it.  Then go back to Settings and it is now removed the setting there and it is an endless loop.

I have deleted the "Helper" app Icon and not using that any more. Do not need it anyway.

I have deleted the helper files in ~/.local/xcfe4/helpers and let them get recreated but no luck.  The settings in either Chrome itself or Settings are mutually exclusive and I cannot get them back in sync.

This will only be a problem when I launch a link from email or some other application it will just continually ask for which browser to launch.

Very weird behavior and all these helpers and defaults do not play nice together.

---

### Post by pqwoerituytrueiwoq on 2013-05-03
```
exo-open --launch WebBrowser %u
exo-open --launch MailReader %u
exo-open --launch TerminalEmulator
```
those are the launder commands
i don't have a [FONT=courier new]~/.local/xcfe4/helpers[/FONT] file and i am using 13.04
i do have a [FONT=courier new]~/.config/xfce4/helpers[/FONT] file, that file does not define by browser it just says it is a custom one
i do have a [FONT=courier new]~/.local/share/xfce4/helpers[/FONT] folder that contains a launcher for my custom browser setting

---

### Post by VideoRoy on 2013-05-03
> **pqwoerituytrueiwoq said:**
> ```
exo-open --launch WebBrowser %u
exo-open --launch MailReader %u
exo-open --launch TerminalEmulator
```
those are the launder commands
i don't have a [FONT=courier new]~/.local/xcfe4/helpers[/FONT] file and i am using 13.04
i do have a [FONT=courier new]~/.config/xfce4/helpers[/FONT] file, that file does not define by browser it just says it is a custom one
i do have a [FONT=courier new]~/.local/share/xfce4/helpers[/FONT] folder that contains a launcher for my custom browser setting

You are right I messed up my path and it was ~/.local/share/xfce4/helpers

Thanks I will give that a try if I have more trouble but here is how I finally solved it.

1. Edited ~/.local/share/applications/mimeapp.list and replaced firefox.desktop with google-chrome.desktop in every place.
2. Settings -->Preferred Applications and set browser to google-chrome
3. Launch Chrome and when it asks to set to default select "Do Not Ask Anymore"
4. Optional launch Firefox and tell it not to ask any more either.

This fixed nagging Chrome asking to be default and when I launch any hyperlink Chrome is launched.

Very messed up config on Xubuntu.  Never had this problem after 8 releases of Ubuntu but Xubuntu is still better.:P

BTW at the end both Chrome and Firefox thought they were default but I have fixed it so neither now thinks they are the default by following these 4 steps.

---

### Post by Dennis N on 2013-05-03
You could try setting the default browser defined in /etc/alternatives and see how that works out.

Use the "Alternatives Configurator" (pkg: galternatives) unless you are handy with the update-alternatives command.

Essentially you are changing this link: 

(from my Xubuntu 12.04) symbolic link to default:

[B]lrwxrwxrwx 1 root root  16 May 21  2012 x-www-browser -> /usr/bin/firefox
[/B]

---

### Post by VideoRoy on 2013-05-03
Thank you.  If this last work around does not help I will give a shot too.

BTW, I completed uninstalled Firefox at one point and it made no difference at all.  The problem I see is that in Xubuntu there are 3 possible ways to set a default browser and none of them are in sync with each other.  That would be OK although bad form if it were not for the fact one setting affects the others but not all of the default settings are for the same purpose if that makes sense.

---

### Post by Dennis N on 2013-05-03
> **VideoRoy said:**
> Thank you.  If this last work around does not help I will give a shot too.

BTW, I completed uninstalled Firefox at one point and it made no difference at all.  The problem I see is that in Xubuntu there are 3 possible ways to set a default browser and none of them are in sync with each other.  That would be OK although bad form if it were not for the fact one setting affects the others but not all of the default settings are for the same purpose if that makes sense.

The "Alternatives Configurator" (package name: galternatives)  is pretty easy to use: after installing galternatives from the Ubuntu repositories, just select **x-www-browser** from the list on the left, and then in the right, mark the little circle in the 'choice' column before your desired default browser, and close the window. You can ignore the 'priority' column. Behind the scenes, it will take care of the details.

---

### Post by VideoRoy on 2013-05-10
I just wanted to follow up on this that my system has been working fine now for a week once I made the tweaks I listed in my post.  Also out of curiosity I loaded Alternatives Configurator and when I checked x-www-browser, it was already set to the correct browser for me which is Chrome.  Not sure what it would have said before I made the manual tweaks.

---

