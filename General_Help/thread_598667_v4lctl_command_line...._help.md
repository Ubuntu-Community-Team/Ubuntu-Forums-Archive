---
title: "v4lctl command line.... help"
date: 2007-10-31
forum: General Help
---

### Post by Bally on 2007-10-31
Hi

I have run v4lctl list and can see the status and default status of the v4l module. I want to modify the settings fro mute and automute but need the "handlers" to instruct it.

I need to change specifically "automute" and "mute" to help me enable sound from my tv tuner card

For example, v4lctl set mute off, v4lctl mute off ..etc all return: unknown handler "set" or  "mute" etc..

Anyone know the commands I need, any other commands for the other settings such as vol, brightness etc... would also be appreicated.



Cheers Bally

---

### Post by Bally on 2007-10-31
Typical ....post a question then minutes later figure out the answer myself.....

[http://linux.about.com/library/cmd/blcmdl1_v4lctl.htm](http://linux.about.com/library/cmd/blcmdl1_v4lctl.htm)

All i needed to know and proves that automute was preventing sound from saa7134 / pctv tuner card.

hope this helps someone....

bally

---

