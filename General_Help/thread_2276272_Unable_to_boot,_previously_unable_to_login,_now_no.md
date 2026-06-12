---
title: "Unable to boot, previously unable to login, now not even able to get to login screen"
date: 2015-05-01
forum: General Help
---

### Post by sam130 on 2015-05-01
So I ran an update yesterday, updated a whole load of stuff (~600MB worth) since I hadn't updated in a while. When I turned my computer on today I found that I wasn't able to login - every time I entered my password the screen went black and I ended up back on the login screen. There are plenty of forum posts about this already and I followed some advice I found there; I did everything in the top post of [this]("http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop") thread, which included doing 'chown username:username .Xauthority', and changing drwxrwxrwx to drwxrwxrwt. I then changed lightdm to gdm, and since then I haven't even been able to get to a login screen. My computer now goes past the purple Ubuntu screen to a flickering black screen - it goes off for a second then comes on but black for a second over and over again.

I've tried running boot-repair from an Ubuntu CD, which didn't change anything, though the information is here if it's at all helpful: [http://paste.ubuntu.com/10961126/](http://paste.ubuntu.com/10961126/) . I've also tried booting from grub with nomodeset, using recovery mode's dpkg option, and still no luck. I also now can't get into tty; if I try (Ctrl+Alt+F3 for example), I get the command line for about 5 seconds before I goes back to a black screen with a single underscore in the corner. Going into tty again returns me to what I was just looking at, but in 5 seconds it will kick me back out again. 

The only thing I can think of that might have caused the original issue is a change of graphics card some months ago - I switched from an ATI card to an Nvidia one and I'm not sure I ever switched drivers, though it worked fine until the update.

Does anyone have any ideas on how to fix this? Thanks.

EDIT: I have now managed to recover lightdm through the recovery's command line. I'm back to the initial issue though - the login loop.

---

### Post by sam130 on 2015-05-01
Fixed. After re-enabling lightdm I was able to install nvidia drivers through tty and was thus able to login. For anyone else facing this issue, the command I used was:
```
sudo apt-get install nvidia-current
```

---

