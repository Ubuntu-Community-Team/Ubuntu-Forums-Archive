---
title: "Preferred applications issue"
date: 2019-03-18
forum: General Help
---

### Post by raleigh3 on 2019-03-18
I want to select Firefox for my default browser using Preferred Applications. Ubuntu Mate 18.04

However, Seamonkey is my only pick.

Don't know if this is relevant, but my Firefox was not installed via synpatic or apt get install.

---

### Post by #&amp;thj^% on 2019-03-19
This could be important, is the firefox the pre-installed version?
If so this should work.
If your preferred browser isn't in the preferred app menu >> you can do it from the command line, this command will let you do the same thing:
Example only;
```

xdg-settings set default-web-browser name-of-browser.desktop
```

For firefox:
```

xdg-settings set default-web-browser firefox.desktop
```

or Chromium:
```

xdg-settings set default-web-browser chromium-browser.desktop
```

or Chrome:
```

xdg-settings set default-web-browser google-chrome.desktop
```

---

### Post by raleigh3 on 2019-03-19
I do not understand 

```
This could be important, is the firefox the pre-installed version?
```

I run it from a launcher.

"/home/andy/Firefox_ ESR_ Ver_ 52.5.0/firefox/firefox-bin"

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=/home/andy/ICONS/Firefox_ESR_Icon.png
Icon[en_US]=mate-panel-launcher
Exec="/home/andy/Firefox_ ESR_ Ver_ 52.5.0/firefox/firefox-bin"
Name[en_US]=Firefox ESR
Name=Firefox ESR
```

---

### Post by #&amp;thj^% on 2019-03-19
> **raleigh3 said:**
> I do not understand 

```
This could be important, is the firefox the pre-installed version?
```


That meant firefox from the original Ubuntu-Mate installer.;)
Firefox ESR is not that.
Next can you tell us how you installed your Firefox ESR?
Might as well included this also:
```
which firefox
whereis firefox
```
have you tried setting it with Firefox ESR in >>Edit..>Preferences.> Set As Default.
>>

---

### Post by raleigh3 on 2019-03-19
I installed FF from firefox-52.5.0esr.tar.bz2.

It is located here.

```
/home/andy/Firefox_ ESR_ Ver_ 52.5.0/firefox/
```

```
andy@7_~/Downloads$ which firefox
andy@7_~/Downloads$ which firefox
andy@7_~/Downloads$ whereis firefox
firefox: /usr/lib/firefox /etc/firefox
```

Firefox will not let me set it as the default browser.

Any way to have Go Advanced set as the default?

---

### Post by #&amp;thj^% on 2019-03-20
If you want to keep it safe and up to date, I would add the PPA to the mix: [https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)
This PPA is alaways current:
```
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt update
sudo apt install firefox-esr
```
Current version is, "60.6.0esr"
[list]
[*]However, This new version does not support LEGACY ADDONS.[/list]
Now you can set it as default with:
```
sudo update-alternatives --config x-www-browser
```
A sample of this shows something like:
```
sudo update-alternatives --config x-www-browser 
There are 3 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                    Priority   Status
------------------------------------------------------------
  0            /usr/bin/google-chrome   200       auto mode
* 1            /usr/bin/firefox         40        manual mode
  2            /usr/bin/google-chrome   200       manual mode
  3            /usr/bin/opera           90        manual mode

    Press enter to keep the default[*].

```

    Right now I have firefox as my default web browser

---

### Post by raleigh3 on 2019-03-20
My point in going to version 52 was the ability to use legacy addons such as ReminderFox.

It is worth the small inconveniences.

---

### Post by #&amp;thj^% on 2019-03-20
As you wish, but I would keep my eyes peeled on this then: [https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox-esr/](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox-esr/)

---

### Post by raleigh3 on 2019-03-20
Thanks.

---

