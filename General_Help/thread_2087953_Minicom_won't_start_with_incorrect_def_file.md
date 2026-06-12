---
title: "Minicom won't start with incorrect def file"
date: 2012-11-25
forum: General Help
---

### Post by RogerDavis on 2012-11-25
I fumblefingered the serial port setup for Minicom, and now it ALWAYS finds the incorrect settings.  

I can start as "sudo minicom -s" and enter the correct info, save it, it says it saved it, then retry and still get the wrong setup

I can remove the program, delete the configuration files (which don't disappear when the program is removed), reinstall the program, and it STILL finds the wrong serial port info!!!!!!!

How do I fix this?

---

### Post by dcstar on 2012-11-25
> **RogerDavis said:**
> I fumblefingered the serial port setup for Minicom, and now it ALWAYS finds the incorrect settings.  

I can start as "sudo minicom -s" and enter the correct info, save it, it says it saved it, then retry and still get the wrong setup

I can remove the program, delete the configuration files (which don't disappear when the program is removed), reinstall the program, and it STILL finds the wrong serial port info!!!!!!!

How do I fix this?

[LIST=1]
[*]Use Synaptic to remove the whole package, not just the program files.
[*]Check your home folder for any relevant hidden files.
[/LIST]

---

### Post by RogerDavis on 2012-11-25
No luck, same result.

Complete removal with Synaptic, then removed the log file from my home folder.

Still says "minicom: cannot open /dev/ttACM0: No such file or directory"

I need to change this to "ttyACM0".

---

### Post by HermanAB on 2012-11-25
$ man minicom

-s   Setup.  Root edits the  system-wide  defaults  in  /etc/minirc.dfl

$ sudo rm /etc/minirc.dfl
$ sudo minicom -s

---

### Post by RogerDavis on 2012-11-25
Nope - before "saving" correction...
minicom: cannot open /dev/ttyACM0: Input/output error
roger@roger-desktop:~$ minicom
after "saving" correction...
minicom: cannot open /dev/ttACM0: No such file or directory
roger@roger-desktop:~$

---

### Post by dcstar on 2012-11-26
> **HermanAB said:**
> $ man minicom

-s   Setup.  Root edits the  system-wide  defaults  in  /etc/minirc.dfl

$ sudo rm /etc/minirc.dfl
$ sudo minicom -s

Running 12.04 minicom and saving new default settings creates a hidden .minirc.dfl file in the user's Home folder.

Unless this is manually deleted then the settings will not change:

```
rm ~/.minirc.dfl
```

---

### Post by RogerDavis on 2012-11-26
Results :
roger@roger-desktop:~$ rm ~/.minirc.dfl
rm: cannot remove `/home/roger/.minirc.dfl': No such file or directory
roger@roger-desktop:~$ 
roger@roger-desktop:~$ minicom
minicom: cannot open /dev/tty8: Permission denied
roger@roger-desktop:~$ 

And how did tty8 get into the picture?  That's not what I had there.

---

### Post by dcstar on 2012-11-26
> **RogerDavis said:**
> Results :
roger@roger-desktop:~$ rm ~/.minirc.dfl
rm: cannot remove `/home/roger/.minirc.dfl': No such file or directory
roger@roger-desktop:~$ 
roger@roger-desktop:~$ minicom
minicom: cannot open /dev/tty8: Permission denied
roger@roger-desktop:~$ 

And how did tty8 get into the picture?  That's not what I had there.

tty8 is the default on a new connection. This will allow you to change it:

```
sudo minicom
```

---

### Post by HermanAB on 2012-11-26
Anyhoo, the default settings file is called minirc.dfl, so you can hunt it down with find, and then blow it away with rm. 

$ find / -name minirc.dfl

When minicom is restarted it will make a new one.

---

### Post by ummelum on 2012-12-03
if this isn't solved yet:

[http://ubuntuforums.org/showthread.php?p=12386577](http://ubuntuforums.org/showthread.php?p=12386577)
[http://ubuntuforums.org/showthread.php?t=2089911](http://ubuntuforums.org/showthread.php?t=2089911)

other people are experiencing problems with terminals on serial ports...

---

### Post by ummelum on 2012-12-06
***can someone clue me in why this isn't working as it should? i find it hard to believe i'm the only ubuntu-user that needs a working serial port.***

---

### Post by RogerDavis on 2012-12-06
I hate to say it like this, but apparently the OS developers either can't take the time to worry about a very basic function, or they simply don't give a damn because they don't need one themselves and think no one else should either.  I'd far prefer to believe the fist one.

Maybe someone can come forward with a way to reach them better than the bug reports (which I have tried, and ended up sidelined.  Or EVERYONE file a bug report at  [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)  .  It's pretty simple to do.

I'd say look at mine at  [https://bugs.launchpad.net/ubuntu/+bug/1087519](https://bugs.launchpad.net/ubuntu/+bug/1087519)  to see what I said, but we each need to file one to better get attention to the problem.

---

### Post by ummelum on 2012-12-07
silent bump, and link to the launchpad bug:
[https://bugs.launchpad.net/ubuntu/+bug/1087519](https://bugs.launchpad.net/ubuntu/+bug/1087519)

---

### Post by RogerDavis on 2012-12-08
Finally, but also note it is categorized as "Importance - Undecided" and "Assigned To - Unassigned".

But it is a major step to have it accepted and "Status - Confirmed"!

Thanks!

---

### Post by ummelum on 2012-12-08
> **RogerDavis said:**
> Finally, but also note it is categorized as "Importance - Undecided" and "Assigned To - Unassigned".

But it is a major step to have it accepted and "Status - Confirmed"!

apparently anyone with a launchpad account can confirm a bug, so i did.

i just hope someone will notice this now.


for the record: i'm currently running a more recent kernel (3.7.0-4-generic) and it isn't making a difference.

---

### Post by ummelum on 2012-12-08
> **RogerDavis said:**
> 
I'd say look at mine at  [https://bugs.launchpad.net/ubuntu/+bug/1087519](https://bugs.launchpad.net/ubuntu/+bug/1087519)  to see what I said, but we each need to file one to better get attention to the problem.
i think it's better to have it all in one single bugreport. i think developpers are swamped and trying to keep up by wading through a sea of bug reports.

---

### Post by RogerDavis on 2012-12-08
I understand how either way could be best, depending on developers intentions.

If they disregarded the serial ports because of just honestly too busy, then add line up the reports to keep it simple.

If they disregarded the serial ports because someone decided "We don't need serial ports any more, they are old-fashioned." (Like they did with floppy drives), then more reports urging to get moving would maybe help.

Then again maybe I'm just sensitized because of the sweat and tears I've put into this to get nothing but frustration until now.

On the other hand, I'm VERY pleased to see it verified now, maybe I should just take a chill pill...

---

