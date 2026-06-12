---
title: "Digikam: Cannot access file ././/share/alsa/alsa.conf"
date: 2018-06-06
forum: General Help
---

### Post by Ralph L on 2018-06-06
I am installing Xubuntu 18.04.  Previously I have run the appimage version of Digikam on Xubuntu 17.04.  When I try to run the exact same version of Digikam (digikam-5.9.0-20180217T042522-x86-64.appimage) on Xubuntu 18.04., I get a series of error messages:```
ALSA lib conf.c:3750:(snd_config_update_r) Cannot access file ././/share/alsa/alsa.conf
ALSA lib control.c:954:(snd_ctl_open_noupdate) Invalid CTL hw:0
AL lib: alsa.c:257: control open (0): No such file or directory
ALSA lib conf.c:3750:(snd_config_update_r) Cannot access file ././/share/alsa/alsa.conf
ALSA lib control.c:954:(snd_ctl_open_noupdate) Invalid CTL hw:0
digikam: src/hostapi/alsa/pa_linux_alsa.c:1454: BuildDeviceList: Assertion `devIdx < numDeviceNames' failed.
/tmp/.mount_digikaQTUFnQ/AppRun: line 73:  1304 Aborted                 (core dumped) digikam $@

```The file /usr/share/alsa/alsa.conf does exist in my system.  However, I don't know what "././/" means, so I don't know for sure what file digikam is looking for.

 Can somebody give me advice on how to fix this problem???

---

### Post by yapidumoac on 2018-06-07
> **Ralph L said:**
> The file /usr/share/alsa/alsa.conf does exist in my system.  However, I don't know what "././/" means, so I don't know for sure what file digikam is looking for.

[COLOR=#000000]"././/" means in the current directory. [/COLOR][COLOR=#000000][FONT=&amp]The current directory presumably being your home directory. [/FONT][/COLOR][COLOR=#000000]So it's looking for a file off of $home/[/COLOR][COLOR=#000000][FONT=&amp]share/alsa/alsa.conf and not finding it.[/FONT][/COLOR]

---

### Post by Ralph L on 2018-06-07
yapidumoac 
Thank you for responding so quickly.  I solved the problem by downloading a later version of Digikam appimage ([http://digikam.1695700.n4.nabble.com/digiKam-users-Digikam-Cannot-access-file-share-alsa-alsa-conf-td4705967.html](http://digikam.1695700.n4.nabble.com/digiKam-users-Digikam-Cannot-access-file-share-alsa-alsa-conf-td4705967.html) and [https://files.kde.org/digikam/](https://files.kde.org/digikam/)).
Back to the notation "././/" . Can you point me to any manual or write-up that discusses this.  I thought that "." stood for present directory, and "./" merely added a slash in the path to the folder or file of interest.  I don't see the need for the additional ".//".  Is this something from Internet standards, or something else non-linux??
Any help appreciated....

---

### Post by Holger_Gehrke on 2018-06-08
That path was assembled from pieces by the program. Multiple path separators get discarded. It's not really an error in programming, more likely a minor bit of carelessness in the configuration of the package.

Holger

---

### Post by Ralph L on 2018-06-08
Holger_Gehrke
Thank you very much.  I learned a lot from this little exercise and your explanation.  It helped demystify several things.

Also, regarding my original problem of not being able to get Digikam appimage running on Xubuntu 18.04, this site explains the problem:  [http://digikam.1695700.n4.nabble.com/digiKam-users-Digikam-Cannot-access-file-share-alsa-alsa-conf-td4705967.html](http://digikam.1695700.n4.nabble.com/digiKam-users-Digikam-Cannot-access-file-share-alsa-alsa-conf-td4705967.html) The solution was to load Digikam 6.0.0 appimage at [https://files.kde.org/digikam/](https://files.kde.org/digikam/).

Ralph

---

