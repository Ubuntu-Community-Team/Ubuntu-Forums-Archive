---
title: "Number Pad not working"
date: 2007-07-31
forum: General Help
---

### Post by yataf on 2007-07-31
I'm running xubuntu and my number pad doesn't work even if I have the num lock enabled.

---

### Post by ZombiePriest on 2007-12-09
Greetings
For the record, I do not use Ubuntu, I use Fedora Core with KDE, but I encountered a similar problem.

It could be your mouse settings. Your keyboard is set to move the cursor with your number pad. It happens with hotkeys - I am not sure which, and for the life of me I can not imagine why you would want to move your cursor with your number pad. Maybe it is for people with disabilities?

How I fixed mine:
KDE icon > Control Centre > Peripherals > Mouse > Mouse Navigation

Untick the box that says "_M_ove pointer with keyboard (using number pad)"

I realise you are probably on Ubuntu, but it should work in a similar fashion under GNOME.

---

### Post by lanort2 on 2008-01-26
For me pressing the **numbers** on the **numpad** always **moved** the **mouse pointer**. 
[SIZE="4"]**[COLOR="DarkGreen"]This worked:[/COLOR]**[/SIZE]

[LIST=1]
[*]Go to **System > Preferences > Accessibility > Keyboard Accessibilit**
[*]Select **[x] Enable keyboard accessibility features**
[*]Go to the tab **Mouse Keys** and deselect** [ ] Enable keyboard accessibility features.**
[/LIST]

similar to article: [Ubuntu 7.04 and Virtual PC 2007 - Mouse Issue Workaround (sort of) « Arcane Code]("http://arcanecode.wordpress.com/2007/04/25/ubuntu-704-and-virtual-pc-2007-mouse-issue-workaround-sort-of/")

best, lanort

---

### Post by trstn on 2008-02-09
excellent, this started for me when i upped to Hardy Heron, thanks lanort2, that worked a treat

---

### Post by dezavoo on 2008-03-03
To fix it on Hardy (If you have the problem) : 
Go to : 
1) System
2) Preferences
3) Keyboard (Tab: Mouse Keys)
4) Uncheck (Allow to control pointer using the keyboard).
This should fix the problem....!!

---

### Post by sipickles on 2008-03-29
I had same issue on hardy upgrade.

Thanks Dezavoo!

---

### Post by agibby5 on 2008-04-22
> **lanort2 said:**
> For me pressing the **numbers** on the **numpad** always **moved** the **mouse pointer**. 
[SIZE="4"]**[COLOR="DarkGreen"]This worked:[/COLOR]**[/SIZE]

[LIST=1]
[*]Go to **System > Preferences > Accessibility > Keyboard Accessibilit**
[*]Select **[x] Enable keyboard accessibility features**
[*]Go to the tab **Mouse Keys** and deselect** [ ] Enable keyboard accessibility features.**
[/LIST]

similar to article: [Ubuntu 7.04 and Virtual PC 2007 - Mouse Issue Workaround (sort of) « Arcane Code]("http://arcanecode.wordpress.com/2007/04/25/ubuntu-704-and-virtual-pc-2007-mouse-issue-workaround-sort-of/")

best, lanort



Had this issue when I just upgraded to Hardy... this repaired it. Thanks!

---

### Post by fluid_motion on 2008-04-24
I encountered this issue as well after ungrading to Hardy Heron and was looking at the keyboard settings but couldn't figure it out until I found this thread. Thanks! :)

---

### Post by tlepes on 2008-04-24
> **dezavoo said:**
> To fix it on Hardy (If you have the problem) : 
Go to : 
1) System
2) Preferences
3) Keyboard (Tab: Mouse Keys)
4) Uncheck (Allow to control pointer using the keyboard).
This should fix the problem....!!

I had do do this, but I also had to [X] Enable assistive technologies...

1. Select from the main menu:
    System > Preferences > Assistive Technologies

2. Check the box labeled:
    [X] Enable assistive technologies

3. Click the button labeled:
    Keyboard Accessibility

4. Select the Mouse Keys tab

5. Un-check the box labeled:
    [ ] Allow to control the pointer using the keyboard

6. Enjoy numeric keypad workiness

Seems for me, anyway, enabling or disabling the "Allow to control..." check box made no difference until I enabled the assistive technologies.  And, handily, there is a button to take you from that dialog to the Keyboard Preferences dialog directly.

THANKS!!!

---

### Post by AldenIsZen on 2008-04-25
I had an even worse issue. I upgraded from Fiesty 7.10 and whenever I tried to use the num_pad I guess it was X-Server crashed and I was eventually brough back to the login screen. Accessablity being enabled didn't seem to matter, as long as I disable the "Allow to control the pointer useing the keyboard." I am good to go.

 Glad a fix has been found, as I have been paranoid I was going to lose everything by hitting the num_pad since I upgraded last Tuesday.  Even worse, the session manager isn't working in Firefox 3 for me, and the addon I used isn't compatible with FF 3 yet.

---

### Post by Humph on 2008-04-25
[LIST=1]
[*]Go to **System > Preferences > Accessibility > Keyboard Accessibilit**
[*]Select **[x] Enable keyboard accessibility features**
[*]Go to the tab **Mouse Keys** and deselect** [ ] Enable keyboard accessibility features.**
[/LIST]
Thanks **lanort2 **that fixed it!

---

### Post by tlepes on 2008-04-25
> **AldenIsZen said:**
> I had an even worse issue. I upgraded from Fiesty 7.10 and whenever I tried to use the num_pad I guess it was X-Server crashed and I was eventually brough back to the login screen. Accessablity being enabled didn't seem to matter, as long as I disable the "Allow to control the pointer useing the keyboard." I am good to go.

Well I suppose YMMV.  It did make a difference for me in that _before_ I enabled assistive technology, the numpad failed.  The mouse keys thing was set, initially.  (Value in gconf database I guess).  But it wasn't "active" because Assistive Techs were off.  So toggling the checkbox there had no effect on me.  Once I enabled the assistive technologies, then I was able to toggle the mousekeys feature and when leaving it off the numpad was fine, even if I disable assistive technology.  Go figure.

> **AldenIsZen said:**
> Glad a fix has been found, as I have been paranoid I was going to lose everything by hitting the num_pad since I upgraded last Tuesday.  Even worse, the session manager isn't working in Firefox 3 for me, and the addon I used isn't compatible with FF 3 yet.

Okay this is off-topic for the thread; but I think I have an idea for you.  I had the same issue (or very similar).  I had the Tab Mix Plus extension and it was configured to use it's own superior session manager (multiple sessions history, crash recovery, etc.).  I didn't do an upgrade install, but rather I did a fresh install but used my old /home partition on the new install.  Anyway, I found that there IS a newer version of Tab Mix Plus that works with 3.0b5.  I installed that newer version and was back in the land of saved-session sweetness.  I have not tested whether disabling the TMP SS will properly revert to the FF SS or not.  Nor have I tested uninstalling TMP.  I am just too damn happy to have it again.

Now if your extension was something OTHER than Tab Mix Plus, I am not sure this helps you or not.  You can try removing the inactive incompatible extension and see if FF SS starts to work.  The TMP update I found is here:  [http://tmp.garyr.net/tab_mix_plus-dev-build.xpi]("http://tmp.garyr.net/tab_mix_plus-dev-build.xpi")

It's not a Mozilla release.  It's a dev-build.  tmp.garyr.net is the TMP developer's site.  I found the link in the the forum, on the 37th page of the "builds" topic, in the sig-line of one of oneman's posts.  Link to the page: [http://tmp.garyr.net/forum/viewtopic.php?t=7031&postdays=0&postorder=asc&start=720]("http://tmp.garyr.net/forum/viewtopic.php?t=7031&postdays=0&postorder=asc&start=720")

_AS_ I was surfing his pages to dig up the links for you, his account got suspended by Bluehost.com.  Hopefully that will be resolved by the time you read this.  For the record, the build is: Tab Mix Plus Dev-Build 0.3.6.1.080416, which worked for me.  Other 0.3.6.x dev-builds might or might not work, I don't know.  For the moment, if you try and download the .xpi you'll get Bluehost's error page html instead of the extension.  I installed directly so I don't have an .xpi - just checked.  But I did find the install directory under my profile for TMP.  Mabye there is a way... I know that the FEBE extension could save-out an installed plugin as an .XPI file.  Unfortunately that extension needs major re-working to be compatible with FF3.x so using that to generate an XPI for you is out of the question.  Sad, I really loved FEBE.  Just have to wait I guess.

Well oh well oh wellie well...  If it doesn't work, I'd at least start a thread dedicated to that separate problem, so this thread can stay clean WRT the number-pad issue.  If you do that, post a link here back to the new thread.  If you email me, I can see about sending you the contents of my TMP install folder.

GOOD LUCK!
Tim

---

### Post by tlepes on 2008-04-25
Okay I uploaded it to FileDen... the link is [http://www.fileden.com/files/2007/1/30/715234/TMP0.3.6.1.080416-install-directory.tar.gz]("http://www.fileden.com/files/2007/1/30/715234/TMP0.3.6.1.080416-install-directory.tar.gz")

Hope that helps.
Tim

---

### Post by acabre on 2008-05-02
I just want to second AldenIsZen's post. As soon as I upgraded to 8.04 hitting any of the numpad keys, with or without numlock on, would kill X. The numpad works fine in GDM or TTY w/o X. Disabling mouse keys as above solved the issue.

Is this worth filing a bug over?

---

### Post by tgice on 2008-05-02
Thanks.  Fixed for me on Hardy.

---

### Post by SL666 on 2008-05-06
Slightly modified

```

1. Go to System > Preferences > Assistive Technologies 
2. Keyboard Accessibility > mouse keys tab
3. Deselect "Allow to control the pointer using the keyboard"

```

Worked for me on Hardy just after upgrade.

---

### Post by Timrit_jr on 2008-05-12
This worked great! I was frustrated after this somehow got activated over ssh-vnc session and I could not get the number pad working. Thanks very much.

---

### Post by kag on 2008-05-15
I had the same problem in Hardy with a clean install. Thanks for the fix!

---

### Post by kag on 2008-05-28
The same problem occured back yesterday. I did the procedure again and was good to go.

Today I get back from work, same problem again!! What could be causing this?

---

### Post by apokkalyps on 2008-06-06
Just to go on the record.  Hardy is weird about this issue.  For me, my numpad wasnt working, so I looked into this mouse/num-pad thing.  Strangely the setting was already turned off for me.  But I turned it on and off again and it fixed it.

If your having this problem and looking for a fix, but this setting is already off, and you think this solution doesnt apply to you, try turning it on and back off again.

---

### Post by Alexstone on 2008-06-07
Yep, thanks for the fix. Works here in Ubstudio hardy 64bit.

The only issue left here is being able to assign mouse right click to the keyboard. (The reverse of what most people are trying to do.)

Alex.

---

### Post by Shrav on 2008-06-09
These tips fixed it for me too. Thanks to all!!! :guitar:

---

### Post by Prada87 on 2008-06-27
This didnt fix it for me! Though something strange I noticed.

I enabled and disabled as people suggested.. didnt work. After disabling it, I test in the firefox address bar with numlock on.. It just uses the arrows and other features usually used when numlock is OFF.. 

Well, I turn numlock off.. And I get use of the numbers.

Not sure whats causing this, works fine with numlock on when im logging in so I know its not my keyboard.




Using Xubuntu Hardy, for those that use ubuntu and never used xubuntu, the preferences layout is slightly different.. Xubuntu is Settings > Settings Manager > Mouse > Accessibility Tab > Uncheck "enable mouse emulation"

Though if anyone has the exact problem I do, thats not really relevant :) but may help new users that havent familiarized themselves with the xubuntu menus.


Note: Just went into Scim Input while typing this.. Have to "restart scim" for settings to take effect, but in global setup my keyboard was set to unknown. Possibly the cause? Set it to english(US) when I installed, and was working fine for a while.. Something may have triggered it to do that.. I will update if it fixes it.

---

