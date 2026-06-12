---
title: "Flash install"
date: 2007-02-21
forum: General Help
---

### Post by JimS on 2007-02-21
...Need Flash 8 or higher.
How to install in Breezy using dowload from
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
....

---

### Post by taurus on 2007-02-21
You can try this guide

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

or

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by llamakc on 2007-02-21
answered above

---

### Post by JimS on 2007-02-21
...
Many thanks for you help.
I had to leave for a while.

Tried the psychocats solution a couple of hours ago and ran into a problem.
Then I rebooted to see if Flash would run and lost error message.

The line
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
did not work.  
Something about not finding a folder - I think.
I ran the line after that and it worked.
I didn't do the last 2 lines (cleanup).

Flash didn't (completely) install.

Now that I am back, I would like to continue toward a solution of installing Flash.
Help is appreciated.
...

---

### Post by llamakc on 2007-02-21
Why would you reboot? You never have to reboot for userspace problems. Never.

When you open Firefox and type "about:plugins" do you see

> 
Shockwave Flash
 File name:  libflashplayer.so Shockwave Flash 9.0 r31   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes
If so, it is installed. If not cp the libflashplayer.so into ~/.mozilla/plugins/ and restart Firefox.

---

### Post by taurus on 2007-02-21
> **JimS said:**
> ...
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/

You need to be in right right directory when you issue that command; that's why you got that error message about not finding libflashplayer.so.

Try something like

```
cd ~/Desktop
cd install_flash_player_9_linux
mv libflashplayer.so ~/.mozilla/plugins
```
Open firefox and see if you have flash.

---

### Post by JimS on 2007-04-14
...
Issue Resolved.

I had to kill the Breezy Badger as the old boy
was just too beat up - too many scars,
too difficult for me to heal with my too few skills.

I made a seperate Home partition,
successfully populated it,
following Psychocats directions,
thinking I should then reinstall Breezy.
But couldn't log in or install,
so I killed Breezy
by installing Edgy.
Flash then installed without issue.

Thanks,
JimS
[email]workfromhome@pobox.com[/email]
...

---

