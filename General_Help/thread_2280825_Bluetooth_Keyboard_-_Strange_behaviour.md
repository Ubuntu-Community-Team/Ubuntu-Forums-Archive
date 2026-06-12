---
title: "Bluetooth Keyboard - Strange behaviour"
date: 2015-06-02
forum: General Help
---

### Post by j2k15 on 2015-06-02
Dears,

I've installed Ubuntu 14.04 LTS on an Intel NUC.
Everything run smooth. I've installed the software Kodi.

To have more convenience I bought a "Maxxter" Bluetooth keyboard.
The pairing between the NUC and the keyboard is fine.

What i'm to do:
- Use the bluetooth keyboard with in the login screen (to type my password)
- Use the bluetooth keyboard in the "guest" Ubuntu session
- Use the bluetooth keyboard in the Kodi standalone session (with my personal user)

What is not working:
- I can't use the keyboard in an Ubuntu session when logging with my personal user. Even if within the session, the keyboard appears as being paired... That's really strange.

Do you know if there is a session parameter defined per user that may prevent the usage of a bluetoot keyboard ?

Regards.

---

### Post by j2k15 on 2015-06-09
Dears,

My problem is not solved.
But found that few keys like delete or fn + volume un/down are working...

So input keys only are not working...

xinput --list gives the same result in my account and in the guest account where the keyboard works...

And xev does not show events for most of the keys for my user. Only the backspace one...

For the guest user the events are well triggered.

Regards.

---

### Post by j2k15 on 2016-02-10
Dears,

The problem is still there.
Any clue to solve this ? Or at least to investigate ?

---

### Post by j2k15 on 2016-02-10
Hi,
I found something interesting :
In the guest session, if I plug a USB keyboard, the bluetooth keyboard suddenly does not respond like in the regular session.

Would it possible that the USB config has priority over the bluetooth one ? If so, how could I handle this ?

---

