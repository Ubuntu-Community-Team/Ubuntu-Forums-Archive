---
title: "Unable to lock .ICEAuthority file when using encfs on entire home directory"
date: 2008-05-26
forum: General Help
---

### Post by aeetos on 2008-05-26
I am trying to use encfs to encrypt my entire home directory in hardy.  I managed to get this working perfectly in gutsy, and while I am quite certain I'm using the same command to mount the folder (I copied the bash script), I may not have remembered all the steps I did to get it working.  I certainly don't remember having this much of a problem in gutsy.

Here's how I set this up:
[LIST=1]
[*]Installed encfs, did modprobe fuse, etc.
[*]Switched to tty6 and logged in as root (my normal user, aeetos, was not logged in)
[*]Created an encfs store in /home/aeetos.crypt mounted in /home/aeetos.temp
[*]Made sure user aeetos owned /home/aeetos.crypt and /home/aeetos.temp and that they had the same perms as /home/aeetos
[*]Added aeetos to fuse group
[*]Copied (with -p) everything from /home/aeetos to /home/aeetos.temp
[*]Unmounted /home/aeetos.temp
[/LIST]

Then, I used this command to mount the directory (still as root, in tty6, not logged in to session yet):
```
encfs --public /home/aeetos.crypt /home/aeetos -- -o nonempty
```

So far, things are good.  At this point, still on tty6, I can su to my normal user (aeetos) and as that user, I can log in, create files in my home directory, delete them, edit existing files, etc.  I'm sure that I'm editing encrypted files because file times are changing on files in /home/aeetos.crypt (the encfs store).

Now for the problem: when I try to log in as aeetos in the gnome session manager, it validates the login and then gives me this message:
"The GNOME session manager was unable to lock '/home/aeetos/.ICEauthority.'".  My only option is to click "okay" which returns me to my login screen.

That error only appears when I have the encrypted home directory mounted to /home/aeetos.  Unmounting and going back to the un-encrypted files still works fine.

I did try adding user "gdm" to group "fuse" (and restarting) but that didn't fix the problem either.

Again, I had this working in gutsy, but now I'm having problems in hardy.  Any ideas?

---

