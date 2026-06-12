---
title: "Gnome + some gnome applications blank/not working"
date: 2007-07-04
forum: General Help
---

### Post by UrbanSlayer on 2007-07-04
For a little while now, some Gnome apps have been coming up like the attached screenshot, so while the window loads, its blank.

It isnt effecting all gtk apps, for instance Sonata, X-Chat, Firefox etc, but some gnome apps, like gnomine, Mahjongg, the gnome-control-centre etc.  GDM loads fine, but gnome itself doesnt, it just brings up a blank screen with an X for the cursor.  I can only close the gnome apps by clicking on the X in the top right corner, and then waiting for the Not Responding dialog to appear, at which point i have to terminate the application.

I've looked at any log file I can think of within /var/log, but there are no errors appearing at all.  Can anyone suggest a log file to check?

I am currently running/using KDE and all the KDE apps appear fine, it is just the gnome ones.

Can anyone help?

Thanks

---

### Post by AlexThomson_NZ on 2007-07-04
It looks to me like you might me missing some core gnome libraries or something in your gnome/kde frankenstein ;)

When you open these apps in a terminal window, does it throw any errors or anything?

---

### Post by rodo-&gt;dave on 2007-07-04
Hi. I think Sonata is a java app:

try adding AWT_TOOLKIT="MToolKit"  to your /etc/environment file.

... may require a reboot to see the changes... 

so 
you could just export the var on the cli and start the app from there to test it...

---

### Post by rodo-&gt;dave on 2007-07-04
Oh... sorry 'typed' too soon... It appears that your sonata is working..

---

### Post by UrbanSlayer on 2007-07-04
Whoops, sorry, forgot to mention the terminal.  Thats almost the oddest thing, I've tried them from the terminal (gedit, gnomine, gnome-control-centre etc), but when I do, nothing happens.  Nothing at all.  No windows appear, no errors appear, the cursor just drops to a newline and sits there.  The prompt doesnt reappear, so it does appear to do what you would expect from loading an app from the terminal (without the trailing & at least).

I've also run ps -ef | grep gedit etc and the process is there, I can kill it, and its goes away.  It doesnt take 100% either, so I am somewhat at a loss to know whats going on.  I'm pretty certain I havent removed any gnome libraries etc.


Ok, update, as I was typing this post, I left the gedit prompt just sitting there.  I havent left it this long before, it was at least 3-4minutes, and eventually it loaded.  So now I am confused..it doesnt appear to broken, just unusably slow.  Whats going on?

---

### Post by AlexThomson_NZ on 2007-07-04
I guess you already checked /var/log/gdm/:0.log?

// I'd backup & reinstall

---

### Post by UrbanSlayer on 2007-07-04
Ya, nothing in there either.  I may have found the cause, although I'm not currently certain on the fix - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048)
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/26419](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/26419)

It does sound like my problem, but I cant seem to resolve it..am going to reboot now and see what happens.

---

### Post by UrbanSlayer on 2007-07-05
Well, fixed it.  I ran an strace over gnome-terminal, found that when it tried to connect to 127.0.0.1 it was timing out after trying for 3min.  I had misconfigured my firewall (used KMyFirewall), have fixed it and now all ok.

Cheers!

---

