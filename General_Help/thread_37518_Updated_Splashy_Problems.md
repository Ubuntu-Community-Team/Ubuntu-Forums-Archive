---
title: "Updated Splashy Problems"
date: 2005-05-27
forum: General Help
---

### Post by Staesys on 2005-05-27
I just updated my working splashy via the automatic updates to .1.3 (i think) and now when I boot it gives me an error that "**You passed an undefined mode number.** " and it wants me to choose one. After i get into gnome, I bring up a terminal and type **splashy boot** and it gives me back the errors:

```
** (process:10867): CRITICAL **: spl_find_element: assertion `(GList*)data != NULL' failed
Splashy: reusing FIFO /etc/splashy/splashy.fifo

** (process:10868): CRITICAL **: spl_find_element: assertion `(GList*)data != NULL' failed

** (process:10868): CRITICAL **: spl_find_element: assertion `(GList*)data != NULL' failed
root@ubuntu:/home/paul # FATAL: video.c <130>:
        (#) DirectFBError [DirectFBCreate(&video->dfb)]: File not found!
``` 

Any ideas?

-Paul

P.S.: I changed the vga=792 to vga=791 in the menu.lst file already.

---

### Post by Xian on 2005-05-27
I also updated this package but didn't encounter any similar errors.
I would suggest that you eliminate the possiblity of a config issue.

Open Synaptic, right click on Splashy and choose, 'Mark For Complete Removal'.
Then re-install the package.

This will use only the default config that comes with the new version.
If you still get errors you might visit the [Splashy Forums](http://kalatlug.nanofreesoft.org/index.php?name=PNphpBB2&file=viewforum&f=7).

---

### Post by Staesys on 2005-05-27
I just did this and there is no change. I'll go check out the forums...

---

### Post by Xian on 2005-05-27
There's also a How-To on the Splashy [Wiki](http://wiki.nanofreesoft.org/index.php/Splashy#Download_Splashy-0.1) that includes a catch-all procedure when there appears to be no clear solution. 

This is the relevant section from the Wiki listed below:

_Splashy just doesn't work:_

In debian: 
apt-get --purge remove splashy libdirectfb libdirectfb-0.9-22 libdirectfb-0.9-20 lib++dfb 
rm -f /etc/init.d/splashy* /etc/init.d/usplash* /etc/init.d/debsplash* 
rm -f /etc/rcS.d/S*splashy* 
update-rc.d -f splashy remove 

Edit your /etc/apt/sources.list and add: 

deb [http://splashy.alioth.debian.org/debian](http://splashy.alioth.debian.org/debian) unstable main 

Then run: 
apt-get update 
apt-get install splashy 

Edit your /boot/grub/menu.lst: 

#kopt= ... vga=0x314 

Then run: 
update-grub 

After that, reboot and it should work fine.

---

### Post by Staesys on 2005-05-28
Thanks very much dude, that seems to have fixed it. I'd a rather stoned looking penguin staring at me when I rebooted this time. 

:-)

---

### Post by dolny on 2005-06-14
[QUOTE=Staesys]I just updated my working splashy via the automatic updates to .1.3 (i think) and now when I boot it gives me an error that "**You passed an undefined mode number.** " and it wants me to choose one. After i get into gnome, I bring up a terminal and type **splashy boot** and it gives me back the errors:

```
** (process:10867): CRITICAL **: spl_find_element: assertion `(GList*)data != NULL' failed
Splashy: reusing FIFO /etc/splashy/splashy.fifo

** (process:10868): CRITICAL **: spl_find_element: assertion `(GList*)data != NULL' failed

** (process:10868): CRITICAL **: spl_find_element: assertion `(GList*)data != NULL' failed
root@ubuntu:/home/paul # FATAL: video.c <130>:
        (#) DirectFBError [DirectFBCreate(&video->dfb)]: File not found!
``` 

Any ideas?

-Paul

P.S.: I changed the vga=792 to vga=791 in the menu.lst file already.[/QUOTE]

I have the same error after purging and reinstalling. :(

---

### Post by Xian on 2005-06-14
You purged, removed all those files, did the update-rc.d step and still no dice?
Hmmm... try using the 'vga=0x314' in place of the 791.

---

### Post by dolny on 2005-06-14
Run through it again. Made everything from scratch for the 1000 time and still it doesn't work. OK, the sun will come up sun so I gotta go :/ DAMN!!!!!!!

---

### Post by headswim on 2005-06-20
I have been trying to get Splashy to work, and I followed the steps in this new thread to uninstall and reinstall it.  That part went off without a hitch, and when I shutdown my laptop I do get the default shutdown splash.  However, on boot, I get the normal verbose mode, albeit in a smaller font indicating that the screen mode did change properly.  I also get the following during boot when it would normally be updating the progress bar I think:

     ```
Splashy is not running... no commands can be sent
     Please verify /etc/default/spalshy and /etc/splashy/config.xml for correctness
```

Obviously in /etc/default there is a splashy not a spalshy.  I tried checking the config.xml for spalshy, but there are no typos there.  Is there something else I should be checking?  I didn't want to rename /etc/default/splashy to spalshy to avoid screwing anything else up, and I assure you that is exactly what I get during boot, that spalshy is not a typo on my part.  Any help would be greatly appreciated.

-Jones

---

### Post by njean on 2005-06-29
[QUOTE=headswim]I have been trying to get Splashy to work, and I followed the steps in this new thread to uninstall and reinstall it.  That part went off without a hitch, and when I shutdown my laptop I do get the default shutdown splash.  However, on boot, I get the normal verbose mode, albeit in a smaller font indicating that the screen mode did change properly.  I also get the following during boot when it would normally be updating the progress bar I think:

     ```
Splashy is not running... no commands can be sent
     Please verify /etc/default/spalshy and /etc/splashy/config.xml for correctness
```

Obviously in /etc/default there is a splashy not a spalshy.  I tried checking the config.xml for spalshy, but there are no typos there.  Is there something else I should be checking?  I didn't want to rename /etc/default/splashy to spalshy to avoid screwing anything else up, and I assure you that is exactly what I get during boot, that spalshy is not a typo on my part.  Any help would be greatly appreciated.

-Jones[/QUOTE]


I get the same error

---

### Post by LaSSarD on 2005-07-19
After almost 3 hours searching for files containing "spalshy" inside them, I found only this one:
/etc/init.d/splashy-functions.sh

Misteryously, it only contains the error message that you said... There's something really wrong here O_O

*sorry for bad English

---

