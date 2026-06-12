---
title: "Cups not working ?"
date: 2024-06-27
forum: General Help
---

### Post by grey1beard on 2024-06-27
Ubuntu 22.04 working well with Epson2640 since 22.04 installed.
Suddenly no printer  - " CUPS Service Stopped" (Printing troubleshooter)

Tried to start - see attachment.
Greatly appreciate guidance.
John

---

### Post by currentshaft on 2024-06-27
Try running cupsd directly without systemd:

sudo cupsd -l -f

Do any errors appear in console?

---

### Post by grey1beard on 2024-06-27
Tried **sudo cupsd -l -f** and the terminal screen said 'Terminated' !
Frightening !!
John

---

### Post by #&amp;thj^% on 2024-06-27
Are the confg's ok?
```
sudo cupsd -t
"/etc/cups/cups-files.conf" is OK.
"/etc/cups/cupsd.conf" is OK.

```
I get the same you get with:
```
sudo cupsd -l -f
Terminated

```
And one more please:
```
cat /var/log/cups/error_log

```

---

### Post by currentshaft on 2024-06-27
> **grey1beard said:**
> Tried **sudo cupsd -l -f** and the terminal screen said 'Terminated' !
Frightening !!
John

Run the following command right after sudo cupsd fails:

echo $?

Is cupsd or another service already running on port 631?

sudo lsof -Pni

---

### Post by grey1beard on 2024-06-27
Terminal produces - 
> sudo cupsd -t
Duplicate listen address "/run/cups/cups.sock" ignored.
Unknown directive JobPrivateAccess on line 125 of /etc/cups/cupsd.conf.
Unknown directive JobPrivateValues on line 126 of /etc/cups/cupsd.conf.
Unknown directive SubscriptionPrivateAccess on line 127 of /etc/cups/cupsd.conf.
Unknown directive SubscriptionPrivateValues on line 128 of /etc/cups/cupsd.conf.
Printer drivers are deprecated and will stop working in a future version of CUPS. See [https://github.com/OpenPrinting/cups/issues/103](https://github.com/OpenPrinting/cups/issues/103)
"/etc/cups/cups-files.conf" is OK.
"/etc/cups/cupsd.conf" is OK.

and then - 
> 
systemctl status cups.service
&#9675; cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: en>
     Active: inactive (dead) (Result: protocol) since Thu 2024-06-27 13:04:26 CDT>
TriggeredBy: × cups.socket
             × cups.path
       Docs: man:cupsd(8)
    Process: 4396 ExecStart=/usr/sbin/cupsd -l (code=killed, signal=TERM)
   Main PID: 4396 (code=killed, signal=TERM)
        CPU: 10ms

Jun 27 13:04:26 john-HP-ProDesk-600-G1-SFF systemd[1]: cups.service: Scheduled re>
Jun 27 13:04:26 john-HP-ProDesk-600-G1-SFF systemd[1]: Stopped CUPS Scheduler.
Jun 27 13:04:26 john-HP-ProDesk-600-G1-SFF systemd[1]: Dependency failed for CUPS>
Jun 27 13:04:26 john-HP-ProDesk-600-G1-SFF systemd[1]: cups.service: Job cups.ser>

John

---

### Post by deadflowr on 2024-06-28
There's more missing info from when you run the status command.
press right arrow to see what it says.
You might also look at what that second command it offered says
```
journalctl -xeu cups.service
```

---

### Post by grey1beard on 2024-06-28
> There's more missing info from when you run the status command.
**press right arrow **to see what it says.

If I press on the right arrow, nothing happens.

The code that I showed, repeated ~14 times [I lost count, but *lines 1-14/14 (END)* seems significant] with long gaps between the repeats.

Then  this followed numerous times -

```
                   SUMMARY OF LESS COMMANDS

      Commands marked with * may be preceded by a number, N.
      Notes in parentheses indicate the behavior if N is given.
      A key preceded by a caret indicates the Ctrl key; thus ^K is ctrl-K.

  h  H                 Display this help.
  q  :q  Q  :Q  ZZ     Exit.
 ---------------------------------------------------------------------------

                           MOVING

  e  ^E  j  ^N  CR  *  Forward  one line   (or N lines).
  y  ^Y  k  ^K  ^P  *  Backward one line   (or N lines).
  f  ^F  ^V  SPACE  *  Forward  one window (or N lines).
  b  ^B  ESC-v      *  Backward one window (or N lines).
  z                 *  Forward  one window (and set window to N).
  w                 *  Backward one window (and set window to N).
  ESC-SPACE         *  Forward  one window, but don't stop at end-of-file.
  d  ^D             *  Forward  one half-window (and set half-window to N).
  u  ^U             *  Backward one half-window (and set half-window to N).
  ESC-)  RightArrow *  Right one half screen width (or N positions).
HELP -- Press RETURN for more, or q when done
```

I note that the > symbol is not mentioned, and I'm afraid it is meaningless to me, but I hope it helps.
Regards
John

---

### Post by deadflowr on 2024-06-28
> Jun 27 13:04:26 john-HP-ProDesk-600-G1-SFF systemd[1]: Dependency failed for CUPS>
The arrow at the end of this line means there is more than what your current terminal can show.
You need to press the arrow key to scroll it over to see what it says.
You need to press it before you exit the pager mode.

Or...
You can run it in no-pager mode
```
systemctl --no-pager --full status cups.service
```
this will make the output wrap to the next line.

Of course this could just be a waste and that little tidbit of info that isn't showing could be useless.
But at least you might know if it is or not.


You'd probably have more useful info from the journalctl command anyway.

---

### Post by grey1beard on 2024-06-28
Tried the last suggestion, and got the attached window in Terminal. My untutored reading is that it tried to start cups, but a missing dependency prevented it.
I'm about to use apt-get update and upgrade, then do a cold boot, to see if that makes any difference.
John

---

### Post by grey1beard on 2024-06-28
Yes, that's done it.
apt-get upgrade showed a lot of cups entries, so I tried printing, and we're off to the races.
Thanks for your help and support. More learned !
Regards
John

---

