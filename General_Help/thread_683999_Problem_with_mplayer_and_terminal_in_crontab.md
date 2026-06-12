---
title: "Problem with mplayer and terminal in crontab"
date: 2008-01-31
forum: General Help
---

### Post by xandorv on 2008-01-31
Hi guys

I have tried a lot but mplayer is simply not working with crontab
Here is my crontab

[COLOR="SeaGreen"]DISPLAY=:0.0
# m h  dom mon dow   command
35 08  * * *   echo "Hello World" 2>>testing.log 1>>testing.log
35 08  * * *   /usr/bin/mplayer -vo x11 /media/sda5/Downloads/Uncha.avi 2>>testing.log
[/COLOR]
The same command ( [COLOR="SeaGreen"]/usr/bin/mplayer -vo x11 /media/sda5/Downloads/Uncha.avi[/COLOR] ) works perfectly in the command line. :(

Here is the log file that i have created (testing.log)

[COLOR="SeaGreen"][COLOR="SeaGreen"]Hello World
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
gnome_screensaver_control()
[/COLOR]
MPlayer interrupted by signal 13 in module: init_video_codec
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

[/COLOR]
Another problem is that the first line in the crontab (echo "Hello World") doesn't display anything on the terminal. It works fine when I redirect the default output to testing.log. Also it gives no error in the log file when it doesn't echo "Hello World" on the terminal.

I have tried many many times and I am tired now. hope u guys can help. Thanks in advance.

---

