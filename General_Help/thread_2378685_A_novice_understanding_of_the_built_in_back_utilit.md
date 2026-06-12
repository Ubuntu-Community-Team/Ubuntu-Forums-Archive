---
title: "A novice understanding of the built in back utility"
date: 2017-11-25
forum: General Help
---

### Post by frappe792 on 2017-11-25
Hi all,

Fairly new to the whole Linux experience and enjoying it more and more. I am running kubuntu at the moment and increasingly realising how much configuring and tweaking there is just to get setup so I figured the " what if scenarios"

I notice there is the built in backup utility and I am backing up now to a folder on my home server.

Question: Is this backing up everything for this pc? ie by everything I mean


[LIST]
[*]Applications and their setttings
[*]Plugins
[*]Panels
[*]Widgets
[*]Keyboard Shortcuts & hotkeys
[/LIST]

Does it back up all of these? if not what does it back-up? 

Is the backup only for the computer that it was backed up from? Or can I do a fresh install of kubuntu on another PC and then restore from this backup? (effectively also migrating current setup to another PC)

I know there are alot of topics about, but the language used can be a little overwhelming and it's not always clear.
I'd appreciate any feedback.

---

### Post by frappe792 on 2017-11-30
surely someone from the 20,000 users online has a deep understanding of this utility?

---

### Post by deadflowr on 2017-11-30
The default backup program backs up the home directory.
Which is all of the user's files and folders.

It does not backup applications but will backup any configuration settings that are stored in the users home folder.

So where is doesn't backup the actual programs it does backup your personal settings that you would use for the programs.


**Edit**: er probably never mind I see this is tagged for Kubuntu, so not sure whether it's default backup program works the same as Ubuntu's does.
I see no reason why it shouldn't work much the same, since most things that cannot be replaced are user data related.
Programs plugins and such can simply be re installed.

---

### Post by frappe792 on 2017-12-06
> **deadflowr said:**
> The default backup program backs up the home directory.
Which is all of the user's files and folders.

It does not backup applications but will backup any configuration settings that are stored in the users home folder.

So where is doesn't backup the actual programs it does backup your personal settings that you would use for the programs.


**Edit**: er probably never mind I see this is tagged for Kubuntu, so not sure whether it's default backup program works the same as Ubuntu's does.
I see no reason why it shouldn't work much the same, since most things that cannot be replaced are user data related.
Programs plugins and such can simply be re installed.

Hi thanks for that

I notice after a backup today it says

"Could not back up the following files. Please make sure you are able to open them.

/home/myname/.dbus"

Any idea what this means?

---

### Post by ian-weisser on 2017-12-06
Short answer: The .dbus directory does not need to be backed up, and can be safely ignored by the user.

Longer answer: DBus is a standard common method for applications and services to communicate among each other (instead of using, say, shell commands). The .dbus dir within your home directory merely contains session-specific socket information so some applications can locate DBus.

Do NOT delete or change permissions of the directory.

---

### Post by frappe792 on 2017-12-06
> **ian-weisser said:**
> Short answer: The .dbus directory does not need to be backed up, and can be safely ignored by the user.

Longer answer: DBus is a standard common method for applications and services to communicate among each other (instead of using, say, shell commands). The .dbus dir within your home directory merely contains session-specific socket information so some applications can locate DBus.

Do NOT delete or change permissions of the directory.

Thank you very much, cheers.

---

