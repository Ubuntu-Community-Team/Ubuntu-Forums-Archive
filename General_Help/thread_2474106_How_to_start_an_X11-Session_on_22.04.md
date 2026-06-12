---
title: "How to start an X11-Session on 22.04?"
date: 2022-04-22
forum: General Help
---

### Post by ninoivanov on 2022-04-22
Hi everyone,

I do hate Wayland and I would like to know, can I start an X11-session in Ubuntu 22.04 - and how?

On the login page, there used to be an option to start an X11-session - which is now gone. What should I do?

Thank you in advance!

EDIT:

A workaround, for the time being:

1. I installed jwm (or any of the other window manager which do not try to control your life).

2. I navigated to a console, e.g. Ctrl-Alt-F5, & logged in.

3. sudo X :7 &
that starts the pure X server and you see a black screen

4. again, do Ctrl-Alt-F5, and press enter, to get your prompt

5. jwm -display 7

6. Ctrl-Alt-F7 brings you now to your X session.

That is not as "nice" as a login into an X session, but at least this works reliably.

---

### Post by ajgreeny on 2022-04-22
I use Xubuntu which does not yet even offer wayland but if I remember correctly you may not see the option to choose the X11 session until you have entered username and password, but before hitting the login button.

---

### Post by ninoivanov on 2022-04-22
My hero, ajgreeny!

Yes, if I log out, and then click on my name to log in, and it opens the password field - then there, on the lower right, a toothed wheel appears and there I can select another session.

Thank you very much!

---

