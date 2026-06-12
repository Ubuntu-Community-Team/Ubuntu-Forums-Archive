---
title: "Recent evolution update breaks gnome / nautilus"
date: 2008-06-07
forum: General Help
---

### Post by lukemack on 2008-06-07
Hi,

The recent update manager updates for evolution have broken some parts of gnome on my system (8.04). Places in the 'Places' menu such as Home and My Computer no longer work and all desktop icons have disappeared - disabling and re-enabling in gconf-editor does NOT fix this problem.

Anyone else having the same problem or know of a fix? I think the problem package may be evolution data-server-common 2.22.2-0ubuntu1 as this seems to have gnome dependencies if I mark it for removal. I'm not keen to do that without knowing the consequences though.

Thanks for any input.

lukemack.

---

### Post by rraj.be on 2008-06-07
Try this

```

sudo apt-get update
sudo apt-get install build-essentials
```

---

### Post by lukemack on 2008-06-07
its build-essential (no s) i think? and I already have the latest version. Do I need to uninstall / reinstall? If so, could you explain why you think this would help? I did the apt-get update too.

many thanks for th reply!

---

### Post by kaboodle_fish on 2008-06-07
I have just updated Evolution with no problems here and checked to see and I am on the same version of date-server-common as yourself 

If there is any other installed dependencies for Evolution you want me to check let me know

---

### Post by rraj.be on 2008-06-07
> **lukemack said:**
> Hi,
I think the problem package may be evolution data-server-common 2.22.2-0ubuntu1 as this seems to have gnome dependencies if I mark it for removal. 




this is the reason.

You might have just removed dependences of gnome.

Tis problem is the result of that.

In windows each applicationwill hav their own librry files and hence deletion of one application wont affect another.

But in linux all libraries are shared and the removal will affect all others.

```

I'm not keen to do that without knowing the consequences though.
```

much happy to here that.But updates will never be a wrong thing.

---

### Post by rraj.be on 2008-06-07
> **kaboodle_fish said:**
> If there is any other installed dependencies for Evolution you want me to check let me know


Cant get you. be a bit more clear plz.

---

### Post by lukemack on 2008-06-07
I didnt remove anything. I just marked it for removal, noticed it was going to remove some stuff I wasnt sure about and so cancelled. All I did was install the updates this morning. 

Ive also noticed that right-clicking the desktop no longer works and the Deleted items gnome panel applet has stopped working i.e nothing happens when I click on it.

---

### Post by rraj.be on 2008-06-07
Are you sure you havn't removed the dependences.

If update requeted removal of packages and then how you updated with out removing those marked for removal..


If you are sure that you havn't deleted the packages then you  should restart and this should fix the problem for you.

---

### Post by lukemack on 2008-06-07
The update did not request the removal of packages. After I noticed the problem, I just looked in synaptic to see what the dependencies were. I have rebooted several times - no change.

---

### Post by kaboodle_fish on 2008-06-07
> **rraj.be said:**
> Cant get you. be a bit more clear plz.

I have also updated Evolution and it has not caused any issues with the Places menu here so I was just saying that I could let you know if the versions of dependent programs I had were the same so you could cross reference that was all

---

### Post by lukemack on 2008-06-07
This error occurs when running nautilus on the command line:

luke@vaio-ubuntu:~$ nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension
**
** Eel:ERROR:(eel-preferences.c:116):preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)
Aborted
luke@vaio-ubuntu:~$ 


basically i think nautilus cannot start which is causing the problem

---

### Post by rraj.be on 2008-06-07
try it like sudo nautilus

---

### Post by lukemack on 2008-06-07
ah ok - now that works and some desktop icons are back but obviously its using the root user preferences file now.

any idea how I can migrate my settings from one user to another?

i now think this has nothing to do with the evolution install - just a coincidence. I think I have corrupted my nautilus preferences somehow.

---

### Post by buntunub on 2008-06-07
Do this command in Terminal:

```
sudo /etc/init.d/dbus restart
```

That should do it for ya. If not, you may need to give a reinstall of Nautilus a shot and see what happens.

---

### Post by lukemack on 2008-06-07
Thanks for all your help guys - this is now RESOLVED.

---

### Post by moogle on 2008-06-09
lukemack
I'm experiencing similar issue, please post your resolution so others can benefit. In addition it seems I've lost all sound support as well. Tried restarting alsamixer to no avail.

---

