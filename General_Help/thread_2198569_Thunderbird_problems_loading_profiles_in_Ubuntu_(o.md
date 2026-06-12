---
title: "Thunderbird problems loading profiles in Ubuntu (old Windows 7 profiles)"
date: 2014-01-09
forum: General Help
---

### Post by marc13 on 2014-01-09
I have a thunderbird profile on an external harddrive that I copied to my Ubuntu system. 

The profile works perfectly with Windows 7. 

I go into Profile Manager in Ubuntu (I am root) by typing "thunderbird -p" in the console

I find the path of my profile, select that, and click "Start Thunderbird"

The output in the console is everytime this: 
** (thunderbird:26736): WARNING **: The connection is closed

** (thunderbird:26736): WARNING **: Unable to create Ubuntu Menu Proxy: The connection is closed

(thunderbird:26736): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I have installed Simple interprocess messaging system (X11 deps), aka. dbus-x11 as suggested after doing some Google searching on this matter. I am however stuck right now, and it would be great if anyone had same experience they solved.

---

### Post by marc13 on 2014-01-10
Can anyone help? It is detrimental for me to get Thunderbird working in Ubuntu, plz help

---

