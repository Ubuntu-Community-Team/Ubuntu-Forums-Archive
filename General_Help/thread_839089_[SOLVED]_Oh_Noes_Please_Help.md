---
title: "[SOLVED] Oh Noes Please Help"
date: 2008-06-24
forum: General Help
---

### Post by pbeesley on 2008-06-24
Please Help. I keep talking up Hardy to my friends but I've hit a wall and its doing my head in.

**Background**
Had my pc on, logged in with a shutdown command on it ```
shutdown -v -P
``` but the PC crashed with about 4mins to go :(

**Problem**
Now I can't log in! Whenever I click on my name I get a pop up saying "This system will shutdown in 4 mins" << or something that that. It also says authentication failed letters must be typed in the correct case. I've tried both users I have by both typing in (upper and lower case) and also by clicking on the user names.

**Other Info**
I can log on as root but as root I can't cancel the shutdown process cause the PID doesn't exist? I can't create a new user. (wanted to see if I could login as a new user)

**Request**
I need to be able to log in. Please help I either need to be able to login OR reinstall and not lose anything! is there a way to back up everything. reinstall and then restore the data so its exactly the same?

Thanks for the help guys:KS

---

### Post by Aearenda on 2008-06-24
Bizarre!

```
sudo shutdown -c
```This cancels a running shutdown. I guess the shutdown was saved in your session somehow. Are you using Gnome?

Also, you should be able to login on a console (Press CTRL and ALT and F1) and prepare a shutdown cancel command, then switch back to the login screen with CTRL and ALT and F7, logon, then immediately switch back to the console and do the cancel.

Also from the console, you should be able to add a new user by
```
sudo adduser <name>
```

---

### Post by darkworld on 2008-06-24
go in as root and try shutdown -c

---

### Post by pbeesley on 2008-06-24
> **darkworld said:**
> go in as root and try shutdown -c

When I did this it said something like 'shutdown PID does not exist'

Also on a separate note I'm unable to login into my girlfriends account which wasn't running the shutdown do-hicky. Also I tried leaving the pc on the shutdown screen for a while (e.g. more than 4mins) but it didn't shut down :(

---

### Post by Aearenda on 2008-06-24
It sounds to me as if a no-login flag of some sort is set - I don't know if GDM or Gnome has such a thing. Can you log on to a console and use 'startx' to get into Gnome?

---

### Post by pbeesley on 2008-06-24
> **Aearenda said:**
> It sounds to me as if a no-login flag of some sort is set - I don't know if GDM or Gnome has such a thing. Can you log on to a console and use 'startx' to get into Gnome?

Please forgive me for being dumb :confused: but how do I log on to a console?

---

### Post by Aearenda on 2008-06-24
Console login:

1. Wait for the system to come the normal login screen.
2. Press CTRL and ALT and F1
3. You should see a black console screen with white writing, and a login prompt. Type your username and press Enter.
4. Type your password and press Enter.
5. You should now get a command prompt.

However, I suspect the PAM nologin flag is set, somehow, and that you will still be unable to login to your normal user. You mentioned using 'root' earlier, so see if you can login to root at the console. If you can, do this as your next command:
```
sudo rm /etc/nologin
```
Actually here the sudo is unnecessary if you have logged in as root.
After you have done this, press CTRL and ALT and F7 to go back to the normal login screen and see if you can login.

---

### Post by Aearenda on 2008-06-24
Unfortunately, I have to go out in a minute. If my previous suggestion has not worked, try this:

1. Reboot your computer.
2. When it says 'Press Esc to enter menu' (or words to that effect), Press ESC.
3. At the boot menu, use the cursor keys to select the first line that says 'recovery mode', then press Enter.
4. Admire the text that goes whizzing past!
5. When it stops and asks you whether to continue, repair X, or drop to a root command session, choose the root command session.
6. Type this command:
```
rm /etc/nologin
```and press enter.
7. If that fails, tell us what it said. Someone else may be able to help while I'm out.
8. If it worked (i.e. no complaints are made), press CTRL and D.
9. Now choose 'Continue' from the options.
10. You should be able to login and work normally now.

Good luck!

---

### Post by pbeesley on 2008-06-24
[QUOTE=Aearenda;5250426]

However, I suspect the PAM nologin flag is set, somehow, and that you will still be unable to login to your normal user. You mentioned using 'root' earlier, so see if you can login to root at the console. If you can, do this as your next command:
```
sudo rm /etc/nologin
```
 tried that and got this ```
root@sol:~# rm /etc/nologin
rm: cannot remove `/etc/nologin': No such file or directory

```


:(

---

### Post by pbeesley on 2008-06-24
Fixed! I think by chaning my BIOS clock....no idea :) fixed now anyway thanks for all the help

---

