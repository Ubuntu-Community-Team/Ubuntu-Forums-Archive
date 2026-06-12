---
title: "Conky Keeps Crashing"
date: 2012-11-05
forum: General Help
---

### Post by wkatastrof on 2012-11-05
Hello,

My conky keeps crashing and I have to restart it quite often. I am not sure if there's any log to look at. It didn't used to crash all the time, but has been now for a while, so I can't give an accurate time frame.

Here's my ubuntu version:
3.0.0-26-generic #43-Ubuntu SMP Tue Sep 25 17:20:50 UTC 2012 i686 i686 i386 GNU/Linux

Here's my conky config:

```
# conky configuration
#
# The list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.
#
# For ideas about how to modify conky, please see:
# http://crunchbanglinux.org/forums/topic/59/my-conky-config/
#
# For help with conky, please see:
# http://crunchbanglinux.org/forums/topic/2047/conky-help/
#
# Enjoy! :)
##############################################
#  Settings
##############################################
background yes
use_xft yes
xftfont sans:size=9
xftalpha 1
update_interval 1.0
total_run_times 0
own_window no
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 260
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color d8d8d8
default_shade_color 000000
default_outline_color d9d7d6
alignment top_right
gap_x 12
gap_y 24
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
##############################################
#  Output
##############################################
TEXT
S Y S T E M    I N F O


Host:$alignr$nodename
Uptime:$alignr$uptime
RAM:$alignr$mem/$memmax
$membar
Swap usage:$alignr$swap/$swapmax
$swapbar
Disk usage:$alignr${fs_used /}/${fs_size /}
${fs_bar /}
CPU usage:$alignr${cpu cpu0}%
${cpugraph cpu0}

NETWORK ${hr}
Down: ${downspeedf wlan0} K/s $alignr ${totaldown wlan0}
${downspeedgraph wlan0}
Up: ${upspeedf wlan0} K/s $alignr ${totalup wlan0}
${upspeedgraph wlan0}

${color white}ROANOKE, VA Weather ${hr 2}$color${execi 600 sh /home/wilheim/conky_weather/weather_script.sh}
${font conkyweather:size=25}${execi 600  sed -n '4p' /home/wilheim/conky_weather/weather1}${font} ${voffset -10}${execi 600 sed -n '1p' /home/wilheim/conky_weather/weather1}

${font conkyweather:size=25}${execi 600  sed -n '5p' /home/wilheim/conky_weather/weather1} ${voffset -10}${font sans:size=9} ${rss http://rss.accuweather.com/rss/liveweather_rss.asp?locCode=08901 10 item_title 1}

${font sans:size=7} ${execi 600 sed -n '2p' /home/wilheim/conky_weather/weather1}

${font conkyweather:size=25}${execi 600  sed -n '6p' /home/wilheim/conky_weather/weather1} ${voffset -10}${font sans:size=9}${rss http://rss.accuweather.com/rss/liveweather_rss.asp?locCode=24016 10 item_title 2}

${font sans:size=7} ${execi 600 sed -n '3p' /home/wilheim/conky_weather/weather1}
${font}
S H O R T C U T    K E Y S
${hr}
Alt+F2$alignr Run Dialog
Alt+F3$alignr Alt Menu
Super+Space$alignr Main Menu
Super+Tab$alignr Client Menu
# Super+t$alignr Terminal
# Super+f$alignr File Manager
# Super+e$alignr Editor
# Super+m$alignr Media Player
# Super+w$alignr Web Browser
# Super+l$alignr Lock Screen
# Super+v$alignr Volume Control
Super+x$alignr Logout
PrtSc$alignr Screenshot
```Please advise! Thanks!

---

### Post by NM5TF on 2012-11-05
I am running your code from the beginning down to your WX info..

it is the Conky on the right hand side....my own Conky is on the 
left hand side...

your code has no problems running on my machine...at least down
to the WX part...I use a different network connection than you
do so it doesn't show up on my machine...

you might consider upgrading to the latest Kernel 3.2.0-32-generic
to see if that will help....

or you might try here for Conky help:

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)


Tommy

---

### Post by 28c64 on 2012-11-05
Can you try running conky from your terminal, and give us the output when it crashes?

---

### Post by wkatastrof on 2012-11-05
```
wilheim@tinydada-u:~$ conky
Conky: forked to background, pid is 1869
wilheim@tinydada-u:~$ 
Conky: desktop window (101) is root window
Conky: drawing to desktop window
Conky: drawing to double buffer
wget: no process found
--2012-11-05 19:10:49--  http://rss.accuweather.com/rss/liveweather_rss.asp?locCode=08901
Resolving rss.accuweather.com... 174.35.36.18, 174.35.35.22
Connecting to rss.accuweather.com|174.35.36.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2858 (2.8K) [text/xml]
Saving to: `/home/wilheim/conky_weather/weather'

100%[=================================================>] 2,858       --.-K/s   in 0s      

2012-11-05 19:10:50 (31.8 MB/s) - `/home/wilheim/conky_weather/weather' saved [2858/2858]

*** longjmp causes uninitialized stack frame ***: conky terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x45)[0x9c4015]
/lib/i386-linux-gnu/libc.so.6(+0xecf8a)[0x9c3f8a]
/lib/i386-linux-gnu/libc.so.6(__longjmp_chk+0x4b)[0x9c3efb]
/usr/lib/i386-linux-gnu/libcurl-gnutls.so.4(+0x9285)[0xec7285]
[0xcbc400]
[0xcbc416]
/lib/i386-linux-gnu/libc.so.6(__select+0x61)[0x9a7611]
conky[0x8078860]
conky[0x804dc32]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0x8f0113]
conky[0x804dc5d]
======= Memory map: ========
00110000-00241000 r-xp 00000000 08:02 5246920    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00241000-00242000 ---p 00131000 08:02 5246920    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00242000-00243000 r--p 00131000 08:02 5246920    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00243000-00245000 rw-p 00132000 08:02 5246920    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00245000-00246000 rw-p 00000000 00:00 0 
00246000-00249000 r-xp 00000000 08:02 4467262    /lib/i386-linux-gnu/libdl-2.13.so
00249000-0024a000 r--p 00002000 08:02 4467262    /lib/i386-linux-gnu/libdl-2.13.so
0024a000-0024b000 rw-p 00003000 08:02 4467262    /lib/i386-linux-gnu/libdl-2.13.so
0024b000-0027d000 r-xp 00000000 08:02 5246907    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
0027d000-0027e000 ---p 00032000 08:02 5246907    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
0027e000-0027f000 r--p 00032000 08:02 5246907    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
0027f000-00280000 rw-p 00033000 08:02 5246907    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
00280000-002bd000 r-xp 00000000 08:02 4456535    /lib/i386-linux-gnu/libpcre.so.3.12.1
002bd000-002be000 r--p 0003c000 08:02 4456535    /lib/i386-linux-gnu/libpcre.so.3.12.1
002be000-002bf000 rw-p 0003d000 08:02 4456535    /lib/i386-linux-gnu/libpcre.so.3.12.1
002bf000-002cc000 r-xp 00000000 08:02 5246955    /usr/lib/i386-linux-gnu/liblber-2.4.so.2.7.0
002cc000-002cd000 r--p 0000c000 08:02 5246955    /usr/lib/i386-linux-gnu/liblber-2.4.so.2.7.0
002cd000-002ce000 rw-p 0000d000 08:02 5246955    /usr/lib/i386-linux-gnu/liblber-2.4.so.2.7.0
002ce000-002e5000 r-xp 00000000 08:02 5246962    /usr/lib/i386-linux-gnu/librtmp.so.0
002e5000-002e6000 r--p 00016000 08:02 5246962    /usr/lib/i386-linux-gnu/librtmp.so.0
002e6000-002e7000 rw-p 00017000 08:02 5246962    /usr/lib/i386-linux-gnu/librtmp.so.0
002e7000-002e9000 r-xp 00000000 08:02 5246911    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
002e9000-002ea000 r--p 00001000 08:02 5246911    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
002ea000-002eb000 rw-p 00002000 08:02 5246911    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
002eb000-002f0000 r-xp 00000000 08:02 5246913    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
002f0000-002f1000 r--p 00004000 08:02 5246913    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
002f1000-002f2000 rw-p 00005000 08:02 5246913    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
002f2000-002f4000 r-xp 00000000 08:02 4456492    /lib/i386-linux-gnu/libcom_err.so.2.1
002f4000-002f5000 r--p 00001000 08:02 4456492    /lib/i386-linux-gnu/libcom_err.so.2.1
002f5000-002f6000 rw-p 00002000 08:02 4456492    /lib/i386-linux-gnu/libcom_err.so.2.1
002f6000-002f9000 r-xp 00000000 08:02 4456805    /lib/i386-linux-gnu/libgpg-error.so.0.8.0
002f9000-002fa000 r--p 00002000 08:02 4456805    /lib/i386-linux-gnu/libgpg-error.so.0.8.0
002fa000-002fb000 rw-p 00003000 08:02 4456805    /lib/i386-linux-gnu/libgpg-error.so.0.8.0
002fb000-00317000 r-xp 00000000 08:02 4456556    /lib/libtinfo.so.5.9
00317000-00319000 r--p 0001b000 08:02 4456556    /lib/libtinfo.so.5.9
00319000-0031a000 rw-p 0001d000 08:02 4456556    /lib/libtinfo.so.5.9
0031a000-0031c000 r-xp 00000000 08:02 4456809    /lib/i386-linux-gnu/libkeyutils.so.1.3
0031c000-0031d000 r--p 00001000 08:02 4456809    /lib/i386-linux-gnu/libkeyutils.so.1.3
0031d000-0031e000 rw-p 00002000 08:02 4456809    /lib/i386-linux-gnu/libkeyutils.so.1.3
0031e000-00320000 r-xp 00000000 08:02 4460581    /lib/libnss_mdns4_minimal.so.2
00320000-00321000 r--p 00001000 08:02 4460581    /lib/libnss_mdns4_minimal.so.2
00321000-00322000 rw-p 00002000 08:02 4460581    /lib/libnss_mdns4_minimal.so.2
00322000-00327000 r-xp 00000000 08:02 4460367    /lib/i386-linux-gnu/libnss_dns-2.13.so
00327000-00328000 r--p 00004000 08:02 4460367    /lib/i386-linux-gnu/libnss_dns-2.13.so
00328000-00329000 rw-p 00005000 08:02 4460367    /lib/i386-linux-gnu/libnss_dns-2.13.so
0032a000-0032c000 r-xp 00000000 08:02 5255896    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
0032c000-0032d000 r--p 00001000 08:02 5255896    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
0032d000-0032e000 rw-p 00002000 08:02 5255896    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
0032e000-00369000 r-xp 00000000 08:02 5246943    /usr/lib/i386-linux-gnu/libgssapi_krb5.so.2.2
00369000-0036a000 ---p 0003b000 08:02 5246943    /usr/lib/i386-linux-gnu/libgssapi_krb5.so.2.2
0036a000-0036b000 r--p 0003b000 08:02 5246943    /usr/lib/i386-linux-gnu/libgssapi_krb5.so.2.2
0036b000-0036c000 rw-p 0003c000 08:02 5246943    /usr/lib/i386-linux-gnu/libgssapi_krb5.so.2.2
0036c000-0037f000 r-xp 00000000 08:02 4456496    /lib/i386-linux-gnu/libresolv-2.13.so
0037f000-00380000 r--p 00012000 08:02 4456496    /lib/i386-linux-gnu/libresolv-2.13.so
00380000-00381000 rw-p 00013000 08:02 4456496    /lib/i386-linux-gnu/libresolv-2.13.so
00381000-00383000 rw-p 00000000 00:00 0 
00387000-0039b000 r-xp 00000000 08:02 5255864    /usr/lib/i386-linux-gnu/libXft.so.2.2.0
0039b000-0039c000 r--p 00013000 08:02 5255864    /usr/lib/i386-linux-gnu/libXft.so.2.2.0
0039c000-0039d000 rw-p 00014000 08:02 5255864    /usr/lib/i386-linux-gnu/libXft.so.2.2.0
0039d000-003a8000 r-xp 00000000 08:02 4467267    /lib/i386-linux-gnu/libnss_files-2.13.so
003a8000-003a9000 r--p 0000a000 08:02 4467267    /lib/i386-linux-gnu/libnss_files-2.13.so
003a9000-003aa000 rw-p 0000b000 08:02 4467267    /lib/i386-linux-gnu/libnss_files-2.13.so
003ae000-003cb000 r-xp 00000000 08:02 5246915    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
```

---

### Post by wkatastrof on 2012-11-05
It looks like there is a problem with the program named curl at this link:

[ [http://stackoverflow.com/questions/9191668/error-longjmp-causes-uninitialized-stack-frame](http://stackoverflow.com/questions/9191668/error-longjmp-causes-uninitialized-stack-frame) ]

I'm assuming curl is being used for the weather script that I have.

I'm not sure what they mean by calling ' curl_easy_setopt(curl, CURLOPT_NOSIGNAL, 1) ' to fix it.

Any ideas?

---

### Post by NM5TF on 2012-11-06
the problem appears to be in the weather_script.sh

can you post the contents???

---

### Post by wkatastrof on 2012-11-06
Here is the weather_script.sh. It looks like it uses a lot of SED which seems like a complex program to learn. I know the script downloads the accuweather rss feed into a text file called 'weather' and then parses the info that is needed for the conky display into a text file called 'weather1'.

Sorry I don't have a link to the original forum post where I got the weather script from.

```
#!/bin/bash
killall wget
wget -O /home/wilheim/conky_weather/weather "http://rss.accuweather.com/rss/liveweather_rss.asp?locCode=24016"
sed -i 's/&/\n/g' /home/wilheim/conky_weather/weather
sed -i 's/>/\n/g' /home/wilheim/conky_weather/weather
sed -i 's/</\n/g' /home/wilheim/conky_weather/weather
egrep -i 'high:|Currently:' /home/wilheim/conky_weather/weather>/home/wilheim/conky_weather/weather1
sed -i 's/\//\n/g' /home/wilheim/conky_weather/weather
grep -i _31x31.gif /home/wilheim/conky_weather/weather>>/home/wilheim/conky_weather/weather1 
sed -i 's/_/\n/g' /home/wilheim/conky_weather/weather1
sed -i "/.gif/d" /home/wilheim/conky_weather/weather1
a=`sed -n '4p' /home/wilheim/conky_weather/weather1`
if test "$a" = "01"
then sed -i '4s/01/a/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "02"
then sed -i '4s/02/b/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "03"
then sed -i '4s/03/c/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "04"
then sed -i '4s/04/d/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "05"
then sed -i '4s/05/c/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "06"
then sed -i '4s/06/d/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "07"
then sed -i '4s/07/e/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "08"
then sed -i '4s/08/f/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "11"
then sed -i '4s/11/0/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "12"
then sed -i '4s/12/h/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "13"
then sed -i '4s/13/g/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "14"
then sed -i '4s/14/g/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "15"
then sed -i '4s/15/n/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "16"
then sed -i '4s/16/k/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "17"
then sed -i '4s/17/k/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "18"
then sed -i '4s/18/j/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "19"
then sed -i '4s/19/p/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "20"
then sed -i '4s/20/o/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "21"
then sed -i '4s/21/o/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "22"
then sed -i '4s/22/q/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "23"
then sed -i '4s/23/o/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "24"
then sed -i '4s/24/r/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "25"
then sed -i '4s/25/w/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "26"
then sed -i '4s/26/w/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "29"
then sed -i '4s/29/x/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "30"
then sed -i '4s/30/5/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "31"
then sed -i '4s/31/r/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "32"
then sed -i '4s/32/6/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "33"
then sed -i '4s/33/A/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "34"
then sed -i '4s/34/B/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "35"
then sed -i '4s/35/C/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "36"
then sed -i '4s/36/D/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "37"
then sed -i '4s/37/B/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "38"
then sed -i '4s/38/C/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "39"
then sed -i '4s/39/G/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "40"
then sed -i '4s/40/G/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "41"
then sed -i '4s/41/K/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "42"
then sed -i '4s/42/K/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "43"
then sed -i '4s/43/O/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "44"
then sed -i '4s/44/O/C/g' /home/wilheim/conky_weather/weather1
fi;
a=`sed -n '5p' /home/wilheim/conky_weather/weather1`
if test "$a" = "01"
then sed -i '5s/01/a/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "02"
then sed -i '5s/02/b/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "03"
then sed -i '5s/03/c/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "04"
then sed -i '5s/04/d/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "05"
then sed -i '5s/05/c/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "06"
then sed -i '5s/06/d/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "07"
then sed -i '5s/07/e/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "08"
then sed -i '5s/08/f/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "11"
then sed -i '5s/11/0/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "12"
then sed -i '5s/12/h/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "13"
then sed -i '5s/13/g/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "14"
then sed -i '5s/14/g/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "15"
then sed -i '5s/15/n/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "16"
then sed -i '5s/16/k/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "17"
then sed -i '5s/17/k/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "18"
then sed -i '5s/18/j/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "19"
then sed -i '5s/19/p/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "20"
then sed -i '5s/20/o/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "21"
then sed -i '5s/21/o/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "22"
then sed -i '5s/22/q/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "23"
then sed -i '5s/23/o/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "24"
then sed -i '5s/24/r/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "25"
then sed -i '5s/25/w/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "26"
then sed -i '5s/26/w/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "29"
then sed -i '5s/29/x/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "30"
then sed -i '5s/30/5/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "31"
then sed -i '5s/31/r/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "32"
then sed -i '5s/32/6/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "33"
then sed -i '5s/33/A/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "34"
then sed -i '5s/34/B/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "35"
then sed -i '5s/35/C/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "36"
then sed -i '5s/36/D/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "37"
then sed -i '5s/37/B/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "38"
then sed -i '5s/38/C/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "39"
then sed -i '5s/39/G/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "40"
then sed -i '5s/40/G/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "41"
then sed -i '5s/41/K/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "42"
then sed -i '5s/42/K/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "43"
then sed -i '5s/43/O/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "44"
then sed -i '5s/44/O/C/g' /home/wilheim/conky_weather/weather1
fi;
a=`sed -n '6p' /home/wilheim/conky_weather/weather1`
if test "$a" = "01"
then sed -i '6s/01/a/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "02"
then sed -i '6s/02/b/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "03"
then sed -i '6s/03/c/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "04"
then sed -i '6s/04/d/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "05"
then sed -i '6s/05/c/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "06"
then sed -i '6s/06/d/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "07"
then sed -i '6s/07/e/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "08"
then sed -i '6s/08/f/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "11"
then sed -i '6s/11/0/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "12"
then sed -i '6s/12/h/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "13"
then sed -i '6s/13/g/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "14"
then sed -i '6s/14/g/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "15"
then sed -i '6s/15/n/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "16"
then sed -i '6s/16/k/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "17"
then sed -i '6s/17/k/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "18"
then sed -i '6s/18/j/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "19"
then sed -i '6s/19/p/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "20"
then sed -i '6s/20/o/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "21"
then sed -i '6s/21/o/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "22"
then sed -i '6s/22/q/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "23"
then sed -i '6s/23/o/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "24"
then sed -i '6s/24/r/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "25"
then sed -i '6s/25/w/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "26"
then sed -i '6s/26/w/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "29"
then sed -i '6s/29/x/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "30"
then sed -i '6s/30/5/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "31"
then sed -i '6s/31/r/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "32"
then sed -i '6s/32/6/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "33"
then sed -i '6s/33/A/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "34"
then sed -i '6s/34/B/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "35"
then sed -i '6s/35/C/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "36"
then sed -i '6s/36/D/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "37"
then sed -i '6s/37/B/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "38"
then sed -i '6s/38/C/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "39"
then sed -i '6s/39/G/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "40"
then sed -i '6s/40/G/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "41"
then sed -i '6s/41/K/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "42"
then sed -i '6s/42/K/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "43"
then sed -i '6s/43/O/g' /home/wilheim/conky_weather/weather1
elif test "$a" = "44"
then sed -i '6s/44/O/C/g' /home/wilheim/conky_weather/weather1
fi;
```

---

### Post by wkatastrof on 2012-11-06
Thanks for everyone's help. It looks like I found the issue after going through my conky config and weather_script.sh. I had moved locations, but only changed the zip code in 1 of four locations in both files!

I'm not sure what problems this was causing, but I've been running conky for 2+ hrs and it hasn't crashed yet.

Unfortunately, this means I've been reading the wrong weather report for about 2 months!

If it starts crashing again... I will be back!

---

### Post by NM5TF on 2012-11-06
WOW!!!

that looks REALLY complicated & possibly redundant...:confused:

I assume that it gives you a 10-12 day forecast for your
area thru AccuWeather via a RSS feed....

I have a script that does very much the same thing, but seems
to be way simpler....and it works!!!:)

it is an XML feed direct from the Nat'l WX service....you would
have to enter the correct info for your area, but that is easy...

if you are interested in seeing it let me know...:P

here is a screenshot of the output...on the right hand side....

---

### Post by wkatastrof on 2012-11-07
> **NM5TF said:**
> WOW!!!

that looks REALLY complicated & possibly redundant...:confused:

I assume that it gives you a 10-12 day forecast for your
area thru AccuWeather via a RSS feed....

I have a script that does very much the same thing, but seems
to be way simpler....and it works!!!:)

it is an XML feed direct from the Nat'l WX service....you would
have to enter the correct info for your area, but that is easy...

if you are interested in seeing it let me know...:P

here is a screenshot of the output...on the right hand side....

That looks really nice, but I hear that the Nat'l WX service isn't free? I remember thats why I chose Accuweather. Also... unfortunately, it only shows today's forcast and the next day's!

---

