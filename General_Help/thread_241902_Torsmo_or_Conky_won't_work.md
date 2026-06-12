---
title: "Torsmo or Conky won't work?"
date: 2006-08-22
forum: General Help
---

### Post by sean_ on 2006-08-22
Hey guys, when I tried to compile Torsmo I got this error: ```
checking for X... no
Sorry, X is very much needed

```

and with Conky I get this: ```
sean@Berserk:~$ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
sean@Berserk:~$ conky
Conky: can't parse X color 'hotpink'
Conky: can't parse X color 'white'
Conky: can't parse X color 'black'
Conky: can't parse X color 'black'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'red'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
^[[5~^[[5~
Conky: drawing to subwindow of root window (e00064)
Conky: drawing to double buffer
conky
Killed
sean@Berserk:~$
sean@Berserk:~$ conky
Conky: can't parse X color 'hotpink'
Conky: can't parse X color 'white'
Conky: can't parse X color 'black'
Conky: can't parse X color 'black'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'red'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: drawing to subwindow of root window (e00064)
Conky: drawing to double buffer
Conky: received SIGINT or SIGTERM to terminate. bye!

```
I did ```
sudo apt-get install conky
``` then did the lines from that point, this is what I get for Torsmo, then Conky.

And I do have build-essential, I read another thread and someone asked if they did or not.

---

### Post by sean_ on 2006-08-23
Nobody has replied to this thread. Please help me.

---

### Post by Tamihania on 2006-08-23
...ok - so for the first - it seems you have quite old version of conky... ;)
if you want something more "up-to-date" click [here]("http://forum.osx86project.org/index.php?showtopic=20799")

for the second - it seems that you are using Gnome where Nautilus rules desktop - so it could be good to check if in your .conkyrc file (/home/yourusername/.conkyrc) conky is drawn to its own window:

> # Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar,sticky
background yes

You can add then:

> own_window_transparent yes

There are some very good tutorials here on forum in Howto's section.

I hope it will help you a bit,

tami :)

---

### Post by sean_ on 2006-08-23
Okay, I went to the link you downloaded and that didn't come with .conkyrc. It said ```
sean@Berserk:~$ conky
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: desktop window (e00064) is subwindow of root window (52)
Conky: drawing to desktop window
Conky: drawing to single buffer
Conky: received SIGINT or SIGTERM to terminate. bye!

```

And the screenshot is [IMG]http://71.139.0.188:23456/DesktopShot.png[/IMG] Please help :x

---

### Post by taurus on 2006-08-23
List the content of ~/.conkyrc here then...

```

more ~/.conkyrc

```

---

### Post by Tamihania on 2006-08-24
Please, follow those steps:
1. Go to your /home/sean/ directory and open .conkyrc file => you can do this from GUI (by clicking) or in Terminal/Console:

> more /home/sean/.conkyrc 
[I hope that your home directory is called "sean" - so you can just copy and paste it  ;) ]

2. Check if you have the lines:

> # Create own window instead of using desktop (required in nautilus)
own_window yes 
in the file. If not - add it to the file

3. If it will not help, go to this page and read part III of the tutorial about setting up conky:

[Tutorial]("http://www.ubuntuforums.org/showthread.php?t=125084&highlight=conky+weather")

4. The examples of .conkyrc are [here]("http://www.ubuntuforums.org/showthread.php?t=205865&page=3")
and [here]("http://knowledge76.com/index.php/Light-weight_System_Monitor")

(you can simply try them out by copying and pasting them into your .conkyrc - one at the time, of course ;))

5.If this all will still not help - please tell us:
a)what DE are you running? (Gnome, KDE, other...?)
b)show us your .conkyrc here.

I hope that this will help you...

Best friendly regards and good luck wishes,

tami

---

### Post by sean_ on 2006-08-24
Uhhh.. I said I don't have a .conkyrc file because the extractor didn't come with it..

---

### Post by Ramses de Norre on 2006-08-24
This one works for me: 
```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

##Removed from TEXT field
##$stippled_hr
##$color$stippled_hr
##${color lightgrey}Temperatures:
## CPU:$color ${i2c temp 2}C${color grey} - MB:$color ${i2c temp 1}C
##${color #88aadd}MPD: ${alignc}$mpd_artist - $mpd_title
##${color #88aadd}$mpd_bar
##${color #88aadd}${alignc}$mpd_status

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
on_bottom yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 35

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color black} $nodename - $sysname $kernel on $machine

${color black}Uptime:${color black} $uptime ${color black}- Load:${color black} $loadavg
${color black}CPU Usage:${color #cc2222} $cpu% ${cpubar}
${color red}${cpugraph 0000ff 00ff00}
${color black}RAM Usage:${color black} $mem/$memmax - $memperc% ${membar}
${color black}Swap Usage:${color black} $swap/$swapmax - $swapperc% ${swapbar}
${color black}Processes:${color black} $processes  ${color black} Running:${color black} $running_processes

${color black}Networking:
 Down:${color black} ${downspeed ath0} k/s${color black} ${offset 80}Up:${color black} ${upspeed ath0} k/s
${color #0000ff}${downspeedgraph ath0 32,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph ath0 32,150 0000ff ff0000}
${color black}File systems:
 / ${color black} ${fs_used /}/${fs_size /} ${fs_bar /}
 /home ${color black} ${fs_used /home}/${fs_size /home} ${fs_bar /home}
 /mnt/hda1 ${color black} ${fs_used /mnt/hda1}/${fs_size /mnt/hda1} ${fs_bar /mnt/hda1}
 /media/hda2 ${color black} ${fs_used /media/hda2}/${fs_size /media/hda2} ${fs_bar /media/hda2}
 /media/hda3 ${color black} ${fs_used /media/hda3}/${fs_size /media/hda3} ${fs_bar /media/hda3}

${color black}Name              PID     CPU%   MEM%
${color #cc2222} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color black} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color black} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color black} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color black}Mem usage
${color #cc2222} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color black} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color black} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color black} ${tail /var/log/apache/access.log 10 30}

```
I've changed quite a lot of things from the default installed file.

---

### Post by sean_ on 2006-08-24
Okay that helped me a bit. Less errors.

Now my errors are:
```
Conky: desktop window (1000066) is subwindow of root window (137)
Conky: drawing to desktop window
Conky: drawing to single buffer

```

---

### Post by sean_ on 2006-08-24
Okay something is really wrong with my X.

I tried to ./configure conky from the tar.gz and I got this error:

```
sean@Berserk:~/Desktop/conky-1.4.2$ ./configure --prefix=/usr --enable-xft --ena ble-mpd --enable-seti --enable-double-buffer --enable-own-window --enable-proc-u ptime
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.17.2... yes
checking for XMMS... checking for XMMS... checking for BMP... checking for AUDAC IOUS... checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for iconv declaration...
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, ch ar * *outbuf, size_t *outbytesleft);
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for X... no
checking for XdbeQueryExtension in -lXext... no
configure: error: something went wrong when checking for Xdbe (double buffer ext ension)

```

---

### Post by sean_ on 2006-08-25
87 views and 9 replies... Please help me......

---

### Post by Tamihania on 2006-08-25
...hm - it seems that nothing is really wrong - You simply do not have dbe enabled - that's why you've got the message about not loading Xdbe probably. Have you read the links I've sent you?...

You say you do not have .conkyrc file - it's not a big deal neither - you can easily create it in your home directory:

create an empty file called .conkyrc-->open it and paste f.i. the file sent  to you here by Ramses de Norre --> save it - and that's all - then you can "tweak" it to your taste ;)

Another examples of such files are [here]("http://conky.sourceforge.net/screenshots.html")

and [here]("http://tamihania.googlepages.com/conkyfile")

is mine used while I was on Gnome (click on "screenies and wallpapers" in my sig to see it in action)...

To load dbe you have to edit your xorg.conf file - all about it is in the links I've sent you earlier...

I'm sorry I cannot help you more.

tami

---

### Post by Tamihania on 2006-08-25
PS. To load dbe (double buffering):
> $ gksudo gedit /etc/X11/xorg.conf

and add Load "dbe" like this:

> Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
    Load    "dbe"

tami

---

### Post by Ramses de Norre on 2006-08-25
And about the ./configure output: ```
sudo aptitude install fortran-compiler fortran77-compiler fortran95-compiler gfortran gfortran-4.0
``` and try it again.

---

### Post by Kashirigi on 2006-08-25
I think there's a .deb for the newest conky in this thread:
[http://www.ubuntuforums.org/showthread.php?t=205865](http://www.ubuntuforums.org/showthread.php?t=205865)

It will also give you a great number of tips on how to get conky working with whichever desktop environment you happen to be using.

---

