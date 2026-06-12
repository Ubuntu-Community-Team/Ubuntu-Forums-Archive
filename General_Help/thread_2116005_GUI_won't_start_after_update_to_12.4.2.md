---
title: "GUI won't start after update to 12.4.2"
date: 2013-02-14
forum: General Help
---

### Post by IT-Joker on 2013-02-14
Hello,
yesterday I installed batch of updates to my Ubuntu 12.4.1 that changed it to 12.4.2.
But after restarting, the GUI now doesn't start.

At first it just dropped to text mode console during boot (so the result was prompt for user name in text mode).
Suspecting some problem with the graphic driver (I use ATI card), I used the console to uninstall the ATI fglrx driver. Then I restarted to recovery mode and reset the graphic settings.

After these changes the boot in normal mode proceeds to the GUI login screen. However, when I type my password, the screen goes dark for a second and then puts me back to login screen.
The guest session *partially* works: After a while of loading I get empty desktop with no icons or bars. I can move the mouse pointer and use keyboard shortcuts, even managed to open terminal via keyboard, but as guest I didn't really get anywhere.

The recovery mode has option to boot to safe GUI mode (don't remember the exact wording), but that doesn't work either: I get the login screen again, but after entering my password the screen goes black and then my monitor powers off, as if there's no signal.

So the problem indeed seems to be related with graphics, but I don't know what else to try.
Any suggestions?

BTW.: It has already happened multiple times that Ubuntu failed to boot after installing system updates. I have already stopped updating to the non-LTS releases because of that. And I think it's quite a serious problem that this happens.

---

### Post by IT-Joker on 2013-02-15
Made some progress.
After updating and reinstalling the ATI drivers:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx
```

the guest session seems to be working normally. Ie I have the top bar and launcher. 

But still no luck with my main account, the problem remains: After entering my password, there's black screen for a second and then it returns to login screen.

---

### Post by Bufeu on 2013-02-15
Maybe the ATI-drivers created some config-files in your home-folder? Try search for ATI and if you find any config-files related to ATI, remove them.

---

### Post by IT-Joker on 2013-02-15
Thanks for the idea Bufeu, but as I was looking through the config files, I tried starting X-server manually from command line and this time paid more attention to all the messages that appeared.
It complained about another session running and lock being present and about files .Xauthority and /tmp/x0-lock.
So I just went brute-force and deleted those files. And voila :)

Seems that the X-server at some point crashed and failed to release the lock. And at some other point I fixed the original problem, but still had to delete the lock manually to make it work.

---

