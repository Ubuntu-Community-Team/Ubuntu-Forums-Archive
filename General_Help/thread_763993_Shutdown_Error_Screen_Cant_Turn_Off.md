---
title: "Shutdown Error Screen Cant Turn Off"
date: 2008-04-23
forum: General Help
---

### Post by kempy1000 on 2008-04-23
Hello,
I am currently experiencing difficulties with turning off my Ubuntu server.

When in an ssh session I type "shutdown now" Mythtv disappears and the system then flashes up a text based menu with a blue background saying recovery menu.
My options are:
1) Resume  - as normal - this which starts the system back up
2) Root - Drop to root shell prompt
3) xfix - Try to fix x server - this resets xorg.conf and system is still broken.

If I type "halt" the system shuts down without a problem.

I tried to log the shutdown output with "shutdown now > shut.log"
but this failed.

Thanks
Chris

---

### Post by Tim Sharitt on 2008-04-23
I hope someone will correct me if I'm wrong, but I believe running shutdown with no options only brings down running processes. In order to halt the system the -h option must be supplied.
```
shutdown -h now
```
The halt command just calls shutdown with the -h option.

---

### Post by dksau on 2008-05-02
Tim Sharitt

Maybe you can help me.  After installing 8.04 after the OS goes off the computer keeps running and shows a black screen with white font and says Make sure the message bus daimon is running and Network Manager nm-dbus signal status change assertion 'cb-data-> data-> dbus connection failed'.  I have to shut down hard with the power on button.

---

### Post by sidcypher on 2009-05-10
kempy1000 - i have the same issue on my server. i didn't have a prob on a old p3 and 8.1...32-bit

but with heron 64bit and with jaunty 64-bit server installs.  

I get that exact same blue screen with the recovery options.
It isn't too big of a deal, except the A/C in my house is out, so i shutdown the server when not in use due to possible overheating. and it is also headless if that makes a diff.

BTW i have been looking for a couple days googling and here on forum for someone with same screen, was starting to think i was nuts, or i messed something up.

and yeah..this did work ```
shutdown -h now
```

---

