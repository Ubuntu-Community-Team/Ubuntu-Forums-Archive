---
title: "How to edit/save autostart file as root"
date: 2015-04-30
forum: General Help
---

### Post by egruber on 2015-04-30
I have a file in my .config/autostart directory that I need to modify.  But my admin privileges won't let me do it.  I have a root ID set up.  Is there a way I can use gedit under my root id to modify the file and save it?  Each time I try it looks like it worked, but when I reboot the file is back to the old version.    Any suggestions?

I never had this problem in older versions of ubuntu.  When did it change?

---

### Post by TheFu on 2015-05-01
Running gedit as root requires special effort so that nothing get screwed in your personal settings.  Anything under your $HOME should NEVER need sudo to edit. If it does, then you've done something wrong and screwed with permissions/settings already.  This can happen accidentally very easy if subtle issue of using sudo/gksudo aren't fully understood.

Ok ... with all that said, the safe way to use any editor as root is to 

a) set your EDITOR environment variable to whatever editor you prefer.  Realize that using a GUI editor in a non-GUI environment WILL-NOT-WORK. Add this to your ~/.bashrc:
```
export EDITOR=gedit
```
also run it in any terminal if you won't logout/login first, but still want to edit a file now.

b) now use **sudoedit {filename}** to edit any file. sudoedit works by copying over the file to a temporary location, using the editor you like (or nano by default) as your userid to edit it, then copying the file back to the correct location when done.

Clear as mud?

You can find which files have improper permissions in your $HOME with this:
```
find $HOME -user root -ls
```  Hopefully, it is a very short list.  Mine had some CPAN stuff and port scanning things that require root to work at all.  No editor config files, no browser files, and no file manager files should be listed.

---

### Post by egruber on 2015-05-01
Thanks for your suggestions!   I did learn from another post that I can use gedit to open hidden files, so I was able to access the file through the gui without having to login as root or doing anything else risky.  

But the weird part is after I edit and save the file, I logout and login and the file is back to the original version...my changes are lost.  I have no idea what is happening.  It's a dropbox.desktop file.  I don't get any errors when editing or saving the file.  But the changes are gone after I logout/login.  Any ideas on this one?

---

### Post by TheFu on 2015-05-01
I don't use dropbox (or any 3rd party storage service) - why when sftp and rsync-over-ssh exists with clients for every platform?

Anyway - I suspect dropbox is running a program as root and perhaps it shouldn't?
What are the permissions?  **ls -al** will show the permissions, owner and group data.

---

### Post by egruber on 2015-05-01
I used dropbox with no issues until I moved to 15.04.  I never was concerned about how it ran.  The file edit is to fix a bug with displaying the status icon...that's all.  I just don't understand why I can't make a simple mod to a file without it reverting back after a reboot.  It makes no sense.

---

### Post by TheFu on 2015-05-01
Once you understand the true cause, it will make perfect sense. That is all I can offer without more facts and data, as requested above. 

I'm almost positive this is NOT Ubuntu, but dropbox causing it - based on your description.

---

