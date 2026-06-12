---
title: "What happened to &quot;Switch User&quot; ?"
date: 2020-10-05
forum: General Help
---

### Post by bugbear6502 on 2020-10-05
Just did a fresh install of Lubuntu, Ubuntu 20.04.1 LTS (was running 18)

On my laptop (only) machine, I have always had two logins, one for me, one for my partner. This allows us to have separate password and bookmark configs in Firefox, and I also have her Desktop setup much simpler than mine.

Since I'm normally logged in, with multiple things running, my partner normally uses "switch user" so that she can log in, do what she needs to do (normally a little on-line banking), then log out leaving all my stuff in place.

The "Switch User" option has gone from the menu (now called the "leave" menu).

Is this deliberate feature-cide, or am I just loooking in the wrong place?


  BugBear

---

### Post by GhX6GZMB on 2020-10-05
Lubuntu 20.04 LTS uses "Logout/Login" in the "Leave" menu. Takes a few seconds.

---

### Post by helen314 on 2020-10-05
I was a pretty happy camper using 16.04 . 
I am now stuck with and issue and wondering if this would be a good time to bite the bullet and "upgrade". 
I am toying with  an idea of fresh install. 
I am not in favor to complicate things and after your post I am wandering if similar changes ( from 16 ) would make life more complicated.
AS it stands now I foresee need for rapid user switching before I get the current issue solved. 
"few seconds " is borderline acceptable...

---

### Post by GhX6GZMB on 2020-10-05
> **helen314 said:**
> 
"few seconds " is borderline acceptable...

The switch is fast. The "few seconds" are PW typing.

---

### Post by ajgreeny on 2020-10-05
Which display-manager does Lubuntu use now?
Xubuntu still uses lightdm and it still has the "Switch User" option in the logout dialogue.

Perhaps worth trying installing lightdm and configuring the system to use that instead of the current dm?

---

### Post by GhX6GZMB on 2020-10-05
> **ajgreeny said:**
> Which display-manager does Lubuntu use now?


sddm.

---

### Post by bugbear6502 on 2020-10-06
That's not the same - logging out is precisely what I'm trying to avoid when I have a load of applications running, with sized and placed windows (i.e. valuable "state").

Switch user does NOT log the original user off - Unix/Linux is more than capable of handling this.

   BugBear

---

### Post by bugbear6502 on 2020-10-06
> **ml9104 said:**
> sddm.

That may not be good - IIRC I selected lightdm at the install window.

Should I reinstall?

EDIT: I clearly misremembered:

[FONT=courier new]cat /etc/X11/default-display-manager
/usr/bin/sddm
[/FONT]
   BugBear

---

### Post by jmclement on 2020-11-11
Hi, 
I also installed Lubuntu 20.04 and am also missing the "Switch Account" functionnality ; is there a way to get it back ? (if not, I'll go back to 18.04, too much hassle with 20.04!)
My install is with the default sddm.
Thanks,
JM

---

### Post by ajgreeny on 2020-11-11
So have you tried installing lightdm and reconfiguring the system to use it instead of ssdm as I suggested?

I don't  know if that will work as you want but it must be worth trying.

---

### Post by jmclement on 2020-11-11
> **ajgreeny said:**
> So have you tried installing lightdm and reconfiguring the system to use it instead of ssdm as I suggested?

I don't  know if that will work as you want but it must be worth trying.

Thanks for suggesting ; I agree that it should work using lightdm. However, I would have enjoyed a solution with the default dm - I simply can't believe that the default installation does not allow for switching user... This and too many other hitches (power button configuration, for example) will probably lead me to revert to 18.04.

JM.

---

### Post by chw9999 on 2021-01-21
The thread is not young anymore, but the problem persists. Lubuntu 18.04 will be outdated this year, so I really want to switch to a new LTS version, 20.04 that is. However, not being able to switch accounts **easily** on the fly bugs me as well big time.

Anyway, I found a crude workaround for this:
If I log into Lubuntu 20.04 as the first user, I will see the login screen displaying all the available logins.
Here I switch to another tty console using **STRG-ALT-F[number]**, with F[number] usually an FKey >=3 (the workaround does not work with "F2"!).
This switches the screen to a prompt. Log in using your credentials, and then enter **startx**. This will run the Display Manager using your user (no more login screen).

If you want to switch to another user in parallel mode, just go to another tty console (say, STRG-ALT-F4), login with whatever other user you want, and use startx again.
STRG-ALT-**F1** will lead you to the login screen, from where you can login with any other user the "regular" way (today, it simply does not work with my computer, but regularily it works ;))!

Switching back to *your* user just needs pressing **STRG-ALT-F[your-number]** again.

Caveat:
* another user may not be aware of your parallel login and simply shuts down the machine after his/her work... 
* another user may not know how to switch users and simply logs you off... 
* it may not work if another user logged in the regular way (tty1)
* since you open multiple display managers, you may need more memory than using only one iteration.

Hope it helps!

Cheers,
 Christoph 
P.S. Honestly: as long as 18.04 is supported, I will only occasionally use 20.04. Still too buggy. If it gets fixed, I may use it in the future, otherweise: other flavours are nice as well! :) 
(Edit: typos)

---

### Post by vidtek on 2021-01-21
See this for SDDM on KDE

Credit to cube2_  on Reddit [https://www.reddit.com/r/kde/comments/i94khf/suddenly_missing_switch_user_button/]("https://www.reddit.com/r/kde/comments/i94khf/suddenly_missing_switch_user_button/")

1 month ago

On kubuntu 20.10, The way I solved it was via xdotool to simulate ctrl+alt+F2, when a custom widget is clicked:


Created a shell script (replace OTHERUSER with appropriate user):

```
#!/usr/bin/bash
rbtty=`who | grep OTHERUSER | grep tty`
parsetty=`echo $rbtty | awk '{print NF}'`
if (( $parsetty > 2)); then
    ntty=`echo $rbtty | awk '{print $2}' | awk -F"y" '{print $2}'`
    xdotool key ctrl+alt+F$ntty
else
    kdialog --msgbox " OTHERUSER Desktop is not running.\n Start a new session first"
fi
```


Then, create a switcher.desktop file, and drag it to your panel. Clicking on it will switch. Note that I still use "User Switcher" widget to start a new session (but it does not do any switching).
```
switcher.desktop:

[Desktop Entry]
Comment[en_US]=
Comment=
Exec=/Path to your shell script above
GenericName[en_US]=
GenericName=
Icon=/User icon
MimeType=
Name[en_US]=Switch To OTHERUSER
Name=Switch To OTHERUSER
Path=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=

```

---

