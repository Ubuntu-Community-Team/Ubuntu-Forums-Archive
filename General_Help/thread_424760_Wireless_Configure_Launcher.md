---
title: "Wireless Configure Launcher?"
date: 2007-04-27
forum: General Help
---

### Post by athleticbum32 on 2007-04-27
I have an Atheros wireless card and would like to save time putting it into monitor mode with a launcher. I have only figured out how to create one with a single line in command: 

gksudo "wlanconfig ath1 create wlandev wifi0 wlanmode monitor"

That works ok, but id like to clean it up a bit. Ive put some time into trying to write a script and launching that, but no go. This is my best shot:

Monitor.sh

    #!/bin/bash

    gksudo gnome-terminal
    ifconfig ath0 down
    wlanconfig ath0 destroy
    wlanconfig ath1 create wlandev wifi0 wlanmode monitor
    ifconfig ath1 up
    iwconfig

Managed.sh

    #!/bin/bash

    gksudo gnome-terminal
    ifconfig ath1 down
    wlanconfig ath1 destroy
    wlanconfig ath0 create wlandev wifi0
    ifconfig ath0 up
    iwconfig

As you can see i know little, well nothing about scripts. And id really like to know where i messed up. So i am ready to start learning if someone is there to teach me.

Also if there is an easier way to issue these commands with one click of a launcher, i up for that.
Id like to save some time in the future to make up for the time ive screwed around with here.

---

### Post by athleticbum32 on 2007-04-28
Well alright with another hour of messing around i figured a way out. I edited the two files a little and checked to see if they were execuable. Here they are:

Monitor.sh

gksudo "ifconfig ath0 down"
gksudo "wlanconfig ath0 destroy"
gksudo "wlanconfig ath1 create wlandev wifi0 wlanmode monitor"
gksudo "ifconfig ath1 up"

Managed.sh

gksudo "ifconfig ath1 down"
gksudo "wlanconfig ath1 destroy"
gksudo "wlanconfig ath0 create wlandev wifi0"
gksudo "ifconfig ath0 up"

I just put the file paths in the launcher and it works. I guess it was more simple than i thought.

---

