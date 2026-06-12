---
title: "Nautilus crashes when browsing &quot;/&quot;"
date: 2008-05-15
forum: General Help
---

### Post by yanyan_leung on 2008-05-15
My Ubuntu version is 8.04 LTS Desktop Edition installed by Wubi and have been used for a few weeks. 

Nautilus crashes when browsing "/" then it reappears showing my home folders. I use "sudo nautilus" in terminal to open nautilus and when it browse "/" it shows:

Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6244): WARNING **: Unable to add monitor: Operation not supported

(nautilus:6244): GLib-GIO-CRITICAL **: g_unix_mount_is_system_internal: assertion `mount_entry != NULL' failed
Segmentation fault

Some other problems are also found, for instance, when I click "Computer" and "Network" in the panel , it shows "Couldn't display "computer:". Nautilus cannot handle computer:locations." and "Couldn't display "network:". Nautilus cannot handle network:locations."

Originally, there is a list showing the removable media and other partitions, like this: [IMG]http://who.hasfiles.com/img/map_ubuntu1.png[/IMG]
but it has gone now.

I don't know how to solve and I have reinstall nautilus and it made no difference. 
The above situation appeared after I have installed virtualbox and I have deleted it and make no difference.
And I cannot mount the other partion using nautilus by can do so under terminal.
Even I open GParted, the other partitions shows an":!:" and unable tomount it. It shows a sentense"Unable to read the file contents of this filesystem!Because of some operations may be unavailable.

Is there anyone know how to solve these problems? Thanks.:?

---

### Post by yanyan_leung on 2008-05-15
Even  the CD/DVD creator is not work, Couldn't display "burn:///". Nautilus cannot handle burn: locations....:confused:

---

### Post by 7DR3AM7 on 2008-05-27
**Hello my friend, I have the same problem!!!I have searched in internet and as far as I know it's a bug... I didn't find any solution to it..I think I'm gonna reinstall Ubuntu...I miss ubuntu 7.10 :( What the Heck sould we do????Any help here 4 us? Plssssss**

---

### Post by chrisccoulson on 2008-05-27
What happens if you create a fresh user? Does it happen with them also?

And running Nautilus with sudo is very bad. My guess is that you will have some user-specific problems with Nautilus due to parts of your users Nautilus profile now being owned by root

---

### Post by epictetus on 2008-09-08
There is a thread at Launchpad regarding this bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233889](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233889)

If you have this problem, consider posting the details there.  So far, it doesn't seem to be solved.

---

