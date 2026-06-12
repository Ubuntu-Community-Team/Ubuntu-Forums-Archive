---
title: "Help I've got an error on my Kubuntu 12.10"
date: 2013-10-06
forum: General Help
---

### Post by andre9 on 2013-10-06
Hello everyone

First, I apologized if my English is bad....:) 

I have several problems with my Kubuntu 12.10....

When I succesfully updated my OS (I was updated the security only not upgrade to 13.04)...then I restarted my system, the problem is : 

1. I can't click the Shutdown, Suspend, and Restart button (the button is on the right bottom of corner)

2. I was unable to connect to my router AFTER I Updated...(in other words, my wireless is always disable at first, then I need to 'check' it manually, but no connection found)

3. I lost the Shutdown, Restart, and Suspend shortcut on the 'Leave' Application (or whatever the name is)

What I must do now? I am a newb on Linux...but want to master it one day...

Thanks before...

Andre9

---

### Post by grahammechanical on 2013-10-06
I cannot advise on using the Kubuntu user interface but to shutdown or reset your can open a terminal and run  either of these two commands.

```
sudo shutdown -r now
```
```
sudo shutdown -h now
```

If you cannot open a terminal try Crtl+Alt+F2 and then enter your user name and then the password and then run the commands. -r = reboot -h = halt.

Regards.

---

