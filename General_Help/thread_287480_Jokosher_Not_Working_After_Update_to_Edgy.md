---
title: "Jokosher Not Working After Update to Edgy"
date: 2006-10-28
forum: General Help
---

### Post by citizenkeith on 2006-10-28
I was originally running Dapper, and managed to install Jokosher via cvs. However, I wasn't able to actually record any audio, but I could start up the program and create a project.

Last night I updated to Edgy. I deleted the original Jokosher (a folder labeled "trunk" in my Home directory). Then I fired up Synaptic and installed Jokosher. I started it up from the Applications menu, and nothing happened.

I pulled up a terminal window and typed 

```
jokosher
```

Here is what came up:

```
Starting up
Traceback (most recent call last):
  File "/usr/share/jokosher/Jokosher.py", line 1058, in ?
    main()
  File "/usr/share/jokosher/Jokosher.py", line 1053, in main
    app=MainApp()
  File "/usr/share/jokosher/Jokosher.py", line 153, in __init__
    self.OpenRecentProjects()
  File "/usr/share/jokosher/Jokosher.py", line 688, in OpenRecentProjects
    self.SaveRecentProjects()
  File "/usr/share/jokosher/Jokosher.py", line 711, in SaveRecentProjects
    Globals.settings.write()
  File "/usr/share/jokosher/Globals.py", line 44, in write
    file = open(self.filename, 'w')
IOError: [Errno 21] Is a directory: '/home/keith/.jokosher'

```

On a whim, I opened Python.py and commented out lines 153 and 154:

```
		# populate the Recent Projects menu
		self.OpenRecentProjects()
		self.PopulateRecentProjects()
```

Now Jokosher would run, but I couldn't get past the new projects window. I'd try to create a project, but I got this error window:

```
Unable to create project.

A file or folder with this name already exists. Please choose a different project name and try again.
```

The only problem is that the project name did NOT actually exist, and anything I try gets the same error.

As a last resort, I pulled the old "trunk" folder out of the trash and put it back in my Home directory. Nothing changed.

It looks to me that my previous installation of Jokosher is in conflict.     I tried posting this in the Jokosher forums, but their forum sign-up spit out an error too, so I can't register and post! I'm having terrible luck this evening. :D

---

### Post by citizenkeith on 2006-10-28
bump :)

---

### Post by Aerandir on 2006-10-28
Jokosher is still very alpha right now.  They *just* came out with 0.1 release I think.  From what I've read, there is still a lot more to implement.

---

### Post by citizenkeith on 2006-10-29
> **Aerandir said:**
> Jokosher is still very alpha right now.  They *just* came out with 0.1 release I think.  From what I've read, there is still a lot more to implement.

I realize that it's in alpha... but it IS offered in the Edgy repositories. I know some people have this program working, so I'm pretty sure I could get it working with the proper help.

---

### Post by jonobacon on 2006-10-31
Hey, I think there are some problems with Jokosher in Edgy - remember it is in the Universe repository, and some stuff may have broken. This can happen occassionally, and Jokosher requires bleeding edge GStreamer packages.

We are currently working towards our 0.2 release that resolves many of these issues. :)

---

### Post by citizenkeith on 2006-10-31
Hi Jono,

I recently subscribed to the developer's mailing list, so I'm following your progress. I'm really excited about this software. I'm not a programmer, but I can probably do some testing for you. :)

---

### Post by David Corrales on 2006-11-11
> **citizenkeith said:**
> Hi Jono,

I recently subscribed to the developer's mailing list, so I'm following your progress. I'm really excited about this software. I'm not a programmer, but I can probably do some testing for you. :)

I'm really excited too :) I even went ahead and did all spanish translations!

---

### Post by rafaelcapanema on 2007-01-29
One weird solution I've discovered by chance: create a new user account without administrative privileges, log on in it an run Jokosher. Works for me!

---

