---
title: "synaptic, reboot, and ghostly installs"
date: 2008-01-24
forum: General Help
---

### Post by ClarkePeters on 2008-01-24
Major prob here, I think.  
Using Gutsy.
I installed some programs from Synaptic that didn't take. I installed flashplugin-nonfree and  php5. After installing flash, synaptic showed that it was installed but about:flash in firefox said no plugins installed. I tried twice. Synaptic showed installed, firefox said NOT. Then finally went to Adobe and got their tar. All is well.

That doesnt' bother me so much as when the same thing happened with php5. I installed through synaptic and restarted synaptic just to be sure. Synaptic said it was installed. I did a terminal search, locate, which, and find, there was no indication of php5. then I did a test.php page with a phpinfo script. No go.  

So I rebooted my system (after my lunch) and just by accident when starting firefox it asked me if I wanted to restore, I said yes, and voila! the php test page worked. So I know my system has Php5, synaptic says php5 is installed, but a search such as which and locate do not show the php5 directory anywhere. So then I did a cd /etc and ls. sure enough, php5 is there as well as apache2. So I did a which apache2 and got the path, but when I did which php5 I got nothing. 

should I report a bug? My system works fine but we need consistency. What can I do?

Oh, and this makes me wonder if I had just rebooted after the flash install, maybe it was really installed after all.  Is Ubuntu going the ways of windows where we need to reboot after every install? oh, please say no!

If someone needs more info, let me know.

---

### Post by p_quarles on 2008-01-24
No, the reboot wasn't what changed anything. The Flash package in the repos is currently broken. Installing the PHP5 module for Apache requires you to restart Apache itself, but not the entire computer. 

As for where PHP5 is, it's not a standalone executable: it's a parsing module for Apache. It's in /usr/lib/apache2/modules.

Threre *is* a standalone executable for PHP5: the package name is php5-cli, and it's a PHP shell interface.

---

### Post by ClarkePeters on 2008-01-24
How do you guys know so much? You're terrific. Thanks for the quick response, but mostly, I'm happy there's no problems.
Thanks again :)

---

