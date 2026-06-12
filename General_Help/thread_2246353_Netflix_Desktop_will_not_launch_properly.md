---
title: "Netflix Desktop will not launch properly"
date: 2014-09-30
forum: General Help
---

### Post by Dustin_Hamlin on 2014-09-30
Ok, so I've been at this for a few hours with no luck. Basically I want to install the Netflix Desktop app instead of using UserAgentSwitcher and Pipelight. The entire installation seems to go smooth but when I try to launch it I get this error. ```
Unable to test extended attributes at location '/home/dustin/.wine-browser'
```

---

### Post by slickymaster on 2014-09-30
Hi Dustin_Hamlin, welcome to the forums.

Have you tried to clear the wine browser directory and then re-installing:```
rm -rf ~/.wine-browser
sudo apt-get install --reinstall netflix-desktop
```

---

### Post by Dustin_Hamlin on 2014-09-30
> **slickymaster said:**
> Hi Dustin_Hamlin, welcome to the forums.

Have you tried to clear the wine browser directory and then re-installing:```
rm -rf ~/.wine-browser
sudo apt-get install --reinstall netflix-desktop
```

Thanks for the welcome.
Well I tried the codes you gave me and still the same error when I attempt to launch it.

---

### Post by Dustin_Hamlin on 2014-09-30
Also if it helps, when i try to launch netflix from the terminal i get this in response after the normal error

```
Traceback (most recent call last):
  File "/usr/share/wine-browser-installer/test-xattr", line 3, in <module>
    import xattr
ImportError: No module named xattr


** (zenity:3677): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-r38KYdMFjN: Connection refused
```

---

### Post by slickymaster on 2014-09-30
You could try the workarounds present at [https://answers.launchpad.net/netflix-desktop/+question/247743](https://answers.launchpad.net/netflix-desktop/+question/247743) to see if any of them might work for you.

---

### Post by Dustin_Hamlin on 2014-09-30
Well I tried this response:

> [COLOR=#333333][FONT=Ubuntu]Well, you could try copying /usr/bin/wine-browser to another place (like your home directory) and then add a line after these two lines:
"${PKG_DIR}/test-xattr" "${WINEPREFIX}";
XATTR="$?";
to read something like:
echo "${PKG_DIR}/test-xattr ${WINEPREFIX}: $XATTR";[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]That should give us a better idea as to why it's failing.[/FONT][/COLOR]


But when I try to use that copy of wine-browser to launch netflix it doesn't do anything. Got any idea why? If not im just gonna have to resort to useragentswitcher and pipelight

---

### Post by slickymaster on 2014-09-30
> **Dustin_Hamlin said:**
> <---snip--->
But when I try to use that copy of wine-browser to launch netflix it doesn't do anything. Got any idea why? If not im just gonna have to resort to useragentswitcher and pipelight

I think you'll need to install a User Agent switcher otherwise you will get some weird errors with Netflix. The required instructions for doing it are described here: [https://answers.launchpad.net/pipelight/+faq/2351](https://answers.launchpad.net/pipelight/+faq/2351)

---

### Post by sammiev on 2014-09-30
Have you tried this [method]("http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins") yet using HTML5.

---

