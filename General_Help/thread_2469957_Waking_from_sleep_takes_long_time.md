---
title: "Waking from sleep takes long time"
date: 2021-12-15
forum: General Help
---

### Post by erik070 on 2021-12-15
I've been having this issue for a while now (only on Ubuntu (again) since summer of 2021), it takes about 1 minute for my laptop to wake from sleep. Usually my laptop powers on from sleep, screen stays black for a minute or so and then the login screen appears. In some rare cases the login screen will appear within a second when waking from sleep, but it will not respond for a minute or so. 

The "funny" thing is, cold booting takes a shorter time then waking from sleep. Usually that takes about 10-15 seconds.

Couldn't find anyone else with similar issues, but that could just be that I use different words to describe the issue.

Is this normal behavior for Ubuntu 20.04/21.04? (Had this issue on both versions)

---

### Post by TheFu on 2021-12-17
hibernate or standby?
Is there a network connection?  I can see wifi taking longer than wired to connect, especially if using DHCP.
If there are more than just essential USB devices connected, those can slow down waking ... or booting ... drastically.

---

### Post by erik070 on 2021-12-20
Not sure if it is hibernate or standby. To be honest, I just click on suspend in the Power Off/Log Out menu.

Network connection is sometimes wired sometimes wifi (depends where I work). I don't see any difference in time in these 2 situations. Could be that one is a second or so faster, but not really noticeable.

Usually I start without any USB devices attached. I've grown accustomed to the long startup time, so when I unpack my stuff at work I unpack and power on my laptop first and then start gathering the cables and such to connect. Usually by the time I connect the first USB device, the laptop is already started.
Only USB device I connect are a keyboard and a USB headset receiver.

---

### Post by TheFu on 2021-12-20
To see what is taking all the time, **systemd-analyze blame** can be helpful.
So can **systemd-analyze critical-chain **

Work through the lists for the longest times and determine how important each is to you.  For example, if you don't use btrfs or zfs or snaps or bluetooth, then there is no reason to have those hold up the boot and time out.  A slow DNS can drastically slow booting too, as will trying to mount USB storage that isn't there anymore.  Do your research, since some things in the list may be absolutely required to boot.

For example, 
```
$ systemd-analyze critical-chain 
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @5.998s
&#9492;&#9472;multi-user.target @5.998s
  &#9492;&#9472;postfix.service @5.994s +3ms
    &#9492;&#9472;postfix@-.service @2.530s +3.463s
      &#9492;&#9472;network-online.target @2.522s
        &#9492;&#9472;network.target @2.521s
          &#9492;&#9472;networking.service @2.391s +124ms
            &#9492;&#9472;apparmor.service @2.271s +118ms
              &#9492;&#9472;local-fs.target @2.270s
                &#9492;&#9472;run-user-114-gvfs.mount @5.283s
                  &#9492;&#9472;run-user-114.mount @4.333s
                    &#9492;&#9472;swap.target @2.042s
                      &#9492;&#9472;dev-vgubuntu\x2dmate-swap_1.swap @2.017s +23ms
                        &#9492;&#9472;dev-dm\x2d1.device @2.014s
```
Shows that my desktop boots in 6 seconds.  I doubt most people can get to that speed. I prefer a minimal system and have disabled many, many, bloated things that were installed by default.

As for suspend, if the exact same hardware isn't there when coming out as it was going in, then that can be confusing ... which requires more time for the OS to figure out what you really intend.  I suspend my laptop nightly, but don't add or remove any hardware connections.  When it comes out of suspend, almost always, everything works.  The networking sometimes has a hiccup and that causes other things like NFS it hiccup too, but that only happens once every 3-4 months. I have a loose network connection.

---

### Post by erik070 on 2021-12-29
Sorry for the late reply. 

While checking some other issue I had with my laptop (powerconsumption during suspend) I switched /sys/power/mem_sleep from *s2idle* to *deep*. After that it seems like resuming from suspend is much quicker.
For other wanting to change this setting, editing in nano or vi(m) won't help, run this command:

```
echo deep | sudo tee /sys/power/mem_sleep
```

Reboot your laptop and it should keep the setting and lower power consumption drastically during suspend (my laptop usually drained during the weekends). Also, it apparently helps with resuming from suspend times :)

---

### Post by TheFu on 2021-12-29
> **erik070 said:**
> Sorry for the late reply. 

While checking some other issue I had with my laptop (powerconsumption during suspend) I switched /sys/power/mem_sleep from *s2idle* to *deep*. After that it seems like resuming from suspend is much quicker.
For other wanting to change this setting, editing in nano or vi(m) won't help, run this command:

```
echo deep | sudo tee /sys/power/mem_sleep
```

Reboot your laptop and it should keep the setting and lower power consumption drastically during suspend (my laptop usually drained during the weekends). Also, it apparently helps with resuming from suspend times :)

Files in /sys/ aren't retained between boots.  /sys is like /proc - both are "pseudo-file systems i.e., not real.  They are created as a way to change internal system settings or to provide information to the system or users.  Run 
```
more /proc/cpuinfo
```
or 
```
more /proc/meminfo
```
See what I mean?

Ok, so there are practical reasons that those files cannot be modified by non-root userids.  To modify a single line setting in one of those files, the method with echo .....|sudo tee ... is the best practice.  It can be used with other system setting files too, just be certain to use the 'append' option   **tee -a** to avoid replacing the entire files. Of course, this only works when files use the last setting seen, not any earlier settings.  There is no agreement on that across all projects or config files, sadly.  

As an aside, the best way to edit system files is to use the **sudoedit** command.  It uses whatever EDITOR is set in that environment variable and works by making a local, temporary, copy of the file.  When editing is complete, it copies that temporary file back, replacing the prior version.  This is much safer than directly using other methods for a number of subtle security reasons.

Regardless, happy that a solution was found.  As you might guess, it is extremely unlikely that someone else would have known the defaults had been changed, but asking others seems to unlock memories that helps figure out the root issue.  That's extremely common for all of us. Thanks for posting the resolution, issue, and fix.

---

### Post by erik070 on 2022-01-02
> **TheFu said:**
> Files in /sys/ aren't retained between boots.  /sys is like /proc - both are "pseudo-file systems i.e., not real.  They are created as a way to change internal system settings or to provide information to the system or users.  Run 
```
more /proc/cpuinfo
```
or 
```
more /proc/meminfo
```
See what I mean?

Ok, so there are practical reasons that those files cannot be modified by non-root userids.  To modify a single line setting in one of those files, the method with echo .....|sudo tee ... is the best practice.  It can be used with other system setting files too, just be certain to use the 'append' option   **tee -a** to avoid replacing the entire files. Of course, this only works when files use the last setting seen, not any earlier settings.  There is no agreement on that across all projects or config files, sadly.  

As an aside, the best way to edit system files is to use the **sudoedit** command.  It uses whatever EDITOR is set in that environment variable and works by making a local, temporary, copy of the file.  When editing is complete, it copies that temporary file back, replacing the prior version.  This is much safer than directly using other methods for a number of subtle security reasons.

Regardless, happy that a solution was found.  As you might guess, it is extremely unlikely that someone else would have known the defaults had been changed, but asking others seems to unlock memories that helps figure out the root issue.  That's extremely common for all of us. Thanks for posting the resolution, issue, and fix.

Good to know about the files in /sys/ 

About the last sentence: s2idle seems to be default, at least in my case. Not sure why it is default, because it is very undesirable behavior if you ask me. Had this solution in my bookmarks somewhere, just forgot to apply after installing Ubuntu.
And about unlocking memories, that is so true. Have this at work as well, if I'm stuck I just go talk to a colleague, explaining what is going wrong. Usually an option to solve it will come up when explaining it to my colleague. I think it is called "the wooden indian", as in talking to a wooden statue, no reply is needed just someone who listens.

---

