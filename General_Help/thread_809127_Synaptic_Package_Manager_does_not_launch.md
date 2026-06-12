---
title: "Synaptic Package Manager does not launch"
date: 2008-05-27
forum: General Help
---

### Post by mainak_sen on 2008-05-27
When I click on System -> Administration -> Synaptic Package Manager, Synaptic does not launch. For a few seconds a tab appears on the bottom panel saying "opening system..." and then it disappears and nothing else happens. If I repeat the procedure, the same thing happens.

If I use the command
sudo syanptic
in the terminal, synaptic launches and seems to work fine.

Synaptic was working both from the panel and terminal till yesterday. The problem started from yesterday after some installations were made (I am not sure which specifically). I am a new Linux user (using this for about 2 weeks now), using Ubuntu 8.04 Hardy i386 desktop. Any help will be appreciated.

Thanks in advance!

---

### Post by skip mcshwang on 2008-05-27
What happens if you type this in the terminal

```
gksu /usr/sbin/synaptic
```

---

### Post by mainak_sen on 2008-05-27
Thanks for your suggestion.

If I type 
gksu /usr/sbin/synaptic

it behaves the same way as clicking System -> Administration -> Synaptic Package Manager as described in my original post. For a few seconds a tab appears in the bottom  panel, titled "Starting Administrative Application...", then it disappears and nothing else happens.

---

### Post by temiatwork on 2008-05-27
This also happened to me last week then I re-installed 8.04 and after 3 days the same problem happened.

I use the same command that mainak_sen uses and it works fine (sudo syanptic) from the terminal.

It also worked fine with the suggestion from skip mcshwang (gksu /usr/sbin/synaptic) 

But it still doesn't respond by running it from the system menu.

---

### Post by skip mcshwang on 2008-05-27
temiatwork: Try resetting the Synaptic command in your system menu by going to System > Preferences > Main Menu > Administration, right-click on Synaptic Package Manager and click Revert to Original.

mainak_sen: If "sudo synaptic" works for you, then you could change the menu option to run that. Go to System > Preferences > Main Menu > Administration, right-click on Synaptic Package Manager and click Properties, then set the Command field to "gksu synaptic" or "sudo synaptic".

*edit* as stated below sudo is a command line program, so if all else fails you can at least put 'xterm -e sudo synaptic' as the command.

---

### Post by superyounan1 on 2008-05-27
> **skip mcshwang said:**
> temiatwork: 
mainak_sen: If "sudo synaptic" works for you, then you could change the menu option to run that. Go to System > Preferences > Main Menu > Administration, right-click on Synaptic Package Manager and click Properties, then set the Command field to "gksu synaptic" or "sudo synaptic".


Changing the command in the launcher to 'sudo synaptic' would be a bad idea because 'sudo' is a command line program, the prompt for the password won't be presented anywhere.

One of the previous posts suggested you do gksu synapic from the command line, and you responded by saying that 'the same thing happens', but what you didn't say is what the terminal output was. Synaptic might be printing out some helpful error information to the terminal just before it exits, can you post that?

---

### Post by headlessspider on 2008-05-28
this not only happens with synaptic but with other applications that need an administrative password to launch -- ie. firestarter for one.

something goes south with a script that checks to see if an program or application needs an admin password or not; if a program needs a password it calls up another program to get the password but somewhere there the password program doesn't get lauched.

this "bug" was introduced about 3 or 4 updates ago from the time of this entry... if i remember right.

---

### Post by mainak_sen on 2008-05-28
> **superyounan1 said:**
> Changing the command in the launcher to 'sudo synaptic' would be a bad idea because 'sudo' is a command line program, the prompt for the password won't be presented anywhere.

One of the previous posts suggested you do gksu synapic from the command line, and you responded by saying that 'the same thing happens', but what you didn't say is what the terminal output was. Synaptic might be printing out some helpful error information to the terminal just before it exits, can you post that?

Thanks.
If I do 
gksu /usr/sbin/synaptic
at the terminal the same thing happens...and there are absolutely NO messages displayed on the terminal, it just sits there...it does not return to the ~$ prompt. But, I can type at the cursor.

I have never tried gksu /usr/sbin/synaptic before (i.e. before this problem) so I am not sure what is the "normal behavior" to expect...is it expecting any subsequent commands or it should just launch the synaptic window just as sudo synaptic does? btw, remember, as I mentioned earlier, sudo synaptic does work from the terminal.

---

### Post by temiatwork on 2008-05-28
> **skip mcshwang said:**
> temiatwork: Try resetting the Synaptic command in your system menu by going to System > Preferences > Main Menu > Administration, right-click on Synaptic Package Manager and click Revert to Original.

Thank you for your reply. I just did this but still no reaction.

> **skip mcshwang said:**
> mainak_sen: If "sudo synaptic" works for you, then you could change the menu option to run that. Go to System > Preferences > Main Menu > Administration, right-click on Synaptic Package Manager and click Properties, then set the Command field to "gksu synaptic" or "sudo synaptic".

I also tried this procedure but still synaptic does not launch from the system menu.

---

### Post by ScottyP on 2008-05-28
I'm glad to find others with the same problem as me.

When I try to start SPM using the menu, a panel item comes up saying "Starting Administrat..." for about 10 seconds or so, then goes away leaving me unsatisfied.

If I try to use SPM using ```
gksu /usr/sbin/synaptic
```
the terminal returns nothing. The cursor moves to the next line and blinks. Leaving me once again unsatisfied.

Piling on...
This is the part where as a noob, I connect many problems into one problem, using noob-like leaps of logic in hopes that I might be on to something...

I saw a thread mentioning the Software Sources in the menu. When I click on that, it also gives me the "Starting Administrat..." in my panel, sticks around for about 10 seconds and also leaves me unsatisfied.

My Update Manager also freezes, but using commands and options that almost make sense to me, I can get that to work in my terminal.

---

### Post by ScottyP on 2008-05-28
Found the fix off of this thread: [http://ubuntuforums.org/showthread.php?t=723361]("http://ubuntuforums.org/showthread.php?t=723361")

Followed the directions given by PmDematagoda

---

### Post by geoff511 on 2008-05-29
The code: gksu /usr/sbin/synaptic 
works on my machine, even tho the Synaptic Manager won't start if you click Sysytem - Administration etc.  - the Konsole still locks after it has started the Synaptic Package Manager, but at least it will close.
Also Software Sources won't start either, same 10 sec delay on task bar then nothing.

But i'm in the same boat with Update manager !! it just locks up when you try to install updates, seems to want my access code but doesn't show the box on the screen, and you can't close it - without restarting Ubuntu ?

Also have tried the code: sudo apt-get update   and that seems to get the updates to my machine (i think) but doesn't install them and leaves the pretty orange star in the system tray saying there is an update.

Am curious tho, if there is a fix for this mess the writers have made, HOW WILL I INSTALL IT ??

Geoff

---

### Post by geoff511 on 2008-05-29
My mistake on code for update, should be sudo apt-get upgrade ...
(can't read my own writing), just tried it and that works.
But still have probs with Synaptic Package Manager starting and update button on system tray.

---

### Post by temiatwork on 2008-05-30
> **ScottyP said:**
> Found the fix off of this thread: [http://ubuntuforums.org/showthread.php?t=723361]("http://ubuntuforums.org/showthread.php?t=723361")

Followed the directions given by PmDematagoda

Yes this is great, this solves everything including the freezing when updating. -thanks!

---

