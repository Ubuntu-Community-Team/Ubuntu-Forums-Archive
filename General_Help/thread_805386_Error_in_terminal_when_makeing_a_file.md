---
title: "Error in terminal when makeing a file"
date: 2008-05-23
forum: General Help
---

### Post by illbashu on 2008-05-23
ok i am trying to get fuppes to work i need to make a file useing terminal

error
```

root@raza-desktop:/home/raza# sudo gedit /etc/network/if-up/fuppes

** (gedit:8586): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

```

this is what i am suppose to do....


> 
Configure multicast route on your machine for the media server to be found by clients, create a file /etc/network/if-up/fuppes with the following content (substitute the interface for the one you are using on your machine) 

```
#!/bin/bash
#
# in this case eth1 is my WLAN interface change to match yours
if [ "" = "eth1" ]; then
        ip ro add 239.0.0.0/8 dev eth1
        /etc/init.d/fuppes restart &>/dev/null
fi
```

tutorial i am following...
[http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04](http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04)

this is what i typed into terminal
```
sudo gedit /etc/network/if-up/fuppes
```

then i pasted in 
```

#
# in this case eth1 is my WLAN interface change to match yours
if [ "" = "eth0" ]; then
        ip ro add 239.0.0.0/8 dev eth1
        /etc/init.d/fuppes restart &>/dev/null
fi
``` 

and i hit save and i got that error :(

---

### Post by tamoneya on 2008-05-23
type ```
sudo touch /etc/network/if-up/fuppes
```Then try your code again.

---

