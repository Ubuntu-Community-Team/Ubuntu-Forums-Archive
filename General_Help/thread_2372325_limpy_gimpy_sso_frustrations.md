---
title: "limpy gimpy sso frustrations"
date: 2017-09-23
forum: General Help
---

### Post by JamButty on 2017-09-23
In attempting a software center install of GiMP after a wipe/reload, I am told I have to sign in with my Ubuntu SSO password. No problem, been using it here for years....nope we don't know you. Ok, I'll play the game and reset my password, done. Test logging on here to ubuntuforums repeatedly, logging out and flushing cookies each time. No problem. Gimp? nope, we don't know you. Wait a day, multiple reboots -Nope, never seen you before.
Why is this even necessary and how do I get around it's obstinance?

---

### Post by deadflowr on 2017-09-23
It's probably because it's the snap package version.
The Software center SSO login problem had been a bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943")

Outside of a chance that a simple update fixes things you can try two things.

Either search gimp in the software center and see if two versions show up
(One would be the normal apt version and the other would be the snap version.
You can try to install the apt version.
(snap packages often are listed in the software center as non-free, for some reason which I forget)
or
install the snap version through the terminal.
(This method does not require SSO:
```
sudo snap install gimp
```
(and of course you can also install the apt version through apt-get too
(Snap packages are isolated from the rest of the system, so you can actually install both versions, if you want)

snap packages get automatic updated and unlike the normal apt versions, will update to completely new versions.

Hope it helps
or that I didn't send you too far off the deep end.

---

### Post by JamButty on 2017-09-23
Terminal install worked fine. Thanks!

---

