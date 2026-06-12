---
title: "Show all startup applications?"
date: 2014-06-24
forum: General Help
---

### Post by psfal on 2014-06-24
I caught a Nixie Pixel video quite some time ago which told how to show all startup applications, this worked and I was able to stop all the apps I didn't want starting at login in 12.04. I've tried on newer installs of 12.04 and it no longer works...

This is what worked before but no longer:
[COLOR=#333333][FONT=arial]sudo sed -i "s/NoDisplay=true/NoDisplay=false/g[/FONT][/COLOR][COLOR=#333333][FONT=arial]*" /etc/xdg/autostart/*.desktop

How would I get all my startup applications to show now? I like to shut down all the bells and whistles that I don't use[/FONT][/COLOR]

---

### Post by grumblebum2 on 2014-06-24
This is similar but you change directory(cd) first then run the command to change to "NoDisplay=**false**".
```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

---

### Post by psfal on 2014-06-24
Thanks very much, I appreciate the help, that's what I needed :-)

---

### Post by grumblebum2 on 2014-06-24
> **psfal said:**
> Thanks very much, I appreciate the help, that's what I needed :-)
Search found your command except without the "*" after "[COLOR="#FF0000"]g[/COLOR]"
[https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications)

```
sudo sed -i "s/NoDisplay=true/NoDisplay=false/[COLOR="#FF0000"]g[/COLOR]" /etc/xdg/autostart/*.desktop
```

Don't know sed but maybe that was the problem.

---

