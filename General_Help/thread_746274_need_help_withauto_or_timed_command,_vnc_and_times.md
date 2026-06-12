---
title: "need help with:auto or timed command, vnc and timeshutdown"
date: 2008-04-05
forum: General Help
---

### Post by mrgreaper on 2008-04-05
[I]ok first the main problem (and i only have 10 minutes before i got to sign off so sorry if my wording is wrong)

I need to get the computer to execute a command on boot up 
```
python2.5 sabnzbd.py --daemon
```
i have googled and found lots of threads where people say they need help then fix it but dont explain how !!!!!grrrrr and a possible method
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)
i followed these to the letter and indeed there is s90foo.sh in some of the rc folders (though there empty ? is that right ???)
if i go to the init.d folder and type ./foo.sh it loads and the command is executed
i have (as another forum suggested) tried adding gnome-terminal -x but to no avail (again the script works when i call it just not on boot up its driving me insane ( and costing me more electric then is needed see explanation)

ok this ties in with above and maybe a way to workround above[/I]**SOLVED**

*every day i want the pc to completly shutdown at a set time (1600) and reboot at 23:00(rebooting not a problem bios can do that) is there a command i can run that will tell it to shut down at a set time (maybe i can add that to my above script ?) since the pc turns on itself at 2300 i could make the above script run at 2310 (someone said i need a cron job to do that, but the name rings a bell i just cant renember what it is lol)***SOLVED**

[B]last problem,
my box is a headless one at the mo to edit it i have to take a monitier through to my kitchen, i have installed vnc but when i use the viewer i do not see my desktop the same as a monitier i just see a blnak screen with a terminal,and user vnc i need it to use the default desktop and me as user any ideas[/B]*not yet solved...help!!:)*

any help greatfully recieved

---

### Post by pointone on 2008-04-05
If the script is already in /etc/init.d, you can configure it to run on startup by running:

```
sudo update-rc.d <script> defaults
```

Using **defaults** will have it start in runlevels 2, 3, 4, and 5, and stop it in runlevels 0, 1, and 6. For more fine-grained control, see the update-rc.d manpage.

If the script is your own custom creation or you just need to run a simple command, you can simply edit "/etc/rc.local" and add your commands to the end, ensuring the last line is still "exit 0". "rc.local" is the last thing to be run during boot.

As far as shutting down, you can edit "/etc/crontab" and add the following:

```
0 16 * * *    root    /sbin/shutdown -h now
```

... to have "shutdown -h now" run every day at 16:00.

---

### Post by mrgreaper on 2008-04-05
> **pointone said:**
> If the script is already in /etc/init.d, you can configure it to run on startup by running:

```
sudo update-rc.d <script> defaults
```

Using **defaults** will have it start in runlevels 2, 3, 4, and 5, and stop it in runlevels 0, 1, and 6. For more fine-grained control, see the update-rc.d manpage.

If the script is your own custom creation or you just need to run a simple command, you can simply edit "/etc/rc.local" and add your commands to the end, ensuring the last line is still "exit 0". "rc.local" is the last thing to be run during boot.

As far as shutting down, you can edit "/etc/crontab" and add the following:

```
0 16 * * *    root    /sbin/shutdown -h now
```

... to have "shutdown -h now" run every day at 16:00.

adding the line from the script to the rc.local worked a treat (thankyou)

the update rc bit i tried first didnt work but meh its loading on boot and thats all that matters 

the cron job worked perfect too (again huge thankyou)

all thats left  now is getting vncserver to load on boot up using the default desktop (so its the same as being at the pc) and i will be happy as larry!

---

