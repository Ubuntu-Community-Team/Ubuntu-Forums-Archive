---
title: "Cannot add desktop icons after 13.10 upgrade"
date: 2013-10-19
forum: General Help
---

### Post by huxley2 on 2013-10-19
Hi, everybody

After upgrading from 13.04 to 13.10 some of the desktop icons had turned grey and locked. When I originally - and successfully - added application icons to desktop I dragged and dropped from Application onto desktop and used the cmd's:

```
sudo chmod +x ~/Desktop/*.desktop
sudo chown <username> ~/Desktop/*.desktop
```

So, after deleting the grey icons I re-entered the cmd but this time when I attempted to drag and drop I received a warning box stating:

```
Error While copying
There was an error getting information about “/”
The specified location is not supported

```

Does anyone know what went wrong and better yet how to mend the situation?

Regards

Hux

---

### Post by mc4man on 2013-10-19
A DnD is basically a move, you don't have permission to do so from /usr/* or anywhere root owns

So just use copy & paste

---

### Post by huxley2 on 2013-10-19
Copy and paste from where? I can't do it from the Applications menu. I thought that the chown cmds I used last time were supposed to give ownership of desktop...which they did

---

### Post by mc4man on 2013-10-19
From where the majority of app .desktops are - /usr/share/applications

---

### Post by huxley2 on 2013-10-19
Thanks, Mc4man problem solved. I still can't get the libre icons in colour - before I kept office in launcer and the rest on desktop - but thats not a big deal.

Regards

---

### Post by mc4man on 2013-10-19
> **huxley2 said:**
> Thanks, Mc4man problem solved. I still can't get the libre icons in colour - before I kept office in launcer and the rest on desktop - but thats not a big deal.

RegardsNot exactly sure what you mean by 'color' but try this
Remove one of the libreoffice lauchers in question from your Desktop

Then navigate here, copy & paste the appropriate .desktop to your Desktop, make executable & see if that resolves

/usr/lib/libreoffice/share/xdg

(- ex. - libreoffice writer would be "writer.desktop"

What's in /usr/share/applications for libreoffice are just links to the actual .desktop's in above location

---

### Post by huxley2 on 2013-10-19
Thanks, Mc4man but still no dice. 

By colour I mean that the icons are grey with a lock symbol in bottom right corner. I tried the other way you suggested and the icons came out even more basic. I couldn't make them executable as Root is the owner and refused me permission, which is kinda why in 13.04 I used the chown cmd and that gave me normal icons for libre.

 As far a I can make out it's only the libre icons acting this way so I think I'll just let it slide. 

Thanks again for the help

---

### Post by mc4man on 2013-10-19
"I couldn't make them executable as Root is the owner and refused me permission, which is kinda why in 13.04 I used the chown cmd and that gave me normal icons for libre."
As you are willing to let slide maybe I should but curiosity...

Are you using a root file browser to do the copy & paste from?

Or does root own your Desktop folder or some files on? (you should not be needing to chown Anything on your Desktop, nor using sudo to chmod Any file in your Home directory inc. the Desktop

What does this show?
ls -la Desktop

or this, should only return 1 entry
ls -la |grep root

---

### Post by mc4man on 2013-10-19
I'm going to attach a small vid that shows the simplest means to do this, in this case copying the .desktop for dconf-editor to my Desktop
Note that files copied from /usr/share/applications are ready to go once copied, no 'chown', no 'chmod', no nothing
.desktops copied from elsewhere like libreoffice may need to be made executable, nothing more (& Not with sudo

(to make the size needed to attach I only recorded part of Desktop, should be enough.

---

### Post by huxley2 on 2013-10-19
O.k, so I own my desktop - just checked - and copying over any other app  icon to Desktop worked straight away. But the libre icons moved to  desktop were owned by root. Before reading your previous two messages I  chowned the libre icons on desktop which allowed me to make them  executable and after refresh everything was normal - full colour icons.


The 2nd terminal cmd you gave me came back as:

```
drwxr-xr-x  3 root  root  4096 Oct 18 18:50 ..
drwx------  2 root  root  4096 Oct 19 20:49 .gvfs

```

When I installed Ubuntu I did it manually with 3 partition: a 22GB partition set as /, a swap and a data partition.

It's getting late now so I'm off to bed. If anyone replies I ay be a few hours responding...

Thanks again

---

### Post by mc4man on 2013-10-20
> **huxley2 said:**
> O.k, so I own my desktop - just checked - and copying over any other app  icon to Desktop worked straight away. But the libre icons moved to  desktop were owned by root. Before reading your previous two messages I  chowned the libre icons on desktop which allowed me to make them  executable and after refresh everything was normal - full colour icons.


The 2nd terminal cmd you gave me came back as:

```
drwxr-xr-x  3 root  root  4096 Oct 18 18:50 ..
drwx------  2 root  root  4096 Oct 19 20:49 .gvfs

```

When I installed Ubuntu I did it manually with 3 partition: a 22GB partition set as /, a swap and a data partition.

It's getting late now so I'm off to bed. If anyone replies I ay be a few hours responding...

Thanks again
Not sure why you're libreoffice .desktops copied as root, but otherwise all looks fine
the presence of .gvfs in your home folder (owned by root) does indicate you probably used sudo with a gui app, most likely gedit or nautilus.
There's no need for .gvfs in your home dir. so you can delete it.
(and refrain from running sudo gedit or sudo nautilus

---

### Post by huxley2 on 2013-10-20
Thanks, Mc4man that's a relief to know, you've been a top help. I used gksudo gedit to add my data partition and UUID to fstab but as a rule I don't like playing about with it and now have further reason not to.

---

