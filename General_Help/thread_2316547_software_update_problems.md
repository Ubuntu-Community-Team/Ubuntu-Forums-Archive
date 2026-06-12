---
title: "software update problems"
date: 2016-03-09
forum: General Help
---

### Post by Saffo on 2016-03-09
Hello all,

So I am still new to Ubuntu so the more simple terms people could explain things in the better...
I tried to run software upgrade and it gave me the message "failed to download repository information". I've had this problem before so I knew that I had to disable one of the respositories (that's what those checkboxes in update manager are called, right?) It turned out the one that was causing the problem was google chrome. So I disabled the repository for chrome. But does this mean that now chrome won't be able to update?

Also, while I'm at it, sorry if this is a stupid question, but does running  sudo apt-get upgrade do the same thing as running software updater?

Thanks in advance!

S

---

### Post by v3.xx on 2016-03-09
Been hit with this?

[http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued](http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued)

---

### Post by slickymaster on 2016-03-09
> **Saffo said:**
> <---snip--->

Also, while I'm at it, sorry if this is a stupid question, but does running  sudo apt-get upgrade do the same thing as running software updater?

Thanks in advance!

S
No, it doesn't. **apt-get upgrade** doesn't handle changing dependencies between versions, so if a package has changed dependencies, it won't be upgraded and will be held back.

---

### Post by v3.xx on 2016-03-09
Running software updater is the same as using the terminal command ..

```
sudo apt-get dist-upgrade
```

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by pfeiffep on 2016-03-09
> **Saffo said:**
> Hello all,

So I am still new to Ubuntu so the more simple terms people could explain things in the better...
I tried to run software upgrade and it gave me the message "failed to download repository information". I've had this problem before so I knew that I had to disable one of the respositories (that's what those checkboxes in update manager are called, right?) It turned out the one that was causing the problem was google chrome. So I disabled the repository for chrome. But does this mean that now chrome won't be able to update?

Also, while I'm at it, sorry if this is a stupid question, but does running  sudo apt-get upgrade do the same thing as running software updater?

Thanks in advance!

S
No such thing as a stupid question :) Take a look at this [post]("http://ubuntuforums.org/showthread.php?t=2316177") it might help

Regarding [COLOR=#b22222]"sudo apt-get upgrade do the same thing as running software updater?" [/COLOR]run sudo apt-get update first

End results are the same - timing might be a bit different however read this for [more info]("http://askubuntu.com/questions/362872/is-using-software-updater-the-same-thing-as-running-apt-get-update-and-apt-get-u")

---

### Post by Dennis N on 2016-03-09
> But does this mean that now chrome won't be able to update?
Yes, I think so. I had the same error when updating (14.04). It refers to an i386 file for 32 bit version. My system is 64-bit. 

The Google software source is this:

**deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main**

So, is seems that one source must deliver both 32 and 64 bit versions. If we disable this source, we won't get the 64 bit-version either. If you leave it enabled, you get the error (until Google fixes their repo files), but the 64 bit version still upgrades.

The apt history log records it was updated despite the error:
chrome-stable:amd64 (48.0.2564.116-1, 49.0.2623.87-1)

---

