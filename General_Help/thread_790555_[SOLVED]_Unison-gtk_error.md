---
title: "[SOLVED] Unison-gtk error"
date: 2008-05-11
forum: General Help
---

### Post by LonelyTraveler on 2008-05-11
Everytime I try to start Unison-gtk I get the following error:

"Fatal error: Preference file PenDriveLinux not found."

PenDriveLinux was a folder I had but not anymore. I tried to completely remove Unison, and even searched for Unison files and deleted it. Reinstalled it then, but still i get the same error. What can I do?

---

### Post by drs305 on 2008-05-11
This might be your problem: I read your post and thought about doing a universal search for a PenDriveLinux file but since you said you already did a search I decided to proceed along another avenue.

I use a shortcut to open unison, but as an experiment, I tried typing 'unison' and got an error message similar to yours. In fact, it said it couldn't find a file I haven't used in years. I'm thinking the information is somewhere in my home folder, which has existed for many versions of ubuntu.

Solution: I checked my shortcut, and instead of just 'unison', it was 'unison-2.27.57-gtk', which opens just fine. I'm guessing just typing 'unison' reverts to an old package. Check synaptic or in terminal 'unison -version' to see what version you have installed. Then type that version in terminal and I think it will work.
Here is how I now open unison:
```
unison-2.27.57-gtk
```

As to why or where the old information still exists, I don't have a clue but I'm going to look around.

Later: The offending file is probably located somewhere in your .unison folder or wherever your .prf files are stored, even though you uninstalled it at some point.  When I renamed my .unison folder (where I keep my .prf files) to something else and then tried to open with 'unison', the file error message was not there, just information about how I need to include more switches to open and run unison.

Good luck.

---

### Post by LonelyTraveler on 2008-05-11
Thanks drs305, but here is what happens:

```
~$ unison -version
unison version 2.13.16
~$ unison-gtk-2.13.16-9
bash: unison-gtk-2.13.16-9: command not found
~$ unison-2.13.16-9-gtk
bash: unison-2.13.16-9-gtk: command not found


```

I usually open unison by going to app-acc-unison

---

### Post by drs305 on 2008-05-11
I did some more digging and on my machine I found the offending file was just 'default.prf'   ](*,)

It has been so long since I had used that file that I forgot it existed. When I deleted that file it got rid of the offending warnings and simply created a new default.prf It still asks for parameters, but doesn't reference the non-existent file any longer. 

If you delete the default.prf file you can probably go back to just typing 'unison' or whatever you used previously.

---

### Post by LonelyTraveler on 2008-05-11
> **drs305 said:**
> I did some more digging and on my machine I found the offending file was just 'default.prf'   ](*,)

It has been so long since I had used that file that I forgot it existed. When I deleted that file it got rid of the offending warnings and simply created a new default.prf It still asks for parameters, but doesn't reference the non-existent file any longer. 

If you delete the default.prf file you can probably go back to just typing 'unison' or whatever you used previously.

Where did you find that file? I can't find it.

---

### Post by drs305 on 2008-05-11
> **LonelyTraveler said:**
> Where did you find that file? I can't find it.

I installed unison in my home directory under .unison . I don't know if that was the default selection. The easiest way to find it if you have everything in one drive would be:
```
sudo find / | grep default.prf
```

If you are searching around in nautilus, make sure you can view hidden folders as the unison file may be in a .folder (hidden by default). (View, Show Hidden Files)

---

### Post by LonelyTraveler on 2008-05-11
> **drs305 said:**
> I installed unison in my home directory under .unison . I don't know if that was the default selection. The easiest way to find it if you have everything in one drive would be:
```
sudo find / | grep default.prf
```

If you are searching around in nautilus, make sure you can view hidden folders as the unison file may be in a .folder (hidden by default). (View, Show Hidden Files)

Turns out I didn't need to find the default file, but the PenDriveLinux files. Found that. Deleted it and now its perfect. Thanks a lot!

---

### Post by drs305 on 2008-05-11
Guess I should have stuck with the first 2 lines of post #2. ;-) Glad you solved your problem.

Note: The capability to mark a thread as solved has returned. You can select it from the thread tools at the top right of the original post.

---

### Post by English Dave on 2012-05-09
Just in case it helps someone with the same issue, I came across another scenario which produces the error 'Fatal error: Preference file Default not found'. It happens if you end up with a .prf file in the ~/.unison folder that is not writeable. The solution is to change the permissions (or delete the offending file) so that it is writeable.

It happened to me because I needed to use Unison to sync some directories that contained files that my normal user didn't have read permission to. So I started Unison using sudo:

```
sudo unison-gtk
```

Then I created a couple of profiles using the Unison GUI and did the syncing (which worked fine). But then Unison wouldn't work any more when not running it as a superuser. The reason was that it had put the .prf profiles, that I set up as root, under my normal user's ~/.unison directory, but with the owner and group set as root. The read permission was set for everyone but only the owner could write to it.

So I used sudo to chmod and chgrp the .prf preferences files back to being owned by my normal userid. This fixed the problem.

```
sudo chown david /home/david/.unison/file_name.pfr
sudo chgrp david /home/david/.unison/file_name.pfr
```

---

