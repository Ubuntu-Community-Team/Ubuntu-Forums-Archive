---
title: "Urgent/important question"
date: 2008-02-23
forum: General Help
---

### Post by irishgoth8822 on 2008-02-23
Ok, I have asked this question, or some form of it, several times in several threads related to other things, and either havent gotten any responses or have only gotten one, and I really need more ideas as to how to fix this.

My computer runs dapper. It is a dell inspiron notebook E1405. I've had it for just over a year and a half or so.  I have gotten to the point where I am forced to do a fresh install about ever two to three days now, because the system starts lagging to the point where administrative apps wont open at all (presumably because the system can't get up the speed to give me the password prompt; sudo in terminal merely sends back the 'cannot look up gethostbyname' error) and all other applications open so slowly that the computer is hardly functional.

At first I thought perhaps it had something to do with the internet, and at the moment, the wireless I'm using is a very slow connection, but I don't know that that makes sense as to be the cause of the problem.  

I have also noticed that when it starts to get like this and I restart it, it slows or lags when it is, according to the boot screen 'loading system log' and then when the load bar is on my main screen after i've logged in my username and password, it lags in between each consecutive step, like 'window manager' 'nautilus' 'update notifier' etc.

The only piece of advice I've ever come across here is to run the 'free' code. Here is the result (and at the moment, the computer is starting to lag, and wont open admin apps, but hasnt quite pushed me to the reinstall point yet--that will probably be later today):

```
             total       used       free     shared    buffers     cached
Mem:       1026836     484212     542624          0      44340     211688
-/+ buffers/cache:     228184     798652
Swap:      3004112          0    3004112

```

So...basically...my question is...is there anything I can do?! Reinstalling my entire system one to two times a week just isnt practical. Is there a chance it could be my actual computer, like, the hardware? I can't see how it could be, esp since the computer is relatively new...but if it's a software problem I'm really at a loss. I've ordered the gutsy cd so that I can do a completely fresh install of that soon, but it will be quite a few weeks till that ships, and until then, this is getting ridiculous.

I really, really hope that somebody here can help me.

---

### Post by forestpixie on 2008-02-23
have you tried running top - you might get some idea what is causing the problem

---

### Post by irishgoth8822 on 2008-02-23
I have run top, and I dont see anything unusual...

---

### Post by dieselpower on 2008-02-23
Edit (sudo nano) the file /etc/hosts, and add your hostname in it like this. The hostname can be gotten form /etc/hostname.
```

127.0.0.1 localhost.localdomain localhost host_name

```

---

### Post by soldats on 2008-02-23
whatever app you run quicky hit ctrl+alt+f1 and you should be at a terminal which may shed light on what part of the apps are stalling or maybe something isnt loading right. that may tell you some info first. also if you get the gusty cd see if the problems persist.

---

### Post by irishgoth8822 on 2008-02-23
> **dieselpower said:**
> Edit (sudo nano) the file /etc/hosts, and add your hostname in it like this. The hostname can be gotten form /etc/hostname.
```

127.0.0.1 localhost.localdomain localhost host_name

```


i know how to get into sudo nano but ive never known what to do once im in. could you explain that a little more step by step? :)

---

### Post by rapiscan on 2008-02-23
try

```
sudo gedit
```

instead of 

```
sudo nano
```

This will open the file in the gedit text editor, which should be easier to use.

---

### Post by irishgoth8822 on 2008-02-23
apparently, i can't do either.

i tried various things:

```
meghan@meghan-laptop:~$ sudo gedit /etc/hosts
sudo: unable to lookup meghan-laptop via gethostbyname()
meghan@meghan-laptop:~$ sudo gedit
sudo: unable to lookup meghan-laptop via gethostbyname()
meghan@meghan-laptop:~$ sudo nano /etc/hosts
sudo: unable to lookup meghan-laptop via gethostbyname()
meghan@meghan-laptop:~$ sudo nano
sudo: unable to lookup meghan-laptop via gethostbyname()

```

---

### Post by seventhc on 2008-02-23
That doesn't look good...what happens with this command
```
cat /etc/hosts
```Does it give the expected output or do you get errors?

---

### Post by rapiscan on 2008-02-23
It looks like there are several potential causes for this, all of which are gone over in this thread:
[http://ubuntuforums.org/archive/index.php/t-78324.html](http://ubuntuforums.org/archive/index.php/t-78324.html)

Probably the most important thing to note is that if you reboot into recover mode, you'll have root access (so you don't have to worry about prepending 'sudo' to your commands).  But be careful with your commands when you're root, because you have access to modify/delete everything.

---

### Post by irishgoth8822 on 2008-02-23
> **seventhc said:**
> That doesn't look good...what happens with this command
```
cat /etc/hosts
```Does it give the expected output or do you get errors?



```
meghan@meghan-laptop:~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts

```

thats all thats there, but no errors.

---

### Post by seventhc on 2008-02-23
Have a look at the link that **rapiscan** posted, that looks like it might help.
my output looks like this
```

127.0.0.1       localhost
127.0.1.1       cipher

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by irishgoth8822 on 2008-02-23
I had actually come across that thread myself while googling the problems, but--hate to be so painfully uneducated about how to do basic stuff--when i get into ctrl+alt+f1 and i type 'gedit /etc/hosts' it tells me that it cant display it (which makes sense) so, if i cant use gedit while in recovery mode, what commands do i need to type to gain access to the etc/hosts file so i can add the lines i need?

once ive got the file, do i just add '127.0.0.1 localhost.localdomain localhostname'? or do i need to add anything else?


and incidentally, while this should fix my sudo problem, do you think it will help my overall lag problem at all?

---

### Post by seventhc on 2008-02-23
nano or vim should work.

I use vim
I'm not sure for nano but for vim you type an 'i' to go into insert mode, you can then add text to the file.
then once you are finished typing in you press the <Esc> key then type
** :wg**
(you type in the colon then the wq)
the 'w' is for write, the q is for quit.
Hope that helps
If your not how to use them, open vim or nano while still in you desktop to make sure you can use it. :)

they would open from the terminal
vim nameoffile
so to create a test file you can just type
vim test
press the i to enter insert mode
then start typing
press <Esc>
then
**:w **to write but not exit
**:wq** to write and exit vim

---

### Post by rapiscan on 2008-02-23
When you're in recovery mode, it's command line only.  You should use nano. 

So your command will look something like this:
```
nano /etc/hosts
```


You will be able to modify the file.  You should atleast have the line 
```

127.0.0.1       localhost

```
at the top of your file.  You can write this in manually using nano.  When using nano, it's similar to a regular text editor, you just can't use the mouse to move your cursor around.  You have to use the arrow keys to move your cursor around.

When you want to save, hit ctrl-O.  If you look at the bottom of the nano screen, you'll see a list of commands that you can use while editing like ctrl-X to exit and ctrl-O to write out (which is the same as saving).

---

### Post by lncoll on 2008-02-23
If you can't do with vim, ( firsts uses of vim are very hard ) try with nano /etc/hosts
write the first lines with 

```
127.0.0.1 localhost
127.0.1.1 yourhostname

```
then type [CTRL]o to write the file and [CTRL]x to quit
before reboot execute:
```
df -h
```
To test if your HD if toot full, that can be the reason of many lags.

---

### Post by Mustard on 2008-02-23
I wrote this litte 'How to' back when I was using Dapper Drake and helping on the forums.  It might be helpful...

**How to edit the /etc/hosts file (troubleshooting guide)**

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the **recovery mode** option from the **grub menu** at bootup.

When you get to a root prompt,
**1. Making a backup of misconfigured file**
If you really have no idea what you are doing then first make a backup of the file just in case you really muck things up.  A misconfigured file is at least a reference you can work from.
```
#make a backup
cp /etc/hosts /etc/hosts_backup
```

**2. Editing the misconfigured file**
Open up the /etc/hosts file with this command.
```

#this will open the hosts file in a command line text editor
nano /etc/hosts 
```

(To save files in in nano use ctrl + o and to exit from nano use ctrl + x)

The /etc/hosts file normally looks something like this...

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What you need to do is to edit the first line so that it contains a hostname for your computer.  Mine is called 'slave' as you can see above.  You can choose any name you like.  The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```

**Additional problems that may be present**
An additional issue you might need to look into in some cases, is whether a file exists in the /etc/ folder called 'hostname'.  For various reasons, usually related to user intervention, it will sometimes not exist at all, or exists but is a blank file.  Normally the /etc/hostname will look like this (using my own host file as an example)..

```
slave
```

If it is absent then you should create a file in /etc/ folder called *hostname* and edit it to include your chosen hostname.  You can create a new file by opening the nano text editor using the path and name of the file you wish to create.
```
nano /etc/hostname
```

**Command relating to the hostname (I've included this for informational purposes)**
An additional command you can look at with regards to hostnames is this command below.
```
hostname
#returns the current hostname
hostname <hostname>
#sets the hostname according to the value entered for <hostname>

```

---

### Post by irishgoth8822 on 2008-02-23
when i run it in recovery mode, it doesnt boot far enough for me to get the command line, and when i simply do ctrl+alt+f1, its telling me i dont have permissions to save the file after ive altered it...

---

### Post by seventhc on 2008-02-23
I'm not positive if this will work but try going to the file through nautilus.
```
gksu nautilus
```Once it opens click on '*File System*' then open the '*etc*' folder, scroll down  and look for the hosts file. Once you find it, try double clicking on it...hopefully it will open with gedit and you will be able to edit it.

---

### Post by irishgoth8822 on 2008-02-23
i went ahead and did a clean install, (although thank you for the gksu command, i had forgotten what it was but i used to have an app launcher on my taskbar for root file system for precisely that reason)

is there any way to prevent the problems from starting again? should i run and install all the upgrades available? as of right now the etc/hosts file looks exactly as it should, i dont understand when or how it lost most of its info last time.

---

### Post by seventhc on 2008-02-23
sudo for terminal stuff and
gksu/gksudo for gui apps
example
[I] sudo vim /etc/hosts
gksu gedit /etc/hosts[/I]
I'm not sure why yours got changed, so it's hard to say how to prevent it. I've never had a problem with mine.
Hopefully it won't change again. :)

I install all available updates, so I would say yes to installing them.

---

### Post by irishgoth8822 on 2008-02-23
both to bump this and to add this as an extra piece of info; i said before that i didnt see anything odd when i ran 'top' but it occured to me that i could be missing something since im not *that* familiar with my system.

these are the recurring processes, particularly the 'xorg' one, but i dont know if the time its been running and the amounts its using is normal or not. i just waited till i saw several programs appear in 'top' along with the xorg to get the information im posting below, just like a screenshot of the terminal.

```
 5727 meghan    15   0 39652  14m 9092 S  1.4  1.4   0:00.98 gnome-terminal
 4514 root      15   0  293m  30m 7020 S  0.9  3.1   1:03.33 Xorg
 5747 meghan    16   0  2200 1100  856 R  0.2  0.1   0:00.08 top

```

---

### Post by rapiscan on 2008-02-23
I don't see any problem with this output, I would recommend running top and pasting the full output if you do get slowdown again.

---

### Post by irishgoth8822 on 2008-02-26
i'm getting the slowdown again, after a brief four days of no trouble following a clean install.

here is the output of top:

```
top - 14:47:37 up 23 min,  2 users,  load average: 0.46, 0.26, 0.20
Tasks:  86 total,   1 running,  83 sleeping,   2 stopped,   0 zombie
Cpu(s): 52.7% us,  2.7% sy,  0.0% ni, 38.3% id,  5.0% wa,  0.7% hi,  0.7% si
Mem:   1026836k total,   372516k used,   654320k free,     7144k buffers
Swap:  3004112k total,        0k used,  3004112k free,   176952k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5545 meghan    15   0  189m  50m  21m S 40.0  5.0   0:25.00 firefox-bin
 4496 root      16   0  289m  26m 7640 S 13.0  2.6   0:57.56 Xorg
 5619 meghan    15   0 39748  14m 9084 S  1.3  1.4   0:00.57 gnome-terminal
 3337 root      13  -2  1620  356  256 S  0.3  0.0   0:01.07 ipw3945d-2.6.15
 4661 meghan    15   0 40360  18m  11m S  0.3  1.9   0:03.18 gnome-panel
 4714 root      21   5  1552  260  192 S  0.3  0.0   0:00.01 powernowd
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.25 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.11 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   10 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kacpid-work-0
  167 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  168 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush


```

it looks normal, from what i can see, but obviously something somewhere is causing this--are there any diagnostics i could run?

---

### Post by Mustard on 2008-02-27
That's a pretty high cpu usage figure for firefox.  Was firefox using java or flash at that particular time?

---

### Post by Mustard on 2008-02-27
Are you using a particular gnome theme, other than the default Ubuntu theme? I've read one thread in which the slowdowns occured when using something other than the default Ubuntu theme.  Just curious, as I have been reading up on some possible reasons for the slow down.

In another thread someone solved their slow down problems by not using gnome.  Running KDE they found the issues disappeared.

Another possible issue was not having dma enabled for the hard drives.

All the threads regarding 'slow downs' seem to have a variety of causes, so its just going to be a case of trial and error.  It would be interesting to know what hardware you are using too.

---

### Post by irishgoth8822 on 2008-02-27
> **Mustard said:**
> Are you using a particular gnome theme, other than the default Ubuntu theme? I've read one thread in which the slowdowns occured when using something other than the default Ubuntu theme.  Just curious, as I have been reading up on some possible reasons for the slow down.

In another thread someone solved their slow down problems by not using gnome.  Running KDE they found the issues disappeared.

Another possible issue was not having dma enabled for the hard drives.

All the threads regarding 'slow downs' seem to have a variety of causes, so its just going to be a case of trial and error.  It would be interesting to know what hardware you are using too.

i'm using the regular theme, the only thing ive tweaked is desktop background and a few icons.

is there a way i can check whether or not dma is enabled? i also have disabled ipv6 at the moment, just in case its internet related and just in case that would help.

its a dell notebook e1405, as i have mentioned, intel core t2300E, with an 80GB 5400RPM SATA hard drive.

not being a computer-building sort of person, i dont know if those were the specs you were looking for, i took 'em straight off the packing slip :-p

---

