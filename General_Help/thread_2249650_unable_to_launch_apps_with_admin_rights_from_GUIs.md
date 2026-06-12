---
title: "unable to launch apps with admin rights from GUIs"
date: 2014-10-23
forum: General Help
---

### Post by Borgoz on 2014-10-23
Hi, after upgrading to utopic I'm facing an issue.
Basically my user cannot gain root privilegies if the trigger (the button) to gain those privilegies is embedded the user interface.
Some examples:
[LIST]
[*]if I open the unity-control-center (formerly gnome-control-settings) and then move to the User Accounts section I see the "unlock" option grayed out and I cannot gain root right to edit users.
[*]I  have the synaptic (package manager) icon stick on my unity laucher. If I click on it nothing happens. If I run unity in debug mode (unity -d) and then click the synaptic icon I get prompt for the user password straight within the terminal window where the unidy -d command was run from.
[/LIST]

Sudo from command line works perfectly so I have been able to create a new user to thest whether the issue was within my user config. Once logged in I noticed the same issue was affecting that new user too.

So, does someone of you have an idea of what's going on with my box?

thanks

---

### Post by 3246251196 on 2014-10-23
I cannot test this as I have a different flavour, but perhaps making sure you have *gksu* installed will enable the prompt box for privilege password?

---

### Post by Borgoz on 2014-10-24
unfortunately gksu is already installed.
thanks for the suggestion though

---

### Post by Bashing-om on 2014-10-24
Borgoz; Hello,

I too have no direct experience, but here is a thought:
> 
Gksudo and others are deprecated now and not recommended any more. Pkexec is the new boy but it is not straightforward either.

Discussion here.

[http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)
&&
> 
< Jordan_U> Bashing-om: The reason they(gksudo) are no longer installed by default is that there are no GUI apps in the default install with launchers using gksudo/gksu. All default GUI apps that need elevated privileges most of the time now use PolicyKit to ask for specific privileges rather that having to run the whole app as root.


In the transition of things to come
[INDENT][INDENT][INDENT]this is food for thought
[/INDENT][/INDENT][/INDENT]

---

