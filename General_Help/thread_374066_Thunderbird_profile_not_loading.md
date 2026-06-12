---
title: "Thunderbird profile not loading"
date: 2007-03-02
forum: General Help
---

### Post by icefaerie on 2007-03-02
Hello.

I had several problems with a recent update...my nvidia drivers stopped working, but that's fixed now.  My other problem is that Thunderbird doesn't seem to be recognizing my profile.  When I start it, it prompts me to create a new account and doesn't have any of my mail, etc.  I think this might be a problem with Thunderbird 1.5.0.9, since the same thing happened on Windows.  (I am dual booting and sharing my Thunderbird profile on a shared partition.)

Here is my profiles.ini:
```
liz@yaoi:~/.mozilla-thunderbird$ cat profiles.ini
[General]
StartWithLastProfile=0

[Profile0]
Name=Liz
IsRelative=0
Path=/mnt/share/thunderbird/Liz
Default=1

```

The files are all still there, so I'm not really sure what happened.... Thanks for any suggestions.

---

### Post by aysiu on 2007-03-02
I'm no expert on Thunderbird profiles, but maybe what you should do is let Thunderbird create a fresh (and empty) profile. Then, you'll have two profile folders in your ~/.mozilla-thunderbird folder--an empty new one and a full old one. You can then move the contents of your old full one to the new empty one.

Worth a shot, anyway.

---

### Post by Xemanth on 2007-03-02
Check with 'ps -A' that is the there thunderbird and thunderbird-bin programs running already.
Kill them with command sudo killall -9 thunderbird.

After this start normally, if TB doesn't open still. Repeat what I said before and start thunderbird with command 'thunderbird --ProfileManager'

---

