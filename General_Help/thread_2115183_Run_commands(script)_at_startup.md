---
title: "Run commands(script) at startup"
date: 2013-02-12
forum: General Help
---

### Post by Balthier1979 on 2013-02-12
Hello guys,
 
I want to run some commands at startup, how do I do that? I've tried the following, make a screen.sh file, and put it in /home/username
 
contents of screen.sh
 
```
#!/bin/bash
xset s 0 0
xset s noblank
xset dpms 30 30 30
xset -dpms
```
 
Then I have made screen.sh an executable, sudo chmod +x screen.sh.
After that I've edited /etc/rc.local
 
```
/home/username/screen.sh <- I've just inserted this
exit 0
```
 
But when I reboot the computer, and check with xset q, the parameters are not set as they are in screen.sh
 
where am I going wrong? All help will be appreciated. :)

---

### Post by slickymaster on 2013-02-12
To execute user specific commands at startup, the commands or scripts that you want to execute should be added to the **/etc/rc.local** script.

The **rc.loca**l script is executed at the end of each multiuser runlevel.

---

### Post by Balthier1979 on 2013-02-12
But isn't that what I do, when I add the path to the script (/home/username/screen.sh) to **/etc/rc.local ?**

---

### Post by Balthier1979 on 2013-02-12
Can I just add those commands to /etc/rc.local? If my rc.local looks like this
 
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
xset s 0 0
xset s noblank
xset dpms 30 30 30
xset -dpms
exit 0

```
 
Will it work? Or do I need to make rc.local an executable first?

---

### Post by slickymaster on 2013-02-12
Yes, that's exactly it. The script **/etc/rc.local** will be similar to a shell script.

Just don't forget that anything written after **exit 0** will never be executed.

---

### Post by Balthier1979 on 2013-02-12
Must rc.local be an executable for it to work? But what if I want to make a simple script with some commands, and then call it from rc.local, how do I do that?
 
Could you please give some (detailed) instructions?
 
I am a windows guy, and in windows I could have made a simple batch file with some commands, and edit the registry to have it executed at startup, but I'm having problems achieving the same in Linux.

---

### Post by slickymaster on 2013-02-12
> **Balthier1979 said:**
> Must rc.local be an executable for it to work? But what if I want to make a simple script with some commands, and then call it from rc.local, how do I do that?

Yes, you'll have to make sure **/etc/rc.local** is executable and that the script it calls is also executable:
```
ls -l /etc/rc.local
```

---

### Post by Balthier1979 on 2013-02-12
Do I need to add sh before calling the script?
 
sh /home/username/screen.sh ?

---

### Post by CaptainMark on 2013-02-12
the file /etc/rc.local will already be executable.
Try not to think of an executable like in windows, they call a file that installs a program an executable, to us an executable file is a file that quite literally has the ability to be executed (run as a program or script) and can do absolutely anything you want it to from installing programs, to setting whether your screen blanks or not, our way makes much more sense when you think of it


Okay, whichever you decide to do, you can add commands directly to /etc/rc.local in which case you don't need to specify anything other than the command you want to run, the only problem is if in the futre you have too many commands doing too many things it can get a bit messy in which case you can just print the path of any other script files you have made, this way you can break groups of commands into separate jobs to keep things tidy, if you choose this second method your scripts must all have the first line set to tell the system which shell to use which in this case is #!/bin/sh or #!/bin/bash

---

### Post by Balthier1979 on 2013-02-12
I understand pretty well the definition of "executable", in the Linux context. No problems there. :)
 
This is my rc.local
 
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/home/username/screen.sh
exit 0

```
 
ls -l /etc/rc.local = -rwxr-xr-x 1 root root 328 Feb 12 11:49 /etc/rc.local
 
And this is /home/username/screen.sh
 
```

#!/bin/bash
xset s 0 0
xset s noblank
xset dpms 30 30 30
xset -dpms

```
 
ls -l screen.sh = -rwxrwxr-x 1 username username 68 Feb 12 11:50 screen.sh
 
username is my name. And that is the only user I have created on the machine. But still no go :( What am I doing wrong? Please help. :)

---

### Post by slickymaster on 2013-02-12
Can you run your script manually? If not, it's a problem with your script.

Does your script needs to run as root?

Another thing, ensure that the target script file is also marked executable.

---

### Post by Balthier1979 on 2013-02-12
> **CaptainMark said:**
> Okay, whichever you decide to do, you can add commands directly to /etc/rc.local in which case you don't need to specify anything other than the command you want to run
 

So this rc.local should work?

 
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
xset s 0 0
xset s noblank
xset dpms 30 30 30
xset -dpms
exit 0

```

Furthermore, what permissions should I set on rc.local with chmod for it to work?

---

### Post by Balthier1979 on 2013-02-12
> **slickymaster said:**
> Can you run your script manually? If not, it's a problem with your script.
 
Does your script needs to run as root?
 
Another thing, ensure that the target script file is also marked executable.
 
 
I can run it manually with **sh screen.sh** command. And it runst just fine. I can also include it in STARTUP APPLICATIONS, and it runs just fine. But I can not have rc.local call it at startup.

---

### Post by pqwoerituytrueiwoq on 2013-02-12
you only need to call a script wish sh if it is not executable
bash is not sh just so you know
your simple script could start with [FONT=Courier New]#!/bin/sh[/FONT] 

there are a few more places you can run commands at boot,there is also startup application in the user session
this is from my [FONT=Courier New]/etc/lighdm/lighdm.conf[/FONT]
```
#display-setup-script=sh -c "numlockx on;if [ -f /var/log/xbacklight ];then xbacklight -set $(cat /var/log/xbacklight);fi"
greeter-setup-script=sh -c "/usr/bin/numlockx on;if [ -f /var/log/xbacklight ];then xbacklight -set $(cat /var/log/xbacklight);fi;"
session-setup-script=sh -c "/usr/local/bin/xfce-login-script &"
session-cleanup-script=sh -c "/usr/local/bin/xfce-logout-script;xbacklight -get > /var/log/xbacklight"
```anything in [FONT=Courier New]/etc/lighdm/lighdm.conf[/FONT] and [FONT=Courier New]/etc/rc.local[/FONT] runs as root

---

### Post by Lars Noodén on 2013-02-12
If you need it to run as your user and after X is running, then you could put it in  ~/.xsessionrc

---

### Post by CaptainMark on 2013-02-12
+1 I use .xsessionrc for my raspberry pi which doesn't remember I have a UK keyboard even though I set the correct locale, and earlier versions worked fine,

it is possible that because x isn't running when /etc/rc.local is run then it is ignoring your commands (i cant remember its been awhile since I used it) , of course the other thing to remember is if you have your home directory encrypted and at boot your system is trying to run a script inside your home directory it will fail

ps. I went through this all before when I was using lxde on my raspberry pi actually so it should work for lubuntu, [http://www.raspberrypi.org/phpBB3/viewtopic.php?f=66&t=18200](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=66&t=18200) check out this post and note the post by jojopi, there are 3 methods to stop screen blanking (or rather to alter it) depending on the situation, 1. Booting straight to terminal 2.Booting to terminal and used startx to start lxde 3.Booting straight to graphical login manager,

---

### Post by Balthier1979 on 2013-02-12
Guys, you are talking to a complete linux noob, so I don't quite understand what you mean by "~/.xsessionrc" . :) Where is that file located? What does ~ mean?
 
I can run the script if I add it to Startup Applications on a test system (new installed with 12.10), but the problem is that on the system I am trying to run it on, has been upgraded from 11.04->11.10->12.04->12.10, and whenever I try to add or edit something on Startup Applications, it is not saved.
 
From where are startup applications files run? Is startup application a single folder?
 
I can find the /etc/xdg/autostart folder which contains a lot of .desktop files, but adding an .sh file there doesn't help. Neither does having a .desktop file call up the .sh file.

---

### Post by CaptainMark on 2013-02-12
Sorry, I got ahead of myself, when talking about file names in linux the tilde(~) character is a shortcut for the users home folder, the slash(/) just helps separates directories when writing them down, the period (.) at the start of a filename means that it is hidden and wont show up by default when you open your file browser (similar to hidden folders in windows but just identified by the leading period), and then the file name itself so the file
~/.xsessionrc

will be found in /home/[username]/.xsessionrc

just replace [username] with your actual username, if you open up a file browser and use the keyboard shortcut ctrl+h all your hidden folders/files will become visible, open ~/.xsessionrc with a text editor and you can add commands there, these commands will be run when you log into a graphical (X) session 
(if you see people say "start x" or "x session" this basically means loading the login manager or desktop as opposed to a command line only interface)

Also as a side note I don't know if you have two desktop environments installed or maybe have done in the past but as far as I'm aware lubuntu doesn't use the startup applications (please anyone point out if this is no longer the case), this is a program from another desktop environment and although it will appear in the menu still it wont actually do anything in lxde (thats lubuntus default environment)

---

### Post by Balthier1979 on 2013-02-12
I'm sorry I managed to set lubuntu as prefix, but I am running **Ubuntu**. I guess I can not change the prefix now?
 
I am running Ubuntu 12.10, and it has been upgraded from 11.04->11.10->12.04->12.10 If I add the script on Startup Applications, its not saved. But if I have a fresh install of 12.10, and add the script to Startup Applications, it is saved, and runs just fine at startup.
 
On my production machine, nothing can be added/removed/edited on Startup Applicataions. Which means that I don't have permissions to make changes there. which is why I was wondering if that is a folder which I can take ownership of? :)
 
I have installed gnome-shell extensions, so the desktop environment I am using is Gnome Classic (with no effects)

---

### Post by Balthier1979 on 2013-02-12
I think Startup Applications is located in /home/username/.config/autostart
So I took ownerrship of that folder
sudo chown username:groupname /home/username/.config/autostart
 
But when I add a file there, it gets the .desktop extension, why is that?
 
Btw, I could not find .xsessionrc, is it located in /home/username/.xsessionrc?

---

### Post by CaptainMark on 2013-02-12
Forget the .xsessionrc, now you've said your not running lubuntu that doesn't apply, if your running ubuntu then you should be able to adjust screen blanking by just going to power in the system settings from the menu, unless I'm mistaken about what you're trying to do, what is it you want to achieve exactly?

You've been getting instructions for lxde which is why you're having no luck so far

---

### Post by schragge on 2013-02-12
For GNOME, you can put your commands into *.gnomerc* in your home folder. That will work for any GNOME session whichever display manager (LightDM, GDM, KDM, XDM,  etc.) you use. 

If you put them into *.xsessionrc* instead, it will work in any desktop environment (GNOME, KDE, XFCE, LXDE), but only for the *default session*.

Besides, each display manager provides its own mechanism to execute startup scripts.  Commands put in there will work for any session managed by that DM.

For LightDM, it's */etc/lightdm/lightdm.conf*. Please do not edit it directly. How to configure LightDM, is described in Ubuntu Wiki: [uwiki]LightDM[/uwiki].

For GDM, it's usually */etc/gdm*/Init/Default*.  Configuration of GDM is described [here]("http://help.gnome.org/admin/gdm/3.1/configuration.html").

---

### Post by Balthier1979 on 2013-02-12
> **CaptainMark said:**
> Forget the .xsessionrc, now you've said your not running lubuntu that doesn't apply, if your running ubuntu then you **should** be able to adjust screen blanking by just going to power in the system settings from the menu, unless I'm mistaken about what you're trying to do, what is it you want to achieve exactly?
 
Should is the keyword. :) Turning off the blank screen/screensaver in Ubuntu 12.10 (and 12.04) seems to be a real pain. It seems to be a problem many are having. Turning it off in Power and Brightness&lock does not help at all. I can turn it off by installing xscrensaver, and have it run at startup, but then I get stuck with this screen in front of the full screen application I am trying to run
 
[http://s12.postimage.org/k0ixkwfb1/xscreensaver.png](http://s12.postimage.org/k0ixkwfb1/xscreensaver.png)
 
(Perhaps I can make a script that sends the ALT+F4 command to Ubuntu about two minutes after startup, to close that window?)
 
More info on what I want to achieve [http://ubuntuforums.org/showthread.php?t=2110791](http://ubuntuforums.org/showthread.php?t=2110791)
 
I really don't get why turning off the dpms for the screen should be so difficult. And why they don't release a patch that fixes the problem.

---

### Post by slickymaster on 2013-02-12
> **Balthier1979 said:**
> I think Startup Applications is located in /home/username/.config/autostart
So I took ownerrship of that folder
sudo chown username:groupname /home/username/.config/autostart
 
But when I add a file there, it gets the .desktop extension, why is that?
 
Btw, I could not find .xsessionrc, is it located in /home/username/.xsessionrc?

No, **.xsessionrc** file is located in ```
/etc/X11/
```

---

### Post by Balthier1979 on 2013-02-12
> **slickymaster said:**
> No, **.xsessionrc** file is located in ```
/etc/X11/
```
 
I am running Ubuntu 12.10 and not lubuntu, I managed to put lubuntu as prefix by a mistake. So perhaps .xsessionrc does not exist in Ubuntu? Because I can not find it there.

---

### Post by slickymaster on 2013-02-12
Lubuntu is a variant of Ubuntu that is lighter, less resource hungry and more energy-efficient by using lightweight applications and LXDE as its default GUI.

Both Lubuntu and Ubuntu share Two Major Important Things:
[LIST]
[*]Same Core System
[*]Same Repositories
[/LIST]

Lubuntu and Ubuntu belong to the same family and talking about each as totally different two systems is not correct since they have some things in common.

The differences between Lubuntu and Ubuntu are:
[LIST]
[*]Different DE (Desktop Enviroment) - Lubuntu uses LXDE while Ubuntu uses Unity as the default DE.
[*]Different Default Applications
[/LIST]
Other than that, they are the same. The DE (Desktop Enviroment) is what makes Lubuntu a lightweight OS, and of course the selected applications too.

---

### Post by slickymaster on 2013-02-12
> **Balthier1979 said:**
> ... So perhaps .xsessionrc does not exist in Ubuntu? Because I can not find it there.

Don't forget that, as CaptainMark mentioned in #18 post, **.xsessionrc** is a hidden file. In order to view it, you have to enable **View Hidden Files** in your file browser by hitting **Ctrl+H**.

---

### Post by Balthier1979 on 2013-02-12
Yes, I get the concept of hidden files, and I actually knew about . files being hidden, I just did not know what ~ was. I might be a linux illiterate, but I'm certified on several microsoft products, and work as an IT professional, so I am not a computer illiterate. So most of these concepts are not new to me. :)
 
I took ownership of /home/username/.config/autostart, so now I can run scripts at startup if I'd like. So I guess the problem can be set to solved.
 
I also noticed that the start up script of the applicaton (SignagePlayer) I was trying to run, was setting the same parameters as well, but it was not setting the xset s parameters, which meant that the screensaver stayed turned on, even if DPMS was turned off.
 
Talk about going the rounds just to turn off a damn screen saver. Would never have been an issue in Windows. :-D
 
Btw, the .desktop extension for the startup applications files is correct. The exec= is just pointing to the sh file to make the script run. And thank you all for the assistance.

---

### Post by CaptainMark on 2013-02-12
I've always just been able to disable screen saver in the power settings, working fine for me here

---

### Post by Balthier1979 on 2013-02-13
I think it depends on the display adapter and driver, whether its easy or hard to turn off the screen blanking/screen saver. I've seen several threads and articles on it, and they are all struggling with the same thing as I was.

---

