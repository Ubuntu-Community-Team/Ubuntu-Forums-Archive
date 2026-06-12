---
title: "EMERGENCY:  NO GUI Interface after restarting, &quot;reinstalled Nvidia drivers, crashed.."
date: 2007-02-10
forum: General Help
---

### Post by uberlounge_com on 2007-02-10
**Brief History/Knowledge:**
OK, as you already know I am sure.... I am a complete n00b.  5 days in the linux world and loving Kubuntu 6.10 32 Bit Edgy

**System Overview **- (I know it is overkill for me to list all that but I know people sometimes take an interest to it)
Dell Power Edge 400SC
P4 2.8Ghz Hyper Threading
4 GIGS OCZ PC3200 Server Memory
BFG nVidia Geforce 6200 256mb
250GB SATA
Dual 16x DL-Burners
SoundBlaster X-Fi Music


**MY PROBLEM IS, **after restarting my computer after using automatix bleeder to install my nvidia drivers over the same drivers installed I got a system crash in the installation I believe, told me I had to restart my computer but first take not of this line of code:

*sudo cp /etc/x11/xorg.conf_backup_200702101353 etc/x11/corg.conf*

I typed exactly that and some mild variants after I was able to log in with my user name/pass in the (your going to kill me) Dos looking screen.  What is it, the console?

Anyways, I keep getting error messages saying it doesn't work or something is missing (i know that's not too helpful)) but it was along the lings of x11 or xorg and some folder not existing.

This all happened because I was going to install Beryl and I read from someone that I had to un-install the nVidia drivers first (I did no problem), then I installed nVidia drivers using some other program just like automatix but without the GUI.  I felt I had to install the nVidia drivers because in another thread on this form, I had to run a script to see if my card, a Geforce4 6200 256mb, had the graphic accelerator enabled and it came back as not enabled.  So, me being the n00b I am, ignored the warning automatix bleeder gave me and attempted to install the drivers again without removing them.  I believe I got 90-95% of  the nVidia drover installed. (who the heck knows... that is just a hunch) and then the system crash or whatever word linux uses, copied the code that it recommended I do just in case there was a problem just like there is right now.  PLEASE PLEASE PLEASE SAVE ME.  I AM DYING TO INSTALL BERYL and XGL  

How do I solve this problem?

Off Subject Mostly:  With automatix bleeder, it will be a hastle free installation for Beryl for a newb like me by using the installer feature, right?    Also, is XGL already installed in my Kubuntu 6.10?

---

### Post by gradedcheese on 2007-02-10
You're missing slash:

sudo cp /etc/x11/xorg.conf_backup_200702101353 **/**etc/x11/corg.conf

The 'dos looking screen' is the shell.  That's what's below all the GUI stuff, ie: X.  It is indeed, like the DOS shell, but much more sophisticated.

---

### Post by Gibbs on 2007-02-10
Heh I just got this a minute ago. I'm always having problems with xorg.conf and nVidia drivers.

Envy is a good program and installs the drivers for you: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I call the "DOS" looking program the "Shell Terminal", I'm new to Lin ux too but have learnt to make lots of backups of xorg.conf.

I don't understand your question but if you still can't log in this is what I do...

When X service fails to start hit OK and then CTRL-ALT-F1. Log in as root. Change to the X11 directory:
```
cd /etc/X11
```

Use ls to see the files in the directory. If you have a backup use a command like this:
```
mv xorg.conf xorg_corrupt.conf
mv xorg_backupfilename.conf xorg.conf
```

Then hit CTRL-ALT-DEL and reboot. Should work. Then give [ENVY]("http://albertomilone.com/nvidia_scripts1.html") a try ;)

Edit: Does anybody know the command to start the X service? That would be handy and save rebooting...

---

### Post by PatrickMay16 on 2007-02-10
Hang in there. At the DOS-looking screen, log in and use this command:

sudo dpkg-reconfigure xserver-xorg

This should at least get your video up again until you can get the official nvidia driver working.

---

### Post by uberlounge_com on 2007-02-10
My bad, I actually have been using the slash.  I just tried it again and this is the OFFICIAL ERROR MESSAGE:

cannot stat '/etc/x11/xorg.conf_backup_200702101353':    No such file or directory

Once again, what I am typing in the shell is:
Sudo cp /etc/x11/xorg.conf_backup_200702101353 /etc/x11/xorg.conf

(I double checked it this time, both on the shell and right above)

---

### Post by uberlounge_com on 2007-02-10
> **PatrickMay16 said:**
> Hang in there. At the DOS-looking screen, log in and use this command:

sudo dpkg-reconfigure xserver-xorg

This should at least get your video up again until you can get the official nvidia driver working.

I just saw your reply while I was typing the one I just left.  I will try it right now and let you know.  Thanks!

---

### Post by gradedcheese on 2007-02-10
type "ls /etc/X11/" -- does that file you're copying even exist?  Is it's name typed correctly?

---

### Post by hotani on 2007-02-10
this happened to me and I got back up and running by entering the grub menu and choosing the *-10-generic kernel instead of the new *-11. At least I can attempt to fix the problem from a working system.

---

### Post by uberlounge_com on 2007-02-10
> **PatrickMay16 said:**
> Hang in there. At the DOS-looking screen, log in and use this command:

sudo dpkg-reconfigure xserver-xorg

This should at least get your video up again until you can get the official nvidia driver working.

Patrick,
I got all the way to the part where I need to pick: Desired default color depth in bits screen.  

I tried to go to the ok but nothing works this occurred when I selected 24 bit:
xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/x11/xorg.conf.200702101651-1

And of course after that, the next line is the login name@comp name: ~$

Thanks for your help in advance.

---

### Post by CocoAUS on 2007-02-10
Well, uh...the "X" in X11 needs to be capitalized.  Does that help?  *nix systems are case-sensitive.

---

### Post by uberlounge_com on 2007-02-10
> **gradedcheese said:**
> type "ls /etc/X11/" -- does that file you're copying even exist?  Is it's name typed correctly?

I double checked with the code I put in my 2nd post and it is all the same.  I even tried it multiple times.  I know I am capable of "fat fingering" it more then once but I pecked like a bird at the keyboard to make sure 2 additional times.  PatrickMay is on to something but I just got hung up at the desired default color depth screen when using the reconfiguration of the xserver.

Thanks for your attention to this matter.  I really am enjoying the Linux community.  I am free of the shackles that Microsoft had on me at last.

---

### Post by OffHand on 2007-02-10
> **Gibbs said:**
> 
Edit: Does anybody know the command to start the X service? That would be handy and save rebooting...

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm restart

---

### Post by Shortgeek on 2007-02-10
> **OffHand said:**
> sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm restart

He said he was using Kubuntu; it should be

```
sudo /etc/init.d/kdm stop
sudo /etc/init.d/kdm start
sudo /etc/init.d/kdm restart
```

---

### Post by uberlounge_com on 2007-02-10
> **CocoAUS said:**
> Well, uh...the "X" in X11 needs to be capitalized.  Does that help?  *nix systems are case-sensitive.

I will give it a try.  Hopefully someone may be able to help me in the reconfiguration process PatrickMay was guiding me in until I got screwed up on the default color depth screen when I couldn't select "OK" and the shell became active on the bottom of the LCD.

---

### Post by Gibbs on 2007-02-10
> **OffHand said:**
> sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm restart

Thank you! :)

---

### Post by uberlounge_com on 2007-02-10
"
Quote:
Originally Posted by CocoAUS View Post
Well, uh...the "X" in X11 needs to be capitalized. Does that help? *nix systems are case-sensitive.
I will give it a try. Hopefully someone may be able to help me in the reconfiguration process PatrickMay was guiding me in until I got screwed up on the default color depth screen when I couldn't select "OK" and the shell became active on the bottom of the LCD.

> **uberlounge_com said:**
> I will give it a try.  Hopefully someone may be able to help me in the reconfiguration process PatrickMay was guiding me in until I got screwed up on the default color depth screen when I couldn't select "OK" and the shell became active on the bottom of the LCD."

CocoAUS, i tried it with the capital X's (only thing I capped) and besides the "S" in sudo being capped and got this error:
-bash: Sudo: command not found

---

### Post by uberlounge_com on 2007-02-10
Anyone Out There?

---

### Post by CocoAUS on 2007-02-10
The "sudo" command should not be capitalized.  Unless your username or anything is capitzalized, the only capital letter in the command should be the X in "X11."

---

### Post by uberlounge_com on 2007-02-10
> **CocoAUS said:**
> The "sudo" command should not be capitalized.  Unless your username or anything is capitzalized, the only capital letter in the command should be the X in "X11."


AND THE WINNER IS: COCOAUS!  Thanks for your help.  Much appreciated.  It all works now.  Up and running.

---

### Post by CocoAUS on 2007-02-10
Glad it's working for you.  :)

---

### Post by MoLE on 2007-02-10
> **uberlounge_com said:**
> I double checked with the code I put in my 2nd post and it is all the same.  I even tried it multiple times.  I know I am capable of "fat fingering" it more then once but I pecked like a bird at the keyboard to make sure 2 additional times.

I highly recommend spending 10-15 minutes reading through a brief tutorial on using the shell.  

Before linux had a GUI, there was the shell.  Of course there are many different options for the shell environment, but [bash]("http://www.gnu.org/software/bash/") is the default shell for Ubuntu.

"TAB autocompletion" is your friend.  Bash has a feature (which I notice has been adopted by the WinXP commandline shell), where you can type the first few letters of a path or filename, press the TAB key, and have the shell software fill in the rest of the path for you.

Try the following:
```

sudo cp /e[TAB]X[TAB]xo[TAB]

```

your commandline should now look like:
```
sudo cp /etc/X11/xorg.conf
```

Now (and here's the best part), you can press [TAB] twice and the shell will present you with a list of files that fit your current pattern.  For example:
```
xorg.conf                 xorg.conf.backup          xorg.conf_partial-backup
```

Then, say you want to use the xorg.conf.backup file to restore from, your next character you type would be a "." (dot), then press [TAB] for the rest.

Then type a space and then the path you want to copy your backup file to - in this case:
```
/e[TAB]X[TAB]xo[TAB]
```, which should leave you with:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Then just press enter and you will be prompted for your password.

Doing it this way has two advantages:
1. you avoid as many typing mistakes, as the shell helps remind you which files are there and the capitalisation of them.
2. it's much quicker than typing out the whole line of commands.

Have fun with the commandline - it has it's advantages.

Google found me a nice [beginner's tutorial]("http://www.linux.org.mt/node/49#N10412") for you.

---

### Post by uberlounge_com on 2007-02-12
Thanks for spending the time to teach me that.  Appreciated.  

NEW PROBLEM:
Starts me up in shell 90% of the time,  what the heck...

---

