---
title: "Setting Thunderbird Mail profile as persistent on new computer."
date: 2015-07-31
forum: General Help
---

### Post by globetrotterdk on 2015-07-31
I have installed Ubuntu Studio 14.04 on a new computer and am trying to migrate my Thunderbird Mail profile. I have been using Thunderbird with my profile on a removable USB stick for some time and can also access my profile from Thunderbird by using the following command:
```
$ thunderbird -profile /media/user/USB/thunderbird_profile
```
Unfortunately, there doesn't seem to be a way to set this path as persistent in Thunderbird, so that under a normal startup of the app, it uses this profile as default behavior.

Any ideas as to how to set this path as default?

---

### Post by nerdtron on 2015-07-31
how about double dash:

```
thunderbird --profile /path/to/desired/profile
```

---

### Post by globetrotterdk on 2015-07-31
> **nerdtron said:**
> how about double dash:

```
thunderbird --profile /path/to/desired/profile
```

Nope. No difference, unfortunately.

---

### Post by howefield on 2015-08-01
You could try using

```
thunderbird -P
```

Delete the current profile and create the new one.

---

### Post by globetrotterdk on 2015-08-01
The point of having it on the USB stick, is that I can access my account from my different computers with different OS's. It should be  a simple operation to add an existing profile to a new computer. Unfortunately, it has been a long time since I tried this last. Deleting the profile isn't an option.

---

### Post by howefield on 2015-08-01
> **globetrotterdk said:**
> The point of having it on the USB stick, is that I can access my account from my different computers with different OS's. It should be  a simple operation to add an existing profile to a new computer.

Yep, I do the same and find it a trivial process using thunderbird -P for each instance of thunderbird to point to the profile folder. 

> Unfortunately, it has been a long time since I tried this last. Deleting the profile isn't an option.

Just in case you thought I was saying delete the profile that you want to point to, I'm not.

---

### Post by globetrotterdk on 2015-08-01
Thanks. Unfortunately, it just brings up the profile manager, which only gives the user the choice between creating a profile, renaming a profile, or deleting a profile. I don't want to do any of those things. I just want to point thunderbird to the profile on my USB stick, so that it will be persistent.

---

### Post by mc4man on 2015-08-01
Have you tried on new install  - 
start & close TB with nothing set
open ~/.thunderbird
Delete the new profile then open the profiles.ini file in a text editor & edit in full path desired, also set IsRelative= to 0
ex. here works fine
```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/doug/a4702606-c920-40c8-b267-74718729c821/home/doug/.thunderbird/71cf3o66.default

```

---

### Post by howefield on 2015-08-01
All I do is..

1. thunderbird -P
2. Delete profile if one is present. (don't delete files)
3. Press Create Profile button, then on Next.
4. Press Choose Folder and navigate to profile folder on USB stick.
5. Press Open then the Finish button.
6. Press Start Thunderbird.

This persists between installs, machines and reboots, ect.

Another way I do it is to append -profile "/media/hugh/Personal/Data_Store/thunderbird"  in the startup command for the icon launcher. Obviously that path is personal to me :)

---

### Post by globetrotterdk on 2015-08-02
Great, thanks. The one caveat is that I moved all files and folders in my profile folder, including hidden ones into a temporary folder that I setup, then created a new profile in the correct folder, removed the file that was created and then moved my profile files and folders back into the original profile folder.

---

