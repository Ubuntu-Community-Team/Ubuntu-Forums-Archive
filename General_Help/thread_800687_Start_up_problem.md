---
title: "Start up problem"
date: 2008-05-20
forum: General Help
---

### Post by misshannah on 2008-05-20
I've recently installed Ubuntu on my laptop and now the majority of the time I start it up it does the ubuntu loading screen then goes black, and never changes to the log in screen. 
When I press the restart button the same thing happens most of the time. But if I reset it by pulling out the battery and then putting it back in it seems to start up just fine. My laptop never did this with windows. 
Is it just a coincidence that it's happened at the same time I installed Ubuntu?

---

### Post by danwood76 on 2008-05-20
I would think that there is some issue with some hardware on your system.
Possibly a graphics driver or something else.

To find out X errors do the following:

When you bootup, screen goes black, press Ctrl+Alt+F1, this should present you with a text login screen.
Then run this command:
```

cat /var/log/Xorg.0.log | grep '(EE)'

```
That will display any errors that the X server had when booting up.
Please post them.

To shutdown your machine from the command line run:
```

sudo shutdown -h now

```
Remember the command line is case sensitive and its important that you type the commands exactly as I have written them.

---

### Post by misshannah on 2008-05-20
Thanks for that. You were right about the drivers, pretty sure it's the wireless. Took some fiddling to get it work in the first place. I've discovered that it boots up fine if I flick the wireless switch off until ubuntu is fully started up.

---

### Post by danwood76 on 2008-05-20
What wireless card do you have in your laptop?
And does the wireless work?

---

### Post by misshannah on 2008-05-22
It's an atheros 5007 in an asus f5RL laptop. 
The wireless didn't work at first, apparently that card isn't supported by Ubuntu but I showed it to a friend who's been using Linux for far longer than me and he managed to get it working. Unsure exactly what he did though.

---

### Post by danwood76 on 2008-05-22
That wireless card isnt supported by the madwifi project due to an incompatible HAL. (blame atheros)
I have the same card in a PCI-E desktop version, so no wireless switch for me.

The fix to get wifi working on that card is to patch and compile the madwifi source which I assume is what your friend has done.
Sorry I cant help any further with the wifi switch issue, that driver uses a closed source binary lump which cant be easily modified.
But if your ok switching it off to boot then I see no issue.

---

### Post by misshannah on 2008-05-22
Well, thanks for your help. :)

---

