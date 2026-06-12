---
title: "Linux Octoshape Plugin"
date: 2008-03-27
forum: General Help
---

### Post by Jameo on 2008-03-27
Hi All,

I'm new to Linux, but am trying to pick it up as soon as possible, so any help will be greatly appreciated! I am running Gnome 2.20.1 with Ubuntu 7.10

I am currently trying to install the octoshape plugin for mplayer, without any great success! I have followed the information provided in:

[http://www.octoshape.com/plugin/linux.asp](http://www.octoshape.com/plugin/linux.asp)
[http://ubuntuforums.org/showthread.php?t=459636&highlight=JavaExec](http://ubuntuforums.org/showthread.php?t=459636&highlight=JavaExec)
[https://help.ubuntu.com/community/Octoshape](https://help.ubuntu.com/community/Octoshape)

I have java-6-sun-1.6.0.00 and the w32 codecs installed, and have used the following command lines:

```
wget -P ~/Desktop http://www.octoshape.com/files/octosetup-linux_i386.bin

chmod +x ~/Desktop/octosetup-linux_i386.bin

cd ~/Desktop

./octosetup-linux_i386.bin
```

And add on was successfully installed.

The location of my libjvm.so is:

/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so

And a setup.cfg file was created with the command line

```
JavaExec=/usr/lib/jvm/ia32-java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so
```

and saved in the Octoshape directory.

Upon executing the command line

```
desktop:~/Desktop/octoshape$ ./Octoshapeclient -url:RTP.800
```

I get the following error message:

```
Could not execute JVM: When loading library /usr/lib/...: /usr/lib/...: cannot open shared object file: No such file or directory
```

Wheres this shared object file then? I'm sure iI'm making a silly mistake, so sorry if it turns out to be glaringly obvious!

Thanks in advance

---

### Post by Jameo on 2008-03-27
Sorry, but *bump*

---

### Post by jrib on 2008-03-27
oops, I get that error too now, don't worry :)  I'll look into it after my classes and let you know.

[http://www.octoshape.com/plugin/linux.asp](http://www.octoshape.com/plugin/linux.asp) suggests it now uses setup.xml, see the syntax there.  Feel free to update wiki if you understand, otherwise I'll try to do it later.

---

### Post by Jameo on 2008-03-27
Hi Jason,

Thanks for getting back to me so quickly. I have just realised the same thing. Changed the setup.xml to link to my libjvm.so and things seem to be working, however it appears that I still need to set a default player (I have mplayer, but do not think its set as default), the following now appears in my terminal:

```
craig@craig-desktop:~/Desktop/octoshape$ ./OctoshapeClient -url:PARADISE.stream1_mp3
Status: Reading configuration
Status: Contacts update server
Status: Processes updates
Status: Finishing updater
Status: Reading configuration
Status: Checks system setup
Status: Registering plugins.
Status: Ready to play
Status: Ready to play
Status: Playing
Info  : No media player connected
Status: Ready to play

```

Cheers again mate

---

### Post by Jameo on 2008-03-27
Unfortunalty I am still having trouble setting a default player. My setup.xml now looks like this

```
<e JavaExec="/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so"
    TempID="Asep_Knujdepsa_04721432"
    PlayerExec="mplayer $url" />
```

And i am still getting the error message

```
Info  : No media player connected
```

I guess I still need to add more to the bottom line of code. I'm a bit confused because i though the client was supposed to mplayer as the default player on its first run?

Cheers mate

---

### Post by jrib on 2008-03-28
After creating setup.xml correctly it is working here.  mplayer opens automatically.  To troubleshoot, create ~/debugger with the following contents:

```

#!/bin/sh

echo $* >> ~/debugger_output

```

Make it executable with ```
chmod +x ~/debugger
```

and change PlayerExec in setup.xml to ```
PlayerExec="/home/jrib/debugger $url"
``` (replacing "jrib" with your username of course).

Then run ```
./OctoshapeClient -url:RTP.800
``` and let it get to "Status: Playing".
```
% ./OctoshapeClient -url:RTP.800
Status: Reading configuration
Status: Contacts update server
Status: Processes updates
Status: Finishing updater
Status: Reading configuration
Status: Checks system setup
Status: Registering plugins.
Status: Ready to play
Status: Ready to play
Status: Playing

```

Then in a new terminal, check ~/debugger_output for a url and pass it to mplayer.  For example:
```
% cat ~/debugger_output
http://127.0.0.1:6498/ms/asf/RTP.800/RTP800?MSWMExt=.asf
% mplayer 'http://127.0.0.1:6498/ms/asf/RTP.800/RTP800?MSWMExt=.asf'

```

Anyway, hopefully that connects and we can continue from there.

---

### Post by aquilax on 2008-05-23
If you get only sound (as I did), You skip the ~/debugger part. Start the OctoshapeClient and when you hear the sound use 

```
ps -aux | grep mpalyer
```

You'll get two rows with the local URL of the stream. Use one of them to start mplayer or xine with it.

---

