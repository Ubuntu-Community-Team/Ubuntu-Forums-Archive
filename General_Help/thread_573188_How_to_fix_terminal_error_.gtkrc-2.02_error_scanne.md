---
title: "How to fix terminal error .gtkrc-2.0:2: error: scanner: unterminated string constant"
date: 2007-10-11
forum: General Help
---

### Post by trinireddman on 2007-10-11
I tried to install envy on my Feisty64 but it refused because of dependences then I installed guake with no problems,it ask me to overwrite my original file(can't remember what that was now) but I didn't and it worked.Now I have a problem with my terminal and guake where if i start a program from the terminal i get " /home/###/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style' ".I'm not getting a problem with the program its just annoying to look at ,hope nothing is being broken.

---

### Post by geraldm on 2007-10-11
The message is stating that there is a parsing error in that file.
Use the manpage for that program to try to identify the error.

The message will go away after you fix that string constant that is in error.
Usually there is a quote to begin a string constant, and a matching quote at the end.
Possibly you are missing a quote, so look for it.

Gerald

---

### Post by trinireddman on 2007-10-12
If I enter exaile in my terminal this is what I get:
anthony@anthony-laptop:~$ exaile
/home/anthony/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
Plugins 'LibNotify Plugin' version '0.1' loaded successfully
Plugins 'Sound Juicer' version '0.1.1' loaded successfully
Plugins 'Shoutcast Radio' version '0.2' loaded successfully
Plugins 'Streamripper!' version '0.1' loaded successfully
Plugins 'Did You Know' version '0.4' loaded successfully
Plugins 'Desktop Cover' version '0.2' loaded successfully
Plugins 'AWN' version '0.7.2' loaded successfully
Plugins 'Resume Playback' version '0.2' loaded successfully
Plugins 'Music Sharing' version '0.7' loaded successfully
Plugins 'Mini Mode' version '0.4.1' loaded successfully
Plugins 'No Taskbar Entry' version '0.1' loaded successfully
Plugins 'Update Notifier' version '0.2' loaded successfully
Plugins 'Alarm Clock' version '0.1' loaded successfully
Created db for thread Thread-2
{'Thread-2': <sqlite3.Connection object at 0x149a390>}
Closed db for thread Thread-2
Using multimedia keys from: gnome
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/anthony/.exaile/saved/playlist0000.m3u
Last playlist loaded
Warning: Gstreamer equalizer element not found, please install the latest gst-plugins-bad package
updated plays 1, rating 1
Loading page 0
Exception in thread Thread-6:
Traceback (most recent call last):
  File "threading.py", line 460, in __bootstrap
    self.run()
  File "threading.py", line 440, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/home/anthony/.exaile/plugins/updates.py", line 28, in start_thread
    urllib.urlopen('http://exaile.org/current_version.txt').read().split('.'))
ValueError: invalid literal for int() with base 10: '11b\n'

next track was reported as  The Internet Is For Porn from Avenue Q by Original Broadway Cast
updated plays 1, rating 1
next track was reported as  Mix Tape from Avenue Q by Original Broadway Cast
updated plays 1, rating 1

I'm not seeing any quote at the begining or ending.

This noob is lost.

---

### Post by teqen on 2008-02-24
> error: scanner: unterminated string constant - e.g. **`style'**

I think that this is where You should look for a quote :)

---

### Post by David_1cog on 2008-03-28
The reason is probably because you followed bad advice for removing menu delay (as I did), e.g. [http://lifehacker.com/software/linux-tip/speed-up-gnome-menu-269934.php](http://lifehacker.com/software/linux-tip/speed-up-gnome-menu-269934.php).  There are many sites that tell you to create ~/.gtkrc-2.0 and then add 'gtk-menu-popup-delay = 0"| tee -a .gtkrc-2.0'.  That's wrong.

It should be either:

  * create file  ~/.gtkrc-2.0 and add 'gtk-menu-popup-delay = 0'

or

  * run in terminal 'echo "gtk-menu-popup-delay = 0"| tee -a .gtkrc-2.0'

Either delete  ~/.gtkrc-2.0 and do one of the two methods above, or edit the file as needed.

---

