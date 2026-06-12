---
title: "keyring password??"
date: 2016-02-08
forum: General Help
---

### Post by VitasLoWang on 2016-02-08
Hello, it may sound silly, but somebody please tell me how this should work. I use my Ubuntu 14.04 for a year or so and suddenly I cannot connect to our company wifi, because it asks for my keyring password and apparently I don't know it. It used to be the same as login password and when I go to "passwords and keys" it says Passwords / login - A keyring that is automatically unlocked on login. But it has a lock icon and upon double clicking it asks me for a password, so how is that unlocked on login? It's friking not! Shouldn't this keyring password be synced with my primary user password every time I change it? I can't figure out what it can be and I am pretty sure it got corrupted, because none of the previously used passwords work. I will remove the keyring and will have to reimport the wiri certs again I guess, but I would like to know what the heck could have happened to it because I would really rather work then fix my machine's problems... Thanks

---

### Post by ian-weisser on 2016-02-08
Open Passwords and Keys
Right-click on your Login Password. Change the password to match your login password.

This sort of problem is rare, and can have many possible causes. Most users never encounter it.
The most common is when a user changes their login password, so it doesn't match the keyring password anymore.
Another, less common cause is when a user installs some other conflicting keyring or password-storage application.
It's also possible to corrupt the password file if, say, power happens to be cut at the wrong moment, or if the wrong block on your storage device happens to go bad.

---

