---
title: "[SOLVED] Help moving home folder to its own partition."
date: 2008-04-30
forum: General Help
---

### Post by Diabolis on 2008-04-30
I decided to move my home folder to its own partition. This is what I did:

1.- Made a new partition of my disk with gparted
2.- Mounted the partition here: **/media/sda6**
3.- Copied my home folder to the new partition like this:
```
sudo mv -v /home/gaston /media/sda6/
```
4.- I tried to changed my HOME environment variable to point to **/media/sda6**
5.- After fooling around with the HOME variable with no success, I figured out that what I had to change the mount point from **/media/sda6** to **/home**.
6.- Since I made lots of different modifications to the files that load environment variables(*/etc/bash.bashrc, .bashrc, /etc/profile, /etc/environment*), I though that It will be easier to do a clean install of hardy heron, so thats what I did.
7.- While installing Ubuntu I pointed the **/home** mount point to my new partition where I copied my old home folder.
8.- At installation I added a user with the exact same name that I used in the past installation so the old home folder would be picked up.

When I tried to log in to the new installation a message appeared, no big deal I clicked the "ok" button and the session started. The message says something like this:
> user's $HOME/.dmrc files is being ignored
file should be owned by user and have 644 permissions.
User's $HOME directory must be owned by user and not writable by other users
It appears every time that I log in.

I know I could try to change its permissions and all that, but I think that the problem lies beyond that. Some of my old settings were picked up from my old configuration folders, stuff like the wallpaper, gnome theme, etc, but not everything worked. For instance, Firefox didn't used all the settings that I had adjusted before (*bookmarks, theme, add ons configurations*), I had to mark it to reinstall it in synaptic package manager and then it showed all the modifications.

After going through all this I decided that it was time to look for some information in the internet. So after screwing up everything I searched for a guide :redface:

I found this guide: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
I actually did pretty much the same thing, except for one step. I didn't execute a command like this one:
```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

I do not fully understand what the command does, but from my experience I conclude that it takes care of the "links" that exist between configuration files in my home folder and installation files.

So after all this, my question is:
How do I update the "links" between my home folder and the installation files?

---

### Post by Diabolis on 2008-05-22
Seems like the problem is fixed. I couldn't figure out what the fancy looking command does, so I decided to deal with the permissions problem and it worked.

I found a [similar thread]("http://ubuntuforums.org/showthread.php?t=796628&highlight=user%27s+%24HOME%2F.dmrc+files") also.

---

