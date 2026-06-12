---
title: "What command line to remove this app"
date: 2023-11-02
forum: General Help
---

### Post by paulshaffer4 on 2023-11-02
What command line to remove this app - Ubuntu software is unable to

---

### Post by jimmyrus on 2023-11-02
> **paulshaffer4 said:**
> What command line to remove this app - Ubuntu software is unable to
Did you run "sudo apt-get clean" to tidy things up? Or "sudo apt-get remove packagename --fix-broken"? 

Lots of information on the man pages for apt-get and tons you can find by doing a quick search if you did one. After so
long using ubuntu don't you know about apt-get and man pages?

---

### Post by #&amp;thj^% on 2023-11-02
I don't use Software GUI's, so is it a snap or a .deb
to see:
```
snap list
```
or for apt:
```
apt policy dclock
```
would need to see both of those returns

---

### Post by MAFoElffen on 2023-11-02
+1 -- 

I use dclock on my PC in the living room, as "my clock" there. That sounds a bit pathetic, but it works and doesn't cost anything. I have it installed on mine from apt.

---

### Post by paulshaffer4 on 2023-11-03
```

$ snap list
Name                       Version                     Rev    Tracking         Publisher      Notes
bare                       1.0                         5      latest/stable    canonical&#10003;     base
brave                      1.60.110                    299    latest/stable    brave&#10003;         -
chromium                   118.0.5993.117              2673   latest/stable    canonical&#10003;     -
core18                     20230901                    2796   latest/stable    canonical&#10003;     base
core20                     20230801                    2015   latest/stable    canonical&#10003;     base
core22                     20230801                    864    latest/stable    canonical&#10003;     base
cups                       2.4.6-4                     980    latest/stable    openprinting&#10003;  -
firefox                    119.0-2                     3290   latest/stable/&#8230;  mozilla&#10003;       -
gnome-3-28-1804            3.28.0-19-g98f9e67.98f9e67  198    latest/stable    canonical&#10003;     -
gnome-3-38-2004            0+git.efb213a               143    latest/stable/&#8230;  canonical&#10003;     -
gnome-42-2204              0+git.ff35a85               141    latest/stable    canonical&#10003;     -
gtk-common-themes          0.1-81-g442e511             1535   latest/stable/&#8230;  canonical&#10003;     -
snap-store                 41.3-71-g709398e            959    latest/stable/&#8230;  canonical&#10003;     -
snapd                      2.60.4                      20290  latest/stable    canonical&#10003;     snapd
snapd-desktop-integration  0.9                         83     latest/stable/&#8230;  canonical&#10003;     -
supertuxkart               1.3                         645    latest/stable    lucyllewy&#10026;     -
WARNING: There is 1 new warning. See 'snap warnings'.

```

---

### Post by paulshaffer4 on 2023-11-03
> 
$ apt policy dclock
dclock:
  Installed: 2.2.2-13
  Candidate: 2.2.2-13
  Version table:
 *** 2.2.2-13 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages
        100 /var/lib/dpkg/status



It won't let me post as my message is too short, so I'm typing this sentence.

---

### Post by paulshaffer4 on 2023-11-03
> **MAFoElffen said:**
> +1 -- 

I use dclock on my PC in the living room, as "my clock" there. That sounds a bit pathetic, but it works and doesn't cost anything. I have it installed on mine from apt.

It doesn't work well for me - sorry.  So I installed Gnome Clocks which actually works.

---

### Post by paulshaffer4 on 2023-11-03
If someone could simply give me the terminal command to remove it/purge it, I'd be much appreciative.

---

### Post by deadflowr on 2023-11-03
Run
```
sudo apt update
sudo apt upgrade
```
The error says you have unmet dependencies.
So post the outputs from the commands.
It should tell you and us what dependency issues are happening, if any.

You can usually fix broken packages with
```
sudo apt install -f
```
but it's not always 100% effective.

If no errors show you can just run
```
sudo apt purge dclock
```



If you are interested in learning more about the apt package manager, you have manuals installed on your system.
Use the man commands to see them.
```
man apt
```

---

### Post by MAFoElffen on 2023-11-03
Also, you have Snap warnings... You can see what is happening there by doing
```

sudo snap warnings

```

---

### Post by jimmyrus on 2023-11-03
> **paulshaffer4 said:**
> If someone could simply give me the terminal command to remove it/purge it, I'd be much appreciative.
You got it in the first reply did you not get it? You got two commands to run did you make the attempt to, like, type them in and press enter?

---

### Post by MAFoElffen on 2023-11-03
Are you 'stuck' not understanding what people have said? Do you need instructions that night be more understandable?

To reiterate, open a terminal, type this, then press the <Enter> key to execute the command... You will then be prompted to enter your password to verify it.
```

sudo apt remove --purge -y dclock

```
If after doing that, if there is an error, please post exactly what that error was, posted within "CODE tags".

If successful, post that and mark your thread as "Solved" by using the "Thread Tools" link in the upper left of this page...

Do you require more information to do that?

---

### Post by #&amp;thj^% on 2023-11-03
^^^^^+1
it did not show in snap list, so this is it "apt --purge"
And to be clear see post #12

---

### Post by jimmyrus on 2023-11-04
> **MAFoElffen said:**
> Are you 'stuck' not understanding what people have said? Do you need instructions that night be more understandable?

To reiterate, open a terminal, type this, then press the <Enter> key to execute the command... You will then be prompted to enter your password to verify it.
```

sudo apt remove --purge -y dclock

```
If after doing that, if there is an error, please post exactly what that error was, posted within "CODE tags".

If successful, post that and mark your thread as "Solved" by using the "Thread Tools" link in the upper left of this page...

Do you require more information to do that?
+1 to all this. Especially since the op's been doing stuff for at least 5 yrs now and keeps creating different users. Theres a c***ton of stuff they
could look up pretty easy about apt to remove things and fix dbs. Guess they think its easier to have us look stuff up

---

### Post by paulshaffer4 on 2023-11-05
The results of the 2 command lines are:

> **1fallen said:**
> I don't use Software GUI's, so is it a snap or a .deb
to see:
```
snap list
```
or for apt:
```
apt policy dclock
```
would need to see both of those returns

```

$ snap list
Name                       Version                     Rev    Tracking         Publisher      Notes
bare                       1.0                         5      latest/stable    canonical&#10003;     base
brave                      1.60.110                    299    latest/stable    brave&#10003;         -
chromium                   119.0.6045.105              2680   latest/stable    canonical&#10003;     -
core18                     20230901                    2796   latest/stable    canonical&#10003;     base
core20                     20230801                    2015   latest/stable    canonical&#10003;     base
core22                     20230801                    864    latest/stable    canonical&#10003;     base
cups                       2.4.6-4                     980    latest/stable    openprinting&#10003;  -
firefox                    119.0-2                     3290   latest/stable/&#8230;  mozilla&#10003;       -
gnome-3-28-1804            3.28.0-19-g98f9e67.98f9e67  198    latest/stable    canonical&#10003;     -
gnome-3-38-2004            0+git.efb213a               143    latest/stable/&#8230;  canonical&#10003;     -
gnome-42-2204              0+git.ff35a85               141    latest/stable    canonical&#10003;     -
gtk-common-themes          0.1-81-g442e511             1535   latest/stable/&#8230;  canonical&#10003;     -
snap-store                 41.3-71-g709398e            959    latest/stable/&#8230;  canonical&#10003;     -
snapd                      2.60.4                      20290  latest/stable    canonical&#10003;     snapd
snapd-desktop-integration  0.9                         83     latest/stable/&#8230;  canonical&#10003;     -
supertuxkart               1.3                         645    latest/stable    lucyllewy&#10026;     -
WARNING: There is 1 new warning. See 'snap warnings'.
michael@michael-HP-EliteDesk-800-G3-SFF:~$ apt policy dclock
dclock:
  Installed: 2.2.2-13
  Candidate: 2.2.2-13
  Version table:
 *** 2.2.2-13 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by coffeecat on 2023-11-05
The OP has left the building. Thanks to all who offered help. Thread closed.

---

