---
title: "How to configure sensible-browser to use firefox instead of chrome?"
date: 2014-03-23
forum: General Help
---

### Post by dewdrop_world on 2014-03-23
Ah yes... it's been a while since I've had one of those wonderful Ubuntu moments, where I've just spent 30 minutes trying to figure out how to convince sensible-browser to open Firefox instead of Chrome, and have found no information of any use whatsoever.

Current state of the problem:

- Applications > System Tools > System Settings > Details > Default Applications already shows Firefox as the default browser. (Side note -- if one is looking for preferred or default applications, "Details" is not exactly the most intuitive place to look for it.)

- I've already set Firefox as the default in "sudo update-alternatives --config x-www-browser" as well. *But*... here's the problem... Chrome has a priority of 200 and Firefox has only 40.

```
$ sudo update-alternatives --config x-www-browser 
There are 3 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                       Priority   Status
------------------------------------------------------------
  0            /usr/bin/google-chrome      200       auto mode
  1            /usr/bin/epiphany-browser   85        manual mode
* 2            /usr/bin/firefox            40        manual mode
  3            /usr/bin/google-chrome      200       manual mode

Press enter to keep the current choice
[*], or type selection number: 2
```

"man update-alternatives" seems to assume that you already know how to use update-alternatives.

I am looking for a command that I can run to raise Firefox's priority here. I've already wasted half an hour on this and the update-alternatives options are *not* simple... Can somebody please just tell me what the answer is?

(In this case, I do actually need to influence the behavior of sensible-browser. I'm using org-mode in Emacs, and it uses sensible-browser for two things: opening http links, and displaying HTML export results.)

(Side note: Why does "Default Applications" ignore update-alternatives?)

hjh

---

### Post by mc4man on 2014-03-24
whether the priority is your issue no clue, sorta doubt, , plus there is also gnome-www-browser you could check, ect.
If you were to install the FF alt again you could raise it's priority #

I would *guess*  it would go something like this, ex. to 250 - 
```
sudo update-alternatives --install  /usr/bin/x-www-browser x-www-browser /usr/bin/firefox 250
```

As far as Details > Default... it just sets mimetypes, take a look in ~/.local/share/applications/mimetypes

---

### Post by claracc on 2014-03-24
Post number 4 in this thread: [http://ubuntuforums.org/showthread.php?t=1715582](http://ubuntuforums.org/showthread.php?t=1715582) addresses a solution which seems to work.

---

