---
title: "Problem connecting to channels with sopcast player"
date: 2018-05-09
forum: General Help
---

### Post by saikari on 2018-05-09
Hi,

I have Ubuntu 16.04 and have installed sopcast from ppa:linuxthebest.net/sopcast
However, I am incapable of viewing any channel. Whenever I try to connect, nothing gets displayed and there is just a message at the bottom of the sopcast player window which says "Connecting" then "Retrying channel". This goes on indefinetely.
From looking on the forum for similar issues, one of the causes pointed out is that library /libstdc++.so.5 is absent or misplaced. However, I seem to have the library in the right place. 
Here is the result of my ls command for the library:

 ls -l /usr/lib/libstdc++.so.*
lrwxrwxrwx 1 root root 38 may  6 21:35 /usr/lib/libstdc++.so.5 -> /usr/lib/i386-linux-gnu/libstdc++.so.5
lrwxrwxrwx 1 root root 42 may  6 21:35 /usr/lib/libstdc++.so.5.0.7 -> /usr/lib/i386-linux-gnu/libstdc++.so.5.0.7
lrwxrwxrwx 1 root root 38 may  6 21:35 /usr/lib/libstdc++.so.6 -> /usr/lib/i386-linux-gnu/libstdc++.so.6
lrwxrwxrwx 1 root root 43 may  6 21:35 /usr/lib/libstdc++.so.6.0.24 -> /usr/lib/i386-linux-gnu/libstdc++.so.6.0.24

Can anyone suggest what I can do to get sopcast working?
Many thanks.

---

### Post by Antnio_Almeida on 2018-08-26
hi,

maybe a little bit late, but the problem you report is with the player itself and not the executable sp-sc (or sp-sc-auth, depending on the origin of the file).
you can still play the channels from the command line:
'sp-sc-auth sop://broker.sopcast.com:3912/150261 3908 8908 > /dev/null &'
'mpv  [http://127.0.0.1:8908/tv.asf](http://127.0.0.1:8908/tv.asf)'
i've made scripts for the channels i watch more, and just drag them to the terminal to execute and watch ( with a sleep 10 command in between to allow connection and buffer)

---

