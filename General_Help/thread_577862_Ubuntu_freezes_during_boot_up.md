---
title: "Ubuntu freezes during boot up"
date: 2007-10-16
forum: General Help
---

### Post by igmo on 2007-10-16
Greetings,

My computer locked up while I was in ubuntu, I hit the reset button on the front of the computer to reboot it.  I have had ubuntu installed on this PC for a couple months now and have had no other difficulties.

Well, I guess it would have been nice to know [http://ubuntuforums.org/showthread.php?t=577753](http://ubuntuforums.org/showthread.php?t=577753) about all of that before I did that.

Anyway, I CAN get into recovery mode (although I am at a COMPLETE loss as to what should be done there)

I see the Ubuntu Logo pop up with an orange progress bar.  Then I see an Nvidia Splash Screen and then a black screen with a circular cursor on it. The cursor DOES move and it is animated but it will not ever load the welcome screen.

I am VERY ubuntu n00b so please explain what needs to be done as if I am a kindergarten student. I consider myself an advanced windows user but this Ubuntu stuff still kinda has me at a loss.

Thanks in advance,

iGmO

---

### Post by igmo on 2007-10-16
Bump. Any help??

---

### Post by igmo on 2007-10-16
Okay guys you have a lovely community for people that already know what they are doing with linux. I want Ubuntu to be my main OS and I want to ditch M$ completely, I even tout the advantages of open source software such as open office to all of my family members.

I build computers for friends and family and I am an advanced windows user and I want to dump it.  Simply though, I am not seeing the level of support and direction from these forums to warrant staying.  If I have an issue I need to be able to at least look something up on it.  Hours of searching these forums have yielded nil and the silence of the llluminati has started to turn me off.

If I have a problem with a windows computer I can find a solution in no time flat.  Here it is much more difficult for me to do so.   I simply don't have the time to research an issue for hours on end on a personal system.  Yeah it broadens my horizons and yeah it's probably good for me but it's got me very frustrated and upset right now.

Sorry to take up valuable forum space.

iGmO

---

### Post by r-mo on 2007-10-16
boot into recovery mode at the command prompt
```

cd /
touch /forcefsck
reboot

```

This should force a file system check on the next normal boot, fingers crossed it fixes things...

This might help if it doesn't work [http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/](http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/)

---

### Post by igmo on 2007-10-17
I tried both methods to fix it.  

The method at the link that was posted was not accurate.  I did not see where the option was to recover a broken system in the CD menu.

What did I do wrong?

---

### Post by Druke on 2007-10-17
hmm when you do a nomral boot, the point where it stops does it 'lock up' to the point that num liock lights no longer work and ctrl-f1 doesn't function? if so, I'm not sure. But from what you've said so far it sounds like metacity isn't starting (basically explorer.exe)

---

### Post by igmo on 2007-10-17
I get a screen that looks like it is all of about .5 secs from showing me the login screen.

It's black and there is a round cursor with an animated black ring inside of it (the cursor IS movable via mouse).  The num-lock key toggles on and off as well as all of the other lights.  Alt-F1 and Alt-f2 have no effect but if I hit
ALT-SysReq-R,S,E,I,U,B  it will reset.

---

### Post by Druke on 2007-10-17
I see, actually its ctrl-alt-f1 but it should work if numlock works. Anyways try doing ctrl-alt-f1 and logging in
then do this
> sudo /etc/init.d/gdm stop

and then 

> sudo /etc/init.d/gdm start

if that doesn't work as a last resort try

> startx

---

### Post by igmo on 2007-10-17
startx did get me to the gui but I get an error message box

INTERNAL ERROR
failed to initialize HAL!

                      (x)close

network is not functional, My video seems to be fine.  I get a message about software updates being available.  What should be my next step?

If I reboot it reverts to my previous issue.

---

### Post by Druke on 2007-10-17
This is the point where someone who actually knows what they're doing should help.

It sounds like gdm is borking... but I have no idea how to work with it.

---

### Post by igmo on 2007-10-17
Cool thanks for your help. That at least gets me into a gui.

Now does anybody else have any ideas on how to fix the HAL error?

---

### Post by asiersar on 2007-10-19
Maybe this can help you:

- Go to /etc/init.d/rc

```
sudo gedit /etc/init.d/rc
```

- Change CONCURRENCY to "none"

If that doesn`t work, follow this thread:

[http://ubuntuforums.org/showthread.php?t=574992]("http://ubuntuforums.org/showthread.php?t=574992")

---

### Post by Nunu on 2007-10-19
Hi Guys Bit of a noob myself reading through the page I saw you mention 

INTERNAL ERROR
failed to initialize HAL!

And you also mention that network isn't working. 

My question is isn't HAL and acronym for Hardware Access List, or am i thinking to microsofty here. Maybe it's trying to load drivers in the back end which causes the OS to divert resources to the HW detection instead of startup. I had this with Fedora and a network card as well.  Fedora whould take up to 20 minutes to start. I manually installed the NIC's drives and that solved the problem for me. I am not saying that is the resolution just a question form my side. 

Sorry I can't be of help regarding this.

---

