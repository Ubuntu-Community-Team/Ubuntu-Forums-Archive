---
title: "Create an Icon for sudo command?"
date: 2008-05-01
forum: General Help
---

### Post by Gripp on 2008-05-01
my problem is that my MX5000 keyboard and mouse loose contact with the bluetooth software after just maybe 30 minutes of inactivity. 

my current solution is to break out the wired keyboard and mouse, which are currently permanent fixtures atop my case because of this, open a terminal and typ in  ```
sudo /etc/init.d/bluetooth restart
```  and then type in my PW

i have to do this very frequently.  and mind you, this is an HTPC in my living room - yeah, eye-swore from hell... 

so what i would like to have is a icon on my desktop that i click and it does this for me, PW included, so that i can at least get the wired keyboard back in storage...

so what do i need to do to get this created?

---

### Post by SPr on 2008-05-01
Right click the Desktop and choose "create launcher". For the command enter
```

gksudo /etc/init.d/bluetooth restart

```
Comments, name and custom icons are your choice.

You'll have to enter the password whenever you run the command though. I would be *very* surprised if there is any way of including the password within the command - which is the sticking point for you. I would look to see why the bluetooth connection keeps getting dropped when the keyboard or mouse is inactive.

---

### Post by chrisccoulson on 2008-05-01
There is a way of making sudo not ask for a password, but it isn't recommended and I'm not going to post how to do it. If you really want to be able to do it, then you can find it by searching Google.

---

### Post by ryanhaigh on 2008-05-01
Because sudo and its gui equivalent gksudo both require a password to be entered if you haven't done so in the last 10 minutes this is going to be a little more complex but is none the less achievable.

Put the following into /etc/rc.local, this script is run at startup as root so there will be no need to use sudo, replace yourusername with...well you get the idea. To edit the file open a terminal an use ```
sudo gedit /etc/rc.local
```

```

#!/bin/bash
#checks for a file in user home directory and if exists restarts service

while [ 1 ]
do
sleep 120
if [ -f /home/yourusername/.restartbluetooth ]; then
echo "file found restarting service"
/etc/init.d/bluetooth restart && rm /home/yourusername/.restartbluetooth
else
echo "file not found looping"
fi
done

```

After entering this into the file ensure that the file is executable using
```
sudo chmod +x /etc/rc.local
```

Now create a launcher on your desktop using whatever icon/name you want with the following command ```
touch /home/yourusername/.restartbluetooth
``` This will create the file that the rc.local script looks for resulting in the service being restarted.

---

### Post by unutbu on 2008-05-01
Perhaps this is not the best fix possible, but here is a way to run ```
/etc/init.d/bluetooth restart
``` as root every 30 minutes without having to type anything:

Go to a terminal and type

```
sudo crontab -e  
```

Edit the root's crontab to look like this:

```
# m h  dom mon dow   command
*/30 * * * * /etc/init.d/bluetooth restart
```

---

### Post by Green_Star on 2008-05-01
If you want to run this commend(using command line or launcher)you can do it with sudoers, you can restrict without password for only this command. Right now I am not at linux machine so I can not give you more details, search google. 
[http://www.google.ca/search?hl=en&q=run+sudo+command+without+password&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=run+sudo+command+without+password&btnG=Search&meta=)
first link may help you,
hope this helps for now.

---

### Post by ryanhaigh on 2008-05-01
A more generic version where the service and username are specified as variables

```

#!/bin/bash
#checks for a file in user home directory and if exists restarts service

SERVICE=ddclient
USERNAME=ryanhaigh

while [ 1 ]
do
sleep 2
if [ -f /home/$USERNAME/.restart$SERVICE ]; then
echo "file found restarting $SERVICE"
/etc/init.d/$SERVICE restart && rm /home/$USERNAME/.restart$SERVICE
else
echo "file not found looping"
fi
done

```

---

### Post by Oldsoldier2003 on 2008-05-01
> **chrisccoulson said:**
> There is a way of making sudo not ask for a password, but it isn't recommended and I'm not going to post how to do it. If you really want to be able to do it, then you can find it by searching Google.

Its posted in the wiki, so its not a problem talking about it. you just need to edit sudoers, but again its not something you should do lightly at a whim. [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Gripp on 2008-05-01
i'm not looking to disable the need for a PW when runnning the command - i do still want some amount of security in this regard

i was think of using bash to create an MD5 code of my PW and using that in a script related to the launcher keeping my PW safe even when being used automatically.  or maybe i can assign my wallet to auto enter it when i click the icon?
i dont know how to code at all, so maybe i'm missing some very basic concepts here ;)

edit: on second thought, if the md5 thing worked then they could still use that code to get to everythiung else... so ... i'm tired, that's my exuse, and i'm sticking to it!
so then, maybe make the viewing/editing of this one icon PW restricted?...


> **ryanhaigh said:**
> Because sudo and its gui equivalent gksudo both require a password to be entered if you haven't done so in the last 10 minutes this is going to be a little more complex but is none the less achievable.

Put the following into /etc/rc.local, this script is run at startup as root so there will be no need to use sudo, replace yourusername with...well you get the idea. To edit the file open a terminal an use ```
sudo gedit /etc/rc.local
```

```

#!/bin/bash
#checks for a file in user home directory and if exists restarts service

while [ 1 ]
do
sleep 120
if [ -f /home/yourusername/.restartbluetooth ]; then
echo "file found restarting service"
/etc/init.d/bluetooth restart && rm /home/yourusername/.restartbluetooth
else
echo "file not found looping"
fi
done

```

After entering this into the file ensure that the file is executable using
```
sudo chmod +x /etc/rc.local
```

Now create a launcher on your desktop using whatever icon/name you want with the following command ```
touch /home/yourusername/.restartbluetooth
``` This will create the file that the rc.local script looks for resulting in the service being restarted.

i've done everything you;ve said here.  replaced it with my username and looked for any typos.  when i clicked the launcher it creates a file .restartbluetooth but nothing happens from there.  and the file never gets removed... maybe the rc.local never runs?
i tried removing the exit 0 at the end as well, both variations produce the same result


edit: maybe i need to restart?  or is there a better way getting rc.local up and running?

---

### Post by chrisccoulson on 2008-05-01
> **ryanhaigh said:**
> A more generic version where the service and username are specified as variables

```

#!/bin/bash
#checks for a file in user home directory and if exists restarts service

SERVICE=ddclient
USERNAME=ryanhaigh

while [ 1 ]
do
sleep 2
if [ -f /home/$USERNAME/.restart$SERVICE ]; then
echo "file found restarting $SERVICE"
/etc/init.d/$SERVICE restart && rm /home/$USERNAME/.restart$SERVICE
else
echo "file not found looping"
fi
done

```

The problem with this is it only works for the one specified user unless you edit /etc/rc.local each time a user logs in (I don't know if that is an issue on the OP's machine).

Instead of creating and checking for a ~/.restartbluetooth, i'd probably create a /tmp/.restartbluetooth. With that, you could make it work in a multi-user setup I think.

Although, I think the OP should also try and get to the bottom of the actual problem

---

### Post by Green_Star on 2008-05-01
I would say editing sudoers is easy way. So that you can run specified command without sudo password, and all other sudo commands needs password.

---

### Post by Gripp on 2008-05-01
okay, so i let my keyboard sit untouched for a while and the luancher didn't work when it came time

there are other threads about this mouse/keyboard having this issue and the best "solution" that has been offered is that logitech has to fix it.  lol. 

it possible that maybe some script be made that sends a request signal to the keyboard asking for a response? just put that on a loop to run every 5 minutes or so and it should be problem solved... 


but back to the original solution - why isn't this working?  i see that the code says that if the file is present then delete it
but this doesn't happen.  even when i run chmod -x on it
and i cant find any errors in the code...

---

### Post by Gripp on 2008-05-01
okay. i did figure out that if i run ```
sudo sh /etc/rc.conf 
``` that it works

it holds the terminal instance and just keeps looping. and if i click the luancher then it does restart the bluetooth and remove the file. 

so i guess the prob is maybe that it isn't being recognized as a shell script?

i'm not certain what chmod does exactly that makes it diff from what i just did (yeah, noob - if ya hadn't already gathered that :) )

---

### Post by ryanhaigh on 2008-05-01
> **Gripp said:**
> okay. i did figure out that if i run ```
sudo sh /etc/rc.conf 
``` that it works

it holds the terminal instance and just keeps looping. and if i click the luancher then it does restart the bluetooth and remove the file. 

so i guess the prob is maybe that it isn't being recognized as a shell script?

i'm not certain what chmod does exactly that makes it diff from what i just did (yeah, noob - if ya hadn't already gathered that :) )


Did you mean rc.local? This file is run at startup so yes you will need to restart for this to take effect.
The #!/bin/bash should ensure that it is recognised as a shell script.
The chmod +x command ensures that the file is executable, if it is not then it wouldn't run at startup. 

I never considered making it multiuser but using /tmp certainly would be a simple way to do so.

Also what are the symptoms of this problem, perhaps instead of looking for a file the applicaiton could check whether a certain process is running or a certain device found when scanning bluetooth. The would completely remove the need for the launcher.

---

### Post by unutbu on 2008-05-02
Gripp, here is a solution where you don't have to do anything -- the computer will detect when bluetooth has lost the connection and will run the restart command (once a minute) until it's back up.

```
sudo crontab -e
```

A text editor (nano) should come up. Add this line:

```
* * * * * val=`hciconfig -a 2>/dev/null | head -c 1`; [ -z $val ] && /etc/init.d/bluetooth restart
```

Exit and save.

---

### Post by Gripp on 2008-05-02
thank you! :)

hopefully it works.  i have a slight angst that it wont b/c when looking in the GUI of the bluetooth manager it will usually show that both devices are still connected even though they aren't,,,

but we'll see!

---

### Post by unutbu on 2008-05-02
Hm. I don't have any experience with bluetooth so I'm a little lost here. Can you ping bluetooth devices?
If so, I could probably fashion a different test to determine if the connection was lost. 

Is there any command line program that shows different output when the connection is lost? If so, post the command and what the output looks like with and without a connection, and we'll be in business...

---

### Post by Gripp on 2008-05-02
no need
from everything i can tell this has worked great

i let it set for over an hour and still had a connection :)

now i just need to figure out how to get it to stop notifying me every few minutes that "the device has been made discoverable"

nothing in the options about notifications... soo?

---

### Post by unutbu on 2008-05-02
Do you know which command is creating this message?

---

### Post by Gripp on 2008-05-03
not a clue.  it is a notify bubble coming from the bluetooth manager icon.  

and YES! i left it over night and it was still connected in the morning :D

---

### Post by Gripp on 2008-05-03
i found this:

[http://article.gmane.org/gmane.linux.bluez.user/12988/match=dinovo+last](http://article.gmane.org/gmane.linux.bluez.user/12988/match=dinovo+last)

and i'm thinking that it might solve my issue, but i'm not certain how to implement it.  

i'm not sure what the XX.XX.XX. ... stuff is, and if it is the MAC address like i'm guessing, then how to find that info? or what hci* device the mouse or keyboard uses... or even how to "add a udev rule" for that matter...

let me know if this is as helpful as i'm guessing it might be... (one day be less of a noob... i swear... *sigh*)

---

### Post by unutbu on 2008-05-03
Sorry Gripp, I haven't the foggiest idea what that guy was talking about. :-k

As far as getting "the device has been made discoverable" message to stop... have you tried just quitting bluetooth manager? Is it a gnome panel icon? What happens if you remove the icon from the panel?

---

### Post by Gripp on 2008-05-05
no go.  now the bubble just appears at the lower right hand corner of the screen...

---

### Post by unutbu on 2008-05-05
run 

```
ps axuww
```

This will show all processes running on your computer. One of those must be making the message bubble.

Select a likely target. (Type 'man' and then the command to read a man page about the command.) The PID (process ID) is the number in the second column. For example

```
gripp    6900  0.0  0.0   2624  1004 pts/0    R+   19:34   0:00 ps axuww
```

The PID is 6900. To kill it, do

```
kill -9 6900
```

Kill the right process and the bubble should go away. Then you will also know what process creates the bubble. Once you know that, there should be a way to either stop that process from running or hopefully configure it to be quiet.

---

