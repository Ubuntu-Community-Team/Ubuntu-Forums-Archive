---
title: "Problems starting a server at boot up."
date: 2021-07-13
forum: General Help
---

### Post by callakskytower on 2021-07-13
Heya all.   I'm trying to run my first game server on Ubuntu 20.04.2.  I'm pretty new to this and could use some advice.

I would like to have it start at boot, and I would prefer to run it as a service.  The server start script works fine if I run it by hand through ssh, but fails to start as a service:

```
&#9679; 7dtd.service - 7 Days to Die
     Loaded: loaded (/lib/systemd/system/7dtd.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2021-07-13 01:10:41 CDT; 4h 12min ago
    Process: 910 ExecStart=/home/callak/7d2d/live-startserver.sh -configfile=live-serverconfig.xml (code=exited, status=0/SUCCESS)
    Process: 922 ExecStop=/bin/kill -s QUIT $MAINPID (code=exited, status=1/FAILURE)
   Main PID: 910 (code=exited, status=0/SUCCESS)


Jul 13 01:10:41 gameroom systemd[1]: 7dtd.service: Scheduled restart job, restart counter is at 5.
Jul 13 01:10:41 gameroom systemd[1]: Stopped 7 Days to Die.
Jul 13 01:10:41 gameroom systemd[1]: 7dtd.service: Start request repeated too quickly.
Jul 13 01:10:41 gameroom systemd[1]: 7dtd.service: Failed with result 'exit-code'.
Jul 13 01:10:41 gameroom systemd[1]: Failed to start 7 Days to Die.

```


I created a unit file in /lib/systemd/system/:
```
[Unit]
Description=7 Days to Die
After=network.target nss-lookup.target


[Service]
Type=simple
PIDFile=/run/7dtd.pid
ExecStart=/home/callak/7d2d/live-startserver.sh -configfile=live-serverconfig.xml
ExecReload=/bin/kill -s HUP $MAINPID
ExecStop=/bin/kill -s QUIT $MAINPID
Restart=always


[Install]
WantedBy=multi-user.target

```

The start up script itself is as follows:
```
#!/bin/sh
SERVERDIR=`dirname "$0"`
cd "$SERVERDIR"


PARAMS=$@


CONFIGFILE=
while test $# -gt 0
do
        if [ `echo $1 | cut -c 1-12` = "-configfile=" ]; then
                CONFIGFILE=`echo $1 | cut -c 13-`
        fi
        shift
done


if [ "$CONFIGFILE" = "" ]; then
        echo "No config file specified. Call this script like this:"
        echo "  ./startserver.sh -configfile=serverconfig.xml"
        exit 1
else
        if [ -f "$CONFIGFILE" ]; then
                echo Using config file: $CONFIGFILE
        else
                echo "Specified config file $CONFIGFILE does not exist."
                exit 1
        fi
fi


export LD_LIBRARY_PATH=.
#export MALLOC_CHECK_=0


screen -dmS 7d2d ./7DaysToDieServer.x86_64 -logfile $SERVERDIR/7DaysToDieServer_Data/output_log__`date +%Y-%m-%d__%H-%M-%S`.txt -quit -batchmode -nographics -dedicated $PARAMS

```




I have also tried to set this up as a cron event instead, the start script runs, but for some reason when I do, the server has problems reading it's configuration XML file:
```
0 0 *  *  *   root /sbin/hwclock -w   # synchronize hardware & system clock each day at 00:00 am
0 1 *  *  *    /sbin/shutdown -r +10
@reboot sh ~/7d2d/live-startserver.sh -configfile=live-startserver.sh > StartserverResult.txt

```

Any advice would be appreciated, thank you.

---

### Post by TheFu on 2021-07-13
```
screen -dmS 7d2d ./7DaysToDieServer.x86_64 -logfile $SERVERDIR/7DaysToDieServer_Data/output_log__`date +%Y-%m-%d__%H-%M-%S`.txt -quit -batchmode -nographics -dedicated $PARAMS
```

Is the problem.

Replace all referenced to files and programs with the full path to those files and programs. Never assume a PWD/CWD in any script.
I don't use screen and don't have that program, but here's an example:
rather than running ./sshd, it run /usr/sbin/sshd.
./sshd assumes the sshd program is in the current directory, which only works if my pwd is /usr/sbin/ - which is pretty much a never-gonna-happen thing.

In short, learn about the difference between a 
[LIST]
[*]relative path
[*]absolute path and 
[*]the PATH environment variable.
[/LIST]
Then all this will make perfect sense.  BTW, this works the same on MS-Windows, so there isn't anything new here.

I would clean up that line in the script a bit too.
```
/path/to/screen -dmS 7d2d /path/to/7DaysToDieServer.x86_64 \
-logfile $SERVERDIR/7DaysToDieServer_Data/7dtd-$(date "+%F__%H-%M-%S").log -quit \
-batchmode -nographics -dedicated $PARAMS
```

But that's me.  Perhaps the $SERVERDIR can be used for the program location?  $SERVERDIR/bin/7DaysToDieServer.x86_64 could be the location, but I don't know.  Also, I would put log files into either /var/log/ somewhere or a separate log directory under  $SERVERDIR/. Don't mix logs and game data.

---

### Post by TheFu on 2021-07-13
The crontab has issues too.  Again, never  assume the cwd/pwd. ALWAYS, ALWAYS, ALWAYS use full paths to any programs or files.
```
@reboot sh ~/7d2d/live-startserver.sh -configfile=live-startserver.sh > StartserverResult.txt
```

So, that should be something like:
```
@reboot /home/thefu/7d2d/live-startserver.sh -configfile=/home/thefu/7d2d/live-startserver.sh > /home/thefu/7d2dStartserverResult.txt 2>&1
```

Full paths. Don't trust that $HOME will be set or that ~/ == $HOME in a batch situation - i.e. non-interactive environment.

---

### Post by callakskytower on 2021-07-13
Ok then, I made some changes to my shell script, tested it by hand and it works from the console, but still not as a service or from crontab:

```
#!/bin/sh
SERVERDIR=`dirname "$0"`
cd "$SERVERDIR"


PARAMS=$@


CONFIGFILE=
while test $# -gt 0
do
        if [ `echo $1 | cut -c 1-12` = "-configfile=" ]; then
                CONFIGFILE=`echo $1 | cut -c 13-`
        fi
        shift
done


if [ "$CONFIGFILE" = "" ]; then
        echo "No config file specified. Call this script like this:"
        echo "  ./startserver.sh -configfile=serverconfig.xml"
        exit 1
else
        if [ -f "$CONFIGFILE" ]; then
                echo Using config file: $CONFIGFILE
        else
                echo "Specified config file $CONFIGFILE does not exist."
                exit 1
        fi
fi


export LD_LIBRARY_PATH=.
#export MALLOC_CHECK_=0


/usr/bin/screen -dmS 7d2d /home/callak/7d2d/7DaysToDieServer.x86_64 -logfile $SERVERDIR/7DaysToDieServer_Data/output_log__`date +%Y-%m-%d__%H-%M-%S`.txt -quit ->

```

Service result:
```
&#9679; 7dtd.service - 7 Days to Die
     Loaded: loaded (/lib/systemd/system/7dtd.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2021-07-13 10:13:14 CDT; 10min ago
    Process: 919 ExecStart=/home/callak/7d2d/live-startserver.sh -configfile=live-serverconfig.xml (code=exited, status=0/SUCCESS)
    Process: 933 ExecStop=/bin/kill -s QUIT $MAINPID (code=exited, status=1/FAILURE)
   Main PID: 919 (code=exited, status=0/SUCCESS)


Jul 13 10:13:14 gameroom systemd[1]: 7dtd.service: Scheduled restart job, restart counter is at 5.
Jul 13 10:13:14 gameroom systemd[1]: Stopped 7 Days to Die.
Jul 13 10:13:14 gameroom systemd[1]: 7dtd.service: Start request repeated too quickly.
Jul 13 10:13:14 gameroom systemd[1]: 7dtd.service: Failed with result 'exit-code'.
Jul 13 10:13:14 gameroom systemd[1]: Failed to start 7 Days to Die.

```

Crontab:
```
@reboot sh /home/callak/7d2d/live-startserver.sh -configfile=/home/callak/7d2d/live-startserver.sh > /home/callak/7d2d/StartserverResult.txt
```



When I try to use crontab, the server still has issues reading it's configuration file:
```
2021-07-13T10:13:16 0.417 INF Command line arguments: /home/callak/7d2d/7DaysToDieServer.x86_64 -logfile /home/callak/7d2d/7DaysToDieServer_Data/output_log__2021-07-13__10-13-14.txt -quit -batchmode -nographics -dedicated -configfile=/home/callak/7d2d/live-startserver.sh2021-07-13T10:13:16 0.421 INF Parsing server configfile: /home/callak/7d2d/live-startserver.sh
2021-07-13T10:13:16 0.480 ERR ====================================================================================================
2021-07-13T10:13:16 0.480 ERR Error parsing configfile:
2021-07-13T10:13:16 0.480 EXC Data at the root level is invalid. Line 1, position 1.
XmlException: Data at the root level is invalid. Line 1, position 1.
  at System.Xml.XmlTextReaderImpl.Throw (System.Exception e) [0x00027] in <1d98d70bb7d8453b80c25aa561fdecd1>:0
  at System.Xml.XmlTextReaderImpl.Throw (System.String res, System.String arg) [0x00029] in <1d98d70bb7d8453b80c25aa561fdecd1>:0
  at System.Xml.XmlTextReaderImpl.Throw (System.String res) [0x00000] in <1d98d70bb7d8453b80c25aa561fdecd1>:0
  at System.Xml.XmlTextReaderImpl.ParseRootLevelWhitespace () [0x0012c] in <1d98d70bb7d8453b80c25aa561fdecd1>:0
  at System.Xml.XmlTextReaderImpl.ParseDocumentContent () [0x002d4] in <1d98d70bb7d8453b80c25aa561fdecd1>:0
  at System.Xml.XmlTextReaderImpl.Read () [0x0008c] in <1d98d70bb7d8453b80c25aa561fdecd1>:0
  at System.Xml.XmlLoader.Load (System.Xml.XmlDocument doc, System.Xml.XmlReader reader, System.Boolean preserveWhitespace) [0x000a6] in <1d98d70bb7d8453b80c25aa561fdecd1>:0
  at System.Xml.XmlDocument.Load (System.Xml.XmlReader reader) [0x0002e] in <1d98d70bb7d8453b80c25aa561fdecd1>:0
  at GameStartupHelper.LoadConfigFile (System.String _filename) [0x00082] in <24b464b028e84a71881593dfdba4c984>:0

```

---

### Post by callakskytower on 2021-07-13
Ok, I spotted my issue with crontab, I had the wrong file specified for the config file.  However I would still like to run this as a service if possible.

---

### Post by TheFu on 2021-07-13
export LD_LIBRARY_PATH=.

Don't do that.  It removes all the other locations for shared libraries and again - it depends on the CWD, which scripts should NEVER, EVER, do.  Whoever created this script needs basic script training.  They clearly aren't Unix people.

BTW, 
the error is right there:
```
2021-07-13T10:13:16 0.480 ERR Error parsing configfile:
2021-07-13T10:13:16 0.480 EXC Data at the root level is invalid. Line 1, position 1.
```
You need to fix that.

---

### Post by callakskytower on 2021-07-13
> **TheFu said:**
> export LD_LIBRARY_PATH=.

Don't do that.  It removes all the other locations for shared libraries and again - it depends on the CWD, which scripts should NEVER, EVER, do.  Whoever created this script needs basic script training.  They clearly aren't Unix people.

BTW, 
the error is right there:
```
2021-07-13T10:13:16 0.480 ERR Error parsing configfile:
2021-07-13T10:13:16 0.480 EXC Data at the root level is invalid. Line 1, position 1.
```
You need to fix that.

> **callakskytower said:**
> Ok, I spotted my issue with crontab, I had the wrong file specified for the config file.  However I would still like to run this as a service if possible.

As mentioned above, I found my problem with using crontab, the crontab solution is now working.   However, I still would like to learn how to get this running as a service if possible.   Also, I didn't make the original script, just altered it some.  However, I'm not exactly a UNIX person myself, but I would like to become one.   I probably know just enough to get myself in trouble.  :p

---

### Post by TheFu on 2021-07-13
> **callakskytower said:**
> As mentioned above, I found my problem with using crontab, the crontab solution is now working.   However, I still would like to learn how to get this running as a service if possible.   Also, I didn't make the original script, just altered it some.  However, I'm not exactly a UNIX person myself, but I would like to become one.   I probably know just enough to get myself in trouble.  :p

I assumed someone else had created these script/unit files.  They are noobs.
You found "a" problem with the crontab version, not "the problem".  Again, scripts should never assume a pwd.


Open a terminal, run "pwd".  You can't trust that inside any script, so don't.  **Always use absolute paths** to files in every script, every file, every reference to every file, and every configuration.  NEVER trust the pwd.  Things break when we do, as you are experiencing.

Never trust the PATH either. Things break when we do, as you already experienced.

These are scripting 101 things.  [https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

---

