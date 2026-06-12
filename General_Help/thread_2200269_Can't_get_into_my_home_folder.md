---
title: "Can't get into my home folder"
date: 2014-01-18
forum: General Help
---

### Post by david98 on 2014-01-18
Hi am using ubutnu 13.10 and my son had been playing on my laptop he said it asked for updates so i gave him my password. Since then every time i switch on my laptop it boot's into what i presume is a guest account with no icons on the top right hand corner so no way to power off no way to switch users. I cant seem to do anything to get into my admin account i have both of my passwords for my admin account witch is dave and also have my root password. I desperately need to get into my account as it has all my file's and folders that i need access to any help would be much appreciated i cant get into the terminal in this account so i haver no clue how to fix this.:confused:

---

### Post by Iowan on 2014-01-18
There are a couple of articles [here]("http://www.psychocats.net/ubuntu/") that might be helpful.
[Reset password]("http://www.psychocats.net/ubuntu/resetpassword")
[Fix sudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by jeanjd63 on 2014-01-18
Hello
You can try to open a terminal by : ctrl+alt+t 
If not, when you have the connection screen you do CTRL+ALT+F1 to open a console. 
You give name and password the you try this :
[B]df  -h
df  -i
[/B]and you control you have not a 100% value on column Use%
If no you can try :
**sudo  rm  .Xauthority .ICEauthority **
Then you comes in graphic : CTRL+ALT+F7 and you try connect with your user.

---

### Post by david98 on 2014-01-18
In the process of reading through the articles now lowan And jean it wont let me open a terminal. I have got into the account now by pressing e on the bootloader screen booting in to text then logging in then typing startx but the desktops not preety no icons but i use the terminal so i can get access to my files atleast till i find out what happend

---

### Post by jeanjd63 on 2014-01-18
You can try this :
[COLOR=#000000][FONT=Arial]1 Open a terminal : CTRL+ALT+T[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]2 Installation of compizconfig_setting :[/FONT][/COLOR]
**[FONT=Consolas]sudo apt-get install compizconfig-settings-manager[/FONT]**[COLOR=white][FONT=Consolas][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]3 Then you do :[/FONT][/COLOR]
**[FONT=Consolas]ccsm[/FONT]**
[COLOR=#000000][FONT=Arial]4 In Desktop / Ubuntu Unity Plugin,  [FONT=Arial] t[/FONT][FONT=Arial]ick at left [/FONT] "Activate Ubuntu Unity Plug"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-01-18
Have you considered that your son may have removed you from being a user? He could have made himself Administrator and even changed the password. Open System Settings>User Accounts and see if you are still listed as a user and if your password still works.

Regards.

---

### Post by david98 on 2014-01-18
@ grahammechanical my user accout is still there am logged into it now via text mode once i logged into text mode used startx now am in a gui mode but do not have any icons the only way i can do anything is via terminal using ctr alt t. As for doing anything in the guest like account i cannot wont open anything. when i go to user accounts my account dave user administrator is there but i can not unlock it so am stuck. Any more advice would be appreciated.

---

### Post by jeanjd63 on 2014-01-18
See the post #5

---

### Post by david98 on 2014-01-18
jeand63 ive done post 5 ive got a a working graphics screen but i still have to boot into text mode then use the startx command to get a working screen. It helps me get into my admin account but it still does not solve the problem of when a boot up it goes into a guest like account and once am there a cant do nothing. Thanks for your help though it got me a working screen to use while a try to fix whatever is wrong with it

---

### Post by jeanjd63 on 2014-01-18
What append exactly when you boot "normally" ?
You have a screen with logon ? or you logon directly in guest user ?

---

### Post by steeldriver on 2014-01-18
Maybe your son configured the system to auto-login to his own account (or the guest account)? you can check from the GUI 'System Settings' --> 'User Accounts' or by looking at the contents of the /etc/lightdm/lightdm.conf file, either by navigating to it and opening it in a text editor (it will only open 'read-only') or by opening a terminal window and typing

```
cat /etc/lightdm/lightdm.conf
```

---

### Post by david98 on 2014-01-18
It logs directly into a guest account with no way to log out or switch user

---

### Post by david98 on 2014-01-18
@ steel driver it says there's no other accounts on the system ?
Puzzled is not the word

---

### Post by jeanjd63 on 2014-01-18
Could you give the return of ::
[B]sudo  ls  -l  /home
[/B]and the contains of :
**sudo  cat  /etc/lightdm/lightdm.conf**

---

### Post by david98 on 2014-01-18
@jeanjd63 
dave@dave-300E5EV-300E4EV-270E5EV-270E4EV:~$ sudo ls -l /home
total 12
drwx------ 55 dave dave 12288 Jan 18 14:45 dave

---

### Post by jeanjd63 on 2014-01-18
and the contains of :
**sudo cat /etc/lightdm/lightdm.conf**

---

### Post by david98 on 2014-01-18
It's saying no such file or directory

---

### Post by jeanjd63 on 2014-01-18
And :
**sudo cat /etc/gdm/custom.conf**

---

### Post by david98 on 2014-01-18
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.


[daemon]
# Enabling automatic login
#  AutomaticLoginEnable = true
#  AutomaticLogin = user1


# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10


# Reserving more VTs for test consoles (default is 7)
#  FirstVT = 9


[security]


[xdmcp]


[greeter]
# Only include selected logins in the greeter
# IncludeAll = false
# Include = user1,user2


[chooser]


[debug]
# More verbose logs
# Additionally lets the X server dump core if it crashes
#  Enable = true

---

### Post by jeanjd63 on 2014-01-18
You can  try, in graphic mode, to force the autologin for the user dave 
In Param System, Users, your user, you valid "Auto cnx" and you try to reboot.

---

### Post by david98 on 2014-01-18
will try it soon got to pop out. Thank's for your help.

---

### Post by david98 on 2014-01-24
Just transferred all  files to another hdd and done a fresh install I've also made a clone of my hdd so as not to have this problem again

---

