---
title: "Flock problems- installs but wont open"
date: 2008-04-01
forum: General Help
---

### Post by lumberjack52 on 2008-04-01
I have always used flock so naturally i installed it into my gutsy when i got it about a month ago and it worked with a few bugs at first certain little things worked weird or not at all so i figured i would reinstall it. so i uninstalled it and reinstalled it and it downloads and installs fine no error messages but then i go to run it and nothing happens no error message or anything it just wont run. i use dansguardian with no gui and as well i use net responsibility  so i am wondering if dansguardian is blocking the program from opening but i am unsure. and i dont know the terminal code to try and run/ edit/ fix flock. so if it is a dansguardian problem what/ where would i find the problem and how would i fix it? firefox works perfect and so does opera so im not sure why it would not work. please help:(:confused:

---

### Post by Fixman on 2008-04-02
Linux has a command called "flock", but that has nohting to do with the browser. If you want to install the flock browser, go [here]("http://fileforum.betanews.com/detail/Flock_for_Linux/1129917212/3").

---

### Post by #Reistlehr- on 2008-04-02
You probably need to do
```
sudo apt-get install libstdc++5
```

if you follow the directions everyone says, flock extracted to /opt/flock

so ./opt/flock/flock or wherever you extracted it from.

---

### Post by lumberjack52 on 2008-04-02
i have the +++5 thing and there are no errors with it so im still confused. is there a way to force open flock or edit dansguardian to allow it without a gui i cant remember the terminal code to open and edit dans guardian

---

### Post by lumberjack52 on 2008-04-03
aslo i have tried to force it open with the termianl herese what came up
jake@jakes-laptop:~$ flock
flock (util-linux-ng 2.13)
Usage: flock [-sxun][-w #] fd#
       flock [-sxon][-w #] file [-c] command...
  -s  --shared     Get a shared lock
  -x  --exclusive  Get an exclusive lock
  -u  --unlock     Remove a lock
  -n  --nonblock   Fail rather than wait
  -w  --timeout    Wait for a limited amount of time
  -o  --close      Close file descriptor before running command
  -c  --command    Run a single command string through the shell
  -h  --help       Display this text
  -V  --version    Display version

that doesnt even look like anything i cant make heads or tails of this please help

---

### Post by lumberjack52 on 2008-04-03
(04:36:51 PM) Jake: jake@jakes-laptop:~$ sudo apt-get install flock-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flock-browser

(04:37:12 PM) Jake: jake@jakes-laptop:~$ sudo apt-get install flock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flock is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flock has no installation candidate


UGG

---

### Post by #Reistlehr- on 2008-04-03
no no no..

ok, open up a terminal. Go to the folder you extracted it to.


if you extracted to /opt/flock
Example:
cd /opt/flock

Then, do, ./flock
in the terminal and copy and paste the output. 

if you wish, you can always put the executable into /usr/bin, by using the following:

```

sudo /usr/bin/flock /usr/bin/f-lock
sudo ln -s /opt/flock/flock /usr/bin

```

This will rename the f-lock (file lock) command, with flock, the social web browser.

Also, if i remmeber right, you might have to install a package that is like ia32-sound or something

i dont have linux infront of me, but if you can, go to a terminal and type:

```

sudo apt-get install ia32- HIT TAB TWICE

```

after typing the ia32- hit tab twice, this will query the available packages. Install the packages it lists, or copy the output so i cna help you out a little more.

---

