---
title: "software updater fails if I delay giving password"
date: 2014-01-03
forum: General Help
---

### Post by cspence on 2014-01-03
Occasionally the software updater asks for a password before it will install updates, like when a new kernel is being installed. I'm in the (bad, apparently) habit of hitting the install button (whatever the label is) and walking away. If I come back and it is asking for a password, I'll type it in, but usually (every time?) it fails immediately. I seem to remember that it asks to report the problem, but then the software updater window doesn't quite go away. It persists in a vertically narrow form, with no content except the title. I can hit the close widget in the title bar and it seems to go away, but the application bar on the left shows it as still active. Clicking on the updater's icon then makes the same narrow window appear. Top shows that some updater programs are still running. (I'd be more precise with the details, but it's difficult to reproduce on demand.)

When I don't walk away, so that I type the password in immediately, there's no problem.

This isn't critical, but it would nice if it were fixed.

---

### Post by mörgæs on 2014-01-03
It's a known bug in Update Manager. 

I couldn't find the bug report in Launchpad (what happened to my Google-Fu skills?) but it's there somewhere...

Instead of using Update Manager you can always run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by cspence on 2014-01-03
Thanks!

---

