---
title: "How to run script from launcher as root?"
date: 2018-01-02
forum: General Help
---

### Post by ianmanning on 2018-01-02
I have a dual boot machine, with Ubuntu 17.04 as the first option on the grub menu and Windows 10 as the 2nd. I am trying to create a launcher icon in Ubuntu which will reboot into Windows 10. The script (/usr/local/bin/bootwindows.sh) looks like this:
```
#!/bin/sh
sudo grub-reboot 1
reboot

```

I then created a file ~/.local/share/applications/bootwindows.desktop:
[Desktop Entry]
Comment=Boot to Windows 10
Terminal=true
Name=Boot Windows
Exec=/usr/local/bin/bootwindows.sh
Type=Application
Icon=/home/myuser/windows10.png

I granted execute permissions on both files (chmod +x).

I then searched for my desktop item and dragged it to the Ubuntu launcher. When I click on the item the machine reboots, but back into Ubuntu - presumably because it did not execute with root privileges (if I run it with sudo from a terminal window it runs fine, and reboots into Windows).

How can I create a launcher item to run this script as root?

---

### Post by Hadaka on 2018-01-02
Hi, here is a simple easy way to do that..

#!/bin/bash
PATH=$PATH:/sbin:/usr/sbin
echo '[COLOR=#ff0000]your-password[/COLOR]' | sudo reboot

chmod +x bootwindows

[Desktop Entry]
Comment=Boot to Windows 10
Terminal=true
Name=Boot Windows
#I wouled save "bootwindows" here..
Exec=/home/myuser/bootwindows  
#Exec=/usr/local/bin/bootwindows
Type=Application
Icon=/home/myuser/windows10.png

---

### Post by ianmanning on 2018-01-02
> **Hadaka said:**
> Hi, here is a simple easy way to do that..

#!/bin/bash
PATH=$PATH:/sbin:/usr/sbin
echo '[COLOR=#ff0000]your-password[/COLOR]' | sudo reboot

chmod +x bootwindows

[Desktop Entry]
Comment=Boot to Windows 10
Terminal=true
Name=Boot Windows
#I wouled save "bootwindows" here..
Exec=/home/myuser/bootwindows  
#Exec=/usr/local/bin/bootwindows
Type=Application
Icon=/home/myuser/windows10.png


Thanks for the suggestion. When I try that I get prompted for my password, and also get a message suggesting a syntax error with the sudo command:

```
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] file ...
[sudo] password for myuser: 

```

---

### Post by ianmanning on 2018-01-02
...My shell script now looks like this:
```
#!/bin/bash
PATH=$PATH:/sbin:/usr/sbin
echo 'password' | sudo grub-reboot 1
echo 'password' | sudo reboot

```

---

### Post by col48 on 2018-01-02
Personally I'd be uneasy about putting my password in plain text on disk - even in somewhere as obscure as this!
Doesn't 
```
sudo reboot
```
just prompt for the password?

---

### Post by ianmanning on 2018-01-02
> **col48 said:**
> Personally I'd be uneasy about putting my password in plain text on disk - even in somewhere as obscure as this!
Doesn't 
```
sudo reboot
```
just prompt for the password?

I'm OK with that in this case, but yes I am still being prompted for my password. Since I don't usually have a keyboard connected to this machine I'd like to bypass that.

---

### Post by HermanAB on 2018-01-02
There are various tricks to get around issues like this.  You could set up a root cron job that periodically looks for the presence of a certain trigger file in /tmp.  If the file exists, delete it and reboot the machine into Windows.  Then, make a trigger script that does 'touch /tmp/triggerfile' to trigger the reboot in a minute or two.

---

### Post by Hadaka on 2018-01-02
Hi, I knew there would be security comments...

where is your file ?
still here ?  
Exec=/usr/local/bin/bootwindows

---

### Post by ianmanning on 2018-01-02
> **Hadaka said:**
> Hi, I knew there would be security comments...

where is your file ?
still here ?  
Exec=/usr/local/bin/bootwindows

Yes it's still there

---

### Post by Hadaka on 2018-01-02
Hi, I should be taken out...tied down and forced to listen
to Barry Manilow records..Please accept my apology for leaving
out the part that keeps it from asking for your password.. "-S "

I tested this and it works 100%

#!/bin/bash
PATH=$PATH:/sbin:/usr/sbin
echo 'XXXXXXX' | sudo -S reboot


hadaka@the-beach:~$ cat reboot.desktop
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=/home/hadaka/reboot
Name=reboot
Icon=/home/hadaka/reset.jpeg

---

### Post by ianmanning on 2018-01-02
> **Hadaka said:**
> Hi, I should be taken out...tied down and forced to listen
to Barry Manilow records..Please accept my apology for leaving
out the part that keeps it from asking for your password.. "-S "

I tested this and it works 100%

#!/bin/bash
PATH=$PATH:/sbin:/usr/sbin
echo 'XXXXXXX' | sudo -S reboot


hadaka@the-beach:~$ cat reboot.desktop
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=/home/hadaka/reboot
Name=reboot
Icon=/home/hadaka/reset.jpeg

You are a genius - thanks! 
And please don't put yourself through the Barry Manilow records - nobody deserves that ;0)

---

### Post by Hadaka on 2018-01-02
I agree..it would be a bit harsh..I'll stand in the corner with
windows 95 and use DOS for a couple hours..that will teach
me a lesson !
If you are now satisfied with the results..Please mark your thread  Solved
by logging into your first post..and click **Thread Tools** and then choose **Solved**.

*Hint..Thread Tools is just above [join date] on the right.

Thank You.

---

### Post by ianmanning on 2018-01-02
Hmmm....there is a bit of a problem...when I now reboot from Windows back to Ubuntu I am prompted for my user password at login (which I had previously configured to bypass). Any idea why I'm now being prompted for it?

---

### Post by raleigh3 on 2018-01-02
Happy for you.

I use that method all the time since I am the only user on my computer.

---

### Post by Hadaka on 2018-01-02
The password bypass on the sudo reboot command is separate
from the user password for the Ubuntu os, so I am not sure why
that is happening. Re-check your configuration for Ubuntu password
bypass to verify nothing has changed. The password for the "reboot"
script is for activating "sudo...root" ..The password for the Ubuntu os
is for  "log in'.

---

### Post by ianmanning on 2018-01-02
> **Hadaka said:**
> The password bypass on the sudo reboot command is separate
from the user password for the Ubuntu os, so I am not sure why
that is happening. Re-check your configuration for Ubuntu password
bypass to verify nothing has changed. The password for the "reboot"
script is for activating "sudo...root" ..The password for the Ubuntu os
is for  "log in'.

Yes that's strange. The Automatic Login option in User Accounts is still set to "On", so I don't understand why it should now be prompting me for a password (it didn't before).
????

---

### Post by sisco311 on 2018-01-02
Storing your password in a plain text file is not the best idea.

There are many better ways to accomplish what you want.

You can edit the sudoers file to allow your user to run the script as root without a password. See: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

But if you check out your original script you can see that you only need *grub-reboot* to be executed as root. grub-reboot is a script which in turn calls the *grub-editenv* command.

systemd allows you to reboot your computer most of the time without prompting you for a password.

So setting the [setuid]("https://en.wikipedia.org/wiki/Setuid") bit on *grub-editenv* will allow you to run your script without a password:
```
sudo chmod 4755 /usr/bin/grub-editenv
```
After making the command setuid root you don't have to use sudo to run it:
```
#!/bin/sh
grub-reboot 1
reboot

```

The downside of this method is that you might have to reset the setuid bit every time the grub package is updated and every user will be able to run grub-editenv as root!



> **HermanAB said:**
> There are various tricks to get around issues like this.  You could set up a root cron job that periodically looks for the presence of a certain trigger file in /tmp.  If the file exists, delete it and reboot the machine into Windows.  Then, make a trigger script that does 'touch /tmp/triggerfile' to trigger the reboot in a minute or two.

On one hand implementing your own solution sounds awesome, on the other hand is probably less secure than configuring the existing tools like sudo/policykit to work how you want.
On a system where sudo and/or policykit is not available I would probably try to implement some kind of server/client architecture where the server runs as root and waits for the client to trigger the event.  

Still like your idea, it's cool!

---

### Post by Hadaka on 2018-01-02
Hi, first let me state..I agree 100% with the concerns about leaving your
password exposed. However the computer was already set up as no password
needed to boot into the Ubuntu and windows os's. Let's try this..
Turn off then back on the "no loggin" feature..set the lock to avoid changes...then
rename your desktop and script to something else... then try a simple build from
your home directory..as the example of my test files in post 10. see if that puts things
back as they were for your no Ubuntu login.
also...please post the output of..
```
ls -al /bin/systemctl
```
and another also..you are aware that 17.04 goes L.O.S this month ?...1/2018..addios support.

---

