---
title: "Disable audio for a specific user"
date: 2014-01-30
forum: General Help
---

### Post by Stormlord on 2014-01-30
Hi,

Is there a way to disable audio completely for a specific user and that user only in Xubuntu or Linux in general?
It's essential that that specific user will not be able to restore sound for their account.  Only a superuser may restore it.
That user does not have sudo rights of course.

Thank you.

---

### Post by Tristan_Williams on 2014-01-30
To remove a user from any particular group, you can use the following command:
```

deluser <username> <groupname>

```

So for instance, if you wanted to remove "George" from the audio group, you would issue:
```

deluser George audio

```

---

### Post by Stormlord on 2014-01-31
> **Tristan_Williams said:**
> To remove a user from any particular group, you can use the following command:
```

deluser <username> <groupname>

```

So for instance, if you wanted to remove "George" from the audio group, you would issue:
```

deluser George audio

```


I am a little lost here my friend.  The only user in the audio group is pulse.  As a matter of fact I don't actually know what it does as a group.  Can you explain please?  :)

---

### Post by Tristan_Williams on 2014-02-01
The "audio" group dictates which users have access to audio. If you are not in the audio group, you use any audio devices.
So, if the user is not in the audio group, the user should not be able to use speakers, sound card, or anything else that is an audio device.

---

### Post by Stormlord on 2014-02-03
> **Tristan_Williams said:**
> The "audio" group dictates which users have access to audio. If you are not in the audio group, you use any audio devices.
So, if the user is not in the audio group, the user should not be able to use speakers, sound card, or anything else that is an audio device.


This:  "**If you are not in the audio group, you use any audio devices.**" is 100% contradictory to this:  "**So, if the user is not in the audio group, the user should not be able to use speakers, sound card, or anything else that is an audio device.**"  Plus, in a typical xubuntu installation there is one and only user in the audio group and that is **pulse**.  All users have access to audio this way.  Therefore, there has to be another way to block audio access to specific users.

---

### Post by Bucky Ball on 2014-02-03
Obviously a typo. If you are not in the audio group you can't use sound would have been the intention I imagine. Makes sense. 

But you are right. I'm not in the audio group and I can use audio just fine. This is me from a minimal install with xfce4 as DE:

adm disk cdrom sudo dip plugdev fuse lpadmin sambashare netdev

Am running 12.04.

---

### Post by Yellow Pasque on 2014-02-03
Genrally, only pulseaudio should have direct access to the sound device (which is why pulse is the only user in the audio group).

You would have to block the user's access to pulseaudio. The easiest way would probably be to set their ~/.config/pulse/<big string of numbers here>default-sink to the null sink (same thing with default source if you don't want them using the mic). If they're not tech-savvy, that would probably suffice.

Another way to go about it would be to limit executable access to /usr/bin/pulseaudio. Make a group that includes every user but the restricted one (I call it 'noisemakers' in the example), and change the group to that one.

```
cd /usr/bin
sudo chgrp noisemakers pulseaudio
sudo chmod 750 pulseaudio
```

Obviously, if you frequently create users, then you'll want to add them to that group by default.

---

### Post by Stormlord on 2014-02-05
> **Temüjin said:**
> Genrally, only pulseaudio should have direct access to the sound device (which is why pulse is the only user in the audio group).

You would have to block the user's access to pulseaudio. The easiest way would probably be to set their ~/.config/pulse/<big string of numbers here>default-sink to the null sink (same thing with default source if you don't want them using the mic). If they're not tech-savvy, that would probably suffice.

Another way to go about it would be to limit executable access to /usr/bin/pulseaudio. Make a group that includes every user but the restricted one (I call it 'noisemakers' in the example), and change the group to that one.

```
cd /usr/bin
sudo chgrp noisemakers pulseaudio
sudo chmod 750 pulseaudio
```

Obviously, if you frequently create users, then you'll want to add them to that group by default.

Hahahahahahaha...  I definitely like the name "noisemakers".  In this case, the one that needs to be blocked is the noisemaker and I will try your solutions since "civilized" talk does not seem to keep the sound level low in "some cases".  :D
Thanks a lot for your help.

---

