---
title: "Linux terminal commands - New user guide"
date: 2008-05-01
forum: General Help
---

### Post by StevenHarper on 2008-05-01
[SIZE="4"]===basics===[/SIZE]

These commands will be useful to you all the time, without knowledge of them most task via a terminal will be impossible.
There are 2 ways to get help on command while in the terminal
[LIST]
[*]man <COMMAND> (man top)
[*]<COMMAND> --help  (top --help)
[/LIST]


[SIZE="4"]===bash===[/SIZE]

bash is actually a shell, another shell is ksh, the shell effects the way some keys and shortcuts work.
Most modern systems default the shell to bash.

**Tips**
[LIST]
[*]Tab - complete the command 
[*]double Tab - list available completions
[*]Crtl+c - kills the command currently running
[*]Ctrl+z - stops the command you are running
[*]append an & to any command - runs the command in its own thread
[*]bg - put a stopped thread into the background and re-start it
[*]fg - list background threads to bring into the foreground
[*]Ctrl+r - recursive lookup of history of commands
[*]exit - exit from the shell
[/LIST]


[SIZE="4"]===cd===[/SIZE]

cd is used to change directory, in linux and unix all file and directories live under the root (/)

There is a structure and a rational layout of the filesystem (this is covered in concepts)

drives can be mounted at any location under the root (see df)

examples of cd
[LIST]
[*]cd ../   - move up a directory
[*]cd /     - move to the root
[*]cd ~     - move to your home directory
[*]cd /home/steven/Desktop    - move to a location specified in full
[*]cd ../home/steven/Desktop  - move to a location relative to yours
[/LIST]


[SIZE="4"]===chmod===[/SIZE]

chmod changes the permissions on a file (or list of files) (ls -l shows the current permissions)

```
 drwxr-xr-x  3 steven steven   4096 Mar 20 11:03 backup
 ^^^^^^^^^^
 1222333444
```

[LIST]
[*]1 ignore this part 
[*]2 This block is the Owner permissions block
[*]3 This block is the Group permissions block
[*]4 This block is the Everyone (all) permissions block
[/LIST]

The permission blocks all have the same format
[LIST]
[*]r - this file is readable
[*]w - this file is writeable
[*]x - this file is executable
[/LIST]

Each block can be represented as a decimal number - many commands and notation references them like this
[LIST]
[*]hs_err_pid16907.log -rw-r--r-- 644
[*]releases drwxr-xr-x 755
[/LIST]

you can use -R to recursively change files

[LIST]
[*]chmod a+r file.log  -  add ALL read rights to the file.log
[*]chmod a-w file.log  -  remove ALL write rights to the file.log
[*]chmod g+x file.sh   -  add GROUP execute rights to the file.sh
[*]chmod -R o+x *.sh   -  add OWNER execute rights to all files that end in .sh
[/LIST]

you can also use the numerical format

[LIST]
[*]chmod 644 file.log - make the file Owner read write - Group Read - ALL read
[*]chmod 754 file.log - make the file Owner read write execute - Group Read execute - ALL read
[/LIST]


[SIZE="4"]===chown===[/SIZE]

chown changes the ownership of a file or list of files

[LIST]
[*]chown steven file.log  - change ownership of the file.log to steven
[*]chown steven *.log     - change ownership of all files in this directory that match the pattern *.log to steven
[*]chown steven:other file.log - change the ownership to steven and the group to other
[*]chown -R steven backups - recursively change the ownership of all files in the directory backups to steven
[/LIST]


[SIZE="4"]===cp===[/SIZE]

cp copies the file you specify to another location

[LIST]
[*]cp a.file b.file  - copy 1 file
[*]cp *.log /var/tmp  - copy all files that end in .log to /var/tmp
[*]cp -r downloads ../../var/tmp - recursive copy downloads to /var/tmp
[/LIST]


[SIZE="4"]===df===[/SIZE]

df is used to see what filesystems are mounted, and how much capacity and space they have, sizes are shown by default in bytes


```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36843208  19401712  15569928  56% /
varrun                 1037816       112   1037704   1% /var/run
varlock                1037816         0   1037816   0% /var/lock
udev                   1037816        44   1037772   1% /dev
devshm                 1037816       108   1037708   1% /dev/shm
lrm                    1037816     38176    999640   4% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon      36843208  19401712  15569928  56% /home/steven/.gvfs
```

handy switches are

[LIST]
[*]k - show sizes in KB
[*]h - show sizes Human Readable (MB / GIG)
[/LIST]


[SIZE="4"]===du===[/SIZE]

du shows the disk usage - its most common usage is with the -s switch 

```
>du -sh *
693M	apps
588K	backup
24K	bin
8.0K	conf
4.0K	deployer
404M	Desktop
58M	Documents
4.7G	downloads
0	Examples
72K	hs_err_pid16907.log
4.0K	Music
850M	MyDownloads
33M	Pictures
4.0K	Public
4.0K	releases
4.0K	Templates
4.0K	Videos
565M	workspace
```

[LIST]
[*]h - Human readable Readable (MB / GIG)
[*]s - summarize, total up the directories inner contents
[/LIST]

**Tips**
Combine this with sort to get them in order (reverse the results and sort numerically)
```
 du -sk * | sort -rn
Combine this with head to the top few (show top 3)
 du -sk * | sort -rn | head -n 3
```


[SIZE="4"]===env===[/SIZE]

env lists the environment variables set up for your user

```
GPG_AGENT_INFO=/tmp/seahorse-TSwm1q/S.gpg-agent:5476:1
SHELL=/bin/bash
DESKTOP_STARTUP_ID=
TERM=xterm
XDG_SESSION_COOKIE=5d533d4d8fa79592b2f2dcac47e12042-1209120135.483311-441331670
GTK_RC_FILES=/etc/gtk/gtkrc:/home/steven/.gtkrc-1.2-gnome2
WINDOWID=35727091
USER=steven
PATH=/home/steven/bin:/home/steven/apps/ant/bin:/home/steven/apps/java/bin:/home/steven/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/steven
JAVA_HOME=/home/steven/apps/java
LANG=en_GB.ISO8859-15
GNOME_KEYRING_PID=5371
GDM_LANG=en_GB.UTF-8
JETTY_HOME=/home/steven/apps/jetty
GDMSESSION=default
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/steven
GNOME_DESKTOP_SESSION_ID=Default
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
```

This is not all the output - its very big.

Many programs need certain environment variables - these are loaded from a file in your home directory when you login 

[LIST]
[*]/home/steven/.bashrc
[/LIST]

If you modify the profile file be careful , to re-read it you can dot it. If you do change it to affect a graphical program you will need to logout and relogin

```
 cd ~
 . .bashrc
```


[SIZE="4"]===find===[/SIZE]

find is used to list files (recursively) from the directory you are in or specify.

it usually outputs lots of data - in most cases you pass the output through grep

```
find /home/steven/backups | grep kylie
```


will get you all the files that have the word kyle in the name ion my backup directory


[SIZE="4"]===grep===[/SIZE]

grep is used to find patterns in files or output from other commands.
```

 grep monkey *.log
```

will show you all the line numbers where the word monkey are in any files that path the *.log pattern

```
 ps -ef | grep backup
```

will grep through the output from ps -ef and show only lines that have the word backup in them


[SIZE="4"]===kill===[/SIZE]

kill is used to kill a process by its id (these id's are found using top or ps)


Kill processes with the id's 4567 456 5678
```
 kill 4567 456 5678
```

Kill (with vengeance - not nicely)  process 45768
```
 kill -9 45768
```

A common use to kill processes that run as root is to sudo the command
```
 sudo kill -9 46565
```


[SIZE="4"]===ln===[/SIZE]

ln is used to link files - the number of hard links to a file or directory show up in ls


```
ls -l
total 136
drwxr-xr-x 6 steven steven  4096 Apr 28 11:06 Desktop
drwxr-xr-x 5 steven steven  4096 Apr 23 10:43 Documents
lrwxrwxrwx 1 steven steven    26 Mar 19 14:12 Examples -> /usr/share/example-content
```

Here you can see the Examples directory is just a link to the location /usr/share/example-content

this was created with the following command
```
ln -s /usr/share/example-content /home/steven/Examples
```

to remove a sim link you simple treat it as any other file and use rm


[SIZE="4"]===ls===[/SIZE]

ls lists the files in the directory you are in.
Most version simply list the names of the directories and files all in alphabetical order
most commonly the -l switch is used to show a full list of the files and directories.

```
ls -l
total 136
drwxr-xr-x 6 steven steven  4096 Apr 28 11:06 Desktop
drwxr-xr-x 5 steven steven  4096 Apr 23 10:43 Documents
lrwxrwxrwx 1 steven steven    26 Mar 19 14:12 Examples -> /usr/share/example-content
drwxr-xr-x 2 steven steven  4096 Mar 19 14:17 Music
drwx------ 2 steven steven  4096 Apr 23 16:09 MyDownloads
drwxr-xr-x 9 steven steven  4096 Mar 27 15:45 Pictures
drwxr-xr-x 2 steven steven  4096 Mar 19 14:17 Public
drwxr-xr-x 2 steven steven  4096 Mar 19 14:17 Templates
drwxr-xr-x 2 steven steven  4096 Apr 15 18:38 Videos
drwxr-xr-x 9 steven steven  4096 Mar 20 12:49 apps
drwxr-xr-x 3 steven steven  4096 Mar 20 11:03 backup
drwxr-xr-x 2 steven steven  4096 Apr 24 14:57 bin
drwxr-xr-x 2 steven steven  4096 Mar 19 15:29 conf
drwxr-xr-x 2 steven steven  4096 Mar 20 11:09 deployer
drwxr-xr-x 7 steven steven  4096 Mar 28 10:31 downloads
-rw-r--r-- 1 steven steven 68296 Apr  8 11:08 hs_err_pid16907.log
drwxr-xr-x 2 steven steven  4096 Mar 20 11:09 releases
drwxr-xr-x 6 steven steven  4096 Mar 20 12:02 workspace
```

Firstly you get a total - this includes all the hidden files (the -a switch will show these) - so in this case there are lots of hidden files.

**The first column** has the file permissions (chmod changes  these) - the permission block is split into 4 sections
```
 1222333444
```
[LIST]
[*]1  either d or - the d signifies that its a directory not a file
[*]2  This block is the Owner permissions block
[*]3  This block is the Group permissions block
[*]4  This block is the Everyone (all) permissions block
[/LIST]

The permission blocks all have the same format
[LIST]
[*]r - this file is readable
[*]w - this file is writeable
[*]x - this file is executable
[/LIST]

Each block can be represented as a decimal number - many commands and notation references them like this
[LIST]
[*]hs_err_pid16907.log -rw-r--r-- 644
[*]releases drwxr-xr-x 755
[/LIST]

**The second column** is the number of hard links fo that file (see ln)

**The Third column** is the owner name

**The Fourth column** is the group name

**The Fifth column** is the size in bytes (-k and -h can make these more readable)

**The Sixth column** is the Date and time the file was last modified

**The Seventh column** is the name of the file

In the output above you can see that the directory Example is a sim link to another location (see ln)

**Tip**
ls -lart  is very handy it lists the most recently modified file last


[SIZE="4"]===mv===[/SIZE]

mv moves the file you specify to another location
[LIST]
[*]mv a.file b.file  - move 1 file
[*]mv *.log /var/tmp  - copy all files that end in .log to /var/tmp
[*]mv  downloads ../../var/tmp - move the directory downloads to /var/tmp
[/LIST]


[SIZE="4"]===pipe===[/SIZE]

Pipe is not a command - the character | is the pipe
It is used for sending the results of a command to another
So if one command is going to produce 1,000 lines of output you can pipe this to another command to filter / reduce / sort them

e.g.
List files in the current directory - filter them by a pattern (xml)
```
 ls -l | grep xml
```
List all open files in the system that have the patter pie
```
 lsof | grep pie
```


[SIZE="4"]===pkill===[/SIZE]

pkill is used to kill a process by its name (these names are found using top or ps)


Kill processes that contain the name apache
```
 pkill apache
```

Kill (with vengeance - not nicely)  all processrs that have a b in it (don't do this in real life)
```
 pkill -9 b
```

A common use to kill processes that run as root is to sudo the command
```
 sudo pkill -9 apache
```


[SIZE="4"]===ps===[/SIZE]

ps by itsself lists the processes running in your shell

```
  PID TTY          TIME CMD
  515 pts/1    00:00:00 bash
 4368 pts/1    00:00:00 ps
```

The first column is the ID of the process
the second column is the terminal ID
the third column is the run time on the CPU that process has used
the fourth column is the name of the process

[LIST]
[*]ps -a  - lists all processes
[*]ps U steven - lists all processes running under the user steven
[*]pe -ef - list all process in full
[/LIST]

'''Tips'''<br>
ps -ef | grep apache - will show you all processes filtered with grep


[SIZE="4"]===pwd===[/SIZE]

pwd is used to display the current directory you shell is in

```
pwd 
/home/steven
```


[SIZE="4"]===rm===[/SIZE]

rm is used to remove files and directories

To remove a file
```
 rm afile.log
```

To remove lots of files matching the patter *.log
```
 rm *.log
```

Recursively remove all files matching the pattern *.log
```
 rm -R *.log
```


[SIZE="4"]===scp===[/SIZE]

scp is used to transfer files from / to other servers

to send one file to the server vadar into the directory /var/tmp
```
 scp afile.log steven@vadar:/var/tmp/
```

to get one file from vadar and put into the current directory
```
 scp . steven@vadar:/var/tmp/afile.log
```

to get many files from vadar and put into the current directory
```
 scp . steven@vadar:/var/tmp/*.log
```

to get a whole directory structure and put into the current directory
```
 scp -r . stevenvadar:/var/tmp/logs
```


[SIZE="4"]===ssh===[/SIZE]

ssh is used to log into other servers

to log into the beta dev server as the user searchdev
```
 ssh searchdev@10.100.221.180
```

the command exit will logout of any server


[SIZE="4"]===sudo===[/SIZE]

sudo is used to run commands under super user

to chown a file you don't own
```
 sudo chown steven afile.log
```

to reboot the server
```
 sudo reboot
```

you can also switch the terminal to be logged in as root
```
 sudo su
```


[SIZE="4"]===telnet===[/SIZE]

telnet is a very basic way of connecting to a port on a server

It is mainly used for debugging network problems or checking that services are running

an example to check to see if you can get a webpage would be


```
>telnet google.com 80
Trying 72.14.207.99...
Connected to google.com.
Escape character is '^]'.
GET /
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>302 Moved</TITLE></HEAD><BODY>
<H1>302 Moved</H1>
The document has moved
<A HREF="http://www.google.co.uk/">here</A>.
</BODY></HTML>
Connection closed by foreign host.
```


CTRL+] logs out 


[SIZE="4"]===top===[/SIZE]

Top is used to view the running process on a server

```
top - 16:21:50 up 5 days,  4:40,  6 users,  load average: 0.33, 0.40, 0.36
Tasks: 121 total,   2 running, 119 sleeping,   0 stopped,   0 zombie
Cpu0  : 24.8%us,  1.7%sy,  0.0%ni, 72.9%id,  0.0%wa,  0.2%hi,  0.3%si,  0.0%st
Mem:   2075636k total,  1953412k used,   122224k free,   295416k buffers
Swap:  1646620k total,    22108k used,  1624512k free,   807328k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                          
11782 steven    20   0  305m 174m  28m R 26.0  8.6  92:30.57 firefox-2-bin                                                    
 5178 root      20   0  939m 115m  12m S  3.3  5.7  54:16.08 Xorg                                                             
 6066 steven    20   0 89780  29m  11m S  1.3  1.5   0:35.06 gnome-terminal                                                   
 1473 root      15  -5     0    0    0 S  0.7  0.0   0:06.50 ata/0                                                            
 5636 steven    20   0 30528  12m 8712 S  0.7  0.6   3:51.17 nm-applet                                                        
 5369 steven    20   0  7720 4832 1920 S  0.3  0.2   5:33.80 gconfd-2                                                         
 5724 steven    20   0 21000 8476 7148 S  0.3  0.4  34:35.54 multiload-apple                                                  
    1 root      20   0  2844 1688  544 S  0.0  0.1   0:01.12 init                                                             
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                         
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                      
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.52 ksoftirqd/0                                                      
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                       
    6 root      15  -5     0    0    0 S  0.0  0.0   0:02.66 events/0                                                         
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                          
   42 root      15  -5     0    0    0 S  0.0  0.0   0:01.04 kblockd/0                                                        
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                           
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
```

When started you can hit several keys to change the reporting and output of top
below are the most common/useful

[LIST]
[*]c - shows full command instead of process name
[*]z - use monotone colouring
[*]1 - Show full CPU stats
[*]s <number> - number of seconds before refresh
[*]u <username> - restrict to processes running under user - blank for all
[*]k - kill a process 
[*]q - quit
[/LIST]

**FAQ**
Q. What does the Load Average mean<br>
A. It's a combined measure of load on the Server, the format is each number is the history of load - the first is the current
The value is calculated by looking at IO on Networks, CPU(s), RAM, Disk(s)


[SIZE="4"]===vi===[/SIZE]

vi is a text editor that works in a terminal - its klunky and hard to use/learn - I suggest you do try as its vital to most tasks.

```
 vi afile.config
```

[LIST]
[*]Cursor keys (arrows) move around the file
[*]i - put your self into insert mode
[*]r - replace one character
[*]a - put your self into append mode
[*]dd - delete the line
[*]u - undo last action
[*]:q! - quit DONT save
[*]:wq! - quit and save
[/LIST]


[SIZE="4"]===wget===[/SIZE]

wget is used to get resources from the internet

an example is
```
 wget http://www.google.com
```

this saves the response as a file in the directory you are in

---

### Post by bilal.17 on 2008-05-01
Thats a great guide for new users! Good job.

---

### Post by dwiedenfeld on 2008-05-01
Thanks--this is great for us newbies. 

By the way, I copied this (Firefox) and pasted into OO Writer and it came through with most formatting intact. So I can save it for easy future reference.

---

### Post by StevenHarper on 2008-05-01
shameless bump!

---

### Post by Vicfred on 2008-05-01
pretty nice, I was thinking about learn this =d

---

### Post by hvacr on 2008-05-01
This is great, thanks very much.

---

### Post by jjk7288 on 2008-05-01
Nice guide indeed. I've learned some things here.

---

### Post by Irony on 2008-05-01
Nice. This should go in the tutorials section.

---

### Post by mailtwogopal on 2008-06-15
hi,

 thanks a lot. its a great guide for newbie in linux.

---

### Post by Jim! on 2008-07-08
Sure, the threads old...... But what kind of person would I be if I didn't say thankyou? Thanks for posting this up;)

---

### Post by pedrogent on 2008-07-18
A really great post. It cleared a few things up for me.

I'd thank you if I knew how...

---

### Post by meazz1 on 2008-07-18
Very helpful for us, newbies.

---

### Post by alimooghashang on 2011-04-13
this topic is very nice
i want to know if there is an ebook (like this topic) about linux terminal tutorial? (with examples like this topic)
i wonder if you tell me.

---

