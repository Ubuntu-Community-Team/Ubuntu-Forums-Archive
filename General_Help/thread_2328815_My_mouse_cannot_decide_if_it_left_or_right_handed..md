---
title: "My mouse cannot decide if it left or right handed."
date: 2016-06-24
forum: General Help
---

### Post by makem2 on 2016-06-24
I have a Logitech M505 mouse which I prefer to use left handed with Ubuntu 14.04.4 LTS. I set it in Mouse and Touchpad and use the close button. It does not have any effect, mouse remains right handed.

I go to Settings Manager as another way of getting to Mouse and Touchpad and make a left hand selection with same result, still right handed.

Now, sometimes when I do these things it does stick and does survive reboots for a while. Then after a reboot, back to square one. This time is seems permanent that I cannot change the hand, hence this post for help.

Is it the mouse of the OS that is causing the problem? Is there another non-gui way to make the setting?

---

### Post by QDR06VV9 on 2016-06-24
What is the output of this in the terminal
```
xinput list
```
Paste Back Here

---

### Post by makem2 on 2016-06-24
```

makem@ssdTOSH:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M505/B605                          id=14    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=12    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                     id=13    [slave  keyboard (3)]
makem@ssdTOSH:~$ 

```

---

### Post by QDR06VV9 on 2016-06-24
In the above the USB mouse has id=14. We will use this id in the following command which will swap buttons to be left handed only for the USB mouse (and not for touchpad):

```
xinput set-button-map 14 3 2 1
```
Let Me know if this works to your liking while I try to make permanent.(Survive a Reboot)

---

### Post by makem2 on 2016-06-24
Yes, that changes the button.

Fstab? Shouldn't need do that?

---

### Post by QDR06VV9 on 2016-06-24
> Fstab? Shouldn't need do that?
Please make clear on what you are saying or asking.

---

### Post by makem2 on 2016-06-24
Sorry, in a roundabout way I was suggesting/asking if an entry in fstab could perform the setting you suggested.

---

### Post by makem2 on 2016-06-24
I found this but a bit beyond me:

[http://askubuntu.com/questions/492744/how-do-i-automatically-remap-buttons-on-my-mouse-at-startup](http://askubuntu.com/questions/492744/how-do-i-automatically-remap-buttons-on-my-mouse-at-startup)

```

makem@ssdTOSH:~$ xinput list 14
Logitech M505/B605                          id=14    [slave  pointer  (2)]
    Reporting 7 classes:
        Class originated from: 14. Type: XIButtonClass
        Buttons supported: 24
        Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" "Button Side" "Button Extra" "Button Forward" "Button Back" "Button Task" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown"
        Button state:
        Class originated from: 14. Type: XIValuatorClass
        Detail for Valuator 0:
          Label: Rel X
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 14. Type: XIValuatorClass
        Detail for Valuator 1:
          Label: Rel Y
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 14. Type: XIValuatorClass
        Detail for Valuator 2:
          Label: Rel Horiz Wheel
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 14. Type: XIValuatorClass
        Detail for Valuator 3:
          Label: Rel Vert Wheel
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 14. Type: XIScrollClass
        Scroll info for Valuator 2
          type: 2 (horizontal)
          increment: 1.000000
          flags: 0x0
        Class originated from: 14. Type: XIScrollClass
        Scroll info for Valuator 3
          type: 1 (vertical)
          increment: -1.000000
          flags: 0x2 ( preferred )

makem@ssdTOSH:~$ 


```
Maybe of help.

---

### Post by QDR06VV9 on 2016-06-24
> Sorry, in a roundabout way I was suggesting/asking if an entry in fstab could perform the setting you suggested.
No I do not think so...The ID on the USB mouse can change after multiple reboots. 
But try this one as added to startup applications.
```
sh -c "for id in `/usr/bin/xinput list | /bin/grep 'USB Mouse' | /bin/grep -o [0-9][0-9]`; do xinput set-button-map $id 3 2 1
```
Test it for a bit with reboots and let me know if you are happy.
Oh yes forgot to add if you want to revert back:
```
xinput set-button-map 14 1 2 3
```
Providing the ID is still the same..I think you now know how to pull that ID#
Kind Regards

---

### Post by makem2 on 2016-06-24
"As added to startup applications

I don't know where the startup applications exist." Would you explain please?

I have added that code as a command in in the Application Autostart in Settings Manager.

I will not know if it worked for many reboots as it sometimes survives multiple reboots.

I will report back and thank you.

---

### Post by QDR06VV9 on 2016-06-24
What Desktop are you using IE Unity, Mate. XFCE,LXDE?

---

### Post by makem2 on 2016-06-25
The method I used to put the code , or the code itself did not work.

After one reboot I am back with a right handed mouse.

I am using the default desktop included in the xubuntu install.

XFCE is what I find.

---

### Post by QDR06VV9 on 2016-06-25
Was this where you placed the sh script?
```
xfce4-session-settings
```

---

### Post by makem2 on 2016-06-25
> **runrickus said:**
> Was this where you placed the sh script?
```
xfce4-session-settings
```

No, I went to settings manager > system > session and startup > application autostart, where I made a new entry in which I put the sh code as the command.

Looking in /usr/bin I see:

-rwxr-xr-x  1 root   root      104680 Mar 21  2014 xfce4-session-settings
-rwxr-xr-x  1 root   root       71920 Mar 31  2014 xfce4-settings-editor
-rwxr-xr-x  1 root   root       51360 Mar 31  2014 xfce4-settings-manager

From that I would assume I need to use the settings editor. correct?

Edit: But looking in those three place, they do not appear to be where anything could be put.

---

### Post by QDR06VV9 on 2016-06-25
> **makem2 said:**
> No, I went to settings manager > system > session and startup > application autostart, where I made a new entry in which I put the sh code as the command.

Looking in /usr/bin I see:

-rwxr-xr-x  1 root   root      104680 Mar 21  2014 xfce4-session-settings
-rwxr-xr-x  1 root   root       71920 Mar 31  2014 xfce4-settings-editor
-rwxr-xr-x  1 root   root       51360 Mar 31  2014 xfce4-settings-manager

_**From that I would assume I need to use the settings editor. correct?**_

Yes That would work.
But I fear my code might be a bit off for the "sh script" give me a little time to see if I can come up with something better.
In the mean time post back the out put of this
```
apt-cache policy xmodmap
```
I might use this way instead.

---

### Post by QDR06VV9 on 2016-06-25
Ok I got it now...I have a close cousin to your mouse mine is a "Logitech M510"
And i have created an VB 14.04 XFCE session and this has survived multiple reboots with the Device ID changing with reboots.
So add this to your Startup Applications.
```
xinput set-button-map "Logitech M505/B605" 3 2 1
```
That should get you happy.:D

---

### Post by makem2 on 2016-06-25
> **runrickus said:**
> Ok I got it now...I have a close cousin to your mouse mine is a "Logitech M510"
And i have created an VB 14.04 XFCE session and this has survived multiple reboots with the Device ID changing with reboots.
So add this to your Startup Applications.
```
xinput set-button-map "Logitech M505/B605" 3 2 1
```
That should get you happy.:D

I have replaced the sh code with the command you suggest and will wait to see what happens.

Thank you for your input.

As a matter of interest, I got fed up of using a right hand mouse with my left hand so used: 
xinput set-button-map 14 3 2 1

When I checked the entry in settings manager it showed I was using a right hand mouse, although in fact it was working as left hand.

The xinput setting had no effect on the setting via the gui.

---

### Post by QDR06VV9 on 2016-06-25
Your Welcome! Hope it works as well for you as it is for me.
> The xinput setting had no effect on the setting via the gui.
Yes that is an on going bug...I don't have the link for it ATM but a couple o friends of mine are also left handed so I had to come up with a work around.
Keep us posted.
Kind Regards

---

### Post by makem2 on 2016-06-25
Yes, I will report later.

I am not left handed but can cope quite well, (rather like I do driving on the right). I swap hands every few months to avoid RSI.

---

### Post by QDR06VV9 on 2016-06-25
> **makem2 said:**
> Yes, I will report later.

I am not left handed but can cope quite well, (rather like I do driving on the right)._** I swap hands every few months to avoid RSI**_.
You know that is a good idea to swap hands from time to time.:)
I should have included the revert back also..but by now you probably already know to just reverse the code to 
```
xinput set-button-map "Logitech M505/B605" 1 2 3
```
To go back to Right Hand.

---

### Post by makem2 on 2016-06-26
After several reboots the setting has survived.

Happy bunny here, many thanks.

---

### Post by makem2 on 2016-07-02
Well here we are again!

I have to report that my mouse is right handed again!

The settings survived many many reboots so I cannot grumble

I have over the past weeks been swapping between xubuntu and windows very often. Most of those times, in windows the user wanted a right hand mouse. Most times when I forgot to change the windows settings, it stayed left handed when I returned to xubuntu, except for this one time today.

Can I mark the thread partially solved?

---

### Post by QDR06VV9 on 2016-07-02
You can leave it unsolved if you wish.:)
Out of curiosity is this a UEFI Bios computer?

---

### Post by makem2 on 2016-07-02
Yes it is.

---

### Post by QDR06VV9 on 2016-07-02
I will run some test's today to see if I can come up with a better option.
Will report back here.
Regards

---

### Post by makem2 on 2016-07-02
```

makem@ssdTOSH:~$ xinput set-button-map 14 3 2 1
device has no buttons
makem@ssdTOSH:~$ xinput set-button-map "Logitech M505/B605" 3 2 1
unable to find device 'Logitech M505/B605'
makem@ssdTOSH:~$ 

```

Edit: Settings manager can change it

---

### Post by QDR06VV9 on 2016-07-02
> **makem2 said:**
> ```

makem@ssdTOSH:~$ xinput set-button-map 14 3 2 1
device has no buttons
makem@ssdTOSH:~$ xinput set-button-map "Logitech M505/B605" 3 2 1
unable to find device 'Logitech M505/B605'
makem@ssdTOSH:~$ 

```

Edit: Settings manager can change it
I am not sure what you are saying here? I can see that the mouse is not found...moving forward now.
New Workaround... Ok This kind of a cheesey work around, what I did is create a couple of panel Application Launchers.
1. Righthanded Mouse and the code was: 
```
xmodmap -e "pointer = 1 2 3"
```
You will have to use the option to run in terminal.

2.Lefthand Mouse and the code was:
```
xmodmap -e "pointer = 3 2 1"
```
Again using the option to run in the terminal.
Test it out and let me know.

---

### Post by makem2 on 2016-07-02
Ok thank you.

The code is working for me so will let you know how stable it is.

---

### Post by QDR06VV9 on 2016-07-02
Your Welcome!:)
That should always work, xmodmap is the command to change the mouse button mapping.

---

### Post by QDR06VV9 on 2016-07-02
So Now if you want to make that persistent over sessions, put the mapping into the file
```
~/.Xmodmap
```
If it does not exist, create it, like 
```
touch ~/.Xmodmap
```
This will add (if not there already) a hidden file in your Home Directory ~/.Xmodmap
Now just add this to that file (Document)
```
pointer = 3 2 1
```
Now you will boot to a left handed mouse on every session...until you edit it to right handed again which I will add that line for clarity
```
pointer = 1 2 3
```
That should also last booting to windows and back to xubuntu.
You can  also keep the two custom Application Launchers, and switch on the fly anytime.
I just should have done it this way in the beginning.:)

---

### Post by makem2 on 2016-07-02
I am very grateful for your input and have recorded the code in my book for reference.

This time I will not mark it solved until a a few weeks, (just before I go traveling again)

---

### Post by makem2 on 2016-07-02
I have just shut down and then restarted xubuntu which was shut down from xubuntu. Not a reboot.

I am afraid the mouse is Right Handed :-(

In /home/makem I have a file .Xmodmap which contains the code::

```

pointer = 3 2 1

```

Settings show the mouse is Left Handed!

Using Settings I changed the mouse to RH but it made the mouse work LH!

Just what is going on? It appears the computer you are testing on is not working as mine is.

---

### Post by QDR06VV9 on 2016-07-02
You know I just do not know what is up with your machine but this is tested on 4 Machine's here.
2 towers AMD and Intel, Operating systems are various Distro's Ubuntu 14.04 Yackkety 16.10 (Development Cycle) Arch, and Debian Rolling.
All have survived multiple reboots with the desired setting, Left Handed Mouse.
I am all out of Idea's Here:confused:
EDIT: Do you still have the first method in Start Up Applications?
If you do remove it.
This from man xmodmap
> EXAMPLES
       Many pointers are designed such that the first button is pressed  using
       the  index  finger  of the right hand.  People who are left-handed fre&#8208;
       quently find that it is more comfortable to reverse  the  button  codes
       that  get  generated  so  that  the primary button is pressed using the
       index finger of the left hand.  This  could  be  done  on  a  3  button
       pointer as follows:
       %  xmodmap -e "pointer = 3 2 1"



---

### Post by makem2 on 2016-07-03
Yes,you are correct, in the Start Up Applications was the entry xinput set-button-map "Logitech M505/B605" 3 2 1.

I have removed it and will continue with testing after a reboot to clear everything.

I have rebooted once, shut down and restarted once. I removed the startup entry first. I have set the mouse to LH in Settings Manager. I have run the code xmodmap -e "pointer = 3 2 1"

The mouse is RH and remains RH. It appears that now I am unable to change it. Is there any way to clear all mouse settings and revert them to default?

Edit: It has settled down again now and is working.

---

### Post by makem2 on 2016-07-05
Still surviving so I am going to mark solved :)

Many thanks.

---

