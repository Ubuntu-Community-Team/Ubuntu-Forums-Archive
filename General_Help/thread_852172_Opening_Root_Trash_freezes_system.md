---
title: "Opening Root Trash freezes system"
date: 2008-07-07
forum: General Help
---

### Post by benny bronx on 2008-07-07
I was removing some files as root, executed the command gksudo nautilus, and moved the files to trash.  While still as root, I opened up the trash and my cpu spiked to 100%, bringing my system to a crawl.  Only by logging out did everything return to normal.  I was able to recreate  this issue every time.

1.  Is this a known bug? If yes, any fixes?
2.  Am I doing something wrong?
3.  What is the command to empty root trash?

Thank you.

---

### Post by jessika-kaos on 2008-07-07
I am having the exact same problem. I deleted a large file from nautilus and I need to find the root trash to free up some space, but my system freezes or slows to a crawl. Anyone?

---

### Post by Mr_Freez3 on 2008-07-07
Same thing happens here if I click on the Trash icon in the file tree, freezes until I force quit.  But I experimented a little and found a workaround for emptying root trash.

After you gksudo nautilus, in the root file browser you will see ".local" folder.  (If you don't see ".local", enable "Show hidden and backup files" in Edit>Preferences.)  Click on ".local", then click on the "share" folder, then "Trash", and you'll find a "files" folder and an "info" folder.  I emptied the content of both of these folders without any problem, using "Delete" in the context menu, which I also have enabled in Edit>Preferences.  Don't know if I should have emptied the "info" folder, but it didn't appear to harm anything.

---

### Post by iaculallad on 2008-07-07
To empty root Trash using terminal:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

I don't know it this [Bug #235759]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/235759") relates to your Trash error.

---

### Post by benny bronx on 2008-07-08
Yes, that would seem to be the same issue, I will try the workaround posted by Mr_Freez3 (thank you) and post whether it worked for me. And thanks iaculallad for the command.  Will add it to my list.

---

### Post by benny bronx on 2008-07-08
The solution posted by Mr_Freez3 worked for me.  I found the files I moved to trash as root in that location, and was able to delete it without any cpu spike.

---

### Post by LMP900 on 2008-07-08
I experienced the same thing about a month ago. I didn't bother to file a bug because I thought something else was causing the lock-up. It's interesting to know that it isn't an isolated case.

---

### Post by fromgi on 2008-07-11
Did a clean install using the new 8.04.1 download.  This problem still exists.

---

### Post by ububaba on 2008-07-11
> **fromgi said:**
> Did a clean install using the new 8.04.1 download.  This problem still exists.

I have been intending to do a clean install myself but apparently it
would be in vain. Thanks for for the information.

---

### Post by NilsE on 2008-07-11
This is a known problem which is one of many when you are running nautilus as root. 

Just a couple of helpful pointers.

A workaround for this problem is to start nautilus with this command either in a terminal or a launcher.

```
gksudo dbus-launch nautilus
```

Also, if it does freeze you can follow these steps to kill it without rebooting

In a terminal:
```
Run top and get the pid # of nautilus then

sudo kill -9 xxxx (xxxx = PID from top)
```

or you can just run the following in a terminal:
```
sudo killall nautilus
```

---

### Post by carl_pr on 2008-07-11
yes this happen to me when i was trying to delete some trash files that i couldnt. Ubuntu freezes and started to consume all the ram and the swap file started to fill out slowly, had to restart. (this happen when i opened nautilus as root and then go to trash)


i had to use a sudo rm command to delete trash, i was scare lol but it all worked out

---

### Post by ChrisC on 2008-08-05
> **NilsE said:**
> This is a known problem which is one of many when you are running nautilus as root.

I had to do a hard reset of my computer to recover it.  I couldn't open terminal, couldn't Ctrl-Alt-Backspace, no recourse except to resort to hardware reset.  That's quite embarrassing for Ubuntu and Gnome.  Fortunately I have Thunderbird set to autosave email drafts (had emails in progress) and Firefox restores sessions.

Thanks to the earlier post that recommended using "sudo dbus-launch nautilus".  That worked for me, so I could at least recover some space.

Here's the Gnome bug that apparently covers this issue:
[http://bugzilla.gnome.org/show_bug.cgi?id=537298](http://bugzilla.gnome.org/show_bug.cgi?id=537298)

It's unclear to me if this is now fixed or not, and if we just have to wait for the package update to work its way through.  Can someone with a bugzilla.gnome.org account post in that bug to find out?

---

### Post by NilsE on 2008-08-06
> **ChrisC said:**
> 
It's unclear to me if this is now fixed or not, and if we just have to wait for the package update to work its way through.  Can someone with a bugzilla.gnome.org account post in that bug to find out?
It was fixed in gvfs about a week ago but it is in the proposed repositories. Just need to be careful if you turn on the proposed repo since it is packages still in test.

EDIT: I should have added that the longer Nautilus churns at 100% CPU and grabbing memory the more difficult it is to kill it since it eventually locks up the system and you have no choice but to do a hard shutdown.

---

