---
title: "login problem"
date: 2007-07-27
forum: General Help
---

### Post by alyak on 2007-07-27
After trying to login when booting up the computer, I get the error message:
"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

What possibly caused this? What needs to be done so I can log in again?

---

### Post by nichipet on 2007-07-27
Can you post the output of this command:

```
ls -l ~/.dmrc
```

---

### Post by alyak on 2007-07-28
The output of the command "ls -1 ~/.dmrc" is

"-rw------- 1 daniel sealy 26 2007-06-22 11:03 /home/sealy/.dmrc"

---

### Post by strabes on 2007-07-28
```
chown -R username:username ~ && chmod 644 -R ~
```

---

### Post by alyak on 2007-07-28
typed in: "chown -R sealy:sealy ~ && chmod 644 -R ~"
(sealy is username)

result: operation not permitted

---

### Post by Koybe on 2007-07-28
I'm not sure 644 -R is a good idea on your home directory. You won't be able to access any directory after.

Just make sure you got rights on your home.
```

sudo chmod 644 .dmrc
sudo chown username. .dmrc
sudo chmod 755 /home/username
sudo chown username. /home/username

```

---

### Post by alyak on 2007-07-28
The earlier stated error message I got when trying to log in no longer shows up, but I get an error message that says:
"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."

When viewing details:
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sealy"
Beginning session setup...
0700 on private per-user gnome configuration directory `/home/sealy/.gnome2_private/` : Operation not permitted

---

### Post by Koybe on 2007-07-28
You seemed to have pretty messed up your profile.

If I were you I would copy my own data in a temporary folder (_**not in /tmp****!!!**_ /home/temp for example). Then I would completely delete my homedir and remake it.
[U][B]
So before doing what's down here, save all your data you have in /home/sealy!!!!!![/B][/U]

boot recovery mode

```
sudo rm -r /home/sealy
sudo mkdir /home/sealy
sudo cp -r /etc/skel /home/sealy
sudo chown -R sealy. /home/sealy
sudo chmod 755 /home/sealy
sudo init 2

```

---

