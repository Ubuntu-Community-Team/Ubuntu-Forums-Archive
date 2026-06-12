---
title: "HOWTO: Fix gutsy bootup"
date: 2007-10-06
forum: General Help
---

### Post by hebetude on 2007-10-06
Something I have noticed on more than one computer is an extremely long bootup time for Gutsy, in the range of 5-20mins to get it to load after logging into gnome.

A quick fix (as in may not be the best way to fix this) is to turn off some of the things that run on gnome bootup.  My bootup time is now about 90seconds from bios POST.

We will be editing $HOME/.gnome2/.session. Make a backup, if you want, 

```
 cd ~/.gnome2
cp session session.bak
```Just for a newbie guide, if this somehow breaks your ability to boot into gnome you can always get to a TTY session by pressing ALT+F1.  Then, restore from the backup (mv session.bak session).

Next, we will comment out some things, these are any I've seen as rumored to slowdown bootup.  I just turned off all of them rather than trying one a time, which you can spend the time on and let me know :P.

Go to #5, it will have a list of about 6 items with the following field: <code>Program=update-notifier</code>.  Comment out all of the 5 entries.

```

5,id=11189fb667000119136942500000117820004
5,RestartStyleHint=1
5,Program=update-notifier
5,CurrentDirectory=/home/drew
5,CloneCommand=update-notifier --sm-config-prefix /update-notifier-CT1988/

```becomes:
```

#5,id=11189fb667000119136942500000117820004
#5,RestartStyleHint=1
#5,Program=update-notifier
#5,CurrentDirectory=/home/drew
#5,CloneCommand=update-notifier --sm-config-prefix /update-notifier-CT1988/

```Do the same for #18
```

18,RestartCommand=trackerd

```I also commented out:
#14 bluetooth-applet, #11 evolution-alarm-notify, #8 gnome-terminal, #7 gnome-power-manager
Mostly because they a. don't work, b. I don't use them

---

### Post by K.Mandla on 2007-10-24
Moved to General Help.

---

### Post by #Reistlehr- on 2007-10-30
I'd like tos ay nice post, but, ~/gnome2/.session doesn't exist , not even ~/.gnome2/.session

lol

---

### Post by Iztari on 2007-10-30
same here, no gnome2 folder

---

### Post by dayvy on 2007-10-30
I believe these items are all listed in "System" -> "Preferences" -> "Sessions" -> "Startup Programs". A much easier method for disabling startup services.

d.

---

### Post by frodon on 2007-10-30
the correct path is ~/.gnome2/session

---

### Post by hebetude on 2007-10-30
> **dayvy said:**
> I believe these items are all listed in "System" -> "Preferences" -> "Sessions" -> "Startup Programs". A much easier method for disabling startup services.

d.

This post is referring to Gutsy Gibson, not Feisty. Go ahead and look around the forums about the differences. Gutsy Gnome, unfortunately, has a lot of bugs not found in the Feisty version including the Startup Program app you are referring to.  You have to manually delete/enter entries in .gnome2/session, because that app apparently is non-functional in Gutsy.

---

### Post by frodon on 2007-10-30
BTW, to all those who have this problem please comment the bug report posting your session file and giving details :
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544)

---

### Post by dayvy on 2007-10-30
> **hebetude said:**
> This post is referring to Gutsy Gibson, not Feisty. Go ahead and look around the forums about the differences. Gutsy Gnome, unfortunately, has a lot of bugs not found in the Feisty version including the Startup Program app you are referring to.  You have to manually delete/enter entries in .gnome2/session, because that app apparently is non-functional in Gutsy.

All I can say is that it is working fine for me in Gutsy. Strange.

d.

---

### Post by #Reistlehr- on 2007-10-30
frodon, that was the bug i've been working on figuring out. lol. This seems to have been relevant, in which i broad the dead thread back.

the only file/dir in .gnome2 taht has the word session in it is, brasero.session, but it's contents are not relevant to the example posted.

So, i dont have the file. If i don't have the file, but everything is still launched, (Even when it's disabled in the GUI session manager, thanks buggy gutsy), where the heck is the script that starts all this stuff?!

I've been digging around the fs non-stop trying to get a fix to the bug since it's been sitting idle with no responses from the devs, and it is still marked as incomplete. wtf?

---

### Post by frodon on 2007-10-30
If you want to create the file just use the "gnome-session-save" command, if the generated file creates problems on next login then just login using the gnome failsafe session and delete it.

---

### Post by #Reistlehr- on 2007-10-30
hehe, thanks for the command, that's what i was looking for!

---

### Post by funnypanks on 2008-03-09
just wanted to say that i tried this method and all it did was disable my panels and trackerd... and bootup took just as long as always

---

