---
title: "Mounting Network share"
date: 2014-04-23
forum: General Help
---

### Post by Ipeek on 2014-04-23
Hello,

I'm needing to know how to mount a network drive that I've got via the cli. It shows up in the "Browse Network" as does every other share on my network. I need to specifically mount a sub dir on that share. 

Can someone help me out? I have looked around and nothing seems to work for me. I know the share I need is on a centos server. If you need anything else, let me know.


Thanks,

---

### Post by bab1 on 2014-04-23
> **Ipeek said:**
> Hello,

I'm needing to know how to mount a network drive that I've got via the cli. It shows up in the "Browse Network" as does every other share on my network. I need to specifically mount a sub dir on that share. 

Can someone help me out? I have looked around and nothing seems to work for me. I know the share I need is on a centos server. If you need anything else, let me know.


Thanks,
If this is a CIFS (SMB) share then the proper way is to mount the share like this```
//SERVER_NAME/SHARE_NAME
```

Are you thinking of using a script or edit the fstab file to mount the share?

---

### Post by Ipeek on 2014-04-24
I am thinking of using a script. My end users hot desk and will need access to their files on that server. I've not yet thought of a way for this to happen quite yet but I figure with some minor scripting they could input the name of their sub dir (ie mine is ipeek) and it would tag it on to the end of the //servername/employeedocs/Specific_employee. Not sure if that is possible.

---

### Post by steeldriver on 2014-04-24
Have you considered using autofs? I've only used it with NFS, but it should do what you want out of the box (i.e. automatically mount each user's remote home directory on demand)

---

### Post by bab1 on 2014-04-24
> **Ipeek said:**
> I am thinking of using a script. My end users hot desk and will need access to their files on that server. I've not yet thought of a way for this to happen quite yet but I figure with some minor scripting they could input the name of their sub dir (ie mine is ipeek) and it would tag it on to the end of the //servername/employeedocs/Specific_employee. Not sure if that is possible.
Why not just use the [homes] share? The [homes] share does exactly what you are talking about.

---

### Post by Ipeek on 2014-04-28
Okay maybe one of you can help me out.

I've got the script working when I run it from the command line and it looks like this:

```
#!/bin/bash

echo "Username :"
read name

sudo mount //myserverip/dir/subdir/$name /home/dirwhere/itneeds/tobe/mounted/$name
```

I've set it up in visudo etc.... to get it to run with out prompting for the password. When I start the script from terminal it works perfectly. What I need it to do is be "launch-able" from double clicking on the icon. Now I can get it to do this when the Nautilus settings are set to "prompt text file each time" or what ever the name of that setting is and choose to run in terminal. The only problem is that i don't want it to confuse my end users. Is there a way around this? Is there something I can add at the top of the script that will force a terminal to open and run the commands?

Thanks

---

### Post by Ipeek on 2014-04-28
I've gotten it to work by calling it from another script that has 
```

[FONT=Times New Roman][SIZE=3][COLOR=#000000]x-terminal-emulator -e /location/of/script.sh[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]
```[/COLOR][/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3][COLOR=#000000]I did try adding that above the username call but it ran in an infinite loop and nearly killed the little pc it was running on.

The problem I've now encountered is that the share that is mounted is read-only unless I open something in the share under root.(ie run nautilus as root and nav to it and open it)

Any ideas?[/COLOR][/SIZE][/FONT]

---

