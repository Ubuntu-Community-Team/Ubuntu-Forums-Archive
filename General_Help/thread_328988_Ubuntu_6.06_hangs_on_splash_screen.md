---
title: "Ubuntu 6.06 hangs on splash screen"
date: 2006-12-31
forum: General Help
---

### Post by thewanabee on 2006-12-31
I apologize if im beating a dead horse of a question here, but ive spent the past two days checking the other posts and none of them seemed to come quite close to zeroing in on my problem. 

Basically, everything was going fine up until a couple of nights ago when I was fiddling around with some installs and uninstalls through apt-get. The last thing I remember doing was uninstalling network-manager and network-manager-gnome. When I tried to reboot the computer a while later, the ubuntu splash screen came up, the progress bar slid all the way through, the screen dissapeared, but then instead of my login screen, the splash screen came back and just sat there. Thats what its been doing ever since.

At the suggestion of a post I read on a problem similar to mine, I booted the system with splash and quiet turned off to see where the process was hanging at. It seems to keep getting hung up at the following point:

```
[17179636.084000] IPv6 over IPv4 tunneling driver
```

If it means anything: My 'system' is a dell inspiron c600 laptop

Any help would be appreciated. Thanks.

---

### Post by Tzumli_D on 2006-12-31
Sorry this is not a reply to your query, but I'm having a similar (I think) issue with Ubuntu 6.10.
After I sign in it takes nearly 4 minutes for the system to start working, and I get an error message about being unable to establish network.
So how did you :
> booted the system with splash and quiet turned off to see where the process was hanging at
It may help me work out what is wrong with my system.

---

### Post by thewanabee on 2007-01-01
As the system is booting, you hit escape to get the grub boot loader to come up (assuming that youre using grub because thats what i have. If youre running lilo or something else, this may not work). You highlight the ubuntu install you want to run (this will usually be the one at the very top of the list) and hit 'e' for edit. A second window will pop up showing all of the commands grub runs to boot that particulat install. One of the commands should be a long one with the words 'splash' and 'quiet' at the end of it. Highlight that line, hit 'e' again and just delete those two words from the end of the line. Finally, hit 'b', and the startup will run without the splash screen or the quiet setup.

Bear in mind that, from what ive seen, this process seems to only work for one startup at a time and it wont make any permanant changes. 

Hope you have better luck than im having right now :evil: ](*,)

---

