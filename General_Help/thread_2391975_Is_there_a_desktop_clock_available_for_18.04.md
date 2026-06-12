---
title: "Is there a desktop clock available for 18.04 ?"
date: 2018-05-15
forum: General Help
---

### Post by linuxyogi on 2018-05-15
Hi,

I used to use cairo-clock under 16.04 but cant find it in 18.04.

Is there a desktop clock available for 18.04 ?

---

### Post by dino99 on 2018-05-15
named: indicator-datetime

---

### Post by linuxyogi on 2018-05-15
> **dino99 said:**
> named: indicator-datetime

Just installed indicator-datetime but how do I launch it ?

```
$ indicator-datetime 
indicator-datetime: command not found


```

---

### Post by ajgreeny on 2018-05-15
I suspect it's a panel applet, not a normal application so right click in the panel and add it there.
PS:
I do not use the new gnome desktop so could be wrong but most clocks are panel applets.

---

### Post by linuxyogi on 2018-05-15
> **ajgreeny said:**
> I suspect it's a panel applet, not a normal application so right click in the panel and add it there.
PS:
I do not use the new gnome desktop so could be wrong but most clocks are panel applets.

In that case its not what I am looking for.

I am looking for something like this

[ATTACH=CONFIG]279706[/ATTACH]

---

### Post by RobGoss on 2018-05-15
Have you tried Conky manager?

---

### Post by linuxyogi on 2018-05-15
> **RobGoss said:**
> Have you tried Conky manager?

No but under 16.04 I was using Cairo Clock. I had set it to always on top,

How do I install Conky manager and how do I configure it ?

---

### Post by RobGoss on 2018-05-15
Please see the link here it has instructions on how to configure Conky
[http://www.teejeetech.in/p/conky-manager.html?m=1](http://www.teejeetech.in/p/conky-manager.html?m=1)

---

### Post by linuxyogi on 2018-05-15
> **RobGoss said:**
> Please see the link here it has instructions on how to configure Conky
[http://www.teejeetech.in/p/conky-manager.html?m=1](http://www.teejeetech.in/p/conky-manager.html?m=1)

Please dont misunderstand. I dont install anything outside of the official repo.

I checked and found that Conky Manager is not available in the repos but these are available

```
$ aptitude search Conky 
p   conky                                                                                         - highly configurable system monitor (transitional package)                                               
p   conky-all                                                                                     - highly configurable system monitor (all features enabled)                                               
p   conky-all:i386                                                                                - highly configurable system monitor (all features enabled)                                               
p   conky-all-dbg                                                                                 - highly configurable system monitor (all features enabled - debug)                                       
p   conky-all-dbg:i386                                                                            - highly configurable system monitor (all features enabled - debug)                                       
p   conky-cli                                                                                     - highly configurable system monitor (basic version)                                                      
p   conky-cli:i386                                                                                - highly configurable system monitor (basic version)                                                      
p   conky-cli-dbg                                                                                 - highly configurable system monitor (basic version - debug)                                              
p   conky-cli-dbg:i386                                                                            - highly configurable system monitor (basic version - debug)                                              
p   conky-std                                                                                     - highly configurable system monitor (default version)                                                    
p   conky-std:i386                                                                                - highly configurable system monitor (default version)                                                    
p   conky-std-dbg                                                                                 - highly configurable system monitor (default version - debug)                                            
p   conky-std-dbg:i386                                                                            - highly configurable system monitor (default version - debug)     

```

---

### Post by axiomanarcho on 2018-05-15
For any desktop type clock I use conky

---

### Post by linuxyogi on 2018-05-15
> **axiomanarcho said:**
> For any desktop type clock I use conky

Are you using Conky Manager or have you configured conky manually ?

---

### Post by deanr2 on 2018-05-15
Perhaps this is stating the obvious, but have you typed 'clock' into the software manager / boutique?

I'm not on Ubuntu 18.04 but there are a number of desktop clocks when I search my 'store'.

---

### Post by axiomanarcho on 2018-05-15
> **linuxyogi said:**
> Are you using Conky Manager or have you configured conky manually ?

I configured it manually I took a minimal lua conky script and configured it to my liking, you can do so much with conky if you are not afraid of changing scripts and editing it.

---

### Post by monkeybrain20122 on 2018-05-15
Can you just grab the .deb for Artful from [launchpad]("https://launchpad.net/ubuntu/+source/cairo-clock") and install it?

---

### Post by RobGoss on 2018-05-15
Conky all might be your best choice

---

### Post by mc4man on 2018-05-15
> **monkeybrain20122 said:**
> Can you just grab the .deb for Artful from [launchpad]("https://launchpad.net/ubuntu/+source/cairo-clock") and install it?
That .deb should work, otherwise there are many around I'd suspect. One could build tzclock in a few minutes, seems full featured.
screen shows cairo (left) and tzclock

---

### Post by again? on 2018-05-16
Here's one using conky.
[ATTACH=CONFIG]279710[/ATTACH]

```
sudo apt install conky-all
```
Download the attachment, extract and follow instructions in readMe.txt

Choose from 27 different clock faces.
Small size video showing the clock faces----> [https://streamable.com/y7bp5](https://streamable.com/y7bp5)

---

### Post by linuxyogi on 2018-05-16
I have installed conky. 

```
sudo apt install conky-all

```
Which file should I edit to configure conky ?

---

### Post by again? on 2018-05-16
There is a default config @ /etc/conky/conky.conf that is used if you haven't placed a config @ ~/.conkyrc

You have to create a config, or find one to download that displays a clock.
If you're new to conky you will have trouble creating a config to display a clock.

The attachment in my previous post contains a config and necessary files to display a clock.

---

### Post by kerry_s on 2018-05-16
> **guber2 said:**
> Here's one using conky.
[ATTACH=CONFIG]279710[/ATTACH]

```
sudo apt install conky-all
```
Download the attachment, extract and follow instructions in readMe.txt

Choose from 27 different clock faces.
Small size video showing the clock faces----> [https://streamable.com/y7bp5](https://streamable.com/y7bp5)

whats the panel at the bottom of your screenshot?

---

### Post by again? on 2018-05-16
> **kerry_s said:**
> whats the panel at the bottom of your screenshot?
tint2 and a one line conky on the right after the clock, designed to match.
(I uninstall xfce4-panel)

---

### Post by kerry_s on 2018-05-16
> **guber2 said:**
> tint2 and a one line conky on the right after the clock, designed to match.
(I uninstall xfce4-panel)

thanks

---

### Post by linuxyogi on 2018-05-16
Please share your conky config so that I can try it on ~/.conkyrc.

---

### Post by again? on 2018-05-16
> **linuxyogi said:**
> Please share your conky config so that I can try it on ~/.conkyrc.
The clock config?

---

### Post by linuxyogi on 2018-05-16
> **guber2 said:**
> The clock config?

Any config that includes a digital or analog clock.

---

### Post by again? on 2018-05-16
The config is in the attachment of my first post.
The attachment includes all the files needed including a conky config.

You don't have to place a config at ~/.conkyrc
You can use the **-c** option to load any config

Look at the readMe.txt in the attachment.
```
conky **-c** ~/.conky/analog_clock/conkyrc
```

or 
you could copy ~/.conky/analog_clock/conkyrc to ~/.conkyrc 
if you want to load the config by just running...
```
conky
```

---

### Post by linuxyogi on 2018-05-16
> **guber2 said:**
> The config is in the attachment of my first post.
The attachment includes all the files needed including a conky config.

You don't have to place a config at ~/.conkyrc
You can use the **-c** option to load any config

Look at the readMe.txt in the attachment.
```
conky **-c** ~/.conky/analog_clock/conkyrc
```

There is only a readme file in your attachment

[ATTACH=CONFIG]279712[/ATTACH]

I am getting this 

  ```
conky -c ~/.conky/analog_clock/conkyrc
conky: cannot open /home/ubuntu/.conky/analog_clock/conkyrc: No such file or directory

```

---

### Post by linuxyogi on 2018-05-16
Sorry I didnt notice it was a hidden folder. Now this works 

```
 conky -c ~/.conky/analog_clock/conkyrc 
```

But when I add it to startup applications it wont launch.

Also is there a way to display it "Always on Top" ?

---

### Post by again? on 2018-05-16
For start ups try adding a  10 sec pause (-p)....
```
conky -p 10 -c ~/.conky/analog_clock/conkyrc
```

For always ontop...
```
gedit ~/.conky/analog_clock/conkyrc 
```

At the fifth line...
```
own_window_hints undecorated,[COLOR="#A52A2A"]below[/COLOR],sticky,skip_taskbar,skip_pager
```

change [COLOR="#A52A2A"]below[/COLOR] to **above**

---

### Post by linuxyogi on 2018-05-16
> **guber2 said:**
> ...and the readMe.txt says

Open another instance of your file browser to Home and drag and drop.

I have already copied the .conky to my home folder,

Is there a way to display it "Always on Top" ?

Thanks a lot.

---

### Post by again? on 2018-05-16
Previous post edited.

---

### Post by linuxyogi on 2018-05-16
> **guber2 said:**
> For start ups try adding a  10 sec pause (-p)....
```
conky -p 10 -c ~/.conky/analog_clock/conkyrc
```

For always ontop...
```
gedit ~/.conky/analog_clock/conkyrc 
```

At the fifth line...
```
own_window_hints undecorated,[COLOR=#A52A2A]below[/COLOR],sticky,skip_taskbar,skip_pager
```

change [COLOR=#A52A2A]below[/COLOR] to **above**

Done but not working. Still stays below.

After modifying that line I closed and relaunched conky but still not working.

---

### Post by linuxyogi on 2018-05-16
[ATTACH]279714[/ATTACH]

This is the file

---

### Post by again? on 2018-05-16
Also modify the 3rd line from...
```
own_window_type **desktop**
```
to
```
own_window_type **normal**
```

---

### Post by linuxyogi on 2018-05-16
> **guber2 said:**
> Also modify the 3rd line from...
```
own_window_type **desktop**
```
to
```
own_window_type **normal**
```

It worked but the fonts are all messed up

Please see attachment
[ATTACH=CONFIG]279715[/ATTACH]

---

### Post by again? on 2018-05-16
OK.
Some settings can wash out images.

Try this config which is pure lua.
Extract and copy the **conky_lua_analog_clock** folder to your **~/.conky** folder.

To run...
```
conky -c ~/.conky/conky_lua_analog_clock/conkyrc
```

---

### Post by linuxyogi on 2018-05-16
> **guber2 said:**
> OK.
Some settings can wash out images.

Try this config which is pure lua.
Extract and copy the **conky_lua_analog_clock** folder to your **~/.conky** folder.

To run...
```
conky -c ~/.conky/conky_lua_analog_clock/conkyrc
```

This worked. Although on black background the clock is difficult to read but I will manage.

Thanks.

---

### Post by again? on 2018-05-16
You can change the colour of the various elements in the ~/.conky/conky_lua_analog_clock/clock3.lua file.

The comments are in Russian. Use google to translate if needed.

Most of the colour elements begin with [COLOR="#FF0000"]0x[/COLOR] then #colour.
eg
```
color_font = [COLOR="#FF0000"]0x[/COLOR]000000,
```
Draws black (#000000)

Changed to purple...
```
color_font = [COLOR="#FF0000"]0x[/COLOR][COLOR="#800080"]A600FF[/COLOR],
```

Make a backup of clock3.lua and have a play around.

---

### Post by linuxyogi on 2018-05-16
Okay. I will try.

---

### Post by again? on 2018-05-16
No problem.
P.S. If you didn't know, you can bring up a zenity dialog to show hex colours with...
```
zenity --color-selection
```

---

### Post by mdebusk on 2018-05-22
My apologies if I missed it, but I didn't see TzClock mentioned.

[https://theknight.co.uk/]("https://theknight.co.uk/")

---

### Post by uboldi on 2018-06-17
> **monkeybrain20122 said:**
> Can you just grab the .deb for Artful from [launchpad]("https://launchpad.net/ubuntu/+source/cairo-clock") and install it?

This solution worked fine for me.:cool:
Only, I had to check the man page and slightly change the command line options in my starting applications,
now it is:
```
cairo-clock -x 1200  --width 160 --height 160 --theme radium --sticky 
```

---

