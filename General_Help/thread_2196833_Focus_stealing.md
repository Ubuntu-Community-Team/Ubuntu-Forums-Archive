---
title: "Focus stealing"
date: 2013-12-31
forum: General Help
---

### Post by Dave_L on 2013-12-31
[Ubuntu 12.04.3]

One of my few annoyances with Ubuntu is the way that a newly launched application will steal the focus.

For example, if you're typing text in one window, and an application launches, the new application's window pops up in the foreground and grabs the focus, interrupting your typing.

Is there any way of configuring this behavior?

---

### Post by deadflowr on 2013-12-31
Do you have apps just randomly launch?

Normally, if an app launches, you instigated that launch.
The system thinks you want focus on the app you just launched, as Spock says, it's only logical.

That said, you could probably set some parameters in ccsm.
I know you can set windows to no focus, among other settings in ccsm > window rules.

---

### Post by kajoky on 2013-12-31
sorry
i finally realized what I suggested does not work
so I edited this to remove it

---

### Post by triqui2 on 2014-01-23
I reported a bug long time ago: [https://bugs.launchpad.net/hundredpapercuts/+bug/495403](https://bugs.launchpad.net/hundredpapercuts/+bug/495403)
But had no success. I was new to Ubuntu to know I could have reported to metacity and/or compiz directly.
So now (13.10) this bug still bugs me and I'm waiting for Mir to see if there is a better focus handling.

---

### Post by triqui2 on 2014-01-23
Wow, now I found this bug which seems to be getting more attention: [https://bugs.launchpad.net/compiz/+bug/455241](https://bugs.launchpad.net/compiz/+bug/455241).
You should go there and check the "this affects me too" button.
BTW, deadflwr, this is what many people expects when opening windows:
[https://git.gnome.org/browse/metacity/tree/doc/how-to-get-focus-right.txt](https://git.gnome.org/browse/metacity/tree/doc/how-to-get-focus-right.txt)> 1) If the window takes a while to launch and the user starts
     interacting with a different application, the new window should
     not take focus.
  2) If the window that will appear was not launched by the user
     (error dialogs, instant messaging windows, etc.), then the window
     should not take focus when it appears.
...
If the newly launched window isn't focused, some things should be done
to alert the user that there is a window to work with:

---

