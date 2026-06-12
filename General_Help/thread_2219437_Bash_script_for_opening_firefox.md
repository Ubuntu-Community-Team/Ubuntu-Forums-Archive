---
title: "Bash script for opening firefox"
date: 2014-04-24
forum: General Help
---

### Post by adam17 on 2014-04-24
Hi,

I have a server at home that I am able to access over the net but when inside my own network it requires me to use the internal address not the www. adress. Regardless, for this reason I have created a script to access the server in two different ways depending on what network I am connected to eg. Home or Other

The code is below:

[FONT=arial narrow]#!/bin/bash
AP=$(iwconfig eth1 | grep 'ESSID:' | awk '{print $4}' | sed 's/ESSID://g' | sed 's/"//g') #looks up network name that I am connected to
HOME='Home-Network-Name'    #The name of my home network
if [ $AP == $HOME ]    #Compairs network connection name to Home network name
then
    notify-send "$AP" "Accessing Media Server Torrent Control from inside home network" #popup message
    firefox 'Internal-Server-Address+port'    #start firefox and goto address
    sleep 2    #code pauses for 2 seconds 
    killall notify-osd    #kills the popup message
    
else
    notify-send "$AP" "Accessing Media Server Torrent Control from outside home network" #popup message
    firefox 'external connection address + port' #start firefox and goto address
    sleep 2 #code pauses for 2 seconds 
    killall notify-osd #kills the popup message
fi[/FONT][I][FONT=arial]
[/FONT][/I]
my problem is the starting of firefox.

if I have firefox already open the script works as it is supposed to. However if firefox is not open it get an error  

 

 Your Firefox profile cannot be loaded. It may be missing or inaccessible
 

 &
 

 (firefox:14441): GnomeUI-WARNING **: While connecting to session manager: 
 None of the authentication protocols specified are supported. 
 

 Can anyone help with this?
 

 Thanks
 

 Adam

---

### Post by ian-weisser on 2014-04-24
What user or condition is triggering the script?

---

### Post by Vaphell on 2014-04-25
don't use all-caps names because you risk overriding some crucial settings. You just did exactly that with $HOME which is not supposed to be a user variable (it points to user's home dir).

also instead of that long chain of pipes you can get ap with 1 awk
```
iwconfig eth1 | awk -F'"' '/ESSID/{print $2}'
```

and wrap your code in [noparse]```

```[/noparse] tags.

---

### Post by adam17 on 2014-04-25
Hi,

Thanks for the reply, I actually managed to solve this myself just before you said about the HOME, only by luck rather than actually knowing what I was doing.

Thanks again.

---

