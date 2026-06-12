---
title: "Pidgin doesn't run."
date: 2008-05-30
forum: General Help
---

### Post by carlwenrich on 2008-05-30
The cursor changes and it looks like something is loading. Then the cursor returns to normal, but nothing appears.

---

### Post by tamoneya on 2008-05-30
first remove and reinstall pidgin```
sudo apt-get remove pidgin
sudo apt-get install pidgin
```Now instead of clicking the pidgin icon try running it through terminal```
pidgin
```Then copy whatever debugging output that gives you and post it here.

---

### Post by EXCiD3 on 2008-05-31
Probably a better thing to do that just remove pidgin is to purge it. Replace the first line tamoneya mentions with this one:
```
sudo apt-get remove --purge pidgin
```

This will remove configuration files that might be causing the problem. Also have you installed any extra plugins? Sometimes these will cause pidgin to crash.

---

### Post by tamoneya on 2008-05-31
> **EXCiD3 said:**
> Probably a better thing to do that just remove pidgin is to purge it. Replace the first line tamoneya mentions with this one:
```
sudo apt-get remove --purge pidgin
```

This will remove configuration files that might be causing the problem. Also have you installed any extra plugins? Sometimes these will cause pidgin to crash.

I was trying to save the config files if possible.  I know that I would have a lot of work to do if I had to reconfigure pidgin from scratch.  The most important thing however in the above post is the result of "pidgin" in terminal.

---

### Post by carlwenrich on 2008-05-31
The remove worked, but the install ended with:

ppp@ppp-desktop:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pidgin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libpurple0
E: Package pidgin has no installation candidate

---

### Post by EXCiD3 on 2008-05-31
Try searching synaptic for pidgin and installing there. Weird that it cant find it. What version of Ubuntu are you using?

---

### Post by inportb on 2008-05-31
this might be a stupid question, but w/e:
have you done an *apt-get update*?

also, what repositories have you got in your */etc/apt/sources.list*?

---

### Post by carlwenrich on 2008-05-31
Ok, I've installed it with synaptic. I tried running it from the icon... nothing. Then from the command line... nothing.

---

### Post by carlwenrich on 2008-05-31
When I run it with debug I get this:

Gtk: gtk_main_quit: assertion `main_loops != NULL' failed

---

### Post by EXCiD3 on 2008-05-31
you dont happen to have a /home/<username>/.gaim folder by chance? other users getting the same issues have just deleted the xml files out of that folder and pidgin has resumed working correctly. You might want to check this out, but thats all i cant think of so far, other than deleted the .purple folder from your home directory also. If you dont mind losing your configuration settings try a --purge if you havent already.

---

### Post by drs305 on 2008-05-31
This may be overly simplistic, but when I started using pidgin (all the way back last week) I thought it wasn't starting because I didn't notice the icon was appearing in my top panel. That was all it did until I clicked on the icon. It's a green ball. Apologies if this is obvious to everyone but me... ;-)


Oops - didn't see the debug error. Oh well, I made EXCiD3 laugh!

---

### Post by EXCiD3 on 2008-05-31
> **drs305 said:**
> This may be overly simplistic, but when I started using pidgin (all the way back last week) I thought it wasn't starting because I didn't notice the icon was appearing in my top panel. That was all it did until I clicked on the icon. It's a green ball. Apologies if this is obvious to everyone but me... ;-)

lol i wish it was that simple, but if he's getting an error using pidgin debug mode then im sure thats not the problem. hope you like pidgin, im hooked and cant get used to anything else...oh how i hate kopete!

---

### Post by carlwenrich on 2008-05-31
No, I don't have a .gaim folder, and I renamed the .purple folder. When I run pidgin --debug I get this:

Gtk: gtk_main_quit: assertion `main_loops != NULL' failed

What does this mean?

---

### Post by EXCiD3 on 2008-06-01
I'm not exactly sure. It has something to do with calling the GTK interface and creating the windows for pidgin. 

I found a thing saying that "sudo pidgin" will allow it to run. Try that and see what happens, at least you can use it for a little while until we find a fix.

---

### Post by EXCiD3 on 2008-06-01
Interesting...it seems that this is caused by multiple instances of pidgin running. Open up System Monitor (in System > Administration menu) and go to the processes tab to make sure no instances of pidgin are already running. If there are end the tasks and then try running pidgin normally again.

---

### Post by carlwenrich on 2008-06-01
Ok, sudo pidgin runs, and after I add an account I get the Buddy List window with my buddie list showing. But if I close it and then reopen it, my buddie list is gone, and the Add Buddie option is disabled.

---

### Post by carlwenrich on 2008-06-01
I reinstalled it (via synaptic) and now I get this:

(22:00:34) pounce: Error reading pounces: Failed to open file '/root/.purple/pounces.xml': No such file or directory
(22:00:34) ui_main: Failed to load the default window icon (scalablepx version)!
(22:00:34) Session Management: No SESSION_MANAGER found, aborting.
(22:00:34) network: NetworkManager not active or reports no connection (retval = 2)
(22:00:34) network: NetworkManager not active or reports no connection (retval = 2)
(22:00:34) account: Network not connected; skipping reconnect
(22:00:34) docklet: embedded
(22:00:34) network: Entering nm_callback_func!
(22:00:39) util: Writing file prefs.xml to directory /root/.purple
(22:00:39) util: Writing file /root/.purple/prefs.xml
(22:00:39) util: Writing file accounts.xml to directory /root/.purple
(22:00:39) util: Writing file /root/.purple/accounts.xml
(22:00:39) util: Writing file blist.xml to directory /root/.purple
(22:00:39) util: Writing file /root/.purple/blist.xml

---

### Post by EXCiD3 on 2008-06-01
Did you check to see if there were any other instances of pidgin running like i mentioned earlier?

Also, which version of Pidgin are you using and after restarting your computer do you still have the same problems with pidgin?

> **drs305 said:**
> Oops - didn't see the debug error. Oh well, I made EXCiD3 laugh!

:lolflag: made me laugh again! i sure didnt notice that until just now!

---

### Post by carlwenrich on 2008-06-01
yes there were other instances but I killed them

pidgin v1:2.4.1

---

### Post by carlwenrich on 2008-06-01
I just rebooted. Now I can run pidgin from the icon, and it even comes up with my buddie list. But how long will it last?

---

### Post by carlwenrich on 2008-06-01
Well it's broke again. What must I do to run the old gaim?

---

### Post by EXCiD3 on 2008-06-01
Every time it breaks, check to make sure there arent 2 instances of it running. I think the problem you are having is that Pidgin keeps launching and doesnt detect the other version currently running.

Version 2.4.2 of pidgin is available currently. It doesnt look like pidgin 2.4.2 is in the repositories yet, but you could try compiling it from source to see if that helps fix your problem. It could be a bug in the version 2.4.1.

Try to make sure that when you close pidgin, you open the buddy list again with the tray icon. It sounds like you are trying to use the menu to open pidgin again but it is not detecting the previous instance like it should.

---

### Post by carlwenrich on 2008-06-02
I think I finally got it figured out.

When you first click the purple bird, the "loading" cursor spins for a while and then stops, and nothing seems to happen.

Minutes later you get a popup asking for a password.

Then instead of opening a window (like a normal program) it just creates a little green (available) button in the upper right of the screen.

When you click the button, you get the pidgin window.

Hopes this helps other frustrated users.

---

### Post by EXCiD3 on 2008-06-02
You should have pidgin just save your password so it will automatically log you in, if thats what is causing the problem.

---

