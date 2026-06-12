---
title: "good commands that nobody knows about"
date: 2007-03-17
forum: General Help
---

### Post by rajan on 2007-03-17
I was surfing the web looking for a few things and I found this site:

[http://www.secguru.com/article/finding_hardware_details_of_your_linux_machine_without_using_screw_driver](http://www.secguru.com/article/finding_hardware_details_of_your_linux_machine_without_using_screw_driver)

and I found it extraordinarily helpful. The title of the site says it all, but most of the commands are useful for other things. Here's a quick summary:

```
dmidecode
``` gets your BIOS settings in english (instead of binary)


```
cat /proc/cpuinfo
``` displays your cpu information on a terminal


```
lshw
``` lists hardware devices


```
dmesg | less 
``` ok, this one isn't as unknown as the other ones, but it's still useful.


```
du
```or```
df
``` also, not very unknown, and not as useful in ubuntu where we can just click on a folder and view the properties.


```
hdparm
``` similar to some other commands, but very unknown (to me)


```
ifconfig
``` displays network interfaces



please post here if you know of any other commands that should be more well-known, and let me know if there's a similar thread like this already out there (I didn't find any).

---

### Post by christhemonkey on 2007-03-17
```
gnome-open foo.whatever 
```
Opens whatever file in its respective program.

Thats the only one that comes to mind just sat here.

---

### Post by ardchoille42 on 2007-03-17
To launch the graphical logout dialog in gnome:
```

/usr/bin/gnome-session-save --gui --kill

```

To lock the screen and activate the screensaver:
```

gnome-screensaver-command --lock

```

To launch any app as admin user:
```

gksuexec

```

To make a launcher for the ALT+F2 run dialog:
```

gnome-panel-control --run-dialog

```

---

### Post by dreadlord_chris on 2007-03-17
> **ardchoille42 said:**
> To launch the graphical logout dialog in gnome:

To launch any app as admin user:
```

gksuexec

```



this should be **gksudo**

---

### Post by ardchoille42 on 2007-03-17
> **dreadlord_chris said:**
> this should be **gksudo**

No, it should be

```

gksuexec

```

Open a terminal, type gksuexec and see the gui dialog that opens to allow you to run any app as root ;)
Here is a screenshot of this nice little app:

---

### Post by dreadlord_chris on 2007-03-18
> **ardchoille42 said:**
> No, it should be

```

gksuexec

```

Open a terminal, type gksuexec and see the gui dialog that opens to allow you to run any app as root ;)
Here is a screenshot of this nice little app:

```
chris@HAL421:~$ gksuexec
bash: gksuexec: command not found

```

```
chris@HAL421:~$ gksudo
```

```
chris@HAL421:~$ file /usr/bin/gksu
/usr/bin/gksu: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), stripped
```

```
chris@HAL421:~$ file /usr/bin/gksudo
/usr/bin/gksudo: symbolic link to `gksu'
```

gksuexec was changed to gksudo sometime last year (google gksuexec) - probably to more conform the Ubuntu's sudo model, as apposed to the more traditional su model.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by rajan on 2007-03-18
I've got both... so there's basically no difference between them?

[http://www.penguin-soft.com/penguin/man/1/gksuexec.html](http://www.penguin-soft.com/penguin/man/1/gksuexec.html)

according to that page, there isn't (except for the fact that there's a graphical front end).

thanks for the tips so far, everyone.

---

### Post by nereid on 2007-03-18
```

find ~ -type f -iname "*.mp3"

```

find one of the best programs around (with the above options it will find all mp3 files in your home directory).

```

xargs

```

Another cool app which works really well with find for example. The input is a list of files and another app and xargs will run the other app with the files from the list.

```

find ~ -type f -iname "*.mp3" -print0 | xargs -r0 mp3gain -r

```

Which will find all mp3 files in your home directory and will pipe them to mp3gain to normalize each file (the -print0 and -r0 flags are for files with spaces in the filename and the full pathname).

---

### Post by Lord Illidan on 2007-03-18
This is more of a warning..

** If anyone posts this code** [COLOR=Red]```
sudo rm - rf /
```[COLOR=Black] claiming it is a nice app.._**don't try it out**_.. It will recursively delete all files in your root directory. If you don't believe me, type [/COLOR][/COLOR]```
man rf
```Now, my own list..

df -h represents diskspace in human readable format, i.e. with GB and stuff.
lynx is a nice consolebased webbrowser, get it from the repos.

And free is a good command for displaying cached memory.

---

### Post by rolando2424 on 2007-03-18
> **Lord Illidan said:**
> This is more of a warning..

** If anyone posts this code** [COLOR=Red]```
sudo rm - rf /
```[COLOR=Black] claiming it is a nice app.._**don't try it out**_.. It will recursively delete all files in your root directory. If you don't believe me, type [/COLOR][/COLOR]```
man rf
```Now, my own list..

df -h represents diskspace in human readable format, i.e. with GB and stuff.
lynx is a nice consolebased webbrowser, get it from the repos.

And free is a good command for displaying cached memory.

Yeah... Older users should not fall for that one, but new users might not know about that...

---

### Post by ardchoille42 on 2007-03-18
> **dreadlord_chris said:**
> ```
chris@HAL421:~$ gksuexec
bash: gksuexec: command not found

```

```
chris@HAL421:~$ gksudo
```

```
chris@HAL421:~$ file /usr/bin/gksu
/usr/bin/gksu: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), stripped
```

```
chris@HAL421:~$ file /usr/bin/gksudo
/usr/bin/gksudo: symbolic link to `gksu'
```

gksuexec was changed to gksudo sometime last year (google gksuexec) - probably to more conform the Ubuntu's sudo model, as apposed to the more traditional su model.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

*sigh* I wish they'd stop changing things around.

```

[~ @ 14:22:52] which gksuexec
/usr/bin/gksuexec
[~ @ 14:34:24] file /usr/bin/gksuexec
/usr/bin/gksuexec: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped
[~ @ 14:34:32]

```

This makes it extremely difficult for people to provide proper support, since things aren't consistent. I run Dapper, on Dapper that app is gksuexec. I never knew they changed it. Sorry for the problem, but you can blame the devs since they don't seem to have a clue about the definition of consitency. Computers would be a lot more user friendly and easier to run if the developers would pick a system and stick with it without changing things around every other release.

---

### Post by barney_1 on 2007-03-18
Thanks for posting these, very useful.  I just recently became familiar with df -h, quite handy!

---

### Post by hikaricore on 2007-03-18
> **Lord Illidan said:**
> This is more of a warning..

** If anyone posts this code** [COLOR=Red]```
sudo rm - rf /
```[COLOR=Black] claiming it is a nice app.._**don't try it out**_.. It will recursively delete all files in your root directory. If you don't believe me, type [/COLOR][/COLOR]```
man rf
```Now, my own list..

df -h represents diskspace in human readable format, i.e. with GB and stuff.
lynx is a nice consolebased webbrowser, get it from the repos.

And free is a good command for displaying cached memory.

I was thinking about it.  ROFL
The thread title kinda left it right open for evil.  :)

---

### Post by Lord Illidan on 2007-03-18
> **hikaricore said:**
> I was thinking about it.  ROFL
The thread title kinda left it right open for evil.  :)
Yes, I did kinda anticipate it:lolflag:

---

### Post by dbott67 on 2007-03-18
Hardware discovery (kind of like the "Find New Hardware Wizard" in Windows).  Use **man discover** to see all pertinent info:
```
discover [options] [devices]
```For those that use Samba:
```
dbott@thedrake:~$ **sudo smbtree**
Password:
WORKGROUP
        \\THEDRAKE                      thedrake server (Samba, Ubuntu) *[COLOR=Blue]<--- My Dapper desktop[/COLOR]*
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\dbott
                \\THEDRAKE\print$               Printer Drivers
        \\PIII-600 [COLOR=Blue]*<--- the kids XP PC; no firewall; no shares*[/COLOR]
        \\OMEGA-XP [COLOR=Blue]*<--- My laptop; Running XP firewall*[/COLOR]
Error connecting to 192.168.1.105 (No route to host)
cli_start_connection: failed to connect to OMEGA-XP<20> (192.168.1.105)
        \\NAS-160GB [COLOR=Blue]*<--- My NAS device*[/COLOR]
                \\NAS-160GB\IPC$
                \\NAS-160GB\Videos
                \\NAS-160GB\Music
                \\NAS-160GB\Archive
                \\NAS-160GB\Data
                \\NAS-160GB\PUBLIC
        \\JBOTT-PC [COLOR=Blue]*<--- My wife's laptop; Running Vista firewall; no open shares*[/COLOR]
timeout connecting to 192.168.1.101:445
timeout connecting to 192.168.1.101:139
Error connecting to 192.168.1.101 (Operation already in progress)
cli_start_connection: failed to connect to JBOTT-PC<20> (192.168.1.101)
dbott@thedrake:~$

```All of the discovered data is stored in **var/cache/samba/browse.dat**:
```
dbott@thedrake:~$ cat /var/cache/samba/browse.dat
"WORKGROUP"               c0001000 "THEDRAKE"                    "WORKGROUP"
"THEDRAKE"                40059a03 "thedrake server (Samba, Ubuntu)" "WORKGROUP"
"NAS-160GB"               40412003 ""                            "WORKGROUP"
"OMEGA-XP"                40011203 ""                            "WORKGROUP"
"JBOTT-PC"                40001003 ""                            "WORKGROUP"
"PIII-600"                40011003 ""                            "WORKGROUP"

```
```
smbclient -L IP.ADDRESS.OF.SERVER -U%
```
```
dbott@thedrake:~$ smbclient -L 192.168.1.2 -U%

        Sharename       Type      Comment
        ---------       ----      -------
        PUBLIC          Disk
        Data            Disk
        Archive         Disk
        Music           Disk
        IPC$            IPC

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
```

I also like the networking tools when troubleshooting networking problems:
```
sudo lshw -C network
```Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```This command tries to detect wireless access points using each NIC:

```
iwlist scanning
``````
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```This command prints out your routing table:

```
route -n
``````
dbott@dapper:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```-Dave

---

### Post by vinnn on 2007-03-18
Off the top of my head...


**l**i**s**t **o**pen **f**iles]
```
lsof
```

**l**i**s**t **usb** devices
```
lsusb
```

EVERYONE should learn to use...
```
find
```

**d**isk **f**ree **-h**uman readable
```
df -h
```

**d**isk **u**sage **-h**uman readable
```
du -h
```

**print env**ironment settings
```
printenv
```

**ch**ange **f**i**n**ger
(change an user's **finger** details)
```
chfn
```

**w**ord **c**ount
Count words, lines or bytes in a given file.
```
wc
```

**user mod**ify
(let's you easily change a user's login name or home directory)
```
usermod -l
usermod -d
```

**g**host**v**iew
A command-line Postscript and PDF viewer
```
gv
```

Reload a running Apache webserver without affecting connected clients
```
apachectl -k graceful
```


**Shell stuff...**
**^D**
Ctrl+D terminates the shell, i.e. logs out of the shell.

**^C**
When running a lengthy process in a shell Ctrl+C cancels it.
Everyone knows this one.

**^Z**
When running a lengthy process in a shell Ctrl+Z suspends it.
When the process is suspended, a job number is displayed.
Not as many peeps seem to use this beauty.

   **bg %jobnumber**
   Sends a suspended process to run as a background process

   **fg %jobnumber**
   Sends a suspended process to run as a foreground process

---

### Post by dreadlord_chris on 2007-03-18
> **ardchoille42 said:**
> *sigh* I wish they'd stop changing things around.

```

[~ @ 14:22:52] which gksuexec
/usr/bin/gksuexec
[~ @ 14:34:24] file /usr/bin/gksuexec
/usr/bin/gksuexec: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped
[~ @ 14:34:32]

```

This makes it extremely difficult for people to provide proper support, since things aren't consistent. I run Dapper, on Dapper that app is gksuexec. I never knew they changed it. Sorry for the problem, but you can blame the devs since they don't seem to have a clue about the definition of consitency. Computers would be a lot more user friendly and easier to run if the developers would pick a system and stick with it without changing things around every other release.

I couldn't agree more...

---

### Post by dreadlord_chris on 2007-03-18
> **rajan said:**
> I've got both... so there's basically no difference between them?

[http://www.penguin-soft.com/penguin/man/1/gksuexec.html](http://www.penguin-soft.com/penguin/man/1/gksuexec.html)

according to that page, there isn't (except for the fact that there's a graphical front end).

thanks for the tips so far, everyone.

Correct - gksudo & gksuexec are graphical front-ends to sudo

if you have both it really doesn't matter which you use.

---

### Post by rajan on 2007-03-18
looks like lsusb and df -h are big winners here. thanks for pointing df -h out, Lord Illidan. I have used it a couple of times today already. 

as far as getting information on a file, is there a command to get the created date of a file? how about the last date that a binary has been executed? 

and the name of the thread.... heheh yeah I guess it should have a "buyer beware" after it.

---

### Post by nereid on 2007-03-19
You can't get the last date a binary was executed, it ain't saved anywhere. But with *ls -l /path/to/file* you can get the date on which the file was last modified and/or created and some other nifty informations.

---

### Post by gradedcheese on 2007-03-19
1) these are not 'codes', these are shell commands ;)
2) you meant "man rm"

for the du and df commands, the -h (human-readable) option is helpful:

```

du -h
df -h

```

---

### Post by andmalc on 2007-03-19
```
pgrep <pattern>
``` and ```
pkill <process name>
``` for searching for and killing a process by name.

```
locate <pattern>
``` for finding files by name.  Much faster than find.  Must run upatedb first.

Not a command but a bash/zsh keybinding: Control+R to search backwards in the history.

---

### Post by dreadlord_chris on 2007-03-25
Just discovered this one:

**xkill** - Kills a misbehaving application. Once this command is run, the mouse cursor will become a skull and crossbones. Any window you click on after that will close immediately.

---

### Post by Ramses de Norre on 2007-03-25
[b]
apt-cache policy *<package_name>*
nohup
screen
finger
[/b]

And to keep it in people's mind: **glxgears -iacknowledgethatthistoolisnotabenchmark**

---

### Post by astoltz on 2007-03-25
How 'bout some not-so-useful ones:

fortune
cal

---

### Post by rajan on 2007-03-30
The fortune one is great.... kinda reminds me of the therapist in emacs (which is an absolutely stellar way to avoid coding). 

is there a command to display the libraries you have? like if i wanted to figure out if I had the OpenGL libraries, would it be quicker for me to search my /usr/lib directory or type a command?

---

### Post by andmalc on 2007-03-30
For installed package names, pass a regex to aptitude's search feature together with the ~i flag to limit to installed packages

```
aptitude search 'open.*lib~i'
```

or for the file names, give locate a globbing pattern

```
locate '*open*lib*' 
```

---

### Post by Ramses de Norre on 2007-03-31
This one I've already given to several people on this forum: **nohup *command* &**.
It runs *command* totally independent from the terminal and outputs everything to ~/nohup.out.

---

### Post by andmalc on 2007-03-31
Ramses,

Why would you want to run a command like this?

Thx

---

### Post by raffytaffy on 2007-03-31
apt-get moo

---

### Post by Horizon on 2007-03-31
> **andmalc said:**
> Ramses,

Why would you want to run a command like this?

Thx

I can see use for this when writing scripts. Also when you want to launch a gui app quickly but don't want it to be tied to the terminal you have open.

---

### Post by Ramses de Norre on 2007-04-01
> **andmalc said:**
> Ramses,

Why would you want to run a command like this?

Thx

When you for instance launch gui apps from terminal, they'll close when you close the terminal. Or when you start a service over ssh, the service dies when you loose your connection.

These things doesn't happen with nohup. I've already been able to help a few people on this forums with it.

---

### Post by rajan on 2007-04-03
thanks, andmalc

---

### Post by andmalc on 2007-04-03
> **Ramses de Norre said:**
> When you for instance launch gui apps from terminal, they'll close when you close the terminal. Or when you start a service over ssh, the service dies when you loose your connection.

These things doesn't happen with nohup. I've already been able to help a few people on this forums with it.

OK - definitely will use this to run GUI apps.

For keeping a ssh session and programs in it alive, I run gnu-screen.  In fact, I think this is the number one indispensable program for a serious shell user.  Check out my bookmarks for this:

[http://del.icio.us/andmalc/screen](http://del.icio.us/andmalc/screen)

I have a permanent screen session going on my Debian server with tabs for Multitail, my mail in mutt, a root shell, irc, a nested screen session to another host, and usually a few other tabs for whatever projects I'm working on.   When I log off the server, the whole thing continues.  When I ssh back in, 'screen -r' in my .zlogin brings me right back into it.

---

