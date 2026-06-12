---
title: "auto log onto network"
date: 2007-10-18
forum: General Help
---

### Post by delfick on 2007-10-18
hello

After following a guide to get wireless network working on my laptop for uni, I have come to the conclusion that the only way to get it running is to do the following (network-manager always fails me)

```

sudo wpa_supplicant -ieth0 -c/etc/wpa_supplicant.conf &#8211;B
sudo wpa_cli
identity student-curtin <OASIS ID>                                                                 
password curtin-curtin <OASIS password>   
Quit
dhclient ath0

```

How do I make that automatic via a single command ?? 

(and make password automatic, or if that's not possible make it prompt for it and not print it out onto screen where others can see as I'm typing ??)

thnx :D

edit : or even better, make it work with network manager ? :D

---

### Post by WedgeHG on 2007-10-18
You could create a a script to run all of those commands:

just a text file that contains this:

```
#!/bin/bash
sudo wpa_supplicant -ieth0 -c/etc/wpa_supplicant.conf –B
sudo wpa_cli
identity student-curtin <OASIS ID>                                                                 
password curtin-curtin <OASIS password>   
Quit
dhclient ath0
```


inserting your password in the proper places.
then just type at a terminal 

```
bash filename
```


(the password that it prompts you for is your sudo password, not the wireless network password.
The obvious problem with this is that your password is now in plain text in that file but if that isn't a problem for you then this should work.

Don't have the foggiest idea how to help you make network manager work. Sorry.

---

### Post by delfick on 2007-10-19
k then.......

thnx :D

for gettting it into network-manager, I've filed this bug here [http://bugzilla.gnome.org/show_bug.cgi?id=488221](http://bugzilla.gnome.org/show_bug.cgi?id=488221)

but I've also found wpagui, so I'll try that out on Monday when I'm back at uni...

---

### Post by haldor61 on 2007-10-19
i had a same problem because of my university but i solved that problem(on feisty) adding my password and username in to the wpa_supplicant.conf
and then i added "pre-up wpa_supplicant -i eth0 -c /etc/wpa_supplicant.conf -D wired" into network/interfaces
the only problem is that it's starting automatically when you start your computer but it couldn't get an automatic ip you should write sudo dhclient eth0 then there is no pproblem..
however on gusty i couldn't do samne thing and i need help:)

---

### Post by delfick on 2007-10-24
hmm, wpa-gui didn't work and my bug hasn't received any attention.....

anyone have any more ideas ?? :D

---

### Post by delfick on 2007-10-24
sorry, ignore this post

---

### Post by delfick on 2007-12-15
sorry, to bump this thread again....

but does anyone know of any progress for this in the network manager?

it'd be so nice for internet to just work when I'm using linux at uni.

:D

---

### Post by delfick on 2008-04-28
the network manager seems to work now :)

in ubuntu-hardy...

(hopefully this isn't a one-off-miracle :P)

---

