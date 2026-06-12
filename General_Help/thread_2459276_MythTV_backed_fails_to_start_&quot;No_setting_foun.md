---
title: "MythTV backed fails to start &quot;No setting found for this machine's BackendServerIP&quot;"
date: 2021-03-15
forum: General Help
---

### Post by Raptor Ramjet on 2021-03-15
Hello,

I've just had to switch an intermittently failing motherboard on my myth machine.  Prior to this I used apt to make sure the machine was up to date ("update" then "upgrade") after which I swapped out the old motherboard, powered on and everything mostly worked (HDMI sound needs attention).  As my mythtv setup was a bit crappy I thought that I'd now take this "opportunity" to set it up again from scratch.

I have three users on this box so I started by renaming their myth config directories to "~/.mythtv.2021-03-13" then renamed "/etc/mythtv" to "/etc/mythtv.2021-03-13".  Next step I backed up the existing "mythconverg" database, dropped it, then purged the old installation with:

```

sudo apt-get remove --auto-remove mythtv
sudo shutdown -r now

```

Once the machine had rebooted I used "w_scan" to generate a test "TVchannels.conf" file and I can happily use this to watch live TV in vlc.  At this point I installed myth using:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mythtv

```

I then ran myth setup but this fails to run properly as the GUI doesn't appear.  You briefly sees a gui "flash up" following which you'd get a prompt to close mythbacked, followed by a prompt to run "mythfilldatabase".  A console window then briefly shows but this closes before you can see what the messages are. A lot of head scratching and manual intervention later (hand editing "/etc/myth/config.xml", manual creation of "mythconverg" database) and I can confirm:

1. The mythconverg database is operational and I can log in directly using mysql and the "mythtv" user.

2. I can run various "select" and "update" queries using mysql from a command line - All tables seem to be present and mostly empty (there is data in some tables but this looks like lookup data).  I can do this using either my own user or the "mythtv" user.

3. All users have "~/.mythtv" symlinked to "/etc/.mythtv".  I have tested that all users can read ~/.mythtv/config.xml" via the symlink.

3. The mysql values in "/etc/mythtv/config.xml" are the same as the credentials I use to log in to mythconverg directly with mysql.  File content is:

```

<Configuration>
  <LocalHostName></LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>localhost</Host>
    <UserName>mythtv</UserName>
    <Password>*MY_PASSWORD* (not shown here :)</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
  <UPnP>
    <UDN>
      <MediaRenderer>6a8cc41c-3bb7-4ce5-be4c-b819c68ae2d2</MediaRenderer>
    </UDN>
  </UPnP>
</Configuration>

```

At this point running "mythtv-setup" fails as decribed previously.  If I try to start the backend I get the following error:

```

sudo mythbacked
2021-03-15 09:36:34.813567 C  mythbackend version: fixes/31 [v31.0+fixes.202102281958.e705d36a36~ubuntu18.04.1] www.mythtv.org
2021-03-15 09:36:34.813601 C  Qt version: compile: 5.9.5, runtime: 5.12.8
2021-03-15 09:36:34.813657 I  Ubuntu 20.04.2 LTS (x86_64)
2021-03-15 09:36:34.813666 N  Enabled verbose msgs:  general
2021-03-15 09:36:34.813683 N  Setting Log Level to LOG_INFO
2021-03-15 09:36:34.824627 I  Added logging to the console
2021-03-15 09:36:34.825227 I  Setup Interrupt handler
2021-03-15 09:36:34.825242 I  Setup Terminated handler
2021-03-15 09:36:34.825255 I  Setup Segmentation fault handler
2021-03-15 09:36:34.825267 I  Setup Aborted handler
2021-03-15 09:36:34.825278 I  Setup Bus error handler
2021-03-15 09:36:34.825290 I  Setup Floating point exception handler
2021-03-15 09:36:34.825304 I  Setup Illegal instruction handler
2021-03-15 09:36:34.825319 I  Setup Real-time signal 0 handler
2021-03-15 09:36:34.825337 I  Setup Hangup handler
2021-03-15 09:36:34.825582 N  Using runtime prefix = /usr
2021-03-15 09:36:34.825588 N  Using configuration directory = /root/.mythtv
2021-03-15 09:36:34.825738 I  Assumed character encoding: en_GB.UTF-8
2021-03-15 09:36:34.826181 I  Empty LocalHostName. This is typical.
2021-03-15 09:36:34.826192 I  Using a profile name of: 'mythic' (Usually the same as this host's name.)
2021-03-15 09:36:34.826277 I  Start up testing connections. DB localhost, BE , attempt 0, status dbAwake, Delay: 2000
2021-03-15 09:36:35.857598 N  Setting QT default locale to en_GB
2021-03-15 09:36:35.857622 I  Current locale en_GB
2021-03-15 09:36:35.857714 N  Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2021-03-15 09:36:35.916174 I  Power: On AC power
2021-03-15 09:36:35.916212 I  Power: Supported actions: Suspend,Restart,Shutdown
2021-03-15 09:36:35.918221 I  Loading en_gb translation for module mythfrontend
2021-03-15 09:36:35.926290 I  Current MythTV Schema Version (DBSchemaVer): 1361
2021-03-15 09:36:35.927059 I  Loading en_gb translation for module mythfrontend
[B]No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.[/B]
2021-03-15 09:36:35.932606 E  MythSocket(55ea5636da80:-1): Unable to lookup:
2021-03-15 09:36:35.936243 I  PowerDBus: Closing interfaces
2021-03-15 09:36:35.938233 I  Exiting

```

No idea what's happening here as "/etc/mythtv/config.xml" looks correct and is definitely symlinked to all 3 users "~/mythtv" directory. Even more head scratchng later and I found the "mythtv-setup.real" command.  Running this at least now shows an error:

```

sudo mythtv-setup.real
**mythtv-setup.real: symbol lookup error: mythtv-setup.real: undefined symbol: _ZN14ChannelScanner4ScanEijRK7QStringjbbbbbbbb19ServiceRequirementsjRK4QMapIS0_S0_ES2_S2_S2_S2_S2_**

```

At this point I'm not sure where to go next ?  Does this look like a code issue ?  

I've installed using "apt-get" from the official Ubuntu repository (not added any PPAs etc.) so I should have the latest "offical working" build.  I can access "mythconverg" from a mysql command line from both my user and the mythv user accounts using credentials "copy & pasted" from "/etc/mythtv/config.cml" ? and "/etc/mythtv/" is definitely symlinked to all 3 users "~/.mythtv" directory ?

Any pointers/niformation/top tips gratefully received.

---

### Post by Tadaen_Sylvermane on 2021-03-16
Double check permissions of the mythtv folder. If this is a single host unless you've moved it it should be in /var/lib/mythtv i believe. Find it before running a command on that directory first though. Also I'm unsure of the mythtv-setup.real command. This is first time I've ever seen it actually. I've always just used mythtv-setup.

---

### Post by Raptor Ramjet on 2021-03-17
All permissions were fine.  All config was fine.  This must have been a software bug as I've just used apt-get and there were updates for myth.  Applied these and it's now working ok.  n.b. I'd made no changes to anything on my box befor running apt-get so the latest version of myth definitely fixed the problem.

FYI: "mythtv-setup.real" enables you to use mythsetup purely from a console (i.e. no GUI window popping up)  In my case mythtv-setup wasn't working and the GUI was simply "flashing up" without me being able to see what the error was.  I'll guess that "mythtv-setup.real" is probably what's called by mythtv-setup.

Cheers.

---

### Post by tea for one on 2021-03-17
> Last edited by Raptor Ramjet; 37 Minutes Ago at 06:06 PM. Reason: Speeling mistaks 

Arf Arf - very witty
I wish that I had thought of it :)

---

