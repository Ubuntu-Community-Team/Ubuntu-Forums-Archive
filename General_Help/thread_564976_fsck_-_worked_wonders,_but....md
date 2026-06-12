---
title: "fsck - worked wonders, but..."
date: 2007-10-01
forum: General Help
---

### Post by Dreamlocked on 2007-10-01
Hello.

**_BACKSTORY_**

Ok, so my system crashed at some point. Not exactly certain of the reason, but I suspect it might be related to me manually killing a java application that allowed my computer to connect to my university's windows 2003 server.

Long story short, I had to do a hard boot. When I reboot, fsck (or e2fsck, can't remember which), helped me with restoring inodes and other things, while blindly accepting all prompts, as I was not familiar with the terminology.

Good news is that most things are where they should be, system seems operational, and whatever data I might have lost I managed to happily find in the lost+found directory.

**_PROBLEM_**

There is only one thing that bugs me. When fsck prompted me:
```
Entry <folder_name> in <path> has an incorrect filetype (was 2, should be 1)
```

Both 2 and 1 were wrong for me, as the former folder is now a file that contains (when opened with mousepad):
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mcs-option SYSTEM "mcs-option.dtd">

<mcs-option>
	<option name="orage/ArchiveFile" type="string" value="/home/marios/.config/xfce4/orage/orage_old.ics"/>
	<option name="orage/Lookback" type="int" value="0"/>
	<option name="orage/NormalMode" type="int" value="1"/>
	<option name="orage/Pager" type="int" value="1"/>
	<option name="orage/ShowStart" type="int" value="1"/>
	<option name="orage/SoundApplication" type="string" value="play"/>
	<option name="orage/Systray" type="int" value="1"/>
	<option name="orage/TaskBar" type="int" value="1"/>
	<option name="orage/Timezone" type="string" value="floating"/>
</mcs-option>

```

So my question is: how do I revert this weird file into being a folder again?

Thank you in advance for any insight.

P.S. : I use Xubuntu 7.04

---

