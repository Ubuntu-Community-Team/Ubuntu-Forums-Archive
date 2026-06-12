---
title: "Hardy Heron 8.04: Turning NumLock On"
date: 2008-05-03
forum: General Help
---

### Post by luvr on 2008-05-03
**_Automatically turning NumLock on under Hardy Heron: What worked for me._**

[LIST]
[*]**Ubuntu (*GNOME*; *GDM* display manager)**
Under Ubuntu, you will have to install the *"numlockx"* utility. Either use the Synaptic package manager, or run the following command:
```
sudo apt-get install numlockx
```
Next, edit the file *"/etc/gdm/Init/Default"* (You will need administrative privileges to do this--e.g., hit <Alt><F2> and enter *"gksudo gedit"* to start the text editor).
Scroll down to the end of the file, where you will find a line that reads:
```
exit 0
```
Just above this line, add the following:
```
[B]if [ -x /usr/bin/numlockx ]
then
   /usr/bin/numlockx on
fi[/B]
*(The *"exit 0"* line comes here.)*
```
This will turn NumLock *on* when the login screen is displayed.
However, when you subsequently log in, GNOME will turn NumLock *off* again.

*****THE NEXT BIT OF INFORMATION SEEMS TO BE INCORRECT*****
[INDENT]To force GNOME to turn NumLock *on* once you log in:
[LIST]
[*]Open *"System"* -> *"Preferences"* -> *"Session"*;
[*]Open the *"Startup Programs"* tab;
[*]Click *"Add"*;
[*]Type in the command *"/usr/bin/numlockx on"* and specify an appropriate name and comment.
[/LIST]
NumLock will get briefly deactivated while GNOME loads, but it will get reactivated when *numlockx* is executed as a startup program.[/INDENT]
*****END OF APPARENTLY INCORRECT INFORMATION*****

**CORRECTION:** If you want to activate NumLock after you log in, then you will have to press the *"NumLock"* key on your keyboard. ***In my experience, if NumLock is active when you log out, then GNOME will reactivate it when you log in the next time.***
[/LIST]
[LIST]
[*]**Xubuntu (*XFCE*; *GDM* display manager)**
Under Xubuntu, you will have to install the *"numlockx"* utility, just as described above for Ubuntu.
You will also have to edit the file *"/etc/gdm/Init/Default"* (again, just as under Ubuntu).
However, as opposed to GNOME, the XFCE environment will *not* deactivate NumLock again. In other words, no further configuration is needed.
[/LIST]
[LIST]
[*]**Kubuntu (*KDE 3*; *KDM* display manager)**
Under Kubuntu, you will have to edit the parameter file *"/etc/kde3/kdm/kdmrc"* (Again, you will need administrative privileges).
Locate the following line in the file:
```
[X-*-Greeter]
```
Just below this line, add the following line *(NOTE: This line is case-sensitive)*:
```
**NumLock=On**
```
Next, make sure that KDE will leave NumLock unchanged (*"System Settings"* -> *"Keyboard and Mouse"*; find the *"NumLock on KDE Startup"* heading, and select *"Leave unchanged"*).
Or, better yet, make sure that KDE turns NumLock *On*--i.e., select *"Turn on"* instead of *"Leave unchanged."*
[/LIST]
[LIST]
[*]**Kubuntu-kde4 (*KDE 4*; *KDM* display manager)**
Under Kubuntu-kde4, you will have to make the exact same modifications as under Kubuntu (see above), but its parameter file is *"/usr/lib/kde4/etc/kde4/kdm/kdmrc"* instead.

**UPDATE FOR KDE 4 UNDER Kubuntu 8.10 (*"Intrepid Ibex"*):** The parameter file is *"/etc/kde4/kdm/kdmrc"*
[/LIST]
**_If you still have problems: Further links._**
[Ubuntu Forums: Number Pad not working.]("http://ubuntuforums.org/showthread.php?p=3113362")
[Ubuntu Launchpad Bug #218202: numlockx does not turn num lock keyboard light on.]("https://bugs.launchpad.net/ubuntu/+source/numlockx/+bug/218202")

---

### Post by dmoyne on 2008-06-13
Strange in KDE 4 (/usr/lib/kde4/etc/kdm/kdmrc) there are 2  [X-*-Greeter] section one said general the other local ; how to discriminate ?
Thanks

---

### Post by Pjotr123 on 2008-06-13
Why make it so difficult? I simply installed numlockx like this:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 11 )

That's all, and it works.  :-)

---

### Post by luvr on 2008-06-14
> **dmoyne said:**
> Strange in KDE 4 (/usr/lib/kde4/etc/kdm/kdmrc) there are 2  [X-*-Greeter] section one said general the other local ; how to discriminate ?
Thanks
I only have **one** *"X-*-Greeter"* section.
There is, however, also a section named *"X-**:***-Greeter"* (with a colon--i.e., *":"*--before the asterisk).
You should select the one **without** the colon.

---

### Post by avtolle on 2008-06-14
> **Pjotr123 said:**
> Why make it so difficult? I simply installed numlockx like this:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 11 )

That's all, and it works.  :-)
True enough, and that's how it works for me, but looking at what was posted, I surmise this is a way to get it turned on "early", that is, before one logs in.

---

### Post by rats54 on 2008-08-03
I have three computers running Ubuntu, one runs 7.10 and the other two run 8.04. The above information works on one of the computers, that is running 8.04, but not on the other two.  The two computers that do not activate number lock before log on are both Dell, the other one is not a Dell.

Both Dell computers have number lock set to on in the BIOS. When both of the computers start to boot the number lock light comes on. It stays on until the Linux kernel starts to load, then it goes off.

When the Log On screen appears the number lock light is off.  I must manually press the Num Lock key to turn it on. (I use alpha-numeric passwords)  The light then stays on through the rest of the boot and is still on when Ubuntu is fully booted. 

Does anyone have any ideas on how to fix this problem?

Thanks.

---

### Post by luvr on 2008-08-03
> **rats54 said:**
> Both Dell computers have number lock set to on in the BIOS. When both of the computers start to boot the number lock light comes on. It stays on until the Linux kernel starts to load, then it goes off.
That seems to be the expected behaviour: Once the Linux kernel gets control, you're out of the BIOS. The Linux kernel then turns NumLock OFF (as does Windows, when--and if ;)--it loads, by the way).

> When the Log On screen appears the number lock light is off.
That must mean that the **numlockx** utility wasn't run (or wasn't instructed to turn NumLock ON). I recommend that you double-check your *"/etc/gdm/Init/Default"* file, and see if there aren't any typos in it. Also, verify that the *numlockx* utility is at the location where the file expects it--i.e., at **/usr/bin/numlockx.**
If everything appears to be OK, then perhaps you could post the contents of your *"/etc/gdm/Init/Default"* file here, along with the output from the command:
```
ls -l /usr/bin/numlockx
```

---

### Post by rats54 on 2008-08-04
Thank you luvr, thank you!

I have the problem fixed, thanks to your comments.

You made me take a closer look at the /usr/gdm/Int/Default file. Made me look further than the entry I made in the file.  In the file on both Dell computers there were if statements that were not closed with the fi statement.  Both files were different and the open if statements were different.

I never thought to look at the whole file. I just assumed everything was ok, went to the end of the file and added the if statement for numlockx and saved it.

Your comments made me check everything and when everthing was ok and numlocx worked when I ran it from a CP that made me look more closely at the Default file.

Thanks again.

rats

---

### Post by dave37 on 2008-08-29
Thanks luvr, this worked great!  Finally I don't tap away at the num pad blindly and then have to log on again!

---

