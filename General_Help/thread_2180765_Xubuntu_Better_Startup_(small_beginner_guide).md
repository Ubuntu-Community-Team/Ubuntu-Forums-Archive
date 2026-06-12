---
title: "Xubuntu Better Startup (small beginner guide)"
date: 2013-10-14
forum: General Help
---

### Post by Arto_Kalishian on 2013-10-14
Hi,

I have had some problems with Xubuntu during startup (very minor but important for me). When I found the solutions I thought of writing a small guide how to fix those problems.

1. Xubuntu starts up the laptop screen too bright on my laptop.
2. Xubuntu starts with the sound muted.
3. Xubuntu starts with bluetooth On, although I rarely use it.

Pre-requisites:
1. You will need to install xbacklight
sudo apt-get install xbacklight

- All the other tools you will need are already installed with Xubuntu 13.

So I decided to write a small script that would solve these problems.

1. Open mouspad and copy paste the following in it.

```
#!/usr/bin/bash
amixer set Master 40db
xbacklight -set 80
sleep 10
rfkill block bluetooth

```
2. Save the file as laptop_startup_mode.ksh in your home folder.

3. Now we need to do 2 things to the script. Give it permissions and move it to /usr/local/bin
```

cd
sudo chmod 755 laptop_startup_mode.ksh
sudo mv laptop_startup_mode.ksh /usr/local/bin/

```

4. Now all we need to do is to make sure that the script runs in startup.
```

1. Go To:
Applications Menu --> Settings Manager --> Sessions Startup -->  Application Autostart [tab] --> 

2. Click:
+Add

3. 
Name: Laptop Startup Mode
Description: Laptop Startup Mode
Command: (click on button beside it, and browse Filesystem to /usr/local/bin/laptop_startup_mode.ksh)

```

----
Extra notes: 
1. You will find that in the script I used "sleep 10" to delay the closing of the bluetooth, because if you don't do that the bluetooth application starts *after* your script is finished.
2. You will notice the permissions are set for the script is 755, that's because we need the root user (administrator) to have full access (read 4, write 2, execute 1 = 7), and the standard user and all others to have read (4 +execute 1 = 5) access.

For any enhancements, comments, feedback, suggestions please do.

---

### Post by CaptainMark on 2013-10-14
The best way to stop bluetooth booting is to edit the file /etc/bluetooth/main.conf and change "[FONT=Courier New]InitiallyPowered = true" to "[/FONT][FONT=Courier New]InitiallyPowered = false[/FONT]" and remove the applet entries from the sessions manager, the way your doing it now starts bluetooth and then blocks it which wastes cpu cycles (which may or may not be crucial)
Also I've been using the amixer method of controlling volume on my desktop for some time and it would better to move that to after the 10 second sleep as on occasion amixer isn't ready in time and wont receive the command
2nd also, the ksh shell is not included in a default install of Xubuntu so you would need to install it first, or you could just change this script to bash as that IS installed and all these commands would work in bash
3rd also, your shebang is incorrect it should be #! not just #

---

### Post by Arto_Kalishian on 2013-10-16
Thanks for the advice Mark. Well said.

---

### Post by Arto_Kalishian on 2013-10-16
Ok,[FONT=Courier New] "[/FONT][FONT=Courier New]InitiallyPowered = false[/FONT]"
didn't work.

I will revert back to the script.

---

