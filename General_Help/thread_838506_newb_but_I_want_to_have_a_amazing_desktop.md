---
title: "newb but I want to have a amazing desktop"
date: 2008-06-23
forum: General Help
---

### Post by ontherooftop on 2008-06-23
OK so my graphics card works good with ubuntu 8.04 and I can 
tell its using its 1200x800 resolution , but I want any programs
or any help to make my desktop look kickass and show windows users
this (even though I dual with xp) but I want fireworks and all kinds
of crazy stuff with ubuntu that you can do to modify the desktop ,
I have seen some crazy youtube videos of how you can make ubuntu look
like that , any pointers. graphics is 965 intel graphics media , so 
it should be decent , it runs last gen games good like half life 2.

---

### Post by dasunst3r on 2008-06-23
To the best of my knowledge, the Intel driver is open-source, so you should be able to just go to System -> Preferences -> Appearance and enable the visual effects via the *visual effects* tab.

If you want even more control over how the effects work, you should install the *compizconfig-settings-manager* package: In the terminal, type *sudo apt-get install compizconfig-settings-manager*.

---

### Post by rainwalker on 2008-06-23
Agreed, compizconfig-settings-manager (usually abbreviated CCSM) is king :)

---

### Post by rico002 on 2008-06-23
hello, im a huge newb this is my first time wit ubuntu, i typed in the given command and i get this message "E: Couldn't find package compizconfig-setting-manager

 i have ubuntu 8.04 32 bit

---

### Post by rainwalker on 2008-06-23
Make sure you type this exactly:
> compizconfig-settings-manager
Copy and paste if you need to.
If that doesn't work, go to System > Administration > Software Sources and enable everything under the "Ubuntu Software" tab except for the CD-ROM, click Close, and reload the packages when it asks. Then, try installing that again

---

### Post by rico002 on 2008-06-23
> **rainwalker said:**
> Make sure you type this exactly:

Copy and paste if you need to.
If that doesn't work, go to System > Administration > Software Sources and enable everything under the "Ubuntu Software" tab except for the CD-ROM, click Close, and reload the packages when it asks. Then, try installing that again

ok i get the same message

---

### Post by rainwalker on 2008-06-23
It still can't find the package? That's really weird...

Let me try to find a deb for you

---

### Post by rico002 on 2008-06-23
yea this is really frustrating for me.....i want the cube and all the different effects like the fire paint and i dunno wut im doing wrong

---

### Post by raul_ on 2008-06-23
could you post the output of 

```

sudo aptitude search compiz

```

including the command?

---

### Post by DaymItzJack on 2008-06-23
In your post you had "setting" instead of "setting**_s_**", type it correctly.

---

### Post by rico002 on 2008-06-23
> **raul_ said:**
> could you post the output of 

```

sudo aptitude search compiz

```

including the command?
i get this 
i   compiz                          - OpenGL window and compositing manager     
p   compiz-bcop                     - Compiz option code generator              
i   compiz-core                     - OpenGL window and compositing manager     
p   compiz-dev                      - OpenGL window and compositing manager - de
i   compiz-fusion-plugins-extra     - Collection of extra plugins from OpenCompo
i   compiz-fusion-plugins-main      - Collection of plugins from OpenCompositing
i   compiz-gnome                    - OpenGL window and compositing manager - GN
i   compiz-plugins                  - OpenGL window and compositing manager - pl
i   compizconfig-backend-gconf      - Settings library for plugins - OpenComposi
i   libcompizconfig0                - Settings library for plugins - OpenComposi
p   libcompizconfig0-dev            - Development file for plugin settings - Ope

> **DaymItzJack said:**
> In your post you had "setting" instead of "setting**_s_**", type it correctly.
 yea i kno i meant to put settings but i typed it in right

---

### Post by raul_ on 2008-06-23
can you run the command ccsm ?

---

### Post by rico002 on 2008-06-23
> **raul_ said:**
> can you run the command ccsm ?
yea but its says couldnt be found

---

### Post by ad_267 on 2008-06-23
compizconfig-settings-manager is in the universe repositories. Go to system - administration - synaptic. Go to settings - repositories and tick next to universe, restricted and multiverse. Hit close then reload and then try again.

You can also install the package from there.

---

### Post by rico002 on 2008-06-23
> **ad_267 said:**
> compizconfig-settings-manager is in the universe repositories. Go to system - administration - synaptic. Go to settings - repositories and tick next to universe, restricted and multiverse. Hit close then reload and then try again.

You can also install the package from there.

ok ill try that....also dont need to be connected to the internet to do this cuz im on my pc and linux is on a laptop and i dunno/cant configure the wifi so i hope i dont need the internet

---

### Post by ad_267 on 2008-06-24
> **rico002 said:**
> ok ill try that....also dont need to be connected to the internet to do this cuz im on my pc and linux is on a laptop and i dunno/cant configure the wifi so i hope i dont need the internet

Yes you need to be connected to the internet.

---

### Post by rico002 on 2008-06-24
> **ad_267 said:**
> Yes you need to be connected to the internet.

nooooooooooooooooooooooooooooooooooooooo

---

### Post by rico002 on 2008-06-24
wait sweetttt i got internet workin

---

### Post by rico002 on 2008-06-24
ok when i do sudo apt-get install compizconfig-settings-manager
i get 
could get lock /var/lib/dpkg/lock -open (11 resource temp unavailable 
E:unable to unlock the administration directory (var/lib/spkg) us another processor using it?

---

### Post by ad_267 on 2008-06-24
Do you still have synaptic package manager open? You need to close that.

---

### Post by rico002 on 2008-06-24
> **ad_267 said:**
> Do you still have synaptic package manager open? You need to close that.

ok i got it workin no i just need 2 kno how to make the cube thing

---

### Post by ad_267 on 2008-06-24
Go to general options - Desktop size. Set the horizontal virtual size to 4, vertical virtual size to 1, number of desktops to 1.

Go back and then enable the "Desktop Cube" plugins and "Rotate Cube" plugins. Experiment with the settings on these. Ctrl + Alt + Left/Right rotates. Ctrl + Alt +  Left Mouse Button lets you rotate it with your mouse.

---

### Post by rico002 on 2008-06-24
i truly love u.....no homo...thanks a million really :guitar::guitar::guitar::guitar::popcorn::popcorn::popcorn::popcorn:
i need to experiment more thanks so much again

---

### Post by guber112 on 2008-06-24
Hello, I'm having a similar problem. I've installed Xgl and Compize; activate the Cube settings but it still doesn't work. I'm using Ubuntu 8.04 with a Nvidia 7800 GT (with the linux drive from Nvidia website). Any suggestions on what's going on? Thank you!

---

### Post by rico002 on 2008-06-24
ok got another problem..ihope its very simple to fix.....the top bar of a window is missing like X button and the minimize and maxmize bar are missing from all windows

---

### Post by ad_267 on 2008-06-24
> **rico002 said:**
> ok got another problem..ihope its very simple to fix.....the top bar of a window is missing like X button and the minimize and maxmize bar are missing from all windows

Is it just the buttons or the whole window border? Try pressing "alt+F2" then enter "gtk-window-decorator --replace" or if you are using emerald "emerald --replace"

> **guber112 said:**
> Hello, I'm having a similar problem. I've installed Xgl and Compize; activate the Cube settings but it still doesn't work. I'm using Ubuntu 8.04 with a Nvidia 7800 GT (with the linux drive from Nvidia website). Any suggestions on what's going on? Thank you!

So is compiz working but just not the cube plugin? Do you have horizontal virtual size set to at least four?

---

### Post by guber112 on 2008-06-24
Yes, I believe compize is working. I did set the screen to 4. Is there a way to check if compize is working properly?

---

### Post by rico002 on 2008-06-24
yea the whole border is gone

---

### Post by ad_267 on 2008-06-24
> **rico002 said:**
> yea the whole border is gone
In the compizconfig-settings-manager make sure the window decoration plugin is enabled and the command is set to "gtk-window-decorator --replace"
Then press alt+F2 and run "gtk-window-decorator --replace"


> **guber112 said:**
> Yes, I believe compize is working. I did set the screen to 4. Is there a way to check if compize is working properly?
Do your windows have shadows? If not press Alt+F2 and run "compiz --replace" or go to system - preferences - appearance - visual effects and set them to custom. If there isn't any custom option then install the simple-ccsm package and then try and select custom.

---

### Post by guber112 on 2008-06-24
I can't apply the visual effect. Any idea what's causing this? Thank you..

---

### Post by ad_267 on 2008-06-24
> **guber112 said:**
> I can't apply the visual effect. Any idea what's causing this? Thank you..

Go to accessories - terminal and enter "compiz --replace" and then post the output here.

What video card do you have? If it is ati or nvidia do you have the restricted drivers enabled? Your video card might not be supported by compiz.

---

### Post by guber112 on 2008-06-24
Here's the output: 
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

I have a nvidia 7800 GT.

---

### Post by ad_267 on 2008-06-24
> **guber112 said:**
> Here's the output: 
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

I have a nvidia 7800 GT.

Have you installed the nvidia driver? Go to system - administration - hardware drivers and make sure there is a tick next to the nvidia drivers. You will need to restart if to enable the driver.

---

### Post by guber112 on 2008-06-24
I thought, I did... the System hardware didn't have anything there

---

### Post by dasunst3r on 2008-06-24
For those of you who just joined in, this person is using an integrated Intel graphics card.

---

### Post by ad_267 on 2008-06-24
> **dasunst3r said:**
> For those of you who just joined in, this person is using an integrated Intel graphics card.

The original poster does but there's two more people asking for help here now. It's a party in here!

> **guber112 said:**
> I thought, I did... the System hardware didn't have anything there

Hmm ok anyone know if the 7800 gt should be recognised by default on Hardy? You might have to install the drivers using envy.

---

### Post by guber112 on 2008-06-24
I'll give that a try... if it doesn't work I'm calling it a night.. Thanks for all the help!

---

### Post by ad_267 on 2008-06-24
> **guber112 said:**
> I'll give that a try... if it doesn't work I'm calling it a night.. Thanks for all the help!

I just had another look at your original post and you said you installed xgl and compiz. How did you install them? Compiz should be included by default and you shouldn't need to install xgl. That could be the problem.

---

### Post by shellhrs on 2008-06-24
FYI: I just installed Hardy on IBM T30, and although it doesn't have any restricted driver -- which means that I should be able to run ccsm without any problem, I had to manually edit xorg.conf (unlike Feisty which automatically detected Radeon 7500). Still, I wasn't able to run ccsm until I installed xserver-xgl. So maybe you DO need to have xgl on some system.

---

### Post by ad_267 on 2008-06-24
> **shellhrs said:**
> FYI: I just installed Hardy on IBM T30, and although it doesn't have any restricted driver -- which means that I should be able to run ccsm without any problem, I had to manually edit xorg.conf (unlike Feisty which automatically detected Radeon 7500). Still, I wasn't able to run ccsm until I installed xserver-xgl. So maybe you DO need to have xgl on some system.

Yeah you do for some systems but I have an nvidia 6600 gt and I didn't need it, I'm guessing it would be the same for a 7800 gt.

---

### Post by rico002 on 2008-06-24
gtk ......replace command doesnt work

---

### Post by ad_267 on 2008-06-24
> **rico002 said:**
> gtk ......replace command doesnt work

What does it say if you enter it in a terminal? Did it only start doing this after enabling the cube plugin?

---

### Post by rico002 on 2008-06-24
> **ad_267 said:**
> What does it say if you enter it in a terminal? Did it only start doing this after enabling the cube plugin?

i thnk it wants to replace the window but it doesnt....and it was ok and then it went away....like when i first got the cube working the window went away like 10 minutes later and gone since then

---

### Post by ad_267 on 2008-06-24
> **rico002 said:**
> i thnk it wants to replace the window but it doesnt....and it was ok and then it went away....like when i first got the cube working the window went away like 10 minutes later and gone since then

Did you enter it into a terminal or into the dialog box with Alt-F2? You need to enter it with Alt-F2 or it will disappear when you close the terminal. If it's just disappearing for no reason after it's been running for a while then I don't know why that would happen.

---

### Post by rico002 on 2008-06-24
> **ad_267 said:**
> Did you enter it into a terminal or into the dialog box with Alt-F2? You need to enter it with Alt-F2 or it will disappear when you close the terminal. If it's just disappearing for no reason after it's been running for a while then I don't know why that would happen.

yea i did both alt2 and terminal...how could that have happened...do u think if i take off compiz and the enable it again will solve the prob.

---

### Post by ad_267 on 2008-06-24
> **rico002 said:**
> yea i did both alt2 and terminal...how could that have happened...do u think if i take off compiz and the enable it again will solve the prob.

It could help. Try going to System - Preferences - Appearance - Visual Effects and set them to normal. Everything should be set to defaults then and should work. Then just change the horizontal virtual size and enable the cube and rotate cube plugins and nothing else and see if that works ok.

---

### Post by Enlitend on 2008-06-24
Hi rico002

Get the compiz-fusion icon tray to handle that problem for you.
```
sudo apt-get install fusion-icon
```
It should be in the Application->System Tools->Compiz Fusion Icon
click to launch it. It will show up on the system tray.
Right click on it and mouse over "Select Window Decorator" and click on "GTK window decorator".

Make it auto-start on startup:

System->Preferences->Sessions->Add

Name: Compiz-Fusion Icon
Command: fusion-icon --no-start

click OK and Ctrl-Alt-BackSpace and re-login to test it.

---

### Post by rico002 on 2008-06-24
> **Enlitend said:**
> Hi rico002

Get the compiz-fusion icon tray to handle that problem for you.
```
sudo apt-get install fusion-icon
```
It should be in the Application->System Tools->Compiz Fusion Icon
click to launch it. It will show up on the system tray.
Right click on it and mouse over "Select Window Decorator" and click on "GTK window decorator".

Make it auto-start on startup:

System->Preferences->Sessions->Add

Name: Compiz-Fusion Icon
Command: fusion-icon --no-start

click OK and Ctrl-Alt-BackSpace and re-login to test it.

i did just that...and i still missing the bar....its too weird

---

### Post by ad_267 on 2008-06-24
That is weird. Do you lose the window borders if you set effects back to normal?

---

### Post by Enlitend on 2008-06-24
hmm...try right click the fusion-icon on the tray and click on "Reload Window Manager".

---

### Post by rico002 on 2008-06-24
> **Enlitend said:**
> hmm...try right click the fusion-icon on the tray and click on "Reload Window Manager".

same thing

---

### Post by ad_267 on 2008-06-24
> **rico002 said:**
> same thing

Well you could try installing Emerald and using that as a window manager for Compiz. It's what I use and has better effects.

> sudo apt-get install emerald

Then you can select emerald as the window decorator using the compiz fusion icon. And from the compiz fusion icon you can select "Emerald Theme Manager" to choose a theme. Ubuntu doesn't have an Emerald theme package for Hardy but you can download themes from [http://gnome-look.org](http://gnome-look.org). I use the radial_thinner theme.

---

### Post by rico002 on 2008-06-24
but i dont have emerald....how and y is compiz so unstable it freezes/crashes when i do some effects

---

### Post by ad_267 on 2008-06-24
> **rico002 said:**
> but i dont have emerald....how and y is compiz so unstable it freezes/crashes when i do some effects

You can install emerald with that command. "sudo apt-get install emerald"

Maybe if compiz is unstable for you you should leave the desktop effects off. It works well for most people but there may be issues with your setup that it doesn't work well with.

---

### Post by Enlitend on 2008-06-24
Well, I think it's getting pretty stable lately once you set it up correctly.

One last try:
CCSM -> Window Decoration ( make sure that box is checked)
look for the "Command" line, along the line to the righ, click the 'reset to default' button.( mine is /usr/bin/compiz-decorator).

Alt-F2 and type in 
```
compiz --replace
```
see what you get or follow ad_267  suggestion and install emerald.

---

