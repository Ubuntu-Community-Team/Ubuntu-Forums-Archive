---
title: "Laptop won't wake up from sleep mode"
date: 2014-04-24
forum: General Help
---

### Post by mitchelvostrez on 2014-04-24
Hello, this is my first post so let me know if I'm doing something wrong here, but recently, as far back as 13.10, Ubuntu will not resume after I close the lid of my laptop, or if I put it to sleep regularly. Every time, it'll either give me an error screen, or it'll show the login screen, but I can't interact with it at all. Any ideas?

---

### Post by trag on 2014-04-26
May have better luck enabling and getting it wake up using hibernate **Test if hibernate works in your case:**[COLOR=#333333][FONT=Helvetica Neue]Before getting started, press Ctrl+ALt+T on your keyboard to open the terminal. When it opens, run:
[/FONT][/COLOR]
sudo pm-hibernate[COLOR=#333333][FONT=Helvetica Neue]After you computer turns off, switch it back on. Did your open applications re-open? If hibernate doesn&#8217;t work, check if your swap partition is at least as large as your available RAM.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]**Enable Hibernate in System Tray Menu:**
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]The indicator-session was updated to use logind instead of upower. Hibernate is disabled by default in both upower and logind.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]To re-enable hibernate, run the commands below one by one to edit the config file:
[/FONT][/COLOR]
sudo -i

cd **/var/lib**/polkit-1/localauthority/50-local.d/

gedit com.ubuntu.enable-hibernate.pkla[COLOR=#333333][FONT=Helvetica Neue]*Tips: if the config file does not work for you, try another one by changing **/var/lib** to**/etc** in the code.*
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Copy and paste below lines into the file and save it.
[/FONT][/COLOR]
[INDENT][Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes

good luck
trag
[/INDENT]

---

### Post by Mr._Pipiens on 2014-04-26
I had the same problem since 13.04. Solved it in 14.04 by changing to the most recent video driver available in Software & Updates/Additional Drivers.

---

### Post by braufrau on 2014-10-25
How strange. Using the NVIDIA proprietary drivers on my Dell Latitude fixed the problem too!
Thanks for the tip!

---

