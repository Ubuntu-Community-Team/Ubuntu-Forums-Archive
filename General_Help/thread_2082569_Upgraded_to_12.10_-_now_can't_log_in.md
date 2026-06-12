---
title: "Upgraded to 12.10 - now can't log in"
date: 2012-11-09
forum: General Help
---

### Post by Tolien on 2012-11-09
I've upgraded a machine from 12.04 to 12.10 and now can't log in to my user account.

When I type in the password, the screen goes black and I get dumped back at the login screen. I can SSH into the machine and can log in from the command line, so I know there's nothing wrong with my password.
Also, if I create a new user, I can login with that fine - so it must be something in my user profile which is broken.

Any pointers?

---

### Post by 2F4U on 2012-11-09
Yes, there is something in your upgraded profile that make Unity crash. If you can ssh into the machine, there should be a file .xsession-errors in the home directory of the user that can't login. It could give you a hint what the problem is.

---

### Post by Tolien on 2012-11-10
Thanks, but that file didn't look like it had been touched in a while, and wasn't updating when I tried to log in.

I did a bit more digging and found a suggestion to look at /var/log/lightdm/lightdm.log. In there was an entry about not being able to find /usr/share/xsessions/xsession.desktop so I symlinked ubuntu.desktop to that. Now I can log in, but I don't get...well anything, really.
The top bar and side bar are nowhere to be seen, though I can open a terminal window.

---

