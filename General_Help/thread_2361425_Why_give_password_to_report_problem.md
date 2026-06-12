---
title: "Why give password to report problem?"
date: 2017-05-16
forum: General Help
---

### Post by garyed on 2017-05-16
Just recently i've picked up some kind of system problem on mu Ubuntu 16.04 desktop. I have no idea what it is & after canceling the notice everything seems to be running fine. My question is why does it ask for my password just to report a problem? It seems like that is something an attacker would do if they wanted access to your computer. It doesn't make sense to me. Below is the screenshot so can anyone verify this is definitely from the Ubuntu team:

---

### Post by TheFu on 2017-05-16
To gather some system-level information needs root authority.  Normal users don't get to see all the secured files.  When a service running as root crashes, the core file is locked down, so only root can access it.  That is why bug reporting often requests sudo access.

But you are correct. An attacker could follow the same pattern and ask for sudo access.  But if I were doing it, I'd hide my desire to get sudo somewhere else and wait, patiently for you to need to use it yourself.  Most end-users aren't too cautious with sudo, so it wouldn't be hard, if that were an inclination.  Heck, I could make a webpage with some linux commands in it. Hidden inside those commands would be other stuff I'd like run too.  Visually, we can't tell the difference, but when copy/pasted !BAM! I get to own your machine.  This can be done through html email too.  

You can protect yourself from these sorts of attacks.  Always copy/paste into an editor, not a shell prompt. This way you can see the extra commands which may not be visible otherwise.

---

### Post by #&amp;thj^% on 2017-05-16
Would just like to add to the **Great answer **already provided by TheFu:
Reporting Crashes in System Processes:

Most of the time when an application crashes or you report a bug manually, you don't have to put in a password for information to be automatically gathered and sent to Launchpad.

However, when a program or service that runs as root crashes, collecting data about that crash requires accessing data that is only accessible as root. In Ubuntu, you can perform actions as root by authenticating with your password, provided that your account has administrative capabilities. (This is facilitated by sudo or one of its graphical frontends, or by PolicyKit.) If your account does not have administrative capabilities, then you will not be prompted to report a crash in a root-owned process until you log in with an account that has administrative capabilities.

When you're logged in as an administrator and you're prompted to report a crash in a root-owned process, you see a password dialog like this:

"Please enter your password to access problem reports of system programs"

This is one of the two situations where you may have to enter a password to report a bug in Ubuntu.

Once you've authenticated, then the crash-reporting process continues the same way as for regular non-root processes.

Credit to: Eliah Kagan From AU: [https://askubuntu.com/questions/150194/should-i-be-asked-for-my-password-when-a-bug-report-is-sent/482517](https://askubuntu.com/questions/150194/should-i-be-asked-for-my-password-when-a-bug-report-is-sent/482517)
And this is also very wise:
> _**Always copy/paste into an editor, not a shell prompt. This way you can see the extra commands which may not be visible otherwise. **_

---

### Post by garyed on 2017-05-16
Thanks,
I'm always a little cautious about giving out information or password unless I'm sure it's necessary & for the right purpose.

---

### Post by ajgreeny on 2017-05-16
You can also see what it was that crashed by clicking on **Details** at bottom left of the second dialogue window that appears asking for your password.
A lot of detail will appear much of which will probably not mean much, but the top line usually shows the executable's name.

---

### Post by vasa1 on 2017-05-16
> **TheFu said:**
> ... Hidden inside those commands would be other stuff I'd like run too.  Visually, we can't tell the difference, but when copy/pasted !BAM! I get to own your machine.  This can be done through html email too.  

You can protect yourself from these sorts of attacks.  Always copy/paste into an editor, not a shell prompt. This way you can see the extra commands which may not be visible otherwise.
+1 and something I don't mind being reminded of repeatedly.

"WYSINWYC (What you see is not what you copy)" or > Great question! I don't really have any convenient answer for you, short of what I'm doing - using an intermediary text editor (set to display all non-printable characters) for clipboard operations and inspect actual copied contents there before pasting it somewhere like a terminal window, or even into files to compile. It becomes your second nature in a while, and I suggest always having one instance of your favorite text editor running for such tasks. One of the first things you learn being involved with IT security is there is no such thing as WYSIWYG.Source: [https://security.stackexchange.com/questions/39118/how-can-i-protect-myself-from-this-kind-of-clipboard-abuse#comment62335_39118](https://security.stackexchange.com/questions/39118/how-can-i-protect-myself-from-this-kind-of-clipboard-abuse#comment62335_39118).

I found a simple illustration here: [http://www.h-online.com/security/services/Copy-Paste-Tricks-1842855.html](http://www.h-online.com/security/services/Copy-Paste-Tricks-1842855.html) where "ls /some/thing/much/too/long/to/type/" expands to something else when pasted into a terminal (and even when pasted into a text editor).

---

### Post by #&amp;thj^% on 2017-05-16
> **vasa1 said:**
> +1 and something I don't mind being reminded of repeatedly.

"WYSINWYC (What you see is not what you copy)" or Source: [https://security.stackexchange.com/questions/39118/how-can-i-protect-myself-from-this-kind-of-clipboard-abuse#comment62335_39118](https://security.stackexchange.com/questions/39118/how-can-i-protect-myself-from-this-kind-of-clipboard-abuse#comment62335_39118).

vasa1 Thanks for this link...Great and useful information. :D

---

