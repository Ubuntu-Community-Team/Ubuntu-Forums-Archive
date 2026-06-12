---
title: "Keepassx copy password does not work"
date: 2016-07-12
forum: General Help
---

### Post by oygle on 2016-07-12
I have only started to use Keepassx , and it is not copying the passwords either.

---

### Post by howefield on 2016-07-12
Post moved to its own thread.

Keepassx is not the same as Keepass2. 

If you open a text editor, can you copy/paste a password from Keepassx to it ?

---

### Post by HermanAB on 2016-07-12
Note that KeepassX will delete the password from the copy buffer after a little while for security reasons, so be quick.

---

### Post by oygle on 2016-07-12
> **howefield said:**
> Post moved to its own thread.

Keepassx is not the same as Keepass2. 

Thanks for moving to own thread. Here is what the history is with Keepasx

1. Been using version 0.4.3 on Trusty (14.02) for quite a few months. No problems at all. I like how it stores the passwords, and you can see them in a seperate bottom window, without having to open/view. This is on a desktop computer, running Kubuntu.

2. Decided to have a clean install on another computer, a Dell laptop. Installed version 16.04, and Keepassx version 2.0.2
    That's when I started to experience the problems. I could see the entry in the clipboard, but couldn't paste it.

> **howefield said:**
> If you open a text editor, can you copy/paste a password from Keepassx to it ?

Opened the text editor (Kate), then used Ctrl-C to copy a password from Keepassx. Was able to then paste to Kate, worked fine. Then I opened Firefox and just tried to used Ctrl-P to paste the password, but nothing there, the 'paste' option was greyed out.

> **HermanAB said:**
> Note that KeepassX will delete the password from the copy buffer after a little while for security reasons, so be quick.

Oh, ....thanks, so that is the problem. Yet vers 0.4.3 doesn't seem to do that ?? Oops, yes it does (just tested it).

Okay, so problem solved. Thank you.  :)

---

### Post by howefield on 2016-07-13
> **oygle said:**
> Opened the text editor (Kate), then used Ctrl-C to copy a password from Keepassx. Was able to then paste to Kate, worked fine. Then I opened Firefox and just tried to used Ctrl-P to paste the password, but nothing there, the 'paste' option was greyed out.

Yes, in that case,, it is just a matter of you getting used to it, as pointed out.

You might be able to alter the time to clear the clipboard with Extras > Settings > Security > Clear clipboard after....

---

### Post by oygle on 2016-07-19
> **howefield said:**
> You might be able to alter the time to clear the clipboard with Extras > Settings > Security > Clear clipboard after....

Okay thanks. Yes, it was set to 10 seconds, which is too quick.  lol

---

### Post by blue-sea on 2017-01-16
I have seen same problem but by using "control + V" on the keyboard to paste it works.

---

### Post by oygle on 2017-01-16
> **blue-sea said:**
> I have seen same problem but by using "control + V" on the keyboard to paste it works.

It's not a problem. The thread is marked solved. It was a setting/config. thing, that's all.  :)

---

