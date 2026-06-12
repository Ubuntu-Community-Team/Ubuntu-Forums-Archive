---
title: "sound problem user/root"
date: 2006-12-06
forum: General Help
---

### Post by schambee on 2006-12-06
hi, i have weird sound problems. using ubuntu 6.10. whenever i log in as user i have no sound. (alsa - cannot write to resource). then i start gstreamer-properties as root und from this moment sound is working, even for the normal user. my user IS IN the audio group. anyone, how to resolve this issue? thanx

---

### Post by drphilngood on 2006-12-06
[QUOTE=Linux ALSA sound notes]

**Check that non-root users can access the sound device special files**

    Run alsamixer both as root and as a non-root ordinary user.
    If the latter fails, the permissions on the device special files don't allow access by ordinary users.
    There are several options to fix this, depending on security requirements, your distribution and how your PC is set up:

        * Allow all users read and write access to all sound devices, for example with

          ```
chmod -R a+rwX /dev/snd/.
```

          This might be slightly insecure.

        * Make sure that the sound device files belong to a specific group, they have group read/write permissions, and add all the users that should have access to the sound cards to that group. In many distributions this is the audio or sound group.

        * If only one user needs access to the sound card, change the ownership of the sound device files to that user.[/QUOTE]
[link]("http://www.sabi.co.uk/Notes/linuxSoundALSA.html#troubles")

Hope this helps.

---

### Post by schambee on 2006-12-06
thanx...will try it when on my ubuntu machine...should be in hmmm....7 hours....thanx a lot

---

### Post by drphilngood on 2006-12-06
> **schambee said:**
> thanx...will try it when on my ubuntu machine...should be in hmmm....7 hours....thanx a lot

You´re welcome; glad to help.

Good luck!

---

### Post by schambee on 2006-12-06
didn´t help.............so i have now write permissions to audio device...running sudo gstreamer once i have the permissions even as user...as far as i understand........weird.......one more suggestion?

---

