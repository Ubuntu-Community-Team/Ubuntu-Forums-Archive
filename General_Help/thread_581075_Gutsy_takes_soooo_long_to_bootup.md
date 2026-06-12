---
title: "Gutsy takes soooo long to bootup"
date: 2007-10-19
forum: General Help
---

### Post by enchance on 2007-10-19
Whenever I'd restart it would take forever for my gutsy to bootup to its user login screen. My screen would just be blank (black) for like 2-3 mins before finally loading gutsy. I think it happens once grub runs. Should I go back to 7.04? I used a fresh install (no dual boot) with manual partioning.

---

### Post by mahousaru on 2007-10-19
Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

---

### Post by entangled on 2007-10-19
My Mac Mini is also much slower to boot Gutsy than Feisty. VT1 shows that it waits a long time just after reporting a problem with libencrypt.

---

### Post by enchance on 2007-10-19
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.


It worked! I changed it since it said 1280x1024, which is wrong for my laptop. But why did it even register my screen as 1280x1024 in the first place?

---

### Post by mahousaru on 2007-10-19
I think the live cd's splash screen messes up some laptop displays.  Sometimes on boot some of them need nosplash=y on the boot options or it hangs during install process.

7.10 seems a bit more aggressive with its initial screen resolution on VMware it went for some crazy resolution and I had to manually set it to a usable one.  I think that 7.04 picked a more sensible one, but it was ages since I tried it so can't really remember.

---

### Post by JoJerome on 2007-10-20
Exact same problem here, so I may as well revive this thread. Way newbie Linux user here:

How do I find out what my screen specs are supposed to be?
What is the actual command to check? Based on the replies here I tried...

```

~$ /etc/usplash.conf
bash: /etc/usplash.conf: Permission denied

```

Thanks in advance for any help.

- Jo

---

### Post by Perpetual on 2007-10-21
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

Thanks for this.  Was getting very annoyed with the minute long pause during boot!

---

### Post by Pro75357 on 2007-10-21
Hello,

I tried mahousaru's method: changed to the proper resolutions, ran the update, and at next boot I get:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

This also occurs when I try to boot in safe mode.  However, other people seem to have this kernel panic problem for different reasons, so it may not be related...

And JoJerome, in a terminal you would type:   sudo gedit /etc/usplash.conf
and then it would want your password...

EDIT:  Did a fresh install, then this fix and it worked... no kernel panic.  Apparently something else crashed my system.

---

### Post by moeFinley on 2007-10-21
Thank you mahousaru it work great with my T41 Thinkpad which should be set to 1024x768.

---

### Post by JoJerome on 2007-10-21
> **Pro75357 said:**
> 
And JoJerome, in a terminal you would type:   sudo gedit /etc/usplash.conf
and then it would want your password...

Actually, learned from another post I need kdesu kate versus sudo gedit. But it worked. Question remains:

I assume /etc/usplash.conf is showing me what Gusty thinks is my screen resolution. How do I find out what it's *supposed* to be so as to change it to the right numbers?

Thanks again!

---

### Post by raul_ on 2007-10-21
This is where I say that I boot Arch in under a minute.

Muhahahaha

On Topic: Try disabling some startup services or so...

---

### Post by styxie on 2007-10-21
Use this:

sudo gedit /etc/usplash.conf

---

### Post by neko18 on 2007-10-21
[QUOTE=raul_]On Topic: Try disabling some startup services or so...[/QUOTE]
It's a problem with usplash, not that there are too many services.

---

### Post by madscientist032 on 2007-10-21
any idea as to why I don't get a boot splash screen when I log in to gutsy? I can hear the intro music and see the cursor, but I wait for about 7 seconds before I see my desktop. 

haven't tried the sudo usplash command yet, as I'm currently dual-booting OS X and Gusty. 

On another note, is there any way to reduce the amount of time GRUB takes to boot gutsy? Would increasing the size of the swap file help?

Thanks in advance.

---

### Post by MatthewPlanchard on 2007-10-21
Thanks for this fix! This the last thing that needed fixing after the upgrade to gutsy. Now to look into joining motu.

---

### Post by JoJerome on 2007-10-21
Hey! Success!

I decided to take a guess (Famous last words - "I know how to edit the thing now, what's the worst that can happen?"). Apparently I guessed right because it boots like a charm now. Thanks everyone!

Now, if we can just get Gusty to run the wifi card
[http://ubuntuforums.org/showthread.php?p=3587124#post3587124](http://ubuntuforums.org/showthread.php?p=3587124#post3587124)
... all should be right with the universe.

- Jo

---

### Post by Pro75357 on 2007-10-22
> Actually, learned from another post I need kdesu kate versus sudo gedit. But it worked.

My bad... didn't think that maybe you were using kubuntu.

I would also like to add that it **may be possible** to put a lower, more common resolution to allow booting correctly... something like 800x600 or 640x480.

---

### Post by avik on 2007-10-22
> **enchance said:**
> It worked! I changed it since it said 1280x1024, which is wrong for my laptop. But why did it even register my screen as 1280x1024 in the first place?

It's not just limited to laptop screens.  It happened to my LCD desktop monitor as well.  In fact, I've been seeing this issue pop up again and again on these forums ever since Gutsy was released.  There's apparently some bug.

---

### Post by cycure on 2007-10-22
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

Thanks alot mahousaru, had the same problem here and this helped.

---

### Post by nisarg on 2007-10-22
Thank you. That was helpful.

---

### Post by Hraefn on 2007-10-22
Fantastic!!! Thank you so much for the help!!!

:)

---

### Post by dizee on 2007-10-22
This thread has fixed this problem for me as well, Xubuntu was taking forever to boot up and all I got was a black screen.

The forum saves the day once again - after several hours of frustration my gusty is up and running the way it should be, compiz fusion and all!

---

### Post by enchance on 2007-10-23
Speaking of Compiz, it just isn't running for me in my laptop. Can anyone tell me what the problem might be? I've attached my .xsession-errors just in case you want to view them.  I don't know what part to post so I'll just post everything if it's ok with you.  [View the text file here.]("http://www.joimbong.com/x.txt"). I'm using Gutsy.

---

### Post by veelos on 2007-10-23
Thanks! This also worked for me and it was the only "bug" in Gutsy for me.

---

### Post by Jimby on 2007-10-23
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

This worked for me as well.  Thanks.

---

### Post by mahiyar on 2007-10-23
I did not have a problem but the bars and all were small and yes changing the resolution worked. Whats that I hear about the running man thingy while loading? Never saw it, or is it because I'am on 7.10 since RC times. Also would be very helpfull to tell me where to set the fonts for "log-in" screen.

---

### Post by tuwxyz on 2007-10-24
Thanks. I was pretty annoyed by this problem.

---

### Post by tutti13 on 2007-10-25
I tried Gutsy as the single operating system first.  It worked fine for my Micron Transport XT2, a great improvement over Feisty.  However, when I went to a dual boot system, I had the problem with the black screen on startup.  Good job on tracking the root of the problem!

---

### Post by muadnu on 2007-10-25
Doesn't work for me... I'm on a Vostro 1400, the native resolution is 1400x900. I tried that and a couple more resolutions, but I still get a black screen on startup, and it sometimes takes too long to start...

---

### Post by kaginken on 2007-10-25
Yo Jo!

Check your 'System/Preferences/Screen Resolution'.  

L8er M8

---

### Post by JPaganel on 2007-10-27
This worked great on my Armada M700. The splash screen was set to 1280X1024, the actual monitor res is 1024x768.  

Edited /etc/usplash.conf, ran sudo update-usplash-theme usplash-theme-ubuntu, everything works properly and I don't have to wait forever for it to boot.

---

### Post by madscientist032 on 2007-10-27
Does that mean you don't get a black screen after you login to the desktop?

---

### Post by Derspankster on 2007-10-27
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```
 My usplash.conf was 1024 x 768 and it was off center to the left. My screen resolution is 1280 x 1024 so I changed my usplash.conf to that and then ran  sudo update-usplash-theme usplash-theme-ubuntu.

Now, upon reboot, my usplash resolution seems correct but it's now off center to the right. What the hell?

---

### Post by fuag155555 on 2007-10-29
thanks, this worked for me as well, mine was also at 1024 x 1248, i switched it to the correct 1280 x 768 and it boodet like a charm

for debuging i'm on a compaq presario v2000 15 inch or so widescreen.

gutsy kicks *** so far, thanks conanical

---

### Post by mahousaru on 2007-10-29
> **Derspankster said:**
> My usplash.conf was 1024 x 768 and it was off center to the left. My screen resolution is 1280 x 1024 so I changed my usplash.conf to that and then ran  sudo update-usplash-theme usplash-theme-ubuntu.

Now, upon reboot, my usplash resolution seems correct but it's now off center to the right. What the hell?

That happened to my nvidia 6200 box, I changed the refresh up a step and it fixed it. I couldn't just manually adjust my monitor as I have a kvm and would be eternally doing so when I swap machines. Another person posted they couldn't change their refresh though.

---

### Post by speedwell68 on 2007-10-29
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

Worked a treat, now Gutsy is back to it's windoze boot up beating self.:)

---

### Post by JoJerome on 2007-10-29
> **kaginken said:**
> Yo Jo!

Check your 'System/Preferences/Screen Resolution'.  

L8er M8

Sorry to sound like such a noob, but where do I find that? In the K Menu under "System" there is no "Preferences." Neither is there anything under "System Settings."

Still, the original fix worked, and seems to be working for my latest re-install (reinstalling to fix an unrelated issue).

- Jo

---

### Post by Derspankster on 2007-10-29
> **mahousaru said:**
> That happened to my nvidia 6200 box, I changed the refresh up a step and it fixed it. I couldn't just manually adjust my monitor as I have a kvm and would be eternally doing so when I swap machines. Another person posted they couldn't change their refresh though.

How about that?  I have exactly the same video card as you and your tip worked!  Yours was the second great fix I found on this forum today. 

Now, if I can figure out why I have no logout sound....I guess a lot of people that run Gutsy have that same issue. No a big deal though.  Thanks again!

---

### Post by smithji2005 on 2007-10-29
Finally!  IBM T42 is booting in normal time again.

---

### Post by isobel on 2007-10-31
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

thanks a lot :)! 
that long bootup was quite upsetting me... resolution was right, i only had to do the update and now it boots up in a few seconds!

---

### Post by bacspasm on 2007-10-31
Thanks everyone.  I thought I missed something on the install on my T30.  Booted Feisty fine but with Gutsy took 3.5 mins to get to the log in screen and of course black screen.  

With the res settings in usplash and the reset for ubuntu theme all is well with a 40 second boot up.  Sound works too!

Couldn't be happier with the Gutsy!:)

---

### Post by hazelnutz18 on 2007-10-31
Thanks so much for the fix - Gutsy starts up in less than 30 seconds now. But I get an error or startup 

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

Any ideas?

I changed usplash.conf to the correct res and then ran "sudo update-usplash-theme usplash-theme-ubuntu" 

Did I miss somthing?

---

### Post by MrWhipplesNipple on 2007-10-31
Nice One!  I was wondering why it was taking 3+ min to boot my laptop.  This fix took care of it.  Now it boots to login in under 30 sec.  I don't know what I would do without this forum!

---

### Post by EBAR on 2007-11-01
This tip worked great for me. Thanks for the help. Just wanted to attach my computer model for anyone with a similar problem to find in a search. IBM Thinkpad a31

Thanks again!

---

### Post by tinaandlee on 2007-11-01
I'm a newbie and had the same problem. I then struggled to change the /etc/usplash.conf settings. I tried with vi, which I haven't used for a long long time. After checking on-line the vi keystrokes and things, I eventually managed to change the incorrect X and Y parameters, I then found that I couldn't save the flippin' file - (read only).

After a while I used vi with 'sudo' first (sudo vi blah blah). This worked, allowed me to edit AND save the file and my laptop now boots in seconds - Many thanks for the tip!

p.s. - What exactly is 'sudo' - like super user something?

---

### Post by madscientist032 on 2007-11-01
ok so I checked /etc/usplash.conf and changed the default 1024x768 to my iMac's 1440x900 screen res. I get a black screen after I log in, and I thought this was supposed to fix it. What happened?

---

### Post by madscientist032 on 2007-11-01
> **tinaandlee said:**
> 

p.s. - What exactly is 'sudo' - like super user something?

sudo is just that. It is a command that lets an 'ordinary' user do 'root' actions. I think if you type 'man sudo' into a terminal for GDM (or Konsole for KDM) you get a text list of what sudo does and can do.

---

### Post by carlos1992 on 2007-11-01
hey thanks i always worried about something wrong with ubuntu but :guitar: this rocks

---

### Post by tinaandlee on 2007-11-02
> **madscientist032 said:**
> sudo is just that. It is a command that lets an 'ordinary' user do 'root' actions. I think if you type 'man sudo' into a terminal for GDM (or Konsole for KDM) you get a text list of what sudo does and can do.

Cool, I should look at some MAN pages really. I need to get to learn more about this. Shame you still have probs with your screen. Thanks again.

---

### Post by Tommy G on 2007-11-02
Thanks much for this.  Here's my story:

I went through 3 installs of Edubuntu 7.10 before I got it right.  The first time it seemed the login screen never came up, I assumed the install was corrupt, so I installed it again.  After the 2nd install, I applied your fix  - although with Edubuntu, the theme update command becomes:

```

sudo update-usplash-theme edubuntu-splash

```

Apparently, I closed Terminal before the command had finished doing its thing, and on next bootup I got a "Kernel panic - not syncing: attempted to kill init" error message, and it wouldn't boot even in recovery mode.  So I had to install for a 3rd time, apply the command (and WAIT until it was done) and now we are in business.  Ay Caramba!


> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

---

### Post by gdp77 on 2007-11-03
This solution worked for my ubuntu 7.10 installation at my laptop + ATI vga

---

### Post by kyrnn on 2007-11-03
I tired install Ubuntu on my laptop many times and with no success.  If I use graphics installer, when it boot, it will get werid display, and it will do that for 6 times then got error screen said something problem with display0 and will retry in 2 min.  Can never figure out.  So, I used alternate installer (text-based) and all I get is black screen after it say Starting up... 

I tried to use sudo gedit usplash.conf and I got error: Cannot open display????

Also, if I use vga=771 on boot, all I get is black screen?

What should I do?

My laptop is Alienware M5790

Thank in advance.

---

### Post by RTrev on 2007-11-05
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

Didn't seem to speed mine up any.. perhaps even made it slower.  I'm wondering if the x and y are reversed?  I have a wide-screen 1680x1050.  X would normally be the horizontal axis, and y the vertical, correct?  Should I use xres=1680 and yres=1050?

Thanks!

---

### Post by #Reistlehr- on 2007-11-05
> 
I have a wide-screen 1680x1050. X would normally be the horizontal axis, and y the vertical, correct? Should I use xres=1680 and yres=1050?


Lol. your comment made me laugh. x = 1680, so yet, use it.

For my laptop usplash.conf looks like:

xres=1680
yres=1050

---

### Post by RTrev on 2007-11-05
> **#Reistlehr- said:**
> Lol. your comment made me laugh. x = 1680, so yet, use it.

For my laptop usplash.conf looks like:

xres=1680
yres=1050

<grin>  Thanks!!

---

### Post by RTrev on 2007-11-05
> **#Reistlehr- said:**
> Lol. your comment made me laugh. x = 1680, so yet, use it.

For my laptop usplash.conf looks like:

xres=1680
yres=1050

Say, would it matter that I'm running dual monitors with Twinview?  Under System | Preferences | Screen Resolution it shows 3360x1050.  Perhaps I need those numbers?

---

### Post by ascus4 on 2007-11-05
/

---

### Post by Ahrk on 2007-11-11
Thanks, I also had this problem and this just solved everything\\:D/

---

### Post by Fruhwirth on 2007-11-12
This worked for me!  Even though I run ubuntu at a higher resolution, putting the splash at 1024x768 worked. Thanks, and easy. :)

---

### Post by frithiof on 2007-11-12
mahousaru's solution worked just swell here on my friend's compaq armada m700 running xubuntu.

The only difference is I had to do:
```
sudo update-usplash-theme usplash-theme-xubuntu
```

tried the ubuntu-one first byt it suggested the right one. sweet.
Thanx a bunch

---

### Post by SteveHillier on 2007-11-12
The original thread title got me excited and so what I say might run in accord with all you clever people talking about screen resolutions, but it is the original title I want to respond to.
I have two machines at work, side by side (I sometimes get confused when I type into the wrong keyboard and wonder why nothing appears of the screen!!).
I come into work in the morning, turn on my Vista machine, and then turn on my Gutsy machine [a lateral movement of about 12 inches and a button depression so not much time difference]
My gusty machine is ready for log on some 10-15 seconds before Vista.
So in order to give it a fair test I wait for both to be ready.
I press ctrl-alt-del to bring up the Vista log on screen, type in my password [the user name is retained from the last session].  I then type into Gutsy, my username and then my password and wait.
I can normally get working and onto this forum through Firefox before my Vista machine is ready for anything.
I now want to make domain logons simple and I will start shipping Ubuntu to clients as a real alternative for you know who!


Just remember Chas keeps time while Mick and Keef rock.

---

### Post by RTrev on 2007-11-12
I wonder it we are all talking about the same problem here.

My issue is that I log in, it draws the top panel (I removed the bottom panel), then the top panel *disappears* again, and there is a 2-10 second delay before it finally comes back and stays.

So, in effect, login takes a lot longer than it used to.. but my symptoms sound a bit different than others as I read more closely.  Ideas?

Thanks,
Bob

---

### Post by madscientist032 on 2007-11-12
> **RTrev said:**
> I wonder it we are all talking about the same problem here.

My issue is that I log in, it draws the top panel (I removed the bottom panel), then the top panel *disappears* again, and there is a 2-10 second delay before it finally comes back and stays.

So, in effect, login takes a lot longer than it used to.. but my symptoms sound a bit different than others as I read more closely.  Ideas?

Thanks,
Bob

What else disappears after you log in? Does your entire screen go black and does your cursor have an 'x' shape? If so, you might have a problem that sounds similar to mine. 

My only idea (and I haven't tried it yet) is to backup all data and reinstall the OS.

---

### Post by RTrev on 2007-11-12
> **madscientist032 said:**
> What else disappears after you log in? Does your entire screen go black and does your cursor have an 'x' shape? If so, you might have a problem that sounds similar to mine. 

My only idea (and I haven't tried it yet) is to backup all data and reinstall the OS.

My entire screen goes blank, but not black.. it goes to the light brown color.  My mouse cursor remains an arrow and doesn't change.

I don't think a reinstall will help, at least with my version of the problem, as I've installed Gutsy at least 7 times for various reasons.  No change in this behavior.

Your mouse cursor turning into an X makes me think xorg.  I think I've seen that sometimes, but can't remember the exact circumstances.

Oh, and here's a weird one.  I normally leave my machine on, but last night I turned it off for the night.  On boot, I had a cursor that looked normal.. in fact everything looked normal, but neither button worked.  I rebooted.. no change.  Had to log in in safe mode and re-run dpkg-reconfigure xserver-xorg.. which either fixed it or it fixed itself coincidentally.  

The only problem remaining, aside from the login oddness, is that Compiz will not hold it's settings.  I put it on normal, then find it on custom.  Or put it on custom and then later it's turned itself off completely.

Not sure how much of this has to do with compiz.  I discovered something odd the other day.  Was setting up an old and slow machine, so installed just a command line system and then added xorg, gdm, gnome-core, and a bunch of other things.  Couldn't get a desktop at all until I added compiz.  Seems it's essential now.. built into the guts of gutsy.

Bob

---

### Post by madscientist032 on 2007-11-12
> **RTrev said:**
> My entire screen goes blank, but not black.. it goes to the light brown color.  My mouse cursor remains an arrow and doesn't change.

I don't think a reinstall will help, at least with my version of the problem, as I've installed Gutsy at least 7 times for various reasons.  No change in this behavior.

Your mouse cursor turning into an X makes me think xorg.  I think I've seen that sometimes, but can't remember the exact circumstances.

Oh, and here's a weird one.  I normally leave my machine on, but last night I turned it off for the night.  On boot, I had a cursor that looked normal.. in fact everything looked normal, but neither button worked.  I rebooted.. no change.  Had to log in in safe mode and re-run dpkg-reconfigure xserver-xorg.. which either fixed it or it fixed itself coincidentally.  

The only problem remaining, aside from the login oddness, is that Compiz will not hold it's settings.  I put it on normal, then find it on custom.  Or put it on custom and then later it's turned itself off completely.

Not sure how much of this has to do with compiz.  I discovered something odd the other day.  Was setting up an old and slow machine, so installed just a command line system and then added xorg, gdm, gnome-core, and a bunch of other things.  Couldn't get a desktop at all until I added compiz.  Seems it's essential now.. built into the guts of gutsy.

Bob

This may sound stupid but what's xorg and what's the command line that I enter in Terminal to configure it?

---

### Post by RTrev on 2007-11-12
> **madscientist032 said:**
> This may sound stupid but what's xorg and what's the command line that I enter in Terminal to configure it?

Xorg is the basic windowing system.  The command line is:

```
sudo dpkg-reconfigure xserver-xorg
```

It gives you a lot of choices to make about the video, mouse and keyboard.  Many can be left at the default.

If you're using a restricted driver for video, this is where you specify it.. like I pick nvidia for mine instead of the "nv" that it sets by default on mine.

Hope this helps.

Bob

---

### Post by minus198 on 2007-11-12
.

---

### Post by RTrev on 2007-11-12
> **minus198 said:**
> .

Okay, I've seen this before.. where someone just posts a period.  What's that supposed to mean?

---

### Post by captain semtex on 2007-11-13
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

This worked perfectly for me. The boot up time from power on to first seeing the desktop was 2 mins 56 seconds. After changing /etc/usplash.conf to the correct values my boot time is now a mere 46 seconds :)

As I run Edubuntu I had to make a small change to the solution and instead did...

```

sudo update-usplash-theme edubuntu-theme

```

Thanks mahousaru

---

### Post by RTrev on 2007-11-13
> **captain semtex said:**
> This worked perfectly for me. The boot up time from power on to first seeing the desktop was 2 mins 56 seconds. After changing /etc/usplash.conf to the correct values my boot time is now a mere 46 seconds :)

As I run Edubuntu I had to make a small change to the solution and instead did...

```

sudo update-usplash-theme edubuntu-theme

```

Thanks mahousaru

What if someone is not using usplash?  Does it still matter?

My system got weirder with todays updates.  Now it *does* go to a black screen, and the digital monitors even flash the "No signal" message.  eventually it comes back, and login is possible, but it still displays the panel, then removes it, then waits a while, then finally things are seemingly normal.

I have two 1680x1050 monitors in Twinview, so the screen size is 3360x1050.  Neither that normal the single monitor 1680x1050 seem to make any difference when used in the /etc/usplash.conf file.

I ran the:

```
sudo update-usplash-theme usplash-theme-ubuntu
```

command, but could see no difference.

Hmm.

---

### Post by vishzilla on 2007-11-15
I followed the directions given by **mahousaru**, but it didnt work!!!....On starting my computer, I get about 2 mins of Blank Screen w/ Grub loading later. What other problem could it be? I have a dual boot XP/Gutsy with an Intel P4 3GHz, Intel 915 Graphics card w/ GMA 900.

---

### Post by RTrev on 2007-11-15
> **vishzilla said:**
> I followed the directions given by **mahousaru**, but it didnt work!!!....On starting my computer, I get about 2 mins of Blank Screen w/ Grub loading later. What other problem could it be? I have a dual boot XP/Gutsy with an Intel P4 3GHz, Intel 915 Graphics card w/ GMA 900.

Whoa there pardner!  I think we're talking about two different things.  The problem I *thought* was being discussed was the delay *after* one had logged in and entered the username and password.

What *you* are describing, a delay *before* GRUB even loads, is a whole different ballgame.

I can't think of what could be holding things up *before* GRUB grabs control except something in your BIOS.

Anyone agree?

---

### Post by vishzilla on 2007-11-15
> **RTrev said:**
> Whoa there pardner!  I think we're talking about two different things.  The problem I *thought* was being discussed was the delay *after* one had logged in and entered the username and password.

What *you* are describing, a delay *before* GRUB even loads, is a whole different ballgame.

I can't think of what could be holding things up *before* GRUB grabs control except something in your BIOS.

Anyone agree?

Ok I got your point. I will have a look at this, may be start a new thread!

---

### Post by djwalker on 2007-11-16
This fix worked like a charm on my Dell Inspiron 5100. I was just about to go back to 7.04 when I found this forum.

---

### Post by enchance on 2007-11-16
This thread has helped so many users since I first posted it. Any chance this could be made into a **Sticky**?

---

### Post by ugm6hr on 2007-11-18
> **enchance said:**
> This thread has helped so many users since I first posted it. Any chance this could be made into a **Sticky**?

Or at least added to this: [http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)
As a slicker solution to Troubleshooting f

---

### Post by imbjr on 2007-11-22
> **Derspankster said:**
> How about that?  I have exactly the same video card as you and your tip worked!  Yours was the second great fix I found on this forum today. 

Now, if I can figure out why I have no logout sound....I guess a lot of people that run Gutsy have that same issue. No a big deal though.  Thanks again!

Try installing esound. Worked for me.

---

### Post by enchance on 2007-11-23
Amazingly, the latest version of [Linux Mint]("http://www.linuxmint.com/") (Daryna) which is based on Gutsy doesn't have this usplash problem. I thought I'd install it and give it a whirl and good news is, Mint works great! It's like Gutsy on steroids and a rocket launcher! Bad news is, I don't think I'll be going back to Gutsy after using Mint 4.0 Daryna.

My laptop actually ran faster and was more OOTB in Mint than it was in Gutsy...XGL and Compiz included.

---

### Post by madscientist032 on 2007-11-24
> **enchance said:**
> Amazingly, the latest version of [Linux Mint]("http://www.linuxmint.com/") (Daryna) which is based on Gutsy doesn't have this usplash problem. I thought I'd install it and give it a whirl and good news is, Mint works great! It's like Gutsy on steroids and a rocket launcher! Bad news is, I don't think I'll be going back to Gutsy after using Mint 4.0 Daryna.

My laptop actually ran faster and was more OOTB in Mint than it was in Gutsy...XGL and Compiz included.

Sorry to sound like a noob (which, unfortunately, I am,) but does OOTB stand for "out of the box?" 

I'm assuming Mint 4.0 Daryna is a different Linux distro.

---

### Post by arron on 2007-11-24
Awesome info.  Went from 3 min 4 seconds boot to 38 seconds.  Im now to 7.10 from 7.04 fully (just this held me back).

Thanks for the info!

---

### Post by madscientist032 on 2007-11-24
> **arron said:**
> Awesome info.  Went from 3 min 4 seconds boot to 38 seconds.  Im now to 7.10 from 7.04 fully (just this held me back).

Thanks for the info!

Funny how I feel guilty for not having this issue at all.

---

### Post by enchance on 2007-11-25
> **madscientist032 said:**
> Sorry to sound like a noob (which, unfortunately, I am,) but does OOTB stand for "out of the box?" 

I'm assuming Mint 4.0 Daryna is a different Linux distro.

Yes, OOTB stands for "out of the box" and, yes, Linux Mint is a fork of Ubuntu meaning it uses the same ubuntu repositories. The latest version of Mint is 4.0 which is based on Gutsy. Give Mint a try, you just might like it. I made the move from gutsy just last week.

---

### Post by SilentTim on 2007-11-27
Some more info on this...

I had this problem when I first installed Gutsy, then I read this thread and others like it and got around it.

I forgot all about it, then one day the problem came back. So I fixed it again, forgot all about it...

Then I realised what it is thats causing it (for me, anyway). I usually use my laptop just as it is, but occasionally plug it into an old monitor I have on my desk. My guess is, the settings change to accommodate the monitor, then next time I use the laptop on its own,  the splash screen has disappeared again.

So be warned, that is a potential cause of this problem. Now, what would be really good, is if I could have two different profiles so I could switch between the two, or even, if the script detected which console I was using and set the resolution accordingly...

---

### Post by madscientist032 on 2007-11-27
> **SilentTim said:**
> Some more info on this...

I had this problem when I first installed Gutsy, then I read this thread and others like it and got around it.

I forgot all about it, then one day the problem came back. So I fixed it again, forgot all about it...

Then I realised what it is thats causing it (for me, anyway). I usually use my laptop just as it is, but occasionally plug it into an old monitor I have on my desk. My guess is, the settings change to accommodate the monitor, then next time I use the laptop on its own,  the splash screen has disappeared again.

So be warned, that is a potential cause of this problem. Now, what would be really good, is if I could have two different profiles so I could switch between the two, or even, if the script detected which console I was using and set the resolution accordingly...

Personally what I would do is to boot the laptop completely, login to your user account, and then plug the monitor in. Do whatever it is to get both running smoothly, and then before you shut down the system, change the settings so that Ubuntu will use the laptop display as its primary.

If I was an Ubuntu guru, I would recommend running xorg.conf to calibrate the display settings. But seeing as I'm not, any Terminal veterans out there can correct me if I'm wrong.

Hope this helped.

EDIT: Wait... do you use the old monitor as a secondary one for your laptop (dual-display mode) or as a standalone monitor?

---

### Post by i_like_you on 2007-11-27
Thanks for the fix. It worked. Boot up time is fast now.

I used JoJerome's method

kdesu kate /etc/usplash.conf

I checked Preferences > Screen Resolution for my laptop resolution, updated the file, then updated the theme. Reboot, and perfect!

---

### Post by sandysandy on 2007-12-02
> **Tommy G said:**
> Thanks much for this.  Here's my story:

I went through 3 installs of Edubuntu 7.10 before I got it right.  The first time it seemed the login screen never came up, I assumed the install was corrupt, so I installed it again.  After the 2nd install, I applied your fix  - although with Edubuntu, the theme update command becomes:

```

sudo update-usplash-theme edubuntu-splash

```

Apparently, I closed Terminal before the command had finished doing its thing, and on next bootup I got a "Kernel panic - not syncing: attempted to kill init" error message, and it wouldn't boot even in recovery mode.  So I had to install for a 3rd time, apply the command (and WAIT until it was done) and now we are in business.  Ay Caramba!

hi 
i tried this command
[COLOR="Blue"]sudo update-usplash-theme edubuntu-splash[/COLOR]
 (i have edubuntu 7.10)
no joy on splash screen. i still get the normal black splashup screen. booting otherwise is ok. just wanted some colours at start up.

regards

---

### Post by Tig3rzhark on 2007-12-07
I'm having the same problems as well, except the splash page appears and stays stuck in one place for a while then goes blank.

Other times it would remain stagnant and would only move after inputting ctrl+alt+del.

I tried running fsck to solve the problem but it failed to do so.

Any solutions?

---

### Post by mahousaru on 2007-12-08
> **Tig3rzhark said:**
> I'm having the same problems as well, except the splash page appears and stays stuck in one place for a while then goes blank.

Other times it would remain stagnant and would only move after inputting ctrl+alt+del.

I tried running fsck to solve the problem but it failed to do so.

Any solutions?

When it boots press ESC when you see the grub menu appear.  Delete the quiet and add nosplash=y  to the line with all the options.  When you boot it should be verbose and have no splash so hopefully you can see what is failing.  The change is only for that boot.

---

### Post by BitSmack on 2007-12-09
Mahousaru, you rock :guitar: !  My wife's laptop has had this problem from the beginning, and this fixed it.

A note for Kubuntu users:
instead of
sudo update-usplash-theme usplash-theme-ubuntu

you need to type
sudo update-usplash-theme usplash-theme-kubuntu

Thanks again!

---

### Post by nedim on 2007-12-10
First of all thanks for the fix - it was really annoying to wait for more than 4 minutes for the Gutsy to boot. Now it only takes about 40 seconds :) 


> How do I find out what it's supposed to be so as to change it to the right numbers?

Here is how you can find out the screen resolution: 

Go to System -> Preferences -> Screen Resolution

In the Resolution field you can see something like XSIZExYSIZE, for example 1024x768 or 1280x800. 

You should set xres to the value of XSIZE and yres to the value of YSIZE like this

```

xres=1024
yres=768

```

(this example assumes that YOUR XSIZE value is 1024 and YSIZE is 768 ).

---

### Post by daviddehoog on 2007-12-17
Greetings

I've tried Gutsy on two (almost identical) laptops with Interesting results ...

Laptop1:
IBM ThinkPad T42 2378-JZM
Pentium4 M 1.6
ATI Radeon Mobility 7500
Intel Wireless
1024x768 ThinkPad LCD

Laptop2:
IBM ThinkPad T42 2373-K38
Pentium4 M 1.7
ATI Radeon Mobility 7500
Cisco Wireless
1024x768 ThinkPad LCD

On both Laptop1 and Laptop2 the configuration file was set to 1280x1024. Both Laptop1 and Laptop2 have a maximum built-in LCD resolution of 1024x768.

On Laptop1, the issue was present. On Laptop2, it was not. The fix suggested at the top of this thread fixed Laptop1.

As far as I can tell, both laptops have ATI Radeon Mobility 7500 chips and identical ThinkPad LCDs. The only other differences are in devices that I wouldn't imagine would be involved in displaying the boot splash screen ...

Thoughts ?

---

### Post by madscientist032 on 2007-12-17
Ok. I recently installed 7.10 again on my mac and there seems to be an issue. I have no idea what it is, but I get weird text after GRUB starts up. I'm going to screenshot it and post it here as an edit, but I figured a heads-up would help or something. 

The only thing that I remember from the text is "....press space or wait 30 sec to continue..."
I also have no boot splash (I assume the splash is the "Ubuntu" over the status bar) but I did have it in my previous two installations. I'm thinking my xorg.conf is involved but I'm a somewhat noob so I'm not sure.

---

### Post by SagaLhan on 2007-12-20
I have this problem on my work PC, but the tough part is that Gutsy won't boot at all no matter how long I wait. So I can't get into the OS to fix it. Anyone got suggestions? (Live CD boots okay with the hpet=disable boot option.)

---

### Post by madscientist032 on 2007-12-20
> **madscientist032 said:**
> Ok. I recently installed 7.10 again on my mac and there seems to be an issue. I have no idea what it is, but I get weird text after GRUB starts up. I'm going to screenshot it and post it here as an edit, but I figured a heads-up would help or something. 

The only thing that I remember from the text is "....press space or wait 30 sec to continue..."
I also have no boot splash (I assume the splash is the "Ubuntu" over the status bar) but I did have it in my previous two installations. I'm thinking my xorg.conf is involved but I'm a somewhat noob so I'm not sure.

Here are the pictures that I promised. (sorry that I replied to my own post)[html]http://i109.photobucket.com/albums/n45/madscientist032/108_4856.jpg[/html]Copy and paste into browser's address bar.

---

### Post by TwoFlightsDown on 2007-12-20
Thanks for posting this fix.  I am new to Ubuntu, and was surprised by how slow it was at booting up.  Now that the resolution seems to be fixed, my computer boots a lot faster and my screen looks so much nicer.  Thanks again!

---

### Post by itsjustarumour on 2007-12-23
The fix didn't work for me, still getting about a minute of blank screen during bootup....

:-(

---

### Post by madscientist032 on 2007-12-24
> **itsjustarumour said:**
> The fix didn't work for me, still getting about a minute of blank screen during bootup....

:-(

Do you have a splash screen during bootup? I know that there is a usplash code line somewhere that can fix it. Ask around - I'm somewhat new to terminal commands (besides sudo and apt-get)

---

### Post by itsjustarumour on 2007-12-30
> **madscientist032 said:**
> Do you have a splash screen during bootup? I know that there is a usplash code line somewhere that can fix it. Ask around - I'm somewhat new to terminal commands (besides sudo and apt-get)

Yep, get the splash screen at bootup, appears to be the correct size (from previous experience running previous versions of Ubuntu), I log on and then thats when I get a minute of blank screen...

---

### Post by madscientist032 on 2007-12-30
> **itsjustarumour said:**
> Yep, get the splash screen at bootup, appears to be the correct size (from previous experience running previous versions of Ubuntu), I log on and then thats when I get a minute of blank screen...

I get that too, but it only lasts for 15 seconds and I think it's a result of X display manager. It doesn't bother me, but if you want to fix it, check your xorg configuration.

Don't forget to backup your current xorg file! 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

And if all goes wrong or you don't like what happened, run this in the Terminal to restore your xorg file to the backup:
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by tooCanad on 2008-01-04
Great post, simple fix. Thanks very much.

---

### Post by loserboy on 2008-01-09
i didnt read all 10 pages but in case it hasn't been mentioned I actually had to adjust it lower than my native resolution to get it working, thanks for this workaround i was starting to think my pixels were going to explode, my dad's monitor was doin' some real freaky stuff.

---

### Post by paul cooke on 2008-01-11
thanks... that's sorted out my laptop

ps the correct command for ubuntu studio users is

```

sudo update-usplash-theme ubuntustudio-theme
```

---

### Post by capt.d on 2008-01-20
I was missing the gedit after sudo, now it works as expected. I fixed  the boot splash and also at shut down. The boot time went from 75 to 50 seconds and looks so much better than a blank screen. Thanks for the great post on this subject. I thought it was due to my old Dell cpx P3 hardware?
capt.d

---

### Post by UnCola on 2008-01-20
This half fixed it for me, boot time down from four minutes to ninety seconds.

And the grey screen is gone, but instead I get told that "There are differences between the boot sector and its backup... Not automatically fixing this"   

This is a fresh install from the 7.10 live CD on a T40, checked the hard drive in XP and it is ok.

---

### Post by alex1001 on 2008-01-27
Hello, I just installed Ubuntu 7.10 yesterday, and I'm having this same problem where once I power on, it takes a few minutes to load to the screen where I type my username and password. It's just black until that point.

So I tried typing etc/usplash.conf in the terminal and I get the following response:

bash: etc/usplash.conf: Permission denied


Then I tried sudo update-usplash-theme usplash-theme-ubuntu and I get the following reponse:

[sudo] password for alex:

When I type in my password, I get "Sorry, try again." and then it tells me my password is incorrect (although I'm sure it's right).

Any ideas on how to fix this? Maybe my issue is slightly different.

Thank you all for your help!

---

### Post by ugm6hr on 2008-01-27
> **alex1001 said:**
> So I tried typing etc/usplash.conf in the terminal and I get the following response:

bash: etc/usplash.conf: Permission denied


It is:

```
gksudo gedit /etc/usplash.conf
```

If it tells you your password is wrong - then it probably is.  Ensure you enter it in the correct case.

I found that using resolution 320x240 works for most systems, irrespective of actual video resolution. i.e.
> xres=320
yres=240 

Then finally:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

Original solution:
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

---

### Post by alex1001 on 2008-01-27
Oh wow, thank you so much for that help! Sheer genius.

Everything works wonderfully now. :D

---

### Post by GStrike- on 2008-01-28
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

how do I change this? I opened the file and change my yres and it doesn't let me. It says I don't have permission to save the file.

EDIT: nevermind I got it

---

### Post by Crimson_Wake on 2008-01-30
Worked for me.

It took me a little while to get things to work, because I had to edit in terminal using nano, but but she's good to go now, and the boot went from 3 minutes to just a hair over 60 seconds.

FANTASTIC!

---

### Post by mgna003 on 2008-02-05
Checking the resolution and updating via
$ sudo update-usplash-theme usplash-theme-ubuntu
worked for me as well.
Used to take about 5mins to boot up now down to about 45 secs.
Thanks for the help.:)

---

### Post by Michl on 2008-02-05
Never had this problem in Gutsy until I did a fresh install,
so it had me perplexed until I realized that before I was
using Gutsy from an upgrade and not an install from a
live CD.  This fixed everything for me.

Thanks!!

---

### Post by usfivemusic on 2008-02-12
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```
This cut down my boot time from 5 mins to 40ish seconds.  Thank you so much!

---

### Post by Perpetual on 2008-02-14
I tested the first Hardy Alpha and this bug was still present.  Has anyone tested later Alpha's and can confirm if this has been fixed?

Edit: Finding things on launchpad.net is damn near impossible :(

Finally found the bug report, so to answer my own question...

[i]
In Ubuntu 7.10, the desktop CD installer did not correctly configure the splash screen's resolution for the current hardware.

This problem is believed to be fixed in Hardy Alpha 2, and so should be fixed in Ubuntu 8.04.

If you are experiencing this bug and wish to verify whether it's due to the problem originally reported here, then please compare the resolution shown in System -> Administration -> Screens and Graphics (assuming you haven't changed it) with that in the file /etc/usplash.conf. They should be the same. For example, on the computer I'm using at the moment, Screens and Graphics says "Resolution: 1280x800" and /etc/usplash.conf has "xres=1280" and "yres=800".

If they are different, then this bug has recurred for some reason and I would like to know about it in this bug report.

If you find that the *live CD* does not display a splash screen while booting, or if you have an installed system that does not display a splash screen while booting but has the *same* values in Screens and Graphics and in /etc/usplash.conf as above, then this is not the same problem as this bug; instead, it is likely to be a deeper problem with the splash screen software, possibly specific to your hardware. Please report that on the 'usplash' package in Ubuntu.[/i]

---

### Post by Mano[FA] on 2008-03-16
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

Thanks!
it worked fine for my Asus 17 inches Widescreen Laptop as well. 
Hope they will fix the problem with next release

---

### Post by ribbonsandbows on 2008-03-20
Its so frustrating to "big up " ubuntu then show off to the boss and watch it snarl up on loading. 
Its so fab to have a support forum that actually supports. 

Thumbs up, the glitch in long boot up solved, and a major "Down with vista" plan for new laptops coming in.

serveral dozen other glitches to go!!! 
and to be able to tackle them all with a smile... that surely can't be right!

---

### Post by RTrev on 2008-03-20
Looks to me like this still isn't fixed in Hardy either.  

Question: if I have two 1680x1050 flat screens running TwinView, and it's seen by the system as a single screen of 3360x1050 dimensions, should I use the individual screen size, or the combined screen size, in the conf file?

Thanks,
Bob

---

### Post by Perpetual on 2008-03-20
> **RTrev said:**
> Looks to me like this still isn't fixed in Hardy either.

That's not good.  Did you find a bug report for Hardy or did you do an install and find the issue?

I may install the Beta tonight to see if it works properly.

---

### Post by DJAKO on 2008-03-21
I just checked my resolution using the technique they mentioned and it was right. Updated the theme files and still long as boot. I'm sitting here waiting right now while I look at a black screen.

---

### Post by ugm6hr on 2008-03-22
> **DJAKO said:**
> I just checked my resolution using the technique they mentioned and it was right. Updated the theme files and still long as boot. I'm sitting here waiting right now while I look at a black screen.

Maybe try this: [http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)
This simply removes the Splash screen (I think).

Also, my Dell 500m laptop needed to use 320 x 240 resolution for Splash screen (edited as in this thread), even though it has a 1024x768 screen in Uguntu Gnome desktop.  I have no idea why, but it worked.

---

### Post by RTrev on 2008-03-22
> **Perpetual said:**
> That's not good.  Did you find a bug report for Hardy or did you do an install and find the issue?

I may install the Beta tonight to see if it works properly.

I found the issue myself after an install.  Although, I have to say that I don't seem to be having the same problems.. e.g., no black screen, and only a reasonable delay after entering my password before all is ready to use (reasonable = ~ 5 seconds.)

But the values in the conf file were 640x480.  So if that file is still even being used for anything, mine should be a lot different than that,.

I'm not sure I should file it as a bug since it doesn't seem to be doing any harm, as far as I can tell.  It may not be being used anymore?

---

### Post by Perpetual on 2008-03-22
> **RTrev said:**
> I found the issue myself after an install.  Although, I have to say that I don't seem to be having the same problems.. e.g., no black screen, and only a reasonable delay after entering my password before all is ready to use (reasonable = ~ 5 seconds.)

But the values in the conf file were 640x480.  So if that file is still even being used for anything, mine should be a lot different than that,.

I'm not sure I should file it as a bug since it doesn't seem to be doing any harm, as far as I can tell.  It may not be being used anymore?

Hmm, good question.  Seems like there are a lot of system changes (xorg) and I don't know  the answer to this either.  I haven't installed the beta yet (played in VBox).  As long as it doesn't have the 2 minute boot due to the usplash.conf being wrong, I will be happy.

---

### Post by RTrev on 2008-03-22
> **Perpetual said:**
> Hmm, good question.  Seems like there are a lot of system changes (xorg) and I don't know  the answer to this either.  I haven't installed the beta yet (played in VBox).  As long as it doesn't have the 2 minute boot due to the usplash.conf being wrong, I will be happy.

Oh, just a warning.. but I can't get vbox to work in Hardy.  One thing I need to do later today is see if this has been filed as a bug yet.  Vbox simply doesn't work anymore, at least for me.  I'll have to install it again and see if it's still doing the same thing.

---

### Post by xmastree on 2008-03-24
Ignore this, I found a more suitable thread for my problem.

---

### Post by Perpetual on 2008-04-02
Just an FYI, I have been running the Beta for a couple of weeks and this problem with the long boot delay (usplash poroblem) has been fixed.  Clean install of 8.04 Beta boots as would be expected.

---

### Post by watsons on 2008-04-06
> **mahousaru said:**
> Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024                                                                                                                    
yres=768 

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

```

sudo update-usplash-theme usplash-theme-ubuntu

```

Thanks for your help!  I've encountered the same problem and now it's fixed!

---

