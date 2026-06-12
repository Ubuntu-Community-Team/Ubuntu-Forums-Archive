---
title: "Ubuntu Software Center malfunctioning and unusable"
date: 2013-07-04
forum: General Help
---

### Post by maggiezzz on 2013-07-04
I recently installed Ubuntu 12.04 and the Software Center has been working fine .... Up until a few days ago. Now when I try to open the program, it behaves very erratically and is impossible to use... I will do my best to describe (though I wish I could just take a "video" screen shot and show you!).

When I launch the program, the top title bar and outline of the Software Center window is visible, but the **entire body of the window is transparent** (can see through to all the windows behind it).

The window immediately starts **flashing and jumping around** on my screen, bouncing to a new location on the screen several times a second, often making its way onto the next workspace.... It **bounces so furiously** that I am unable to "catch" it by clicking on the top title bar to lock it in place. I am also unable to switch to any other windows while it's doing this.

The only way to stop the mad window from "bouncing" around my screen is to right click its icon on my launcher and force it to quit! FRUSTRATING!

This bizarre issue is not occuring with any other programs. I have installed all available software updates, and turned my machine on/off several times, but the issue persists. I wasn't able to find any info about this, but being as it's so strange, I wasn't sure how to phrase my search terms .... I am not even able to uninstall the program, because I  can't get the Software Center to work, which is where install/uninstalls  must be done!

I hope this makes sense to someone who can advise how to fix it. Argh!

Thanks!

---

### Post by Dennis N on 2013-07-04
> I can't get the Software Center to work, which is where install/uninstalls must be done!

I don't know what's up with your window, but no, you have other options for installing software. Synaptic is an excellent and powerful package manager. Not too long ago it was the default choice for gui package manager for Ubuntu. No problem with having it installed as well as the Software Center. Of course, you can also install packages from the terminal if you wish using **apt-get** if you know the package name.

**sudo apt-get install synaptic**

will install synaptic (package manager) from the terminal.

---

### Post by Bashing-om on 2013-07-04
maggiezzz; Hi !
If it were me and I wanted to keep  "Software Center" I would - in addition to installing "synaptic" do:
```

sudo dpkg -C 
sudo apt-get install --reinstall software-center

```
A non return from "dpkg - C" is a good thing;
And any errors returned from the "reinstall" can be looked at from the command line.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by maggiezzz on 2013-07-04
**Dennis N:** Ah yes, I forgot about Synaptic...had that on an old version of Ubuntu. Thank you.

So, I installed Synaptic via the terminal as per your instructions, and now I'm trying to locate it in the Dash so I can use it .... but I'm having another problem apparently that I just realized ... My dash is totally empty :( ....

[ATTACH=CONFIG]244408[/ATTACH]

Can't get anything to show up in the Dash regardless of which of the 5 bottom icons I click. I don't have any text entered up in the Search bar.

Since y'all are here, any help with this one???

**Bashing-om: **Thanks, I will run those commands after I figure out what's up with my dash and can find Synaptic!

Sorry if these questions are kinda "duh," I've been having difficulty finding my way around and trouble shooting on 12.04 since I upgraded. Appreciate the help.

---

### Post by Bashing-om on 2013-07-04
maggiezzz;

Coincidence ? Related to Software Center failure ??? Humm,, Right now we do not know.
What results from terminal command:
```
unity --reset
```
Log out and then log back in to see if that resolves dash .........any good affect on SC ?

[INDENT][INDENT]hey, it is a thought[/INDENT][/INDENT]

---

### Post by Dennis N on 2013-07-05
> I'm having another problem apparently that I just realized ... My dash is totally empty...

This has happened to other people. Here is one post on askubuntu with several solutions suggested.
 
[http://askubuntu.com/questions/125843/dash-search-gives-no-result](http://askubuntu.com/questions/125843/dash-search-gives-no-result)

[B]Top rated answer:
[/B]
> **rm ~/.cache/software-center -R**

worked like a charm. I did need to run:

**unity --reset &**

afterwards though, for the changes to take effect within dash, but the software center just started working straightaway.


---

### Post by maggiezzz on 2013-07-06
I entered the code **rm ~/.cache/software-center -R **and got: 

*rm: cannot remove `/home/maggie/.cache/software-center': No such file or directory*

sooo... then I entered the code **unity --reset **and got a whole bunch of outputs, don't know what it means, but now my terminal window is locked to the top of my screen (no button available to close it, can't grab the top bar to move it), and all the icons from the top bar on the desktop are gone - including the power button - so I can't figure out how to restart/shut down.... Dash still EMPTY ...software center still malfunctioning...... can't restart computer .... what am I doing wrong here????Maybe I will just unplug laptop and wait til battery dies and force it to turn off that way...

edit: ok got it restarted by killing the battery. The buttons on the desktop top bar have returned, but dash still empty/software center still doesn't work.

---

### Post by Bashing-om on 2013-07-06
maggiezzz; Hey..
Can't hurt to try ... what results with my post # 3 at this time ?

[INDENT][INDENT]one thing or another .. maybe both[/INDENT][/INDENT]

---

### Post by maggiezzz on 2013-07-06
Hi Bashing-om.

the code **sudo dpkg -C** doesn't seem to do anything:
[I]
maggie@maggie-HP-Pavilion-dv6000-RP304UA-ABA:~$ sudo dpkg -C 
[sudo] password for maggie: 
maggie@maggie-HP-Pavilion-dv6000-RP304UA-ABA:~$ [/I]

(dash/SC problems persist)

The code **sudo apt-get install --reinstall software-center** does the following:

maggie@maggie-HP-Pavilion-dv6000-RP304UA-ABA:~$ sudo apt-get install --reinstall software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base kde-l10n-engb
  calligra-l10n-engb linux-headers-3.5.0-23 linux-headers-3.5.0-23-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 10 not upgraded.
Need to get 0 B/624 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 248618 files and directories currently installed.)
Preparing to replace software-center 5.2.9 (using .../software-center_5.2.9_all.deb) ...
Unpacking replacement software-center ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up software-center (5.2.9) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.

BUT ... Hasn't fixed anything (dash/SC problems persist). :( I'll restart and see if anything happens.

Thanks for the help all

edit: restarted, but still broken! :(:(

---

### Post by Bashing-om on 2013-07-06
maggiezzz; Hey...
Seems then that the underlying problem is within the desktop:
You can reset the configuration for all packages that use debconf with the command:
```
sudo dpkg-reconfigure -phigh -a
```
This will restore a large portion of your system, although there will likely be things that are still configured and set.
But, you will loose any changes you have made to the default desk top settings.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-07
maggiezzz; 

Done for the night... will check you tomorrow.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by maggiezzz on 2013-07-09
Hi Bashing-om, thanks for keeping tabs on my issue. I just input your command into terminal and nothing seemed to happen. No response appeared after I entered my admin password. SC and dash are still inoperable.  I tried to close the terminal and it said "There is still a process running in this terminal. Closing the terminal will kill it." Does this take a long time to take effect? Should I just leave it open for a while? Do I need to restart afterward?

Any more ideas? Anyone? Thanks!!!

---

### Post by Bashing-om on 2013-07-10
maggiezzz;
No to (re-)install SC should not take tooo long ... if you still have a terminal open and you do not know what is open and hanging up ... do in terminal:
```

top

```
watch it for a few minutes and see what is running - type "q' without the quotes to 'q'uit.
to see all processes
```

ps aux

```and see if you recognize something that you have started and should be killed.
to kill a process 
```

kill -9 <pid>

``` where "<pid>" is that first set of numbers .

Now to restore dash ,, as other measures have failed, try:
```
sudo dpkg-reconfigure -phigh -a
```

N again my eys are crossing and my think'n has become cloudy ... I am off to my la-la land .. 
will check ya later !

[INDENT][INDENT]read ya[/INDENT][/INDENT]

---

### Post by maggiezzz on 2013-07-15
Hi, sorry it's taken me a while to respond - been busy. That command still isn't fixing anything. 

I read through the other options to restore dash @ [http://askubuntu.com/questions/125843/dash-search-gives-no-result](http://askubuntu.com/questions/125843/dash-search-gives-no-result), such as:

> You should ensure that you have these 2 packages installed:
  
[LIST]
[*][unity-place-applications [IMG]http://hostmar.co/software-small[/IMG]]("https://apps.ubuntu.com/cat/applications/unity-place-applications") 
[*][unity-place-files [IMG]http://hostmar.co/software-small[/IMG]]("https://apps.ubuntu.com/cat/applications/unity-place-files") 
[/LIST]
  Then logout/login and you will get back you the 2 lenses and the search will search applications and files.

 

  
I need to get into an "installation" application in order to do this ... Since my SC is toast, and my dash isn't listing the Synaptic that I just downloaded (or anything else for that matter), I ran a search for "synaptic" in Nautilus (both in file system and my home folder) ... NO RESULTS!! So, I can't find Synaptic that I recently installed via the terminal, and I'm still stuck at not being able to install the packages recommended above to restore the dash...... 

ANYONE... Additional suggestions please on how to fix my SC and dash ... other than a complete ubuntu re-install ??? I am running out of hope. Thank you very much.

---

### Post by Bashing-om on 2013-07-15
maggiezzz; Hi !

Try this:
```

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo apt-get upgrade

```
and if that still does not resolve the situation; 
do:
```

sudo apt-get purge ubuntu-desktop
##This will get rid of any desktop packages currently installed AND the config files. This gives us a nice blank slate to re-install the desktop.
sudo apt-get install ubuntu-desktop
##This will install the desktop environment again. After that, reboot and (fingers crossed) you'll get a desktop again.

```
[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by maggiezzz on 2013-07-17
Hi, thanks again. Entered all those commands, restarted computer, and got no results.

Finally managed to locate Synaptic via Nautilus search, but it won't let me apply any changes (the "apply" button is greyed out) ... it gives me the following error on starting: "Starting without administrative privileges: You will not be able to apply any changes. But you can still export the marked changes or create a download script for them."

BUT I AM THE ONLY USER, ONLY ADMIN ON THIS MACHINE! Why do I not have admin privs? What the heck????

Why is everything so messed up? I am nearly at my wit's end.... maybe I should just reinstall the OS .... this is so frustrating.

---

### Post by Bashing-om on 2013-07-17
maggiezzz; Still hanging with you.

I am about at my wits end as to what is broken.. still think'n about it.

In respect to admin privileges: It works like this. The admin user is the user who may temporarily promote to perform administrative task. To attain this level that user precedes the command with the term sudo (Super User DO). 
synaptic: try:
```
gksudo synaptic
``` that is the graphical equivalent of "sudo".
info:
```
man sudo
```
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[INDENT][INDENT]I will be back
[/INDENT][/INDENT]

---

### Post by maggiezzz on 2013-07-19
> **Bashing-om said:**
> 
synaptic: try:
```
gksudo synaptic
``` 

YES! finally something worked.
Running this code, I was able to mark and apply changes via Synaptic. 

So, I installed the following packages in attempts to restore my dash:

> You should ensure that you have these 2 packages installed:
  
[LIST]
[*][unity-place-applications [IMG]http://hostmar.co/software-small[/IMG]]("https://apps.ubuntu.com/cat/applications/unity-place-applications")
[*][unity-place-files [IMG]http://hostmar.co/software-small[/IMG]]("https://apps.ubuntu.com/cat/applications/unity-place-files")
[/LIST]
  Then logout/login and you will get back you the 2 lenses and the search will search applications and files.


Installed successfully, but NO DASH still .... so now I've tried 2 of the recommended items in the thread [http://askubuntu.com/questions/125843/dash-search-gives-no-result](http://askubuntu.com/questions/125843/dash-search-gives-no-result) and neither has restored my dash. I'm afraid I don't really understand the remaining suggestions there, so I don't know if I should try them ....

Results thus far:
1. Installed Synaptic. Able to install packages using the gksudo code in terminal.
2. Dash still empty
3. Software Center still malfunctioning

So I'm still left with my original problems.

---

### Post by Bashing-om on 2013-07-19
maggiezzz; Hey,

A bit of good news that.

I also do not understand why software-center and the dash continue to be so stubborn.
Be advised I am aware of a command sequence (LOOONG one) that will check/rebuild the entire desktop and all of it's dependencies.
It is a sledge hammer approach, If I can not come up with a better option, I would be willing to offer it as a solution.

I can't know everything, but I sure would like to know this.

[INDENT][INDENT]inquiring minds want to know[/INDENT][/INDENT]

---

### Post by maggiezzz on 2013-08-02
Soo. I've just checked back in after the forum hack. Good to see the place is still here.

Bashing-om: would it just be simpler to re-install the OS at this point? Rather than entering that long sledge-hammer command sequence to rebuild the desktop?

Have to say that I am disappointed that some key functions of Ubuntu 12.04 are already inexplicably malfunctioning, without an apparent repair solution ...just fresh installed it less than 2 months ago :(

---

### Post by Bashing-om on 2013-08-02
maggiezzz;

Well, let me put (re-)install in this light --- It is a guaranteed solution and will work to resolve any mishap. However, little is learned from doing so and gives no insight as to what caused the malfunction. Presently I have exhausted other means within my knowledge to resolve.... and if you are considering (re-)installing, run this command sequence... it is all to be entered as one sequence command ... and will rebuild that desk top. I have run it so I know it is safe and effective.
```

sudo apt-cache depends ubuntu-desktop | awk -F ":" '{print $2}' | \
sed '/^$/d' | xargs sudo apt-get \
install --reinstall --install-recommends --yes

```
copy and paste as is into the terminal; the "\" character at the ends of the lines will be interpreted as "continue line" for a single command sequence.
It will take a lot of time and as well a lot of bandwidth... let 'er rip !

And then advise me on the result ...

[INDENT][INDENT]'nother instance of my failure of knowledge
[/INDENT][/INDENT]

---

### Post by maggiezzz on 2013-08-10
Hi again, sorry for delay, life gets in the way .. I will enter this code in terminal in the next few days and report back what happens... Fingers crossed :)

---

### Post by maggiezzz on 2013-08-15
I entered this code, took about 30-40 mins. Then restarted. 
No resolution :(
Dash is still empty, SC is still jumping erratically around screen and unusuable.
I've also been having problems lately with computer freezing while trying to organize photos into folders ... Has happened about 5 times .... Been needing to kill the power to recover from the freeze....

Unless anyone's got any ideas left, I guess I'll be reinstalling the OS soon.

---

### Post by Bashing-om on 2013-08-15
maggiezzz; Wehelll;

I am out of suggestions.. perhaps in this instance, with such disparate problems seemingly not related one to the other ... the better course is to (re-)install.

[INDENT][INDENT]peace of mind is worth a lot[/INDENT][/INDENT]

---

