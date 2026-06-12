---
title: "Applications won't run"
date: 2021-06-10
forum: General Help
---

### Post by anneranch on 2021-06-10
I am currently  using 21.04 and having an issue with NOT running application from desktop.
I won;t even get the spinning circle, but I can run the app using command line. 

**How can I check what the desktop app is NOT trying to run?**

On top of that some app take forever to start , but I get the spinning  wheel OK.

My Disks , perfectly  working before upgrade, keeps crashing on start-uo too.
\
LibreOffice will not open "new document " from desktop - it gets  to normal "recovering " mode instead. 
(this has been an issue for last few versions )

---

### Post by vanadium on 2021-06-11
I understand that you do not have error messages or warning when running an application that won't start from the terminal.

You may want to try logging in to another session to see if the problem persists (e.g. Xorg instead of Wayland).

You may want to temporarily create a new account to see if the problem persists in a default new account.

That will already delineate the issue a bit more.

---

### Post by TheFu on 2021-06-11
Whenever there are repeated issues on a system for different reasons, I'd to back to the most common parts of the problem.
If different programs have issues, then it can be 
[LIST]
[*]the userid's configuration files - solution, move the ~/.config/ directory to ~/.config-old/ and test again.
[*]the userid's problems - solution, create a new userid and test again.
[*]the DE being used - solution, install a different DE that isn't part of the same family normally used, create a new userid and login with that under the new DE. Test again.
[*]the kernel for the OS. Lots of ways to test this, but the easiest is to boot into a "Try Ubuntu" environment off a flash drive and test again.
[*]the hardware running all these things. Solution, try using a different computer or swapping the suspected bad parts (check the system log files for hardware errors).
[/LIST]
I'd start by eliminating each of those issues.  If you have a Try Ubuntu flash drive handy, it can test all but the last item usually. Try that, see how your programs work or don't work.  If they show the same issues, then it is hardware as the root problem.

---

### Post by grahammechanical on 2021-06-11
From my own recent experience I would say that there are some messed up configuration files.  Both system and user configuration files. On my machine an install of Ubuntu 20.04 blinked out of existence as the web browser was loading a newspaper web site. I was left with a blank screen with the same error message repeated continuously.

I tried to be smart. I re-installed without formatting the Home partition but the problem remained. A re-install of Ubuntu 20.04.2 and formatting both the Root partition and the Home partition gave me a much better working OS. Solving the problem that way was quicker and less frustrating than trying to fix what was wrong.

Regards

---

### Post by Impavidus on 2021-06-11
> **anneranch said:**
> I am currently  using 21.04 and having an issue with **NOT running application from desktop**.
I won;t even get the spinning circle, but **I can run the app using command line**. 


If you can run the application from command line, there's nothing wrong with the application itself or the config files of that application.

When you start an application from the GUI, you use a .desktop file. .desktop files control the title, description and icon of an application and the command line that launches it and the directory where it should start, amongst other things. It looks like there's something wrong with your .desktop files.

A .desktop file in your Desktop directory should put a launcher on your desktop, so maybe that's where your .desktop files can be found. Other than that, they may be in /usr/share/applications or in the user config directory for your desktop environment, somewhere in $HOME/.config. Details depend on your desktop environment.

.desktop files are plain text, so you can open them in a text editor. Maybe you can find what's wrong with the command in the .desktop file, compared to the command you use to start the application from command line.

The issue with the app taking forever to start may be related. Something interesting may turn up from the .desktop files there too.

The issues with Disks and LibreOffice appear unrelated, unless there's a common cause like filesystem damage. If there doesn't appear to be filesystem damage, better to deal with that in a separate thread.

---

