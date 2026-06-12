---
title: "Suddenly can't get into Gnome"
date: 2006-12-10
forum: General Help
---

### Post by jhenager on 2006-12-10
I am getting a message right after I see the window manager loading. Something like 'Your login session lasted less than ten seconds' and suggested either a configuration problem or low disk space.
I got into Failsafe Terminal and blew away a bunch of downloads, including a rescue iso, the partimage iso, and another file I know was 300 MB, but still am getting the error.
Any hints?:-k

---

### Post by mayonaise15 on 2006-12-10
Have you changed any permissions in your home directory lately?

---

### Post by GrumpyBob on 2006-12-10
Isn't this something to do with .ICEauthority?  Try searching the forums...I'm sure this was the solution when this happened to me some years ago.  Perhaps someone with a better memory or more experience could advise?

Edit: [http://ubuntuforums.org/showthread.php?t=191358&highlight=Your+login+session+lasted+less+than+ten+seconds](http://ubuntuforums.org/showthread.php?t=191358&highlight=Your+login+session+lasted+less+than+ten+seconds) suggests deleting .ICEauthority from the failsafe login.  The file gets recreated when you login to gnome.

Robert

---

### Post by jhenager on 2006-12-12
No, no permission changes at all.

---

### Post by jhenager on 2006-12-12
> **GrumpyBob said:**
> Isn't this something to do with .ICEauthority?  Try searching the forums...I'm sure this was the solution when this happened to me some years ago.  Perhaps someone with a better memory or more experience could advise?

Edit: [http://ubuntuforums.org/showthread.php?t=191358&highlight=Your+login+session+lasted+less+than+ten+seconds](http://ubuntuforums.org/showthread.php?t=191358&highlight=Your+login+session+lasted+less+than+ten+seconds) suggests deleting .ICEauthority from the failsafe login.  The file gets recreated when you login to gnome.

Robert
I'll try that. The only changes I have made to the system recently was installing IE6.
One clue that might help was that hda1 was listed as inaccessible in Disk Management, and there was no mount point. I could set a mount point to either / or /root, but I really am over my head here.
The sessionerror file said something about my sound service already being started, but I only saw that once.
It sure would be nice to keep my existing setup, but if I have to, it wouldn't be such a big deal to blow everything away and start over.

---

### Post by mayonaise15 on 2006-12-12
Before reinstalling everything, I would try creating a new user account and see if you can login with that.

---

### Post by jhenager on 2006-12-14
> **mayonaise15 said:**
> Before reinstalling everything, I would try creating a new user account and see if you can login with that.

Thank you. I hadn't even considered doing that.

---

### Post by Devilotx on 2006-12-14
I've done this to myself a few times.

What to do is Ctrl+alt+F1 to drop to console

login, issue Sudo chmod 0755 /home/*username*
enter your password

then do ctrl+alt+f6 to get back to the GDM

should let you in, 

 I like to have a home folder on my desktop and I can't get an easy way of setting one up, so I always end up futzing the permissions on my home folder and getting the $home .dmrc is not the right permission error or getting locked out like you did

---

### Post by jhenager on 2006-12-14
> **mayonaise15 said:**
> Before reinstalling everything, I would try creating a new user account and see if you can login with that.

Hey, you da man.

Now I will see if I can use Devilotx's fix to get back into my old beryl setup. I got used to the wiggly windows.

---

### Post by hikaricore on 2006-12-14
> **Devilotx said:**
> 
then do ctrl+alt+f6 to get back to the GDM


ctrl+alt+f7 is the default for X GDM/KDM but this may vary if you have reconfigured things outside of the standard.   :)

---

### Post by Devilotx on 2006-12-22
ah yes, my bad.

Did it work out for you? did you get back in?

---

### Post by jhenager on 2006-12-25
> **Devilotx said:**
> ah yes, my bad.

Did it work out for you? did you get back in?

I can get in as jh (new account) but not as jeff (original account).
I have setup a new ubuntu on another drive and installed compiz through Synaptic on that one, so I have the wobbly windows again.
It is interesting to see the differences between Beryl and Compiz, but contrary to some opinions that compiz is better, I have issues with it. For one thing, I have to log out to get the option to shut down.

---

### Post by jhenager on 2006-12-25
I went ahead and restored from a ghost image. Didn't lose too much stuff. I will mark it as resolved.

---

### Post by GrumpyBob on 2006-12-25
Did you try deleting/renaming ICEauthority?

Robert

---

### Post by jhenager on 2006-12-26
> **GrumpyBob said:**
> Did you try deleting/renaming ICEauthority?

Robert

I couldn't find anything by that name.
It was just easier to blow everything away by re-ghosting.

---

### Post by GrumpyBob on 2006-12-26
That's my fault for not writing the filename correctly - it's .ICEauthority, so you won't see it in nautilus unless you click View | See hidden files.  The leading dot in the filename marks it as a hidden file (same for folders).

Robert

---

