---
title: "Can't use any software for 5-10 minutes after boot"
date: 2016-12-31
forum: General Help
---

### Post by turvy on 2016-12-31
Hi, 
I have Ubuntu 16.10 updated from 16.04, running on a Sony Vaio VGN-NR38E.

Every time i turn the laptop on, I have to wait between 5 and 10 minutes before I can use it after it has booted to desktop. 

If I open Firefox or any other software, it crashes and kicks me back out to the login screen to enter my password. When I login again everything is closed.
 Usually when Firefox does eventually start (after roughly 5-10 minutes) it asks me to start in safe mode or Refresh Firefox and then I lose any addons I have installed (Only two - Google Translate and Ublock Origin). 

Hope someone can help.

---

### Post by dragonfly41 on 2016-12-31
Can you log out immediately after booting up
then login in to guest account?

---

### Post by turvy on 2016-12-31
I'll try now.

Hi, 
I can't figure out how to launch guest session.. 

[http://i.imgur.com/5QHXaDM.jpg](http://i.imgur.com/5QHXaDM.jpg)

---

### Post by dragonfly41 on 2016-12-31
See tip #10 in this checklist ... [http://www.linuxtechi.com/top-10-task-to-do-after-installing-ubuntu-16-04/](http://www.linuxtechi.com/top-10-task-to-do-after-installing-ubuntu-16-04/)

You can also try creating a new user account ... 

[COLOR=#111111]Ctrl+Alt+F1[/COLOR]

sudo adduser newusername

to give account admin privileges

sudo adduser newusername sudo

and reboot to login to new user account to see if same problem arises.

---

### Post by turvy on 2016-12-31
Thanks, I did that but unfortunately it is the same problem when I login to the Guest account.

---

### Post by dragonfly41 on 2016-12-31
Well at least that workflow eliminated the possibility that the problem is in your user profile.

Since you can use command line without crashing I would now try inspecting logs .. e.g. **/var/log/syslog**

---

### Post by turvy on 2016-12-31
Is this correct?
> vaio@ubuntu:/var/log$ more -f /var/log/syslog
Dec 31 01:47:35 ubuntu gnome-settings-[9440]: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/cups_Photosmart_C3100_series
Dec 31 01:47:36 ubuntu gnome-settings-[1481]: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/cups_Photosmart_C3100_series
Dec 31 01:47:36 ubuntu colord[1088]: failed to get session [pid 24503]: No such device or address
Dec 31 01:47:45 ubuntu kernel: [184899.004701] ath5k: ath5k_hw_get_isr: ISR: 0x00000080 IMR: 0x00000000
Dec 31 01:48:36 ubuntu anacron[24154]: Job `cron.daily' terminated (mailing output)
Dec 31 01:48:36 ubuntu anacron[24154]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Dec 31 01:48:36 ubuntu anacron[24154]: anacron: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Dec 31 01:48:36 ubuntu anacron[24154]: Normal exit (1 job run)
Dec 31 01:48:42 ubuntu dbus-daemon[6836]: Activating service name='org.gnome.Nautilus'
Dec 31 01:48:43 ubuntu dbus-daemon[6836]: Successfully activated service 'org.gnome.Nautilus'
Dec 31 01:48:44 ubuntu nautilus[24566]: Theme parsing error: <broken file>:1:0: Failed to import: The resource at '/org/gnome/libgd/tagged-entry/default.css' does not exist
Dec 31 01:48:45 ubuntu dbus[830]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Dec 31 01:48:45 ubuntu systemd[1]: Starting Hostname Service...
Dec 31 01:48:45 ubuntu nautilus[24566]: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Dec 31 01:48:45 ubuntu dbus[830]: [system] Successfully activated service 'org.freedesktop.hostname1'
Dec 31 01:48:45 ubuntu systemd[1]: Started Hostname Service.
Dec 31 01:49:31 ubuntu firefox.desktop[24297]: NOT SANDBOXED
Dec 31 01:49:31 ubuntu firefox.desktop[24297]: [fresh 24593] not implemented: PPB_OpenGLES2VertexArrayObject;1.0
Dec 31 01:49:31 ubuntu firefox.desktop[24297]: [fresh 24593] not implemented: PPB_OpenGLES2DrawBuffers(Dev);1.0
Dec 31 01:49:31 ubuntu firefox.desktop[24297]: Vector smash protection is enabled.
Dec 31 01:49:31 ubuntu firefox.desktop[24297]: [fresh 24593] not implemented: PPB_BrokerTrusted;0.3
Dec 31 01:49:31 ubuntu firefox.desktop[24297]: [fresh 24593] [PPB] {zilch} ppb_network_monitor_update_network_list
Dec 31 01:49:31 ubuntu firefox.desktop[24297]: [fresh 24593] [PPB] {zilch} ppb_flash_set_instance_al



---

### Post by dragonfly41 on 2016-12-31
Now that you can begin to dive into your syslog files (and other log files) I'm hoping that others might step in to
help troubleshoot. There are lots of errors there to get you going.

Read here ... [http://askubuntu.com/questions/545504/ubuntu-crash-how-to-read-log-files](http://askubuntu.com/questions/545504/ubuntu-crash-how-to-read-log-files)

[http://unix.stackexchange.com/questions/38608/how-to-determine-why-my-computer-crashed](http://unix.stackexchange.com/questions/38608/how-to-determine-why-my-computer-crashed)


[Later edit]

Digging around it might be an ownership issue ...

[https://answers.launchpad.net/ubuntu/+question/403167](https://answers.launchpad.net/ubuntu/+question/403167)

---

### Post by turvy on 2016-12-31
Ok, thanks. I'll read through the errors and see if I can figure any of it out.

---

### Post by dragonfly41 on 2016-12-31
This error line ...
```
[COLOR=#000000]ubuntu kernel: [184899.004701] ath5k: ath5k_hw_get_isr: ISR: 0x00000080 IMR: 0x00000000[/COLOR]
```[COLOR=#000000]was suggested in this thread to point to a bad memory module.[I]
[URL="https://www.reddit.com/r/linux4noobs/comments/2od1xb/ubuntu_1404mint_17_randomly_freezing/"]
[/URL][/I][/COLOR][https://www.reddit.com/r/linux4noobs/comments/2od1xb/ubuntu_1404mint_17_randomly_freezing/](https://www.reddit.com/r/linux4noobs/comments/2od1xb/ubuntu_1404mint_17_randomly_freezing/)

Perhaps run a memory test when you bootup?
Although it is odd that the errors arise from an update.
Does a Live USB run o.k.?

---

### Post by turvy on 2016-12-31
I cannot figure it out at all................ 
:-(
I have tried all day and I can't get to whatever it is. 

I know if I backup the bits I have and wipe it, reinstall it I will have most of the issues gone, but I am trying to see if I can figure out what it is. 
I think I am lost from the start. I thought I might be able to read the logs and associate them with errors and maybe search them on google or yandex etc. 
But I am lost....... :o

---

### Post by SeijiSensei on 2017-01-01
Select the memory test from the boot menu and let it run for as long as it wants.

---

### Post by turvy on 2017-01-01
Apologies, - I didn't see dragonfly41's post. 
Thanks, I will try that. Will post back with results good, bad or indifferent.

It doesn't seem to find any errors. - [http://i.imgur.com/z14vyUw.jpg](http://i.imgur.com/z14vyUw.jpg)

I also get this "Run Action" message a lot.
 If it comes at startup, it stops me from opening anything for an extra 10 minutes. 

> Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.



If I run the action to download the fonts, it fails.

---

### Post by dragonfly41 on 2017-01-02
To address that last message "Failure to download extra data files"
a simple search found this recent discussion ...

[http://askubuntu.com/questions/766491/failure-to-download-extra-data-files-with-ttf-mscorefonts-installer-on-ubuntu](http://askubuntu.com/questions/766491/failure-to-download-extra-data-files-with-ttf-mscorefonts-installer-on-ubuntu)

and from that thread ...

[https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/1543280](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/1543280)

which suggests ... 

> 
[COLOR=#333333][FONT=monospace]Quick and dirty workaround:
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]sudo chmod 777 /var/lib/update-notifier/package-data-downloads/partial
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]

You can try that from Ctrl+Alt+F1.

But I emphasise that this is all guess work, hunting for clues (which you can also do).


[/FONT][/COLOR]

---

