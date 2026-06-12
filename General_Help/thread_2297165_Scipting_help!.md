---
title: "Scipting help!"
date: 2015-10-01
forum: General Help
---

### Post by Terry_Baxendale on 2015-10-01
Hi All,

I need to get specific help in the way I need to get a script to work, as I have been struggling to get it to function the way required.

I need a script to execute on startup and I need it then to run a number of things, what I have done so far is this.

in  /etc/rc.local I have added the below line

sudo /bin/vlcboot.sh

To me that should execute the file vlcboot.sh I have created,

Within this, I need it to do a number of things

I need it to start, and automatically set a shutdown time for 21:00 (I think I know this)

I need it to execute a folder mount, so that a specific video can play (I know this, but we had problems with certain hardwares not liking the commands so had to use the sudo mount -a)

It then needs to copy a file from a server over to it's own hdd

once completed I need it to run the video in question.

What I have written is this

gnome-terminal
echo "video transfer"
sudo mount -a
cp -f /media/video/totem.mov /media/localvideo
echo "system shutdown confirmed"
sudo shutdown -h 21:00
echo "VLC player will start"
/usr/bin/vlc -f -R "/media/video/totem.mov" 

The reason for the echo is it would be nice to have a visual display of whats being done, so if something should fail, am able to just ask "what stage has it stopped?"

I would want the terminal to close once all completed, or at least hope that the vlc player kicks in over the terminal, then that's fine.

Am VERY new to Ubuntu, and under pressure to pull of this script idea.

The sudo shutdown works just typing it into terminal

The mount idea generally worked until for some random reason different systems for some reason wouldn't play ball and load the file as expected, using the -a command which my manager found seemed to work regardless but I have not been able to find anything on what -a does!

the /usr/bin/vlc etc works as well on it's own, it's trying to put this all together and make it work as one.

I hope I can get some help, cause am seriously sweating with worry trying to make it work!

apologies if I have placed this in the wrong place :/ general help sounded right!

Thanks for any support and help!

Terry

---

### Post by TheFu on 2015-10-01
You cannot put GUI programs into system-level scripts like rc.local. These won't work.
* gnome-terminal
* vlc

Running normal GUI programs as root (or with sudo) is a really bad idea. It is asking for problems if those tools aren't specifically designed to be  run in that way. Most are not.

Definitely do not use /etc/rc.local for anything except system-level startup stuff.  No need for sudo in this file - it is already running at root. Don't use it to run a program as your normal userid.

GUI programs should be started only as part of a login session that includes X/Windows. There are non-GUI logins, so trying to run a GUI program when there isn't a GUI will crash the program. Normally, that doesn't do any harm.

Please use "code tags" for the script.  That makes it easier to read. "Adv Reply" has a button, but the tags  can be manually  typed too.

I would do this  stuff differently.
To start a playing at login,  add the cp and playback to the autostart folder under my HOME. Different DEs support autostart  applications in a different way. 
[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html) should help if you are using Unity as the DE. I do not.

As for shutdown and mounting, the mount should just be added to the /etc/fstab. [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) The shutdown can be placed into the crontab for root or the system crontab. Be aware that crontabs and system startup scripts do not have much "environment", so be certain to follow scripting best practices. I'll put a link below.

I don't understand what the terminal launch is for? I don't believe it does anything.

When scripting, there are a number of best practices. Here is a short list: 
[http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

There are many beginning scripting guides.
* [http://www.howtogeek.com/67469/the-beginners-guide-to-shell-scripting-the-basics/](http://www.howtogeek.com/67469/the-beginners-guide-to-shell-scripting-the-basics/)
* [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)
* [http://wiki.bash-hackers.org/scripting/tutoriallist](http://wiki.bash-hackers.org/scripting/tutoriallist)

There are lots of youtube videos on this topic too. Good luck and have fun!

---

