---
title: "[SOLVED] HP printer help"
date: 2008-06-20
forum: General Help
---

### Post by Ralphie on 2008-06-20
Hi everyone, I am setting up a computer for a friend, and she has a HP Deskjet 3915 printer which is supported under the HPLIP driver.

I am having trouble getting ubuntu to recognize it. 

At first it was auto detected, but when I went to print, it came up with an error "printer may not be connected" I messed with it for a while, and eventually deleted the printer through CUPS [http://localhost:631/](http://localhost:631/)

Now it will not auto detect whatsoever, and I have no clue what to do now.

If anyone could help it would be much appreciated! I don't want her to want to go back to windows!! lol

---

### Post by editrix on 2008-06-21
I had much, much trouble installing my HP Deskjet in Hardy, although it worked beautifully in Dapper. One suggestion was to try using HPLIP.

You might want to scan through my thread on the topic: [http://ubuntuforums.org/showthread.php?t=834212](http://ubuntuforums.org/showthread.php?t=834212)  (Can't install printer)

The only problem is I broke the printer before I got anything going, and I couldn't get hplip to run. So the thread never got solved.

---

### Post by ramjet_1953 on 2008-06-21
I don't know why, but the developers of Ubuntu do not include the [COLOR="Blue"]python-qt3 package[/COLOR], when installing.

During install, it will see a HP printer and install [COLOR="Blue"]hplip[/COLOR], but this package is useless, without [COLOR="Blue"]python-qt3[/COLOR].

1. [COLOR="Red"]sudo apt-get install python-qt3[/COLOR]
After it has installed, make sure your printer is plugged-in and powered.

2. In a terminal type in [COLOR="Red"]sudo hp-setup[/COLOR]
A window should open, guiding you through the install.

3. The printer should now automatically print a test page.

4. After this type in a terminal [COLOR="Red"]hp-toolbox[/COLOR]
A window should open giving you access to all sorts of goodies on the printer, including head cleaning and ink levels.

5. You can add hp-tool box easily to your menus in Preferences>Main Menu.

p.s. If [COLOR="Blue"]hplip[/COLOR] is not already installed [COLOR="Red"]sudo apt-get install hplip
[/COLOR]
Regards,
Roger :cool:

---

### Post by editrix on 2008-06-21
Oh, ramjet_1953, this is wonderfully clear, many thanks. Only problem is, I got this message trying to install the python-qt3:
> 
Reading state information... Done
python-qt3 is already the newest version.
python-qt3 set to manually installed.

What the heck does that last line mean? I've never seen it before.

And, as I said in that other thread, sudo hp-setup just hangs--because of the manually installed thing?

(yes, my printer's broken, but I'll be getting another one and I'd like to be prepared)

---

### Post by gatorbrit on 2008-06-21
> **ramjet_1953 said:**
> I don't know why, but the developers of Ubuntu do not include the [COLOR="Blue"]python-qt3 package[/COLOR], when installing.

During install, it will see a HP printer and install [COLOR="Blue"]hplip[/COLOR], but this package is useless, without [COLOR="Blue"]python-qt3[/COLOR].

1. [COLOR="Red"]sudo apt-get install python-qt3[/COLOR]
After it has installed, make sure your printer is plugged-in and powered.

2. In a terminal type in [COLOR="Red"]sudo hp-setup[/COLOR]
A window should open, guiding you through the install.

3. The printer should now automatically print a test page.

4. After this type in a terminal [COLOR="Red"]hp-toolbox[/COLOR]
A window should open giving you access to all sorts of goodies on the printer, including head cleaning and ink levels.

5. You can add hp-tool box easily to your menus in Preferences>Main Menu.

p.s. If [COLOR="Blue"]hplip[/COLOR] is not already installed [COLOR="Red"]sudo apt-get install hplip
[/COLOR]
Regards,
Roger :cool:

I just did this to install a HP LaserJet 1006P and it worked perfectly.   Fantastic!!!!

:)

---

### Post by ramjet_1953 on 2008-06-21
Hi, Editrix!

Try this first: [COLOR="Red"]sudo apt-get install -f[/COLOR]

If you are not comfortable with the command line, go into Synaptic Package Manager and then click[COLOR="Blue"] Edit>Fix Broken Packages[/COLOR].

If you still have problems, try removing and re-installing python-qt3, using Synaptic.

Regards,
Roger :cool:

---

### Post by editrix on 2008-06-22
> **ramjet_1953 said:**
> Hi, Editrix!

Try this first: [COLOR="Red"]sudo apt-get install -f[/COLOR]

I got no visual/verbal feedback. Should I have?

> If you still have problems, try removing and re-installing python-qt3, using Synaptic.

Still having problems, but I see that python-qt3 is 20 MB--a bit of a PITA on dialup. Also, removing it seemed to want to remove a few other things like gdebi-kde and python-kde which seems a bit drastic. Presumably I'd get them back on a reinstall but that would take even longer?

Can I just reinstall without removing?

Also, there's a few other python-qt3 programs that aren't installed. One of them is the documentation and two are debug extensions, but maybe I need the python-qt3-gl?

Thanks.

---

### Post by gmcpheron on 2008-06-22
Thanks ramjet_1953. 

This variation on your instructions got my hp 1020 printing in Hardy:

Install python-qt3 with Synaptic.

Run "sudo hp-setup" in terminal and follow the setup wizard including the download from an HP server of the HP plugin.

The test page printed.

Thanks again for your support!

---

### Post by Ralphie on 2008-06-22
I have the same issue as editrix, 
the printer is not found.
```

error: No devices found. Please make sure your printer is properly connected and powered-on.
```
the printer is connected and it is on, hmm

anyone have any other insight?

---

### Post by editrix on 2008-06-23
> **Ralphie said:**
> I have the same issue as editrix, the printer is not found.

Actually, no. I can't even run hplip or hp-setup. So you're one step, maybe two, ahead of me. :)

Get to google linux (see my sig) and search your printer model and the error message ```
 error: No devices found.
```

It looks like a fairly common problem.

UPDATE: Got my problem solved by correcting my /etc/hosts file, which *should* read: 127.0.0.1 localhost.localdomain localhost ubuntu

---

### Post by Ralphie on 2008-07-02
I am still having trouble with this, and the woman I am setting the system up for is needing to use her printer, please if anyone has any more info, don't hesitate!

It was auto detected at one point in time, but refused to print, i am now thinking that it was refusing due to the lack of python-qt3, as mentioned above, so I removed the printer with cups, to try and start all over again, but it refuses to find it.

If I cant get this to work I will be forced to install Windows back onto her system, which would be as fun as pulling a band aid off my arm!!

thanks

---

### Post by VMC on 2008-07-02
If you go here "System-Administration-Printing" Does "Settings" reveal the correct Device URI? Mine was printing one page and then stoppling. 

I pushed the "Change" and it found another recommended setting and I choose that, and it worked.

---

### Post by raygj on 2008-07-03
it could be that cups cannot  access "/dev/usb/lp0"

CUPS really doesn't like having "SystemGroup" and "Group" values being the same in the cupsd.conf file.so enter in a konsole

"sudo gedit /etc/cups/cupsd.conf" and change the following settings from

"SystemGroup lpadmin"

"User lp"
"Group lpadmin"

to

"SystemGroup lpadmin"

"User lp"
"Group lp"

now save the changes ( back to /etc/cups/cupsd.conf )
then open a Konsole and run "testparm" to make sure you haven't made a typing mistake.
then in konsole run "sudo /etc/init.d/cupsys restart"
now cups can access "/dev/usb/lp0" properly
and now you should be  able to  print

---

### Post by eotakos on 2008-07-03
actually i have a deskjet 940c.

the printer was recognized from the beginning but it wouldn't print with "fit to page" (although it was enabled).

what finally fixed the problem, was the official site of hp. i found my printer, searched for drivers (linux drivers) and i found the following link: [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

this does pretty much everything by itself. 

the one thing i don't like is the shortcut icon placed on my panel -i didn't ask for it :( - but since it works i guess... but someday i'll learn how to take that thing OFF!!

---

### Post by moore.bryan on 2008-07-15
i'm still having this issue... cups/lp/anything won't even SEE my usb hp printer as connected. any suggestions?
====
EDIT:
nevermind... got it working. looked like it was an issue with the ehci module; manually loading the uhci module solved everything.

---

### Post by Ralphie on 2008-07-17
welp thanks everyone for the help, hopefully you guys figure it out. the lady who i am doing this for really needs to print and so back to windows it is for them this weekend :(


Maybe someday!
Darn crappy HP printers from who knows when...

---

### Post by ramjet_1953 on 2008-07-18
Another problem can be with the [COLOR="Blue"]/etc/udev/rules.d/55-hpmud.rules[/COLOR] file.

Have a look at this file and if you see references to OWNER="root" or GROUP="root", all of those references should be changed to "lp".

TO do this you will need to be in sudo mode.

ie. [COLOR="Red"]sudo gedit /etc/udev/rules.d/55-hpmud.rules[/COLOR]

I would also suggest that you back-up the original file before tinkering with it. ie copy the file and re-name it with a .bak suffix.

Regards,
Roger :cool:

---

### Post by Cotopaxi on 2008-07-18
Ralphie,

Is the printer of your friend connected via USB?

---

### Post by Ralphie on 2008-07-18
Cotopaxi, Yes, it is
ramjet_1953, i will have a look at that right now, thanks!

*edit*
ramjet, The GROUP was set to "scanner" i changed them all to lp, restarted the computer, and it still did not work.

any last suggestions? 
I have a lot of projects piling up so I am going to be installing Windows again later tonight otherwise.

I was tempted to go out and buy them a new printer the other day hahaha, but they are attached to this little one.

---

### Post by Cotopaxi on 2008-07-19
Ok Ralphie, eventually you will find a help in the following thread:

[http://kubuntuforums.net/forums/index.php?topic=3089184.0](http://kubuntuforums.net/forums/index.php?topic=3089184.0)

In this thread, go to the second post of tomstrong and look at how he solved the problem.

Eventually this will solve your problem too.

Good Luck!

---

### Post by Ralphie on 2008-07-19
Thanks so much everyone, I am sure there is enough information here to solve ANYONES problems installing a fussy printer.

My problem has also been solved, it ended up being a faulty usb cable!

I switched it out for a different one as a last resort and there it was! automatically detected!

Thanks again for all the help, I will mark this solved, and hopefully people will use it in the future.


*note*
People, don't forget to check your hardware!
:D

---

### Post by matchstich on 2008-07-19
my psc 2355 worked fine till the last set of updates. 

after they installed  my prints jobs were coming out mirror image.

this thread fixed it.

just wondering, what setting would save me the most ink.

now, it is set on print job.

thanks

---

### Post by jamesdcarroll on 2008-07-19
> **ramjet_1953 said:**
> I don't know why, but the developers of Ubuntu do not include the [COLOR="Blue"]python-qt3 package[/COLOR], when installing.

During install, it will see a HP printer and install [COLOR="Blue"]hplip[/COLOR], but this package is useless, without [COLOR="Blue"]python-qt3[/COLOR].

1. [COLOR="Red"]sudo apt-get install python-qt3[/COLOR]
After it has installed, make sure your printer is plugged-in and powered.

2. In a terminal type in [COLOR="Red"]sudo hp-setup[/COLOR]
A window should open, guiding you through the install.

3. The printer should now automatically print a test page.

4. After this type in a terminal [COLOR="Red"]hp-toolbox[/COLOR]
A window should open giving you access to all sorts of goodies on the printer, including head cleaning and ink levels.

5. You can add hp-tool box easily to your menus in Preferences>Main Menu.

p.s. If [COLOR="Blue"]hplip[/COLOR] is not already installed [COLOR="Red"]sudo apt-get install hplip
[/COLOR]
Regards,
Roger :cool:

Awesome. Many thanks!

---

### Post by jamesdcarroll on 2008-07-19
> **ramjet_1953 said:**
> I don't know why, but the developers of Ubuntu do not include the [COLOR="Blue"]python-qt3 package[/COLOR], when installing.

During install, it will see a HP printer and install [COLOR="Blue"]hplip[/COLOR], but this package is useless, without [COLOR="Blue"]python-qt3[/COLOR].

1. [COLOR="Red"]sudo apt-get install python-qt3[/COLOR]
After it has installed, make sure your printer is plugged-in and powered.

2. In a terminal type in [COLOR="Red"]sudo hp-setup[/COLOR]
A window should open, guiding you through the install.

3. The printer should now automatically print a test page.

4. After this type in a terminal [COLOR="Red"]hp-toolbox[/COLOR]
A window should open giving you access to all sorts of goodies on the printer, including head cleaning and ink levels.

5. You can add hp-tool box easily to your menus in Preferences>Main Menu.

p.s. If [COLOR="Blue"]hplip[/COLOR] is not already installed [COLOR="Red"]sudo apt-get install hplip
[/COLOR]
Regards,
Roger :cool:

Awesome. Many thn

---

### Post by boron on 2011-03-13
Thanks for the advice on installing hp psc 2355 printer.
I thought it was solved when the graphical interface appeared, but my printer was not detected. I suspect this is because I'm running Ubuntu 10.10 in VirtualBox, perhaps, though I had no trouble with the printer when running Ubuntu 10.04. Any further suggestions, pls?

---

