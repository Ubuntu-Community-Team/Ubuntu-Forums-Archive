---
title: "Black screen when logging in after upgrade 18.04 -&gt; 18.10"
date: 2018-10-23
forum: General Help
---

### Post by bthornton842 on 2018-10-23
I have a Lenovo Thinkpad X1 Carbon (6th gen) + Thunderbolt dock that was previously running flawlessly on 18.04 . When docked, the laptop drives two external monitors (the laptop lid is closed when docked so it's just dual-monitor).

After upgrading to 18.10, logging in just takes me to a black screen when docked. The login screen displays flawlessly on both monitors; it's only after logging in using Xorg that both of my monitors go black. Incidentally, changing my session to "Ubuntu with Wayland" does allow me to log in while docked--but this is not an acceptable workaround as many apps (esp. Skype) instantly crash the session. Also, if I'm NOT docked, I can still log in normally (even using Xorg). So it seems there is some incompatibility between Xorg and the dock with 18.10 .

Any ideas on what I can check?

Thanks!

---

### Post by HermanAB on 2018-10-24
Howdy,

To see what is going on when the screen is black, you can enable sshd.  Then you can log into the box over ethernet from another computer to look at the logs and debug the problem.

---

