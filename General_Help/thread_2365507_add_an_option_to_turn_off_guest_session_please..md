---
title: "add an option to turn off guest session please."
date: 2017-07-07
forum: General Help
---

### Post by unityforever on 2017-07-07
after two years there is still no way to turn off guest entrance on system user interface.

i know how to modify .conf file, but it would be nice for many ordinary users if there have a check-box in system preference.

---

### Post by coffeecat on 2017-07-07
You've posted in General Help which is a technical support area. Do you have a specific question to ask, or were you just making an observation?

---

### Post by unityforever on 2017-07-07
so how to give my suggestion to developer?

---

### Post by QIII on 2017-07-08
Hello!

One place to start might be joining this mailing list:  [email]ubuntu-devel-discuss@lists.ubuntu.com[/email]

I don't know if this would be the right IRC channel, but you could try #ubuntu-discuss on Freenode.

Cheers!

---

### Post by wildmanne39 on 2017-07-08
In case you do not already know you can disable the guess session, how to do it is at the following link.
[http://ubuntuhandbook.org/index.php/2016/04/remove-guest-session-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/04/remove-guest-session-ubuntu-16-04/)

---

### Post by deadflowr on 2017-07-08
I doubt they'll ever add anything for Ubuntu's unity-greeter for gui settings like this.
However maybe the developers of the lightdm-gtk-greeter-settings packages, which offers a gui method of setting up the lightdm-gtk-greeter (which is used by most every other flavor of Ubuntu except Kubuntu and Ubuntu)
might be receptive of adding such a feature.

Also of note, in 16.10 and 17.04(and 17.10) guest session was disabled as there is a systemd login vulnerabilty which allowed guest sessions far more access than should have been able.
See: [https://www.ubuntu.com/usn/usn-3285-1/]("https://www.ubuntu.com/usn/usn-3285-1/")

And on top of all that, it's not really clear as to what display manager will be used going forward (I think gdm will be used going into 17.10 18.04, but things are quite fluid at this time)
So that adds a whole 'nother level...

---

