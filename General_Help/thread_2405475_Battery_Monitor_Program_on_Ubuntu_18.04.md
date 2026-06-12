---
title: "Battery Monitor Program on Ubuntu 18.04"
date: 2018-11-06
forum: General Help
---

### Post by michael-goose on 2018-11-06
I have tried to install Battery Monitor on Ubuntu 18.04 on my Lenovo S300 Ideapad but, although to icon appears in Applications and in the Startup panel, it will not launch. Any idea what I might have done wrong and any suggestions on how to proceed would be greatly appreciated. Regards

---

### Post by #&amp;thj^% on 2018-11-06
Try running it in the terminal
```
battery-monitor

```

---

### Post by michael-goose on 2018-11-06
Yes, tried that but it just gives the following response:- <pre>Traceback (most recent call last):  File &quot;/usr/share/battery-monitor/run.py&quot;, line 14, in &lt;module&gt;
    from AppIndicator import AppIndicator
  File &quot;/usr/share/battery-monitor/AppIndicator.py&quot;, line 10, in &lt;module&gt;
    gi.require_version(&apos;AppIndicator3&apos;, &apos;0.1&apos;)
  File &quot;/usr/lib/python3/dist-packages/gi/__init__.py&quot;, line 130, in require_version
    raise ValueError(&apos;Namespace %s not available&apos; % namespace)
ValueError: Namespace AppIndicator3 not available
</pre>

Unfortunately, I have no idea what this means. Thanks for your response. Regards

---

### Post by #&amp;thj^% on 2018-11-06
Looks like the dev needs to to update "Battery Monitor" for 18.04.
You can also use Gnome-Tweak-Tool to show your battery level via:
```
sudo apt install gnome-tweaks
```
Then launch the tool, navigate to "Top Bar" settings page. There you can see the option for turning on / off battery percentage.
Or if your dead-set on battery-monitor you may have better luck adding a PPA:
> Let's install from PPA (currently supported: 14.04, 17.10 & 18.04; we're struggling with Ubuntu 16.04 right now):
```

sudo add-apt-repository ppa:maateen/battery-monitor -y

sudo apt-get update

sudo apt-get install battery-monitor -y
```
Let us know how it works.

---

### Post by michael-goose on 2018-11-06
Thank you again for your response. I had already tweaked Gnome to show battery percentage but wanted something more to avoid running the battery flat. I had also tried installing via ppa, as you suggested. I have just reinstalled again following your instructions but, unfortunately, with the same result, ie. it does not launch and gives the message I reported previously. I wondered if it was missing a dependency but does not report that. So at the moment I'm stuck for any other ideas. Regards

---

### Post by #&amp;thj^% on 2018-11-06
I got it installed on my system with the ppa via:
```

sudo apt install  acpi python3 python3-gi python3-setuptools libnotify4 libappindicator3-1 gir1.2-appindicator3-0.1
```
And then:
```
sudo apt install battery-monitor
```
Now shows:
```
 apt policy battery-monitor
battery-monitor:
  Installed: 0.6-beta-4-bionic
  Candidate: 0.6-beta-4-bionic
  Version table:
 *** 0.6-beta-4-bionic 500
        500 http://ppa.launchpad.net/maateen/battery-monitor/ubuntu bionic/main amd64 Packages
        500 http://ppa.launchpad.net/maateen/battery-monitor/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by michael-goose on 2018-11-06
Yes! It now works. Thank you so much for your help and guidance. Regards.

---

