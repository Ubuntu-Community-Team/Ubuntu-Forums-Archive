---
title: "Zapped?"
date: 2014-03-25
forum: General Help
---

### Post by jackbn on 2014-03-25
Yesterday, my system worked, but would not allow some system functions.

Today, when I boot, it shows the normal sign-in screen, but blacks out when I enter my CORRECT password.
The monitor remains black, no matter how long I wait.

The system is drawing nominal idle power (per power readout on my APC UPS) while the screen is black.

I have tried with and without Internet connection.

This is a dedicated Ubuntu 13.10 system, no Windows on it.

Is there any way to recover, or must I format and start over?

Thanks

---

### Post by ajgreeny on 2014-03-25
What system functions were not allowed yesterday?

Can you use Ctrl+Alt+F1 at the login screen to get to a command line and login there with your name and password, the latter of which will not be shown on screen in any way.

If you get to that point run ```
sudo apt-get update
sudo apt-get upgrade
``` and see if that helps.

---

### Post by jackbn on 2014-03-25
Thanks for the reply.

Tools would not open. Ubuntu update would not work. Probably others.

When I now try control + alt + F1, it first asks for login.
I don't know what to enter. When I enter my password, it repeats request for login.



Different question, for if I must reinstall -- is there any way to recover files from the SSD with my Windows 7 computer?
In the past, when I have connected an Ubuntu drive to Windows, it was not recognized.

---

### Post by PondPuppy on 2014-03-25
This may be a stupid question, but have you tried booting from a thumb drive or DVD/CD?

---

### Post by jackbn on 2014-03-25
Great idea, PondPuppy. That works.

I want to transfer my old Firefox bookmarks to a flash drive.
The two listed computers are "478 volume" and "Computer".

I don't know which is the DVD volume and which is the main drive,
but my main drive is a nominal 512GB and probably has 478GB. 

Any idea where to find Firefox bookmarks?

---

### Post by jackbn on 2014-03-25
I have been looking, and think I found the bookmarks in:
478GB volume -> firefoxbookmarks ->unity_firefoxbookmarks_daemon.py

BUT I know that exported or imported bookmarks are in HTML format.

Will I be able to use the .py file to transfer the bookmarks to a new Ubuntu 13.10 build?
Or, is there a way to change the .py file to an HTML file?

---

### Post by jackbn on 2014-03-26
Well, i abandoned this software build, and lost my work of the last week or ten days, since my last backup to flash. 

I put the (Ubuntu) Samsung 512GB 840 Pro in my Windows 7 computer, and discovered this drive had issues, which surely caused the Ubuntu hangup.
This is my THIRD Samsung 840 Pro drive that's had problems. I have two 512GB 840 Pros and several 256GB 840 Pros.

In two cases, I patched them up by deleting the partitions and reformatting.
Then I use Samsung Magician to apply the full treatment: Run a full trim, set up overprovisioning again, and run all available tests.

The third 840 Pro ran an automatic fdisk upon boot (don't recall ever seeing that before), but no problems since.

I've NEVER had a problem with an Intel SSD, going back five or so years. I am inclined to buy only Intel now.
So far as I know, only Samsung and Intel have decent SSD maintenance software, thus other brands fall short.

---

### Post by ajgreeny on 2014-03-27
For future reference all the bookmarks for FF are kept in the .mozilla/firefox/x#x#x#x#.default/bookmarkbackups/ as **bookmarks-date_###.json **files which you can copy then restore in any other FF installation by going to** Bookmarks ->Show all bookmarks ->Import and Backup** then navigating to the .json file you want to use..

---

### Post by buzzingrobot on 2014-03-27
When you did the ctrl-alt-f1 and were prompted to login, it wanted your username. Next, it would have prompted for a password.

---

