---
title: "Firewall fails to load &gt; G/UFW &gt;"
date: 2022-06-19
forum: General Help
---

### Post by GeordieJedi on 2022-06-19
Hi there guys, I was hoping that you could help with a quirky issue that I've
just started experiencing

**Issue:**
UFW / GUFW is failing to load.

This has just started today (19/06/22)

I have G/UFW set to auto load at each boot
When I boot the computer, I normally get a dialogue box asking me for me PW.

However, this is STILL happening (I see the dialogue box) I enter my PW
(Correctly !) the dialogue box dissappears, then......nothing further happens

I've also checked the running processes (with HTOP in Guake) and there is no
sign of G/UFW running at all


**Troubleshooting:**
1. Tried using different DE (Desktop Environments) = MATE & KDE Plasma =
G/UFW fails to load

2. Completley removed both UFW and GUFW via Synaptic
Then re-installed both UFW & GUFW via synaptic = Same. G/UFW fails to load.

3. Multiple reboots = Same. G/UFW fails to load.


**4. Questions:**
4.1. What could be causing this behavior ?
4.2. What can I do to resolve this issue please ?


**Useful information:**
OS: KUbuntu 20.04 (LTS)
DE: KDE Plasma - version 5.18.8
Kernel version: 5.14.0-1042-oem

CPU: 4 x Intel Core 2 Quad core Q8200 @2.33 Ghz
RAM: 8 GB


TIA for any help or advice

---

### Post by The Cog on 2022-06-19
gufw is just a GUI utility for configuring the ufw firewall rules. You should not expect to see this running unless you launch it in order to do some firewall rule configuration.

Similarly, ufw is also just a utility for configuring iptables (or nftables rules on Ubuntu 22.04, I gather) firewall rules. It just runs for a few milliseconds when you issue a ufw command on the command line, or if gufw calls it when you click OK to a rules change.

Similarly, both iptables and its successor, nftables are utilities for configuring firewalls in the Linux kernel. They too, only run for a few milliseconds when they are called to make a firewall change, by a direct command-line iptables/nftables command or called from ufw/gufw to make changes. 

The firewall rules are implemented in the kernel, and there is no active process you can check on to see if it's "running". The only thing you can do is ask iptables/nftables to tell you what the current rules are that the kernel is using. Don't trust ufw of gufw, they will just tell you what they are configured to tell iptables/nftables to do. To see what rules the kernel is currently using, use one of these two commands (or indeed use both to get the full picture):
```
sudo iptables-save   # this prints a full iptables config if there is any
sudo nft list ruleset
```

So strictly speaking, the firewall is never "running", it's just configured or not.
That said, is the problem just that gufw application doesn't auto-start, or the firewall rules don't get configured, or both, or something else I haven't understood from your post?

---

### Post by GeordieJedi on 2022-06-20
Hi - The Cog, thanks for coming back to me on this issue.

Thanks for the log location, thats a good shout.
I am aware that once you "set" your firewall rules they're supposed to be "fire and forget".

However I like to make sure that the firewall (and its processes are working properly all the  time).
As a result,  I set G/UFW to auto start at each boot.
So that I can make sure that the firewall is working properly.

I have done some further troubleshooting though:

5. (With my laptop) also running Ubuntu (18.04 LTS, this time)
and has GUFW set to auto start at each boot.

Interestingly I found the following -

5.1. (G/UFW is working) and the GUI app loads

When using HTOP I see the following app/prcocess when searching for GUFW:
```
python3 /usr/share/gufw/gufw.py (my username)
```


5.2. However when searching for either GUFW or UFW in HTOP on my desktop PC
(that has the issue), there are no instances of anything relating to either
GUFW or UFW in the process monitor.

5.3. When I reboot my desktop PC, I login and access my account and deskop.
However (after putting in the correct PW into the GUFW dialogue box)
The GUFW app does not load or appear on the desktop or taskbar

This leads me to believe that the G/UFW has not loaded and is not running.


6. I have had a cursory look at the update history on both machines
There doesnt appear to be any recent history of GUFW being updated.

However I have done a recent Kernel update (to my desktop PC)
(see version in my original post)
So this, may be the reason for the changes in the behaviour of G/UFW
(not running) anymore.

However thank you for responding to my inital request for help
It is appreciated.

---

### Post by The Cog on 2022-06-21
You're welcome.
Have you tried to launch gufw from the command prompt? It might print some error messages that could indicate what the problem is.

---

### Post by GeordieJedi on 2022-06-21
7. Yes, I ran the following command and got a honking great big error message / log:

Command:
```
sudo gufw
```


Result:
```
ls: cannot access '/usr/lib/python*/site-packages/gufw/gufw.py': No such file or directory
Traceback (most recent call last):
  File "/usr/share/gufw/gufw/gufw.py", line 30, in <module>
    gufw = Gufw(controler.get_frontend())
  File "/usr/share/gufw/gufw/gufw/view/gufw.py", line 80, in __init__
    self._set_initial_values()
  File "/usr/share/gufw/gufw/gufw/view/gufw.py", line 283, in _set_initial_values
    self.listening = ListeningReport(self)
  File "/usr/share/gufw/gufw/gufw/view/listening.py", line 35, in __init__
    self._show_report()
  File "/usr/share/gufw/gufw/gufw/view/listening.py", line 48, in _show_report
    self._view_report(report, self.previous_report)
  File "/usr/share/gufw/gufw/gufw/view/listening.py", line 83, in _view_report
    self.gufw.listening_model.set_value(iter_row, 1, int(line_split[1].strip())) # port
ValueError: invalid literal for int() with base 10: 'WARN:'
```

(To my untrained eye) - This appears like either -
7.1. The GUFW app doesnt exist
7.2. The GUFW app has been moved

either way, it's a bit more helpful

---

### Post by TheFu on 2022-06-21
What's the status for ufw after reboot?

```
$ sudo systemctl status ufw
 ufw.service - Uncomplicated firewall
   Loaded: loaded (/lib/systemd/system/ufw.service; enabled; vendor preset: enab
   Active: active (exited) since Sat 2022-06-18 20:33:26 EDT; 2 days ago

```

If is doesn't look like that, then it wasn't run at boot, which would be odd.  The DE shouldn't matter. ufw works regardless of the GUI. I haven't a clue about gufw. Looked at it once years ago.

```
sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

```
See the "active"?  That means it is on and working.

UFW is just a higher level tool to interact with iptables on releases before 22.04.  In 22.04, there may or may not be nftables rather than iptables. I vaguely remember seeing that ufw was compatible with both nftables and iptables.

ufw startup and enabling is handled with the systemctl command just like every other daemon on Ubuntu, Debian, Fedora, SuSE, and all systemd init distros. Nothing special.  There must be a thousand web articles about the top 8 command options we need to know.  start, stop, restart, status, enable, disable, mask, unmask.  Those are all I've every used.  Pick one to learn more.

---

