---
title: "Conky Script not working after reboot."
date: 2013-03-01
forum: General Help
---

### Post by c2tarun on 2013-03-01
Hi friends,

I copied a conky script, modified it a bit and it was working fine for the first time. [Here]("http://paste.ubuntu.com/5578291/") is my .conkyrc.
I added conky to startup applications
[ATTACH=CONFIG]239608[/ATTACH]

Now when I restart my laptop conky is not working at all, I mean its not getting started automatically, even I start it manually its not starting.
Can anyone please help?

Now when I am running conky on terminal I am getting following message:

```
tarun@tarun-Inspiron-N4010:~$ conkyConky: forked to background, pid is 2402
tarun@tarun-Inspiron-N4010:~$ 
Conky: desktop window (2000095) is subwindow of root window (a8)
Conky: window type - desktop
Conky: drawing to created window (0x3c00001)
Conky: drawing to double buffer
```

---

### Post by fdrake on 2013-03-02
can you attach the concky script here?

edit : never mind i saw your link to it.

---

### Post by c2tarun on 2013-03-02
> **fdrake said:**
> can you attach the concky script here?
```
background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type yes 
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 400
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 10
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer right 
text_buffer_size 256


TEXT


           ${font openlogos:size=20}U${font Arial:size=20}${color Tan1}GNU${color Ivory}LINUX${font openlogos:size=20}t


${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}


${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
CPU2  ${cpu cpu2}% ${cpubar cpu2}


${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar


${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}


${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %


${font Arial:bold:size=10}${color Tan2}TIME ${color DarkSlateGray}${hr 2}


${color DarkSlateGray} ${font :size=30}$alignc${time %H:%Mh}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}


${font Arial:bold:size=10}${color Tan2}GMAIL ${color DarkSlateGray}${hr 2}
${color white}${execpi 300 ~/.scripts/imap.pl} New Messages ${color DimGray}

```

---

### Post by c2tarun on 2013-03-02
I am facing one more problem, my color changes are not reflecting properly. Like with color as DimGray it looks like this [ATTACH=CONFIG]239609[/ATTACH]

But if I change my color to navy from DimGray in this line: "[COLOR=#000000][FONT=Ubuntu Mono]$font${color DimGray}$sysname $kernel $alignr $machine"
it looks like this
[/FONT][/COLOR][ATTACH=CONFIG]239610[/ATTACH]

It is hardly visible. But according to [this]("http://hans.fugal.net/vim/rgbtxt.html") page, navy is pretty bright color.

---

### Post by fdrake on 2013-03-02
concy vers being used?
 "conky -v"
also check the debug option
"conky -D" and post here the possible errors

---

### Post by c2tarun on 2013-03-02
> **fdrake said:**
> concy vers being used?
 "conky -v"
also check the debug option
"conky -D" and post here the possible errors

Hi,

I am facing lots of different issues like sometimes my conky don't run. But if I killall conky and try again and again then sometimes its possible that all the three conky I have on my desktop run.

Here I am running all conky's in debug mode:
```
tarun@tarun-Inspiron-N4010:~$ conky -D
DEBUG(0) [../../src/conky.c:5376]: reading contents from config file '/home/tarun/.conkyrc'
Conky: forked to background, pid is 4528
tarun@tarun-Inspiron-N4010:~$ 
Conky: desktop window (2000095) is subwindow of root window (a8)
Conky: window type - override
Conky: drawing to created window (0x3c00001)
Conky: drawing to double buffer


tarun@tarun-Inspiron-N4010:~$ conky -c .conkyrc_cal 
Conky: forked to background, pid is 4542
tarun@tarun-Inspiron-N4010:~$ 
Conky: desktop window (2000095) is subwindow of root window (a8)
Conky: window type - override
Conky: drawing to created window (0x4000001)
Conky: drawing to double buffer


tarun@tarun-Inspiron-N4010:~$ conky -cD .conkyrc_gmail 
Conky: invalid configuration file 'D'


Conky: forked to background, pid is 4595
tarun@tarun-Inspiron-N4010:~$ 
Conky: desktop window (2000095) is subwindow of root window (a8)
Conky: window type - override
Conky: drawing to created window (0x4200001)
Conky: drawing to double buffer

```

Now we can see that three conky's are running:
```
tarun@tarun-Inspiron-N4010:~$ ps -A | grep conky 4528 pts/0    00:00:02 conky
 4542 pts/0    00:00:00 conky
 4595 pts/0    00:00:01 conky
```

But only two are running (third one is aligned to bottom_left with gap_x=50:
[ATTACH=CONFIG]239623[/ATTACH]

I created a small startconky.sh file with start command for three conky's
```
tarun@tarun-Inspiron-N4010:~$ cat startconky.sh 
conky &
conky -c .conkyrc_cal
conky -c .conkyrc_gmail

```

Now see if I killall conky and run this script:
```
Conky: desktop window (2000095) is subwindow of root window (a8)

Conky: desktop window (2000095) is subwindow of root window (a8)
Conky: window type - override
Conky: drawing to created window (0x4000001)
Conky: window type - override
Conky: drawing to created window (0x3c00001)
Conky: drawing to double buffer
Conky: drawing to double buffer
Conky: desktop window (2000095) is subwindow of root window (a8)
Conky: window type - override
Conky: drawing to created window (0x4200001)
Conky: drawing to double buffer
```

All conky's are running:
[ATTACH=CONFIG]239624[/ATTACH]

My conky -version is 
```
Conky 1.8.1 compiled Fri Dec 16 18:29:36 UTC 2011 for Linux 2.6.24-30-server (x86_64)
```

My all three conky files are:
.conkyrc
```
background yesuse_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type override 
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 400
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 10
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer right 
text_buffer_size 256


TEXT




         ${color Tan1}${font openlogos:size=20}u ${font Arial:bold:size=20}UBUNTU 12.04${font openlogos:size=20} S


${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}


${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
${execpi 60 sensors | grep 'Core 0'}
CPU2  ${cpu cpu2}% ${cpubar cpu2}
${execpi 60 sensors | grep 'Core 2'}


${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar


${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}


${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %


${font Arial:bold:size=10}${color Tan2}TIME ${color DarkSlateGray}${hr 2}


${color DarkSlateGray} ${font :size=30}$alignc${time %I:%M %p}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}
```

.conkyrc_cal
```
background yesuse_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type override 
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 163
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment tl 
gap_x 55
gap_y 35
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer right 
text_buffer_size 256


TEXT
${font Arial:bold:size=10}${color Tan2}CALENDAR ${color DarkSlateGray}${hr 2}
${color gray}${font Monospace:size=10}${exec ncal -bh}

```


.conkyrc_gmail
```
background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type override 
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 120
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment bl 
gap_x 55
gap_y 15
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer right 
text_buffer_size 256


TEXT
${font Arial:bold:size=10}${color Tan2}GMAIL ${color DarkSlateGray}${hr 2}
${color white}${execpi 300 ~/.scripts/imap.pl} New Messages ${color DimGray}
```

The script that is running to get gmail status is:
```
#!/usr/bin/perl


# gimap.pl by gxmsgx
# description: get the count of unread messages on imap


use strict;
use Mail::IMAPClient;
use IO::Socket::SSL;


my $username = 'username@gmail.com'; 
my $password = 'password'; 


my $socket = IO::Socket::SSL->new(
  PeerAddr => 'imap.gmail.com',
  PeerPort => 993
 )
 or die "socket(): $@";


my $client = Mail::IMAPClient->new(
  Socket   => $socket,
  User     => $username,
  Password => $password,
 )
 or die "new(): $@";


if ($client->IsAuthenticated()) {
   my $msgct;


   $client->select("INBOX");
   $msgct = $client->unseen_count||'0';
   print "$msgct\n";
}


$client->logout();



```

---

### Post by c2tarun on 2013-03-03
bump

---

