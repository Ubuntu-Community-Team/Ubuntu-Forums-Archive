---
title: "Some weird keyboard issue"
date: 2015-03-19
forum: General Help
---

### Post by luvshines on 2015-03-19
Hi all

I am a Ubuntu 14.04 user on Thinkpad T420.
All was fine till couple of days ago, when my keyboard suddenly started acting funny.

I can no longer use the arrow keys in the address bar of the browsers(firefox, chrome). I mean, a type a letter and it shows all the pages from history but I can't go up/down using arrows.
I can no longer type in some applications(lotus notes for instance). Facebook search bar for another example. Even arrow keys while writing this very post message box didn't work
It works fine in other apps though, like gedit.

I also noticed some lag and blinking while typing in terminal and browser address bars

Tried a reinstall(just the root partition) today but no luck. I thought some recent upgrade might have broken it but vanilla install of 14.04.2 is also behaving in same way. Is anything in my home folder config causing this ?

It's irritating and just renderes me helpless in some cases.

Any suggestions how to fix/debug this ?

---

### Post by CantankRus on 2015-03-19
Do you see the same if using Onboard (On-screen Keyboard).
Test in guest account.

---

### Post by luvshines on 2015-03-19
Hi
> **CantankRus said:**
> Do you see the same if using Onboard (On-screen Keyboard).
    Sorry, I didn't understand this. Which on-screen keyboard ?

> Test in guest account.
    You meant repeat the tests in guest account ?

---

### Post by CantankRus on 2015-03-20
> **luvshines said:**
> Hi

    Sorry, I didn't understand this. Which on-screen keyboard ?


    You meant repeat the tests in guest account ?

The on-screen keyboard is called **Onboard**. See how that functions.
and also test how your normal keyboard performs in the guest account.

---

### Post by luvshines on 2015-03-20
> **CantankRus said:**
> The on-screen keyboard is called **Onboard**. See how that functions.
Same behaviour with on-screen keyboard too

> and also test how your normal keyboard performs in the guest account.
With normal keyboard in guest account, I couldn't open google-chrome and lotus notes so couldn't check that. Firefox seemed to work okay.

But again, the issue is random. I mean even under my regular account, once in a while it works OK. So I can't be sure that in guest account it always works.

Looks like the fields which give a dropdown while typing like 'facebook search', 'browser address bar', 'lotus notes address bar' seems to have problem.
But one exception is the lotus notes mail compose area.

---

### Post by CantankRus on 2015-03-20
It could be a compiz issue.
Do you have **gnome-session-flashback** installed, where you can login into the
Flashback Metacity session to test.
I always install gnome-session-flashback anyway as a backup if I mess up compiz/unity.

Is the issue you can't focus the input field with the mouse to type in?

---

### Post by luvshines on 2015-03-20
> **CantankRus said:**
> It could be a compiz issue.
Do you have **gnome-session-flashback** installed, where you can login into the
Flashback Metacity session to test.
I always install gnome-session-flashback anyway as a backup if I mess up compiz/unity.
I am a Unity user not Gnome. Does this work with that ?

> Is the issue you can't focus the input field with the mouse to type in?
Mouse always works and I am somehow managing with mouse only to go up/down for typing/editing

---

### Post by CantankRus on 2015-03-20
> **luvshines said:**
> I am a Unity user not Gnome. Does this work with that ?


Mouse always works and I am somehow managing with mouse only to go up/down for typing/editing
gnome-session-flashback is a session using the old style gnome-panel.
It's not gnome-shell.
It will give you 2 extra desktop sessions at the greeter.
[LIST]
[*]GNOME Flashback (Compiz)
[*]GNOME Flashback (Metacity)
[/LIST]
By logging into the Metacity session you can check if it's being caused by compiz.
```
sudo apt-get install gnome-session-flashback
```

---

### Post by luvshines on 2015-03-20
Ah, OK !!

I'll give it a try. I just noticed that I am unable to type in the Gmail mail compose area too. The cursor just goes crazy and keeps jumping back a few characters. However, if I type really slow, it works. :-k

---

### Post by luvshines on 2015-03-23
So I have been using gnome flashback since morning and things seem to be fine.

Now should I stick to this or instead install gnome shell ?
What's the difference between the two of them ?

---

### Post by CantankRus on 2015-03-23
That seems to indicate the problem may be with the window manager....compiz and your gfx/drivers.
It is no longer possible to get the full Ubuntu experience using Metacity as the window manager 
because the unity interface (dash, launcher and panel) is a plugin for compiz.

The Gnome Flashback (Metacity) session uses Metacity as the window manager and the old style panel adapted to work with gnome3.
Actual description from synaptic...
> Metacity is a small window manager, using GTK+ to do everything.
As the author says, metacity is a "Boring window manager for the adult in
you. Many window managers are like Marshmallow Froot Loops; Metacity is
like Cheerios."

Flashback is a basic session designed for those that do not have the gfx capable of running compiz/unity.
Nothing wrong with using it but if you want a bit more whizzbang you can try gnome-shell which uses it's own window manager.
[**_[COLOR="#B22222"]Youtube-Unity vs gnome-shell[/COLOR]_**]("https://www.youtube.com/watch?v=SZU9XzJBgVc")

---

### Post by luvshines on 2015-05-02
BUMP !!

I am using metacity as a workaround but am not happy with it. I miss Compiz :(

Any suggestions on how to fix this ?

---

### Post by CantankRus on 2015-05-02
If you can, install inxi (sys info script)...
```
sudo apt-get install inxi
```
and post the output of...
```
inxi -b
```

---

### Post by luvshines on 2015-05-03
Here you go:

System:    Host: Hiccups-server Kernel: 3.16.0-34-generic i686 (32 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty

Machine:   System: LENOVO product: 4180F59 version: ThinkPad T420
           
Mobo: LENOVO model: 4180F59 Bios: LENOVO version: 83ET70WW (1.40 ) date: 06/12/2012

CPU:       Dual core Intel Core i5-2540M CPU (-HT-MCP-) clocked at 800.210 MHz

Graphics:  Card-1: Intel 2nd Generation Core Processor Family Integrated Graphics Controller 
           
Card-2: NVIDIA GF119M [Quadro NVS 4200M] 
           
X.Org: 1.16.0 drivers: nvidia,intel Resolution: 1600x900@60.0hz 
           
GLX Renderer: NVS 4200M/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.113

Network:   Card-1: Intel 82579LM Gigabit Network Connection driver: e1000e 
           
Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak] driver: iwlwifi 

Drives:    HDD Total Size: 500.1GB (50.4% used)

Info:      Processes: 232 Uptime: 6 min Memory: 778.0/7998.4MB Client: Shell (bash) inxi: 1.9.17

---

### Post by CantankRus on 2015-05-03
Is the **GNOME Flashback (Compiz)** session buggy for you as well?
Don't have experience with dual gfx but that is the area I would be looking for the problem.
Perhaps try a more recent driver from the [**_[COLOR="#B22222"]xorg-edgers ppa[/COLOR]_**]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa")

Try logging into your **Ubuntu** session and setting compiz back to default with 
```
dconf reset -f /org/compiz/
```
Log out and back in.

---

### Post by luvshines on 2015-05-03
> **CantankRus said:**
> Is the **GNOME Flashback (Compiz)** session buggy for you as well?
Yeah, even that is buggy

> 
Perhaps try a more recent driver from the **_[COLOR=#B22222][xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa")[/COLOR]_**

Doing this now...

> 
Try logging into your **Ubuntu** session and setting compiz back to default with 
```
dconf reset -f /org/compiz/
```
Log out and back in.
Will try this too and let you know

Thanks for being onboard ...

---

### Post by luvshines on 2015-05-03
Nope !!
That didn't help.

Tried switching back to xserver-xorg driver.
Then updated to latest Nvidia drivers.

Also tried resetting compiz to default

---

### Post by CantankRus on 2015-05-03
Create a new account and log into the Ubuntu session with that account and test.

---

### Post by luvshines on 2015-05-03
> **CantankRus said:**
> Create a new account and log into the Ubuntu session with that account and test.

I created a 'testuser' and my observations with this:

1. 
- At system startup, I logged into my regular account - Issue prevailed
- I then switch account to 'testuser' - It didn't have issue
- Then switched back to regular user - Voila !! Issue gone

2.
- At system startup, I logged into 'testuser' account - It didn't have issue
- I switched account to regular user - Issue prevailed
- I reswitched to testuser - It didn't have issue
- Then swtiched back to regular user - Voila !! Issue gone

---

### Post by CantankRus on 2015-05-03
You can try logging in with a new **~/.config/dconf/user** file.
Boot up to the greeter and hit ctrl+alt+F1
Login as your normal user and run...
```
mv ~/.config/dconf/user ~/.config/dconf/user.bak
```

Then type in "exit" and hit Enter.
Press ctrl+alt+F7 to return to the greeter.
Login to your normal account.

---

### Post by luvshines on 2015-05-03
> **CantankRus said:**
> You can try logging in with a new **~/.config/dconf/user** file.

This seems to have worked :guitar:
My customizations have gone missing, but atleast this particular issue is no longer seen.

What did recreating this file change ?

---

### Post by CantankRus on 2015-05-04
> **luvshines said:**
> This seems to have worked :guitar:
My customizations have gone missing, but atleast this particular issue is no longer seen.

What did recreating this file change ?
Yeah sorry, should have warned you about that.
It removes anything you may have changed that is stored in dconf settings.
It's like starting as a new user.

You can restore by following the same procedure in [**_[COLOR="#B22222"]post #20[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2269986&p=13278088#post13278088") but running...
```
mv ~/.config/dconf/user.bak ~/.config/dconf/user
```
but then you would have to try and find which dconf setting is causing the problem.

---

### Post by luvshines on 2015-05-04
> **CantankRus said:**
> Yeah sorry, should have warned you about that.
It removes anything you may have changed that is stored in dconf settings.
It's like starting as a new user.

No problem. I am adding everything I had one by one, keeping an eye if it breaks anything

Will post here if I find "that one thing" which breaks it :KS

Happy to mark this SOLVED \\:D/

Thanks a bunch.

---

