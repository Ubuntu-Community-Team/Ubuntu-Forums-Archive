---
title: "Xubuntu 14 user login problem"
date: 2014-11-02
forum: General Help
---

### Post by garymcrobertpdx on 2014-11-02
I turned on the machine every thing seemed to work until I try to login
as I usualy do.  When I enter my pass it acts like I have entered the
correct pass but No icons appear and I get no response to keyboard
or mouse clicks.  I can log in as guest that works.  How can I fix this
and get acess to my acount???

---

### Post by ajgreeny on 2014-11-02
Temporarily rename the /home/<user>/.config/xfce4 folder as /home/<user>/.config/xfce4bak and login again.  That should take you to a default desktop and from that you can try to get back to what you want it to look like.

You may need to do this from recovery mode if you have no mouse or keyboard working after a guyi login, or you can try using a command line mode, not a GUI by hitting E at the grub menu(to edit) and changing the words "quiet splash" in the kernel line to "text", use F10 or Ctrl+X to boot and use command ```
mv /home/<user>/.config/xfce4 /home/<user>/.config/xfce4bak && startx
```

---

### Post by garymcrobertpdx on 2014-11-02
Thank you for responding to my help request.  I am having trouble in getting into the text mode.
I never see any reference to Grub during the boot process.  When I boot just after the BIOS messages
I have tried entering  Ctrl x or F10 .   For a few seconds there is a scroll of text then the login splash
appears and I am right back to the problem. There is no response to any keyboard input during the text
scroll.  Is there some other setting that enables the Grub message at boot time? Perhaps in the BIOS
I have it set to a quick boot mode.

---

### Post by Elfy on 2014-11-02
> **garymcrobertpdx said:**
> Thank you for responding to my help request.  I am having trouble in getting into the text mode.
I never see any reference to Grub during the boot process.  When I boot just after the BIOS messages
I have tried entering  Ctrl x or F10 .   For a few seconds there is a scroll of text then the login splash
appears and I am right back to the problem. There is no response to any keyboard input during the text
scroll.  Is there some other setting that enables the Grub message at boot time? Perhaps in the BIOS
I have it set to a quick boot mode.

Press and hold Shift.

Then you'll get grub menu and you can follow ajgreeny's post.

---

### Post by garymcrobertpdx on 2014-11-02
I would like to amend my last message during the text scrol I have tried
various keyboard inputs and there is some response but only delays
the appearance of the login splash.  I have not been able to pause or
stop the process and get terminal input control.

Is there any posablity of using a Xubuntu 14 live disk to help solve
the problem I am having?

---

### Post by garymcrobertpdx on 2014-11-02
Thanks Elfy  Pressing the shift key works wonders.  Tried ajgreeny's sugestion but it seems not to yeild results.
I have reason to supect that the HD is totaly full perhaps this maybe the cause of my problem.  I also note that
there exists Advanced options for Ubuntu various boot options in the recovery mode there is a clean function 
pehaps this would help or make maters worse.  Also there are other functions what they do is not as clear as
I would like and supect can cause harm if not used correctly.

---

### Post by Bashing-om on 2014-11-02
garymcrobertpdx; Hello;

I offer my aid. Following ajgreeny's advise to get to a text terminal, in order to follow through.

Booting with the 'text' boot parameter one does have all the booting messages on the screen, you should get to a text terminal (TTY1).
Log in here at this terminal with you username followed by the requested pass word. There will be no response to the screen when the pass word is entered - security reasons. These edits are a one time thing that does not persist when rebooted.

Advise us if you are unable to activate this terminal interface, then yes, we may employ the liveDVD to effect repairs .

With time, effort, thought and a liveDVD ->

[INDENT][INDENT]it's all fixable
[/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2014-11-02
Thank you!!!

Success I am loged into my account!  The first thing I would like to do is copy several files to a USB or to the other hard disk that is in the box
before any other attempts are made to recover the system.  How ever I do not know how to copy to ether of the forementiond storage devices.

---

### Post by Bashing-om on 2014-11-02
garymcrobertpdx; Great;

You do not advise what the level of success is. Are you now able to boot to the GUI desktop ?

> **garymcrobertpdx said:**
> Thank you!!!

Success I am loged into my account!  The first thing I would like to do is copy several files to a USB or to the other hard disk that is in the box
before any other attempts are made to recover the system.  How ever I do not know how to copy to ether of the forementiond storage devices.

If you are in the GUI it is a simple matter to open the file manager, activate an additional window as the target, and drag/drop files between the two windows.

[INDENT][INDENT]else:
[INDENT][INDENT]'buntu, we can do something else
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2014-11-02
At the moment I only have text access.  The GUI still is not working. If I type a Dir I see a list of directories and files that are in my home dir.
I have been researching how to mount a USB drive or the other hard drive that is in my box.  Then make back up copys of important data files.
So far I have not found out how to do this operation via a command line input.  At the moment if I type lsusb I see the Lexar thumb drive listed
as Device 005 and a ID in hex

---

### Post by Bashing-om on 2014-11-02
garymcrobertpdx; Well.

To the present GUI; Have you ran ajgreeny's recommendation:
```

mv /home/<user>/.config/xfce4 /home/<user>/.config/xfce4bak && startx

```
What results when "startx" is executed ?

As to setting up the USB from terminal. What is the device Identification; What file system is on the USB?  these will be factors in mounting it.
Plug in the USB drive and post the output of terminal command:
```

sudo fdisk -lu

```
Once known what the system sees the device as and assigns the identification, we can mount it from terminal and copy files to it.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2014-11-02
I found A soulution.  I was correct the HD was compleatly full.  When I removed a Gig or so of unimportant files
and rebooted the GUI started working again.

Thanks to all for the helping hand.

---

### Post by Bashing-om on 2014-11-02
garymcrobertpdx; Well done .
Glad it has all worked out.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2015-01-17
Once agian the login via the GUI is screwed up.  I have attemped the fix that worked before but this fails to fix it.

When I use the comand 
mv /home/<user>/.config/xfce4 /home/<user>/.config/xfce4bak && startx

I recive an error mesage cannot move /home/<user>/.config/xfce4 to /home/<user>/.config/xfce4bak/xfce4 Directory not empty

So do I have to remove the dir xfce4 then do this ????

---

### Post by Bucky Ball on 2015-01-17
From the text window:

```
startxfce4
```

GUI?

---

### Post by garymcrobertpdx on 2015-01-18
thanks seems to setup my user desktop and things work but it is not permanent. If I restart the computer the login problem reappears.
Is there a dir or file I should remove then run startxfce4?

---

### Post by garymcrobertpdx on 2015-01-19
Still unsolved problem Xubuntu 14 login.  Boot the system get the splash screen,  login works for guest but not for my user account despite the proper password
it loops back to the login tile.  If I input a bogus pass it rejects it as would be expected.

I have been learing about xfce4 and have tried several fixes but have not discovered where the cause of this problem is.  I can login using the Grub edit to text
and use startxfec4 this works but dose not permanently fix the problem when I restart the system I am back where I started.

This all started after allowing a routine upgrade the next time I started up the computer it did not display my user login tile now after messing around I have
the login tile but it dose not work.

---

### Post by Bashing-om on 2015-01-19
garymcrobertpdx; Welp,

Now, that sounds like you have been 'sudo'n' in your /home where you should not have and have lost authorization to either/both the Xserver/home.

What authorizations exist ?
```

ls -al .Xauthority
ls -al .ICEauthority

```
Who owns 'your' /home ?
```

ls -al /home
ls -al /home/<user_name>

```

[INDENT][INDENT]sometimes, it matters
[/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2015-01-19
Thank you for replying to my request for help.

I avoid messing with anything unless I am left no other choice.  As I said this problem
appeared spontaneously after the last auto OS update.  At this point I started trying 
remedies suggested here.

I did the  &#65279;Lists the contents of a directory commands but the lists it produced is not
meaningful to me at least as to how they relate to the problem.

I see seven columns of charters like drwx , digits 1-40,  root or user name,  another 
root or user name,  a file size,  date & time and finally directory or file names.

ls -al /home/<user_name >  produced a large list with names I recognize
the results from the other three commands are much shorter and not understood.

Is there a particular clue in these outputs I should look for?

---

### Post by Bashing-om on 2015-01-19
garymcrobertpdx; Hey ;

Dinner called me away from the keyboard .

What ya need to do is post those outputs back to this thread - Between Code Tags -> to maintain readability.
We will examine them .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then give a lesson on how to read these outputs .

[INDENT][INDENT]ain't nothing put a thing
[/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2015-01-19
Here is the outputs I got.    for some reason all the text gets jamed togather tag or no tag    ```
 root@thing:~# ls -al .Xauthority -rw------- 1 root root 248 Jan 19 16:53 .Xauthority root@thing:~# ls -al .ICEauthority -rw------- 1 root root 36742 Jan 19 16:53 .ICEauthority root@thing:~# ls -al /home total 28 drwxr-xr-x  4 root  root   4096 Jul 28 21:44 . drwxr-xr-x 24 root  root   4096 Jan 14 17:10 .. drwxr-xr-x  3 root  root   4096 Jul 28 21:44 .ecryptfs drwx------ 40 Linuxuser1 Luser1 16384 Jan 19 16:53 Luser1 root@thing:~# ls -al /home/Luser1 total 8192472 drwx------ 40 Luser1 Luser1      16384 Jan 19 16:53 . drwxr-xr-x  4 root  root        4096 Jul 28 21:44 .. drwx------  3 Luser1 Luser1       4096 Jul 29 20:59 .adobe -rw-------  1 Luser1 Luser1        891 Jan 19 17:50 .bash_history -rw-r--r--  1 Luser1 Luser1        220 Jul 28 21:44 .bash_logout -rw-r--r--  1 Luser1 Luser1       3637 Jul 28 21:44 .bashrc drwx------  6 Luser1 Luser1       4096 Jan 19 17:51 .cache drwxrwxr-x  6 Luser1 Luser1       4096 Sep 20 19:30 .clamtk drwx------ 32 Luser1 Luser1       4096 Jan 19 16:25 .config -rwx------  1 Luser1 Luser1 4194308096 Jan  2 21:43 data0 -rwx------  1 Luser1 Luser1 4194308096 Jan 18 19:59 data1 drwx------  3 root  root        4096 Aug  5 20:03 .dbus drwxr-xr-x  5 Luser1 Luser1      12288 Jan 19 17:50 Desktop -rw-r--r--  1 Luser1 Luser1         38 Jan 18 03:55 .dmrc drwxr-xr-x  2 Luser1 Luser1       4096 Dec  8 11:14 Documents drwxr-xr-x  2 Luser1 Luser1       4096 Jan 17 15:43 Downloads lrwxrwxrwx  1 Luser1 Luser1         31 Jul 28 21:44 .ecryptfs -> /home/.ecryptfs/Luser1/.ecryptfs drwxrwxr-x  2 Luser1 Luser1       4096 Nov  2 17:00 flash drwx------  3 Luser1 Luser1       4096 Jan 19 16:53 .gconf drwxr-xr-x 24 Luser1 Luser1       4096 Dec 10 10:38 .gimp-2.8 -rw-r-----  1 Luser1 Luser1          0 Jan 17 01:52 .gksu.lock drwx------  3 Luser1 Luser1       4096 Nov 10 12:57 .gnome2 drwxrwxr-x  2 Luser1 Luser1       4096 Nov  9 11:14 .gstreamer-0.10 dr-x------  2 root  root           0 Jan 19 16:48 .gvfs -rw-------  1 root  root       36742 Jan 19 16:53 .ICEauthority drwxrwxr-x  2 Luser1 Luser1       4096 Oct 29 12:02 Installers drwxrwxr-x  3 Luser1 Luser1       4096 Oct  7 11:16 .java drwx------  3 Luser1 Luser1       4096 Sep 14 23:28 .kde -rw-------  1 Luser1 Luser1         35 Aug 21 10:26 .lesshst drwxrwxr-x  3 Luser1 Luser1       4096 Jul 29 07:26 .local drwx------  3 Luser1 Luser1       4096 Jul 29 20:59 .macromedia drwx------  4 Luser1 Luser1       4096 Jul 29 07:43 .mozilla drwxr-xr-x  2 Luser1 Luser1       4096 Jul 29 07:25 Music drwxr-xr-x  2 Luser1 Luser1      12288 Jan 10 13:11 Pictures drwx--x--x  5 Luser1 Luser1       4096 Oct 14 08:26 .pokerth lrwxrwxrwx  1 Luser1 Luser1         30 Jul 28 21:44 .Private -> /home/.ecryptfs/Luser1/.Private -rw-r--r--  1 Luser1 Luser1        675 Jul 28 21:44 .profile drwxr-xr-x  2 Luser1 Luser1       4096 Jul 29 07:25 Public drwx------  4 Luser1 Luser1       4096 Aug 19 22:13 .purple drwxr-xr-x  2 Luser1 Luser1       4096 Oct  6 16:27 .rpmdb drwxrwxr-x  2 Luser1 Luser1       4096 Jul 30 13:12 TEMP1 drwxrwxr-x  2 Luser1 Luser1       4096 Nov  1 09:50 TEMP2 drwxrwxr-x  2 Luser1 Luser1       4096 Dec 10 21:02 TEMP3 drwxr-xr-x  2 Luser1 Luser1       4096 Jul 29 07:25 Templates drwx------  4 Luser1 Luser1       4096 Jul 29 22:15 .thumbnails drwx------  4 Luser1 Luser1       4096 Aug 22 18:18 .thunderbird drwx------  2 Luser1 Luser1       4096 Jan 11 21:00 .TC -rw-------  1 Luser1 Luser1          6 Jan 11 21:00 .TC-lock-Luser1 drwxrwxr-x  2 Luser1 Luser1       4096 Jul 29 10:04 .vidalia drwxr-xr-x  2 Luser1 Luser1      61440 Jan 12 01:21 Videos drwxrwxr-x  4 Luser1 Luser1       4096 Jan 18 02:38 .wine drwxrwxr-x 12 Luser1 Luser1       4096 Sep  5 23:05 wine-1.6.2 drwxrwxr-x 13 Luser1 Luser1       4096 Sep  5 23:08 wine-git -rw-------  1 root  root         248 Jan 19 16:53 .Xauthority -rw-r--r--  1 Luser1 Luser1       1601 Jul 28 21:44 .Xdefaults -rw-r--r--  1 Luser1 Luser1         14 Jul 28 21:44 .xscreensaver -rw-------  1 root  root        6061 Jan 19 17:59 .xsession-errors root@thing:~#        
```

---

### Post by Bashing-om on 2015-01-20
garymcrobertpdx; Yep.

Root is authorized to all .. but NOT "YOU" .

Will take a bit of time to fix these . I am done for this session so will address this next evening .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2015-01-20
Would I be better off trashing the OS and reinstalling?

---

### Post by Bashing-om on 2015-01-20
garymcrobertpdx; Hey;

I am back ...
as too:
> 
Would I be better off trashing the OS and reinstalling?


Nope, I am not of that opinion .. Look at all you are learning and as well gaining in the comfort level in system administration. But, It is your system, your time and your call ..
Re-establishing the ownerships should not be a big deal;

I am not comfortable with you working in a root shell, and it is possible that working as 'root' may impede what we need to do in your /home directory. 
Can you boot to the log in screen and there get to a console by pressing the key combo ctl+alt+F1 ?
I know of no reason presently that you can not, once you get to the console enter your user name and then your password - there will be no response to the screen when pass word is entered . Enter your pass word blindly .

If required to shut the system down from the console:
```

sudo shutdown -h now

``` will do that for ya.


When you get logged into this console, we will continue.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2015-01-20
OK Im game to give it a go. I let the system boot up and display the user login. pressed the ctr+alt+F1 combo, got the terminal login mesage, I loged in sucsessfully.
whats next?

---

### Post by Bashing-om on 2015-01-20
garymcrobertpdx; Great ...

from the F1 console; terminal commands:
```

chown USERNAME:USERNAME .ICEauthority
chown USERNAME:USERNAME .Xauthority
chown USERNAME:USERNAME /home/USERNAME

```
Where "USERNAME" is your actual name you use to log onto the system .

Reboot, and see now that you have access to the GUI desktop .

[INDENT][INDENT][INDENT]Hey, it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2015-01-20
Results:

chown USERNAME:USERNAME .ICEauthority
chown: changing ownership of .ICEauthority : Operation not permitted
chown USERNAME:USERNAME .Xauthority
chown: changing ownership of .Xauthority : Operation not permitted
chown USERNAME:USERNAME /home/USERNAME
happy with this line

Apparently it's not in a cooperative mood

---

### Post by Bashing-om on 2015-01-20
garymcrobertpdx; Humm .. unexpected result.

I would have thought that as we are working in "your' /home directory .. elevated privileges would not have been required .... but, from that advisory:
```

sudo chown USERNAME:USERNAME .ICEauthority
sudo chown USERNAME:USERNAME .Xauthority

```
USERNAME still as your login name .

[INDENT][INDENT]how now
[INDENT][INDENT][INDENT]brown cow
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2015-01-20
sudo chown USERNAME:USERNAME .ICEauthority
sudo chown USERNAME:USERNAME .Xauthority
OK it swallowed those lines with out barfing whats next?

---

### Post by garymcrobertpdx on 2015-01-21
I went ahead and entered 
chown USERNAME:USERNAME /home/USERNAME
and rebooted YOW it's alive

Super thanks! Are there any other things that should be done?

---

### Post by Bashing-om on 2015-01-21
garymcrobertpdx; Great ...
Ok:
> 
Super thanks! Are there any other things that should be done?

From your desktop activate a terminal.
Now execute:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```
If all runs clean ->

[INDENT][INDENT]you are good to go
[/INDENT][/INDENT]

---

### Post by garymcrobertpdx on 2015-01-21
Looks good many many thanks for the helping hand.  In time I hope to aquire a much better understanding of Linux but probably will be in need of this sort of help for some time. Again thanks for all the assistance.

---

### Post by Bashing-om on 2015-01-21
> **garymcrobertpdx said:**
> Looks good many many thanks for the helping hand.  In time I hope to aquire a much better understanding of Linux but probably will be in need of this sort of help for some time. Again thanks for all the assistance.

That is all it takes; time, effort and a willingness to learn. We are all at some point on that learning curve.

This is open source at it best
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-01-21
> **Bashing-om said:**
> That is all it takes; time, effort and a willingness to learn. We are all at some point on that learning curve.

This is open source at it best
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT]

Indeed. ;)

Enjoy the OS, the forums and the learning curve, garymcrobertpdx, and thanks for marking the thread as solved. It is a great help to future travelers.

---

