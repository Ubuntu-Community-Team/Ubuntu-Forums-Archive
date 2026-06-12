---
title: "Display message prior to logon"
date: 2014-03-22
forum: General Help
---

### Post by RWMills on 2014-03-22
On my previous OS (WinXP) I used the  LegalNoticeCaption and LegalNoticeText registry entries to display a  message which had to be acknowledged before the login screen was  displayed.

After  some experimenting I have come up with the following script (I haven't  tried it with the shutdown command enabled but from what I've read it  should work OK):

```
#!/bin/sh
FILE=`dirname $0`/LegalNotice # place text to be displayed in this file.
zenity --text-info \
  --title="Legal Notice" \
  --width=550 \
  --height=500 \
  --filename=$FILE \
  --checkbox="I have read and accept the legal notice."
response=$?
if ((response != 0)); then
  # shutdown the system.
  echo "shutting down..."
  # remove the following # when testing completed.
  #/sbin/shutdown now -P
fi


```

From  my searches using the LBSE Google Custom Search Engine (lovely tool  that, should have a sticky entry in this forum) it looks as if I need to  call it from /etc/rc.local so that it runs BEFORE the GUI (and user  logon prompt) is loaded.

Is this correct or will I end up 'bricking' my system?

                                               
_________________
Linux Mint 16 "Petra" Cinnamon (32-bit) Edition
HP Compaq dc 7600 (Dual Pentium D 3.4GHz)

---

### Post by ian-weisser on 2014-03-22
You won't brick your system...but it won't work.
Everything between login and logout is drawn by the windowing system, called X.
Zenity uses X to create the windows.
*Everything* in the GUI uses X.

Except the login screen.

The login prompt application (lightdm, or sometimes kdm or gdm) directly controls the screen. That's not lightdm using the X toolkit to draw stuff on the screen using X. Lightdm does it directly. There is no X session to start creating a window environment until lightdm gets a valid login and then starts X. Logout is the reverse - stopping X at logout automatically restarts lightdm...which is why when X crashes or logs out you return to the login prompt.

Lightdm does not have any option to add an acknowledgement window. I suppose you could patch the lightdm source code and compile your own version if you really wanted to. But easier alternatives may be available.

You could easily use Zenity *after* login. Then zenity will work great, though you will need to do a bit of script-fu to identify the DISPLAY environment variable that Zenity should be showing to (linux assumes a multi-user environment).

I won't bring up the "you-should-disable-their-account-if-you-dont-trust-them" argument. You will hear it enough from others, and it's not relevant to your technical question.

Is there some reason it *needs* to be before login? Can it be after login? Can it be after login but before making the desktop usable?
Both Upstart and Systemd make changing the post-login service start order very easy.

---

### Post by RWMills on 2014-03-24
Ian,

Thanks for the info.

In answer to your question, you can't display the following to a user AFTER they have logged onto your system. The legal bods don't like that.

*** Access to this system is restricted to authorised users only. ***

By acknowledging this notice and then logging on to this computer,
you agree to abide by the computer usage rules and regulations of
<company name goes here> and The Computer Misuse Act 1990.

** The Computer Misuse Act 1990 **

<description removed for brevity>

In my searches I did find a document that said if you entered some text into the file /etc/issue it would be displayed before the login: prompt was displayed.

I found 2 problems when I tried this.
1) If the text and login: prompt was displayed it was never seen because the desktop wallpaper and GUI Login dialog appeard too soon.
2) When checking /etc/issue after I had logged back in I found it had returned to its original pre edit state. It is probable that my text had been removed during the shutdown or startup phases.

regards,
Robert

---

### Post by ian-weisser on 2014-03-24
Well, I suppose you could use change Plymouth's pretty login screen to show the warning instead, but there won't be an "OK" box to click.

Perhaps the lawers would approve a minor change to "By logging on to this computer, you agree to" ?

If I recall correctly, on earlier versions of Windows you couldn't change the login screen...but could throw a warning window fairly easily. Ubuntu is currently the opposite. As Mir replaces X in Ubuntu, that may change.

Another recent thread on the same topic, with a few ideas: [http://ubuntuforums.org/showthread.php?t=2186061](http://ubuntuforums.org/showthread.php?t=2186061)

---

### Post by pqwoerituytrueiwoq on 2014-03-24
add this to you lightdm.conf file
[FONT=courier new]session-setup-script=sh -c 'DISPLAY=":0.0" zenity --info --text "By pressing OK, you agree that Cats Rule and Dogs Drool"'
[[IMG]http://www.zimagez.com/miniature/screenshot-03092014-092722pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-03092014-092722pm.php")
[/FONT]
[FONT=courier new]/etc/lightdm/lightdm.conf

/etc/lightdm/lightdm.conf.d/$something.conf[/FONT] (as of 14.04)
you can use this for a separate script
[FONT=courier new]session-setup-script=/path/to/script[/FONT]

just restart lightdm instead of rebooting
[FONT=courier new]service lightdm restart[/FONT]
i think if this script has a error it will send you to the login screen
you may have a issue with restarting the service because when the service is stop the restart process is owned by the stopped process

---

### Post by RWMills on 2014-03-24
The only file in /etc/lightdm/lightdm.conf.d/ is 10-ubuntu.conf which contains:

    [SeatDefaults]
    user-session=ubuntu

so I appended the following line:

    session-setup-script=/usr/local/bin/LegalNotice.sh

and placed the script and the message text file in /usr/local/bin/ ensuring the script was executable. root is the owner of both files, would that be correct?

The script contained:

  #!/bin/sh
  # ------------------------------------------------------------------------------
  # Display a legal notice and request acceptance of it.
  # Powerdown the system if it is rejected.
  # ------------------------------------------------------------------------------
  FILE=`dirname $0`/LegalNotice
  zenity --text-info \
    --title="Legal Notice" \
    --width=550 \
    --height=500 \
    --filename=$FILE \
    --checkbox="I have read and accept the legal notice."
  response=$?
  if ((response != 0)); then
    # shutdown the system.
    echo "shutting down..."
    #/sbin/shutdown now -P
  fi

Rebooted but nothing different happened :(

Commented my session-setup-script line and added the one suggested by [                                                      ]("http://ubuntuforums.org/member.php?u=865458") [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458"):

   session-setup-script=sh -c 'DISPLAY=":0.0" zenity --info --text "By pressing OK, you agree that Cats Rule and Dogs Drool"'

Rebooted but still nothing different happened :( :(

Any suggestions?

---

### Post by ian-weisser on 2014-03-24
Well, it's good to learn something new!

Thanks, pqwoerituytrueiwoq

---

### Post by pqwoerituytrueiwoq on 2014-03-24
works fine on my xubuntu 14.04 virtualbox install
```
chad@chad-VirtualBox:~$ cat /etc/lightdm/lightdm.conf.d/10-xubuntu.conf 
[SeatDefaults]
user-session=xubuntu
session-setup-script=sh -c 'DISPLAY=":0.0" zenity --info --text "By pressing OK, you agree that Cats Rule and Dogs Drool"'
chad@chad-VirtualBox:~$ echo $DISPLAY
:0.0
```
the display part is important, that tells it what screen to put the message on

---

### Post by RWMills on 2014-03-25
I've been told that Mint 16 does not use lightdm but MDM (a fork of GDM 2) which is why nothing worked. Looks as if I need to read up on MDM.

#ian-weisser & #pqwoerituytrueiwoq
Thanks for your help guys.

---

