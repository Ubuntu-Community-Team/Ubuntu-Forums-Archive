---
title: "Open folder as Admin/Root?"
date: 2014-08-27
forum: General Help
---

### Post by 2CV67 on 2014-08-27
I am just trying to get a new PC running with Ubuntu 14.04.1 Unity.

With previous versions, including 14.04 Xfce, it was easy to get a right-click option to "Open as Root".

I can't see how to do this with current Unity.

Thanks for any help!

---

### Post by nerdtron on 2014-08-27
It's because of different file manager Thunar in Xfce and Nautilus in Unity.

Anyway, try running "gksudo nautilus", you should be prompted for you password and will open nautilus as root user.

---

### Post by 2CV67 on 2014-08-29
Thanks for that suggestion.
gksudo nautilus does work, so I could do the job I wanted, but not without some reserves.

I get a bunch of warnings when using this method:

```
chris@Aspire-TC:~$ sudo gksu nautilus
[sudo] password for chris: 

(nautilus:2739): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(nautilus:2739): GLib-CRITICAL **: Source ID 112 was not found when attempting to remove it

(nautilus:2739): GLib-CRITICAL **: Source ID 113 was not found when attempting to remove it

(nautilus:2739): GLib-CRITICAL **: Source ID 114 was not found when attempting to remove it
chris@Aspire-TC:~$
```

Realizing that "Files" is actually Nautilus (it doesn't say so in "About") then I remembered Nautilus Actions from my pre-xfce days.
So I installed Nautilus Actions with Synapt & set up an action as described here:
[http://ubuntuforums.org/showthread.php?t=2148346](http://ubuntuforums.org/showthread.php?t=2148346)

In fact I tried both parameters suggested (nautilus %d/%w & xdg-open %f) and get similar results.
It does work, but I have to wait 45 seconds for the password prompt to appear, which seems altogether too long.

Suggestions for all above problems welcome!

Thanks!

---

### Post by nerdtron on 2014-08-31
Hmmm...
gksudo is different from gksu, but what you can try both. And if for some warnings like that, those are normal. Not sure about the 45secs wait time though.

---

### Post by 2CV67 on 2014-08-31
Hey! Thanks for your continuing interest!

In the last couple of days, I just about managed to get most of my new installation how I wanted, but with various error messages, so I guessed I had corrupted things along the way.

So I wiped everything & started the installation again from scratch, but avoiding the things which had seemed problematic.

In my new clean set-up, both the "gksudo nautilus" command in the terminal and the Nautilus-Actions method work well, with no big delays.

I see now that I was previously using "sudo gksu nautilus" not "gksudo nautilus".
Not sure how that happened.
If I try "sudo gksu nautilus" again, I do still get error messages as above, but with "gksudo nautilus" - no problem.

So I will call this item 'SOLVED' now.

Thanks again for your help! :D

---

