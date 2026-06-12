---
title: "Installing Flash for Chromium Web Browser"
date: 2014-11-28
forum: General Help
---

### Post by michael-piziak on 2014-11-28
I was prompted and downloaded the "install_flash_player_11_linux.x86_64.tar.gz"  for Chromium, but what do I do with the file?

Or is there a way through the software center to get it    (or a Terminal command line)  ?

---

### Post by Bucky Ball on 2014-11-28
Are you using 14.04? If so a tool to install flash is in the repos (software Centre). This makes it easy. (I am unsure if this tool is available in 12.04 as not using it).

Look for 'pepperflashplugin-nonfree' in Software Centre, or:

```
sudo apt-get install pepperflashplugin-nonfree
```

... in a terminal.

Good luck. ;)

---

### Post by michael-piziak on 2014-11-28
I got it from the software center.   It said to run a terminal code line, but that line wouldn't work.

But I think the flash IS working with Chromium, even though the terminal code line wouldn't take.

---

### Post by ajgreeny on 2014-11-29
You can easily see if flash is installed in chromium by typing chrome://plugins in the locationbar at the top.  It should show something like
> Adobe Flash Player - Version: 15.0.0.239
Shockwave Flash 15.0 r0
Name:    Shockwave Flash
Description:    Shockwave Flash 15.0 r0
Version:    15.0.0.239

Disable &#65532; Always allowed?
What do you mean by "terminal code line wouldn't take."?  If there was no output or errors from the command it did work.
Which package did you install from the software-centre?  You need the **pepperflashplugin-nonfree** not adobe-flashplugin, which will not work in chromium.

---

### Post by michael-piziak on 2014-11-29
Thanks,
I got the pepperflashplugin-nonfree
Everything is working now - it does say [COLOR=#000000][I]Adobe Flash Player - Version: 15.0.0.239

[/I]Concerning the terminal code line that wouldn't take.  When I installed pepper flash nonfree from the Software Center, at the end it said to run a code in terminal to make it work - my terminal did report back an error, but it still works when I test the browsers.

Cheers[/COLOR]

---

### Post by ajgreeny on 2014-11-29
Presumably you can't remember the error?

---

### Post by michael-piziak on 2014-11-29
After allowing software center to install it, then it says it is run from terminal with this command line:

update-pepperflashplugin-nonfree

The error reported in terminal when putting that line in is:

Error Must Be Root

---

### Post by nerdtron on 2014-11-29
> update-pepperflashplugin-nonfree

The error reported in terminal when putting that line in is:

Error Must Be Root


Ah yes... When you encounter error like this, prefix the command with the word sudo.
```
sudo update-pepperflashplugin-nonfree
```

It won't do anything though since it is already working.

---

### Post by michael-piziak on 2014-11-29
I typed that in and all it did was report:

Usage:
  update-pepperflashplugin-nonfree --install
  update-pepperflashplugin-nonfree --uninstall
  update-pepperflashplugin-nonfree --status
Additional options:
  --verbose
  --quiet


I suppose one should do a **sudo update-pepperflashplugin-nonfree --install **because typing in **update-pepperflashplugin-nonfree --install **didn't do anything.

---

