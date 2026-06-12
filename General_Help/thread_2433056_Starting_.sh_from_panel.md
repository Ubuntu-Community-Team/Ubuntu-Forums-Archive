---
title: "Starting .sh from panel"
date: 2019-12-13
forum: General Help
---

### Post by dkolars on 2019-12-13
Running a program (K40 Whisperer) for my laser cutter on my laptop, Ubuntu 16.04...  created a shortcut on the panel for a quick start...  start command is "sudo ./k40.sh"...  Have to run in Terminal for this to work, then enter password.. every time... <sigh>

So, thought I'd simply make the "./k40.sh" totally accessible with a "chmod 700 ./k40.sh"... That worked!  Can uncheck the "Run in Terminal" box, and the program opens just fine.  BUT, then I get the message:  "USB error:  Unable to set USB Device Configuration"...  

Have NO clue what's going on with that.  So, back to the Run in Terminal set-up...  

Any clues?

<rant>This is my one major gripe with Linux... I, as the only user, should be able to do whatever I want, and run any program easily.  I should be the admin by default, not just a user.</rant>

TIA -- DK

---

### Post by Holger_Gehrke on 2019-12-13
On 16.04 you've still got the graphical sudo frontend gksudo (in the package gksu,deprecated on newer versions of Ubuntu), so replacing 'sudo' in the command with that should get you a graphical password prompt. 'sudo' is meant for use in a terminal, it uses the terminal it's run from to request the password; if it's run without a terminal it will fail. The reason you need to be root to run this is obviously that it directly accesses the USB-device for your laser cutter. <rant>It really shouldn't do that, the program should be split into a small device-driver started at boot by root and into an application that communicates with that driver. Blame lazy developers for your problem.</rant>

Another solution would be to chown the script to root ('chown root k40.sh') and make it setuid ('chmod u+s k40.sh';basically the program would run as root, no matter who actually calls it; only do this with programs you absolutely trust on systems that you don't care about breaking).

Or you could configure sudo to use a graphical helper to request the password (either by setting SUDO_ASKPASS to the path and name of an appropriate program and adding the option -A to sudo or by changing sudo.conf; a helper that I know works is ssh-askpass from the package of the same name).

Or if you feel like learning something, try setting up a policy for the program and use pkexec (policy kit exec) instead of sudo.

And regarding your rant: Please NO. I can't count the times where not being root has saved me from doing something horribly stupid. Add that this would allow any program you start to do whatever it wants to do (think about your browser running scripts from who-knows-where) and you can see the security nightmare ... It has been tried (Windows XP and earlier) and has failed.

Holger

---

### Post by dkolars on 2019-12-13
> **Holger_Gehrke said:**
> On 16.04 you've still got the graphical sudo frontend gksudo (in the package gksu,deprecated on newer versions of Ubuntu), so replacing 'sudo' in the command with that should get you a graphical password prompt. 'sudo' is meant for use in a terminal, it uses the terminal it's run from to request the password; if it's run without a terminal it will fail. The reason you need to be root to run this is obviously that it directly accesses the USB-device for your laser cutter. <rant>It really shouldn't do that, the program should be split into a small device-driver started at boot by root and into an application that communicates with that driver. Blame lazy developers for your problem.</rant>

Nope, don't have gksudo...  And, was wanting to skip the pw requirement entirely.

> Another solution would be to chown the script to root ('chown root k40.sh') and make it setuid ('chmod u+s k40.sh';basically the program would run as root, no matter who actually calls it; only do this with programs you absolutely trust on systems that you don't care about breaking).

Did that, and nope, doesn't work... get "Failed to execute child process "./k40.sh" (Permission denied)".   So, I changed the permissions to allow ANYONE to run the program... Again, nope.

> Or you could configure sudo to use a graphical helper to request the password (either by setting SUDO_ASKPASS to the path and name of an appropriate program and adding the option -A to sudo or by changing sudo.conf; a helper that I know works is ssh-askpass from the package of the same name).

Or if you feel like learning something, try setting up a policy for the program and use pkexec (policy kit exec) instead of sudo.

At a certain point, the ride is not worth the fare...  I have better things to do, it would seem.  Thanks for the assist...  

I'm using this laptop to only run Inkscape & K40 Whisperer... Occasionally check Firefox for something, but seldom.  Was just hoping there was a way to simply "run" the program by only clicking a link and NOT needing a password to be input.  So, back to running in Terminal.

> And regarding your rant: Please NO. I can't count the times where not being root has saved me from doing something horribly stupid. Add that this would allow any program you start to do whatever it wants to do (think about your browser running scripts from who-knows-where) and you can see the security nightmare ... It has been tried (Windows XP and earlier) and has failed.

Well, I'm retired NT admin (2001)... Loved NT...  "Back then" programs dint do the stuff they do now (i.e., browser running scripts, etc) , so having total control was very nice...

---

### Post by CatKiller on 2019-12-13
I don't think that the permissions of the script have anything to do with it. It seems very likely to me that the issue is that your application is writing directly to the hardware, which standard users and malware are generally prevented from doing.

You might be able to use group membership to control access to that hardware without always needing to run your script as root.

---

