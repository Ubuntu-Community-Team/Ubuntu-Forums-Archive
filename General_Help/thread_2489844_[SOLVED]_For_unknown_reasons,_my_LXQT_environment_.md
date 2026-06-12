---
title: "[SOLVED] For unknown reasons, my LXQT environment had gone to hell"
date: 2023-08-11
forum: General Help
---

### Post by mag-linares on 2023-08-11
Since a few months I use Lubuntu 22.04 with LXQT.Despite some difficulties, I have been making progress little by little.But since today, without having changed anything in my system, when I boot up, a terminal window tty1 appears asking me to enter my username and password.Despite the fact that I put the correct username and password (both user and root), it always answers me "incorrect login", and I cannot enter.This problem has left me without Linux. What can I do?

---

### Post by guiverc on 2023-08-11
If you have insufficient space in your $HOME (home/user directory), a GUI login will fail and you'll be returned to the greeter (ie. *login loop*), without error message which doesn't fit your description.

Lubuntu 22.04 LTS *if you're using the HWE kernel stack *(*default kernel stack is dictated by what installation media you used to install, with 22.04 & 22.04.1 media defaulting to the GA kernel stack, and 22.04.2 & later installs defaulting to HWE*) recently switched to the 6.2 kernel (from 23.04), but this change rolled out last weekend (*not a day or so ago*), but maybe you are using a mirror that was slow to update its packages, don't upgrade packages daily etc... but I can't see how that would impact your login.

In your case I'd stop trying to login via GUI & login via text terminal... then again that maybe what you're actually trying to do.

When you boot; are you seeing the greeter (sddm) or display manager which allows you to login?  I wonder if you're just seeing a text terminal? and have suffered the removal of your desktop ([https://bugs.launchpad.net/ubuntu/+source/apt/+bug/2025462](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/2025462)) and thus this is what you're trying to describe & I'm misunderstanding your situation in my earlier paragraphs.

A fellow Lubuntu member gave a warning on [linux.org]("https://www.linux.org/threads/if-youre-using-ubuntu-22-04-or-an-official-flavor-you-might-want-to-put-off-updating-for-a-few-days.46228/") noting he'd expect users to see it, [I agreed]("https://www.linux.org/threads/if-youre-using-ubuntu-22-04-or-an-official-flavor-you-might-want-to-put-off-updating-for-a-few-days.46228/post-201380") but accepted the change anyway (*to [confirm it was easy to correct]("https://www.linux.org/threads/if-youre-using-ubuntu-22-04-or-an-official-flavor-you-might-want-to-put-off-updating-for-a-few-days.46228/post-201396")*), however I don't have the *additional complexity* of login with a *non-machine-native-character-set* (ie. *I'm a dumb aussie that **can barely speak english, but that's okay as my machines all assume an english/US keyboard is attached & thus I my keys match perfectly what the BIOS & OS expect*).  Your issue maybe related to the *language-mixup* between your machine *firmware* and the *language you chose at install time* (*which will work when you login via GUI, but maybe a problem at terminal*)... This however is just a thought, as sorry I'm not sure what your actual problem is.

I've just written my various '*thoughts*' here.. Maybe something will be useful, or maybe none will be (*ie. I completely miss understood your problem, if so sorry*).  If non-english is involved you should mention that detail (*it's not really english directly; its just the default for US designed & chinese manufactured components & thus outnumbers other options, but french default firmware exists too** as does some hardware that uses other non-english defaults; but what matters is if you local language default differs to the machine-native-assumed-language that  terminal may be using*)

---

### Post by mag-linares on 2023-08-12
Hi, friend. First of all, thanks for answering.


It seems that, for unknown reasons, my LXQT environment had gone to hell. And for reasons, also unknown, he had been determined to deny my correct credentials.


But in one of my attempts to access the system, it did accept my credentials. And, from that same TTY1 console terminal, I tried to restart it with **sudo systemctl restart lightdm**, but it gave me an error.


I reinstalled it with **sudo apt install --reinstall lightdm**


So yes the **sudo systemctl restart lightdm** worked


Issue resolved.


The language configuration had been lost, which in my case is Spanish, with all the messages appearing in English within LXQT.
I solved it with **sudo apt install language-pack-es language-pack-gnome-es**, then **sudo update-locale LANG=es_ES.UTF-8**, and everything goes back to how it was before.


I reiterate my thanks.

---

### Post by guiverc on 2023-08-12
Lubuntu uses `sddm`, and have done so for the last *ten* releases.

Your first attempt to restart it you mentioned gave an error; I'd expect an error as it's not used.

Regardless, **glad you got it solved.  Well done.**

*FYI:  The manifest file when you download contains a list of what is included on the ISO, here's [the manifest for 22.04.3]("https://cdimage.ubuntu.com/lubuntu/releases/22.04/release/lubuntu-22.04.3-desktop-amd64.manifest"), but it'll match all prior 22.04 systems except for the package versions included.*

---

