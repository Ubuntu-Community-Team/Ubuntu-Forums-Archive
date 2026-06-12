---
title: "Firefox won't work"
date: 2005-09-24
forum: General Help
---

### Post by Goober on 2005-09-24
Hello,

I have run into a problem which might quickly become a crisis.  Firefox refuses to work for me in Linux.  I am in XP, typing this, unfortunately.  I have no clue why, but Firefox literally will not open in Linux.  I have a little round blue button for it on my top bar, I click it, nothing happens.  i see the square black lines for a sec, like something is opening, but nothing happens.

I go to Applications -> Internet -> Firefox, click that, nada.  The little arrow mouse button turns into the little spinning wheel, I see a box at the bottom bar that says "Starting Firefox", then nothing happens.

I remember installing some Updates last night, but no clue what they were.  They might have been related to Firefox, but I have honestly gotten so used to just clicking "Update", and letting Linux happily install them that I don't read them anymore.  Perhaps there was a faulty Update for Firefox?

Anyway, this is a big problem for me because I have bookmarks only on my Linux in Firefox that I have to be able to open.  I would appreciate help, please.

Thanks in advance,
Goober.

Also, a different Internet Browser other then Firefox would be ok, but i would prefer to get Firefox working again.

---

### Post by greenstar on 2005-09-24
open a console window and enter:

```
firefox
```

---

### Post by Goober on 2005-09-24
[QUOTE=greenstar]open a console window and enter:

```
firefox
```[/QUOTE]
 I tried that.  Nothing happened.  Literally.  

i managed to install Konquerer, so I can at least access the web in Linux, but I still kinda need back Firefox.  There are 2 Updates availble, "mozilla-firefox", and "mozilla-firefox-gnome-support", both are version 1.07-0ubuntu0.1, but neither will install.  They download, but then it gives me the following error:

"E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support"

And I had a Terminal open, which said nothing.

Umm, anybody have any suggestions?  I do want to keep my bookmarks as well, if all possible.  i did search, and apparently this is a re-occuring error, but the only solution seems to be wipe out Firefox, and i really wanna save my bookmarks.  is this possible?

---

### Post by professor_chaos on 2005-09-24
I had the same thing happen after the recent upgade. Had to uninstall mozilla and mozilla-gnome-support, and then reinstall. Bookmarks and settings were preserved (don't do complete removal when removing). If your worried, make a copy of your ~/.mozilla directory.

---

### Post by greenstar on 2005-09-24
prof_chaos:> I had the same thing happen after the recent upgade. Had to uninstall mozilla and mozilla-gnome-support, and then reinstall. Bookmarks and settings were preserved (don't do complete removal when removing). If your worried, make a copy of your ~/.mozilla directory. 

I am confirming what he said. I had the same experience. Go for it. My bookmarks are still here, even my Sessionsaver restored the last session - including this thread, everything still works.

greenstar

---

### Post by Goober on 2005-09-25
Ok, it worked.  I typed in something I read on a different page, something like sudo apt-get uninstall mozilla-firefox, and then sudo apt-get install mozilla-firefox.  

Then restart.  It comes back with bookmarks, everything.  Thanks for the help, guys.  Gave me a lovely little Saturday night heart attack.

I am not going to upgrade again until Breezy.  No point, its so close.  Time to save my precious Bookmarks . . .

---

### Post by danhm on 2005-09-25
[QUOTE=Goober]Ok, it worked.  I typed in something I read on a different page, something like sudo apt-get uninstall mozilla-firefox, and then sudo apt-get install mozilla-firefox.  

Then restart.  It comes back with bookmarks, everything.  Thanks for the help, guys.  Gave me a lovely little Saturday night heart attack.

I am not going to upgrade again until Breezy.  No point, its so close.  Time to save my precious Bookmarks . . .[/QUOTE]
 I'm getting the same problem. However, when I try to remove Firefox via synaptic, I get the same error of:

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support



Any suggestions? I'm using Opera for the meantime. It's cool....but no StumbleUpon or Adblock!


EDIT - I just tried "sudo apt-get remove mozilla-firefox" in the terminal and got this error:
dan@ubuntu:~$ sudo apt-get remove mozilla-firefox
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  firefox firefox-gnome-support mozilla-firefox mozilla-firefox-gnome-support
  mozilla-mplayer ubuntu-desktop yelp
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
2 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by Goober on 2005-09-25
Hrm, that could work, I never thought to use Synpatic to try and fix things.  I don't actually use Synaptic.  Never have, actually.  I prefer the Command Line in the terminal.

Try logging in as the Root.  That works sometimes if the regular command line doesn't.

And there is an Opera for Linux?  Cool . . .

---

### Post by garak on 2005-09-25
I have same problem.
Same error from synaptic.
So, tried to remove packages firefox and mozilla-firefox, then install again mozilla-firefox.
Now, Firefox doesn't start.
I tried this
```
/usr/lib/mozilla-firefox/firefox-bin --g-fatal-warnings
``` 
and got this

/usr/lib/mozilla-firefox/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

---

### Post by greenstar on 2005-09-25
use apt-get at the command line

```
sudo apt-get remove mozilla-firefox 
sudo apt-get remove mozilla-firefox-gnome-support 
sudo apt-get remove firefox 
sudo apt-get remove ubuntu-desktop
``` 

You will only need to enter all 4 of the above if the first command doesn't remove all of them.

```
sudo apt-get install mozilla-firefox 
sudo apt-get install mozilla-firefox-gnome-support 
sudo apt-get install firefox 
sudo apt-get install ubuntu-desktop
``` 

I also found that a package called yelp was uninstalled with mozilla-firefox, so if that happens, just apt-get install it also.

```
sudo apt-get install yelp
```

I'm not sure that _all_ of these are necessary, but that's what got my firefox back up and running smoothly. Your mileage may vary.

Hope this helps.

greenstar

---

### Post by RadixLecti on 2005-09-25
[QUOTE=garak]I have same problem.
Same error from synaptic.
So, tried to remove packages firefox and mozilla-firefox, then install again mozilla-firefox.
Now, Firefox doesn't start.
I tried this
```
/usr/lib/mozilla-firefox/firefox-bin --g-fatal-warnings
``` 
and got this

/usr/lib/mozilla-firefox/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory[/QUOTE]
 I've alread tried uninstalling and reinstalling mozilla-firefox and gnome support...
And I still get the same problem.

Thinking about a complete reinstall, but since the repos are down, I think I'll wait. ;-)

---

### Post by danhm on 2005-09-25
[QUOTE=Goober]Hrm, that could work, I never thought to use Synpatic to try and fix things.  I don't actually use Synaptic.  Never have, actually.  I prefer the Command Line in the terminal.

Try logging in as the Root.  That works sometimes if the regular command line doesn't.

And there is an Opera for Linux?  Cool . . .[/QUOTE]

Yeah, it went free (price-wise) a few days ago. It's also on FreeBSD, Solaris, and a few others.


And sudo apt-get remove mozilla-firefox worked without error this time. There was a reboot between this try and my last one, because I went to go play a game in XP.

---

