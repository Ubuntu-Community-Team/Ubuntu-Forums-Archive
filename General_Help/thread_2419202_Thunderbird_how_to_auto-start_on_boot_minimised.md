---
title: "Thunderbird how to auto-start on boot minimised?"
date: 2019-05-17
forum: General Help
---

### Post by jebi on 2019-05-17
hi,

using 18.04.

i am trying to get thunderbird to autostart BUT minimised on boot.

i tried the startup app, then adding it but it always starts up the window.

i tried changing to thunderbird --headless

that i thought worked as it started but when you click on the icon it says that the app is already running and to close it before starting it up again.

i cant seem to find out how to do it is there a command thunderbird --something?

if not how do you do it?

edit a conf file?

if you know please a simple step by step idiots guide would be appreciated.

thx

---

### Post by Xian on 2019-05-18
One method is to install the firetray plugin : [https://addons.thunderbird.net/en-US/thunderbird/addon/firetray/](https://addons.thunderbird.net/en-US/thunderbird/addon/firetray/)

But first verify that you have added Thunderbird to the list of Startup Applications in System Preferences. 

After restarting Thunderbird GOTO:

Tools -> Add-ons -> FireTray - Preferences and check Start program minimized.

---

### Post by TheFu on 2019-05-19
The prior post sounds easier, if you trust the addon author. I have no opinion.

A window manager should be able to "iconize" any window.  [https://askubuntu.com/questions/703628/how-to-close-minimize-and-maximize-a-specified-window-from-terminal](https://askubuntu.com/questions/703628/how-to-close-minimize-and-maximize-a-specified-window-from-terminal)

And just to be clear for lurkers. None of this is possible at boot.  No GUI application can be controlled at boot.  There is a sequence of events that must happen before **any** GUI program can be run. 

First, the system has to be setup to start a GUI - in the systemd terminology, this is the "graphical.target"

Second, automatic login for some userid has to be setup.  There are security implications in doing this.

Third, the WM session has to startup. This is normally an X-Session, but if Wayland is used, it might be something different. IDK.

Forth, the WM or DE has to support an autorun or autostart configuration. I think they all do, but I don't know. There are lots of WMs (50+) that I've never touched.

Fifth, the correct application has to be configured to be run, under the session, with the desired options.  Options for any program should be documented in the manpage for that program. Programs with huge, complex, GUIs tend to have extremely poor documentation. Thunderbird is a perfect example of this terrible documentation.  Firefox is another. Chrome and Chromium are also in that group.  GUI programmers think that F1 should be sufficient. Getting help when there isn't any internet won't work in thunderbird - they try to open a webpage.

All the options for well-written X applications are documented here: [https://www.x.org/releases/X11R6.7.0/doc/X.7.html](https://www.x.org/releases/X11R6.7.0/doc/X.7.html)
Well-written X-applications running on WMs that follow standards, like openbox, should support the -iconic CLI option.  Alas, thunderbird does not. I tested it.  It worked with a number of other x-apps, but not thunderbird. Perhaps the mozilla cross-platform code team decided that supporting non-X-Windows platforms with native capabilities is too hard.

So ... that link near the top has an xdotool method.  A little scripting might be needed to get the windowID.  I've done this to launch chromium-browser go to full-screen mode for years. This sends the "Chomium" Window the F11 key:
```
$ xdotool search --sync --onlyvisible --class "Chromium" windowactivate key F11
``` 
If you did something like that after launching thunderbird with a 1, 2, or 3 second delay (whatever it requires),  it should work. Just need to find the x-event to send.  

A different WM might provide control over this more easily.  I know fvwm does, but it isn't everyone's taste.

---

### Post by pqwoerituytrueiwoq on 2019-05-19
To my knowledge there is no clean way to do this anymore, i used to have it setup like that (start minimized and say in the tray), but with firetray, minimize to tray, and minimize to tray revived no longer being supported by recent versions of Thunderbird
the most you can do is use xdotool to minimize it automatically after it opens, but it still uses space in the task list and if you close it it will not minimize like you could have happen with those addons
at this time what i have resorted to is having my raspberry pi blink a LED when i have email
here is the script i made to blink the led when i have mail
```
#!/usr/bin/python
import RPi.GPIO as GPIO, feedparser
from time import sleep
from thread import start_new_thread
from subprocess import call

# recommend file permission being root only access since the password are in plain text here
ACCOUNTS = [["googleUserName1", "googlePassword1"],
    ["googleUserName2","googlePassword2"],
    ["googleUserName3","googlePassword3"],
    ["googleUserName4","googlePassword4]]

GPIO.setmode(GPIO.BOARD)
pin = 37
GPIO.setup(pin, GPIO.OUT)
def blink_LED():
    while True:
        if found:
            GPIO.output(pin, not GPIO.input(pin))
        else:
            GPIO.output(pin, 0)
        #print found, GPIO.input(pin)
        sleep(1)
ACT_LEN = len(ACCOUNTS)
found = False
start_new_thread(blink_LED,())
while True:
    try:
        if int(call('ping -c1 -w1 -W1 10.0.0.50 > /dev/null',shell=True)) == 1:
            found = False # do not bother checking if the main computer is not on, meaning i am not around to see it blink
        else:
            test = False
            for x in range(0,ACT_LEN):
                #print "checking", ACCOUNTS[x][0]
                cur_mails = feedparser.parse("https://" + ACCOUNTS[x][0] + ":" + ACCOUNTS[x][1] +"@mail.google.com/gmail/feed/atom")
                total=int(cur_mails["feed"]["fullcount"])
                if total > 0: # check if unread cound is greater than 0
                    test = True
                    break # found a unread message no nead to check remaining accounts
            found = test
            #print "found",test
        if found:
            sleep(30)
        else:
            sleep(60)
    except Exception,e: # Probally a network conection error
        print e
        sleep(60)
```

---

### Post by TheFu on 2019-05-19
Life was so much easier when xbiff worked.
> xbiff is a small utility for the X Window System that shows a mailbox with its flag raised whenever the user has new e-mail.  It is only a little icon that had 2 settings - no mail (white, flag down) and mail received (black, flag up).  If you pull all email local and use the mbox format, it will probably still work.  It is loaded on my systems already. I didn't specifically load it, so that's good.  Just tested it with thunderbird. I only have imap email accounts and it didn't work. Bummer.

Hummmmm, perhaps ... 

[https://www.nongnu.org/imapbiff/](https://www.nongnu.org/imapbiff/)   it isn't in the repos I have setup. Hummm.  It is perl and Tk.  I like perl. Not a big fan of Tk, but that is how we did GUI stuff in them-thar-olden-days.  Looks like manual dependency solutions are needed.  If there is interest, I might figure it out, otherwise, not really that interested myself.

---

### Post by Xian on 2019-05-19
A version of FireTray that works Thunderbird +60 versions can be found here:

[https://github.com/Ximi1970/FireTray/releases/tag/v0.6.2](https://github.com/Ximi1970/FireTray/releases/tag/v0.6.2)

Right-click on the tray icon -> Preferences -> Windows -> Choose Start Application Hidden To Tray
Close Thunderbird. Log Out/In. Restart Thunderbird.

This is tested to work on Ubuntu Budgie 19.04. 

You may need to install a Gnome extension to create a System Tray in Gnome 3.26+.

---

### Post by jeftobias on 2019-07-02
> **Xian said:**
> A version of FireTray that works Thunderbird +60 versions can be found here:

[https://github.com/Ximi1970/FireTray/releases/tag/v0.6.2](https://github.com/Ximi1970/FireTray/releases/tag/v0.6.2)

Right-click on the tray icon -> Preferences -> Windows -> Choose Start Application Hidden To Tray
Close Thunderbird. Log Out/In. Restart Thunderbird.

This is tested to work on Ubuntu Budgie 19.04. 

You may need to install a Gnome extension to create a System Tray in Gnome 3.26+.

You are my friggin' hero. Been looking for something like this ever since they discontinued firetray some time back. *Thank You!*

---

