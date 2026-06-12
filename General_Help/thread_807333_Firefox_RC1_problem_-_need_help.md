---
title: "Firefox RC1 problem - need help"
date: 2008-05-25
forum: General Help
---

### Post by Chandler Mike on 2008-05-25
So I know enough about Ubuntu to do damage and stuff, but when things go wrong I have a hard time knowing why and how to fix it.

I was annoyed at waiting for Firefox RC1 to show up in my Latest Updates alert, so I downloaded it and read how to install it.

The basic instruction was:

$ sudo ./firefox

That's the command I ran in the tar.bz2 package I downloaded. 

The problem is that now when I try to run Firefox normally with the icon or whatever, it's not right. There are no bookmarks, no history, etc.

Then I went to another site that had me change the sources.list file to do the upgrade that way, so I did it, that all installed, but I'm still having the same problem.

The only way I can run it with all my preferences is from the downloaded package on my desktop, not the icon that points to the normal location.

How do I fix this? I really need some help here because of school and work and it's semi-urgent.

Thank you!

Mike

---

### Post by drs305 on 2008-05-25
It sounds like it is not using your old profile.

Were you using FF 3.05b or FF2 before you installed RC1? I know there were issues between FF2 and FF3.05b.  If you were using FF3.05b and you know where your old profile was stored, you could try opening firefox with "firefox -p" and point it to your old profile folder. I'm not using any version of FF3 for now so that's all I can suggest. Good luck.

---

### Post by Chandler Mike on 2008-05-25
> **drs305 said:**
> It sounds like it is not using your old profile.

Were you using FF 3.05b or FF2 before you installed RC1? I know there were issues between FF2 and FF3.05b.  If you were using FF3.05b and you know where your old profile was stored, you could try opening firefox with "firefox -p" and point it to your old profile folder.

I was using FF3.05b....

---

### Post by Chandler Mike on 2008-05-25
> **drs305 said:**
> It sounds like it is not using your old profile.

Were you using FF 3.05b or FF2 before you installed RC1? I know there were issues between FF2 and FF3.05b.  If you were using FF3.05b and you know where your old profile was stored, you could try opening firefox with "firefox -p" and point it to your old profile folder. I'm not using any version of FF3 for now so that's all I can suggest. Good luck.

I tried that, and I select default profile (which is all that's there) and it's still all blank.

This could be a permissions problem, as I was in a school folder, downloaded some files and they are locked under "root"...

So when I am running firefox now regularly, it's like it's trying to access "root" profiles or something.

Ugh.

---

### Post by drs305 on 2008-05-25
> **Chandler Mike said:**
> I tried that, and I select default profile (which is all that's there) and it's still all blank.
Ugh.

The default profile that you saw would be the new one. You would have to select Create Profile and then Choose Folder, pointing it to the folder containing your old profile if you know where it was stored. It's possible that the new install overwrote the old one but I doubt it. It also sounds like your profile may be in root. Your old profile would probably be in /home/username/.mozilla/firefox  or something like that. That is where all the FF profiles used to reside. If you didn't name your old profile, it probably has an 8-character name that makes no sense, ending with .default

You could do a search of your partition for an old default profile:
```
sudo find / -name ????????.default
```

---

### Post by Chandler Mike on 2008-05-25
> **drs305 said:**
> The default profile that you saw would be the new one. You would have to select Create Profile and then Choose Folder, pointing it to the folder containing your old profile if you know where it was stored. It's possible that the new install overwrote the old one but I doubt it. It also sounds like your profile may be in root. Your old profile would probably be in /home/username/.mozilla/firefox  or something like that. That is where all the FF profiles used to reside. If you didn't name your old profile, it probably has an 8-character name that makes no sense, ending with .default

You could do a search of your partition for an old default profile:
```
sudo find / -name ????????.default
```

Thanks man, that seemed to work! I appreciate your help!

---

