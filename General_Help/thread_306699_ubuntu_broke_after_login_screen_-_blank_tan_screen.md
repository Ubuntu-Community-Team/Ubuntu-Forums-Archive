---
title: "ubuntu broke after login screen - blank tan screen"
date: 2006-11-25
forum: General Help
---

### Post by onesojourner on 2006-11-25
I had my nvidia driver all screwed up so I was uninstalling it and reconfiguring xorg. my first problem was xorg was so screwed up it wouldn't load. now I get to my normal gnome login screen but after that the screen stays tan and nothing ever loads up. I can use ctrl alt delete and get my system monitor. samba seems to be running and I can ctrl alt F1 and switch to the command line. if let to sit the blank tan screen never makes any progress. it will just sit there. any think they can walk me through fixing this one?
](*,)

---

### Post by taurus on 2006-11-25
Get into a console and log in with your username and password.  Then, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by onesojourner on 2006-11-26
I have tried that a few times. I have tried to use the nv driver and the vesus (I think) and neither one of those fixed anything. is there any thing specific I need to change or look out for?

---

### Post by taurus on 2006-11-26
What graphic card do you have and what does your /etc/X11/xorg.conf look like?

```
cat /etc/X11/xorg.conf
```

---

### Post by charlottevdveer on 2006-11-26
try changing the driver drom nv to nvidia. That helped for me

---

### Post by taurus on 2006-11-26
> **charlottevdveer said:**
> try changing the driver drom nv to nvidia. That helped for me
Yes, if you have installed an nvidia driver for your card first!!!

---

### Post by onesojourner on 2006-11-26
well changing it to nvidia is not even an option when I am reconfiguring xorg. can some one walk me through totally uninstalling any kind of video drivers I have installed and reinstalling the newest nvidia drivers? my video card is an nvidia 5200 (64mb) if that matters. is there any kind of safe mode I can go into to use a gui as it is now? if I try to reconfigure xorg to use the nv driver xorg fails to start the only thing that is working at all right now is the vesa driver.

---

### Post by taurus on 2006-11-26
```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```
Then restart X with <Ctrl><Alt>Backspace.

---

### Post by onesojourner on 2006-11-26
ok I did that and the nvidia logo screen is thrown in to the boot up mix but I still get stuck on the tan screen after login.

---

### Post by onesojourner on 2006-11-26
and I reconfigured xorg to use the nvidia driver

---

### Post by taurus on 2006-11-26
> **onesojourner said:**
> and I reconfigured xorg to use the nvidia driver
"sudo nvidia-xorg" should have already taken care of that for you...

---

### Post by taurus on 2006-11-26
> **onesojourner said:**
> ok I did that and the nvidia logo screen is thrown in to the boot up mix but I still get stuck on the tan screen after login.
Do you mean Gnome desktop?  Look at the upper left corner, do you see Ubuntu logo?  Then, you should see Applications and when you click on that, you will see more menus about Office, Internet, Games, Video & Sound, etc.

---

### Post by onesojourner on 2006-11-26
> **taurus said:**
> "sudo nvidia-xorg" should have already taken care of that for you...

I got command not found.

---

### Post by taurus on 2006-11-26
It should be "sudo nvidia-xconfig" but if you see the nVidia white logo, then you are using nvidia driver so no need to do anything else!!!

---

### Post by onesojourner on 2006-11-26
but I still have the tan screen... it never finishes the boot into gnome. after login it just sits there with a blank tan screen.

---

### Post by taurus on 2006-11-26
I am not exactly sure what you mean black tan screen!  :confused:

---

### Post by onesojourner on 2006-11-26
ok see the back grount of the screen that you login at? I get to my login in screen and all seems normal, but after I login instead of the little splash thing showing everything getting loaded up it just sits there at the tan screen. the spash screen never appears. just a blank tan screen. I have a cursor thats it.

---

### Post by taurus on 2006-11-26
After entering your login name and password, do you hear any music playing at all?

---

### Post by onesojourner on 2006-11-26
I hear the du du when the login window pops up but nothing after login.

---

### Post by taurus on 2006-11-26
Do you see anything like icons and words in the upper left corner or a digital clock in the upper right corner?

---

### Post by onesojourner on 2006-11-26
nope nothing. just tan screen with a cursor.

---

### Post by onesojourner on 2006-11-27
I am giving this a bump. I have to get this fixed.

---

### Post by taurus on 2006-11-27
Got a digital camera that you can take a screenshot!!!

---

### Post by onesojourner on 2006-11-27
not with me but I can make a mock up real quick.

---

### Post by taurus on 2006-11-27
Just want to see exactly what it looks like...

---

### Post by onesojourner on 2006-11-27
ok here are a couple pics. the only difference from mine - I can see the cursor on the blank tank screen.

this first is what a normal boot would look like, the second is what I get after I log in now.

---

### Post by taurus on 2006-11-27
At the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Log in with your name and password.  Paste the output of this command here (remove names of files/directories you don't want people to see or know!).

```
ls -la
```

---

### Post by onesojourner on 2006-11-27
ok I will, but it will have to wait til I get home tonight.

---

### Post by onesojourner on 2006-11-27
ok I ran that command, what am I looking for? its over a page long and I am not sure how to scroll up. you want me to just start typing all of it?

---

### Post by taurus on 2006-11-27
Are you doing that from a terminal (as from a window manager) or a console?  If it's from a terminal, you can use the left button to cut and the middle to paste (or press both left & right at the same time).  But if you only have a console, then you can save the output to a file by

```
ls -la > file
```
Just want to see the permissions of your own $HOME directory...

---

### Post by acascianelli on 2006-11-27
I've also got this problem.  I'm using a Radeon 9800Pro.  I had everything working fine, X + Beryl, then I tried to install something thru synaptic for my video card and it killed X.  I can't remember what it was, something for my video card that required a Qt lib.

---

### Post by onesojourner on 2006-11-27
I am in a console, not windowed. how would I go about saving the file to a flash drive? saving it to the home directory won't get me any where that I could use the information.

---

### Post by scrooge_74 on 2006-11-27
A few days ago i got stuck after loging in, it would hang after log screen, but I happend because i messed up the config files of my user, I manage to fix things going in as another user or in safe mode then made changes to the config files of my gnome session and after that   all problems went away.

Check the file .xsession-errors

I found the solution in another thread around here

---

### Post by onesojourner on 2006-11-28
ok thanks. the only other user I have is root so I will try logging in that way and see what happens. where is the file .xsession-errors going to be at?

---

### Post by taurus on 2006-11-28
```
more ~/.xsession-errors
```

---

### Post by onesojourner on 2006-11-28
ok I finally have the output of ls -la

total 196
drwxr-xr-x 19 root root  4096 2006-11-28 19:06 .
drwxr-xr-x 21 root root  4096 2006-11-15 00:33 ..
drwx------  2 root root  4096 2006-11-26 17:48 .aptitude
-rw-------  1 root root   183 2006-11-02 10:52 .bash_history
-rw-r--r--  1 root root  2227 2006-06-30 09:03 .bashrc
drwx------  3 root root  4096 2006-11-04 16:39 .beagle
drwxr-xr-x  2 root root  4096 2006-11-04 16:39 Desktop
-rw-------  1 root root    26 2006-11-04 16:39 .dmrc
-rw-------  1 root root    16 2006-10-27 16:53 .esd_auth
-rw-r--r--  1 root root 73356 2006-11-22 10:28 .fonts.cache-1
drwx------  4 root root  4096 2006-11-28 16:28 .gconf
drwx------  2 root root  4096 2006-11-28 16:28 .gconfd
drwxr-xr-x  3 root root  4096 2006-11-04 16:39 .gnome
drwx------  7 root root  4096 2006-11-04 16:40 .gnome2
drwx------  2 root root  4096 2006-10-27 08:55 .gnome2_private
drwx------  2 root root  4096 2006-10-27 16:32 .gnupg
drwxr-xr-x  2 root root  4096 2006-11-04 16:39 .gstreamer-0.10
-rw-r--r--  1 root root    81 2006-11-04 16:39 .gtkrc-1.2-gnome2
-rw-------  1 root root   173 2006-11-04 16:39 .ICEauthority
drwx------  3 root root  4096 2006-11-04 16:39 .metacity
drwxr-xr-x  3 root root  4096 2006-11-04 16:39 .nautilus
-rw-r--r--  1 root root     0 2006-11-28 19:06 output
-rw-r--r--  1 root root   141 2006-06-30 09:03 .profile
-rw-r--r--  1 root root  5238 2006-11-21 22:43 .recently-used.xbel
drwx------  3 root root  4096 2006-11-22 10:27 .synaptic
drwx------  3 root root  4096 2006-11-04 16:40 .thumbnails
drwx------  2 root root  4096 2006-11-04 16:39 .Trash
drwxr-xr-x  2 root root  4096 2006-11-04 16:40 .wapi
-rw-------  1 root root   250 2006-11-28 16:28 .Xauthority
drwxr-xr-x  2 root root  4096 2006-11-04 16:40 .xine
-rw-r--r--  1 root root   318 2006-11-28 16:28 .xsession-errors

---

### Post by onesojourner on 2006-11-28
how do I boot into safe mode?

---

### Post by onesojourner on 2006-11-29
here is the output of more ~/.xsession-errors

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "root"
/etc/gdm/Xsession: Beginning session setup...
stdin: is not a tty
[: 12: closing paren expected

---

### Post by taurus on 2006-11-29
> **onesojourner said:**
> ok I finally have the output of ls -la

total 196
drwxr-xr-x 19 root root  4096 2006-11-28 19:06 .
drwxr-xr-x 21 root root  4096 2006-11-15 00:33 ..
drwx------  2 root root  4096 2006-11-26 17:48 .aptitude
-rw-------  1 root root   183 2006-11-02 10:52 .bash_history
-rw-r--r--  1 root root  2227 2006-06-30 09:03 .bashrc
drwx------  3 root root  4096 2006-11-04 16:39 .beagle
drwxr-xr-x  2 root root  4096 2006-11-04 16:39 Desktop
-rw-------  1 root root    26 2006-11-04 16:39 .dmrc
-rw-------  1 root root    16 2006-10-27 16:53 .esd_auth
-rw-r--r--  1 root root 73356 2006-11-22 10:28 .fonts.cache-1
drwx------  4 root root  4096 2006-11-28 16:28 .gconf
drwx------  2 root root  4096 2006-11-28 16:28 .gconfd
drwxr-xr-x  3 root root  4096 2006-11-04 16:39 .gnome
drwx------  7 root root  4096 2006-11-04 16:40 .gnome2
drwx------  2 root root  4096 2006-10-27 08:55 .gnome2_private
drwx------  2 root root  4096 2006-10-27 16:32 .gnupg
drwxr-xr-x  2 root root  4096 2006-11-04 16:39 .gstreamer-0.10
-rw-r--r--  1 root root    81 2006-11-04 16:39 .gtkrc-1.2-gnome2
-rw-------  1 root root   173 2006-11-04 16:39 .ICEauthority
drwx------  3 root root  4096 2006-11-04 16:39 .metacity
drwxr-xr-x  3 root root  4096 2006-11-04 16:39 .nautilus
-rw-r--r--  1 root root     0 2006-11-28 19:06 output
-rw-r--r--  1 root root   141 2006-06-30 09:03 .profile
-rw-r--r--  1 root root  5238 2006-11-21 22:43 .recently-used.xbel
drwx------  3 root root  4096 2006-11-22 10:27 .synaptic
drwx------  3 root root  4096 2006-11-04 16:40 .thumbnails
drwx------  2 root root  4096 2006-11-04 16:39 .Trash
drwxr-xr-x  2 root root  4096 2006-11-04 16:40 .wapi
-rw-------  1 root root   250 2006-11-28 16:28 .Xauthority
drwxr-xr-x  2 root root  4096 2006-11-04 16:40 .xine
-rw-r--r--  1 root root   318 2006-11-28 16:28 .xsession-errors

But that's the output of the root account, not your own account!  You need to look at hteh .xsession-errors in your account to see while Gnome wouldn't come up!!!

```
more /home/onesojourner/.xsession-errors
-or-
ls -la /home/onesojourner
(assuming onesojourner is your log in name...)
```

---

### Post by acascianelli on 2006-11-30
I just remembered what packages I installed to screw up my X.

fglrx-control
libqt3-mt (Dependancy)

X stopped working as soon as I installed these.  I tried to uninstall them from a console but it still doesn't work.  I tried reconfiguring xorg and gdm but still nothing.

I have a Radeon 9800Pro and I was using the ati driver, everything was running great.  I was trying to switch to the fglrx driver to see if I could get any better performance in Beryl.  Beryl was running great before all this.

---

### Post by onesojourner on 2006-11-30
> **taurus said:**
> But that's the output of the root account, not your own account!  You need to look at hteh .xsession-errors in your account to see while Gnome wouldn't come up!!!

```
more /home/onesojourner/.xsession-errors
-or-
ls -la /home/onesojourner
(assuming onesojourner is your log in name...)
```


the problem is also happening with the root account.

---

### Post by onesojourner on 2006-12-01
bump bump

---

### Post by sarc on 2006-12-02
I had EXACTLY the same problem installing nvidia drivers on my HP Pavilion dv2000 (Edgy). Felt pretty dumb staring at a blank tan color desktop at 3am for 2 days straight.

I tried EVERYTHING I could find on this forum and nothing worked (see my posts as Sarc and the king help by Catkiller).  Including reinstalling X from console. 

Eventually I copied my home directory using Windows XP and a Linux file browser that works in Windows (do a google search).  Then I nuked the whole partition and reinstalled from LiveCD.

After fresh install I downloaded the nvidia-glx  (**NOT** the nvidia-glx-legacy!!!) from Synaptics and then changed the /etc/X11/xorg.conf file from 'nv' to 'nvidia' (see other posts on this subject).  

By the way that fixed a lot of other problems in Edgy: the suspend/hybernate crashes in X stopped, and I was able to boot even if the bluetooth/wireless switch was off (previously Edgy boot would freeze if the switch was off).

---

### Post by acascianelli on 2006-12-02
> **sarc said:**
> I had EXACTLY the same problem installing nvidia drivers on my HP Pavilion dv2000 (Edgy). Felt pretty dumb staring at a blank tan color desktop at 3am for 2 days straight.

I tried EVERYTHING I could find on this forum and nothing worked (see my posts as Sarc and the king help by Catkiller).  Including reinstalling X from console. 

Eventually I copied my home directory using Windows XP and a Linux file browser that works in Windows (do a google search).  Then I nuked the whole partition and reinstalled from LiveCD.

After fresh install I downloaded the nvidia-glx  (**NOT** the nvidia-glx-legacy!!!) from Synaptics and then changed the /etc/X11/xorg.conf file from 'nv' to 'nvidia' (see other posts on this subject).  

By the way that fixed a lot of other problems in Edgy: the suspend/hybernate crashes in X stopped, and I was able to boot even if the bluetooth/wireless switch was off (previously Edgy boot would freeze if the switch was off).

That is not what I want to hear, but I have a feeling thats what I'll be doing...

---

### Post by meshback on 2006-12-04
I was having this same problem, blank tan screen after booting into gnome.  I had switched out an ati card for an nvidia card when it started.  

This worked for me, to delete the config folder in gnome.  boot into gnome, when it gets to the blank tan screen, ctrl-alt-F1 to get to the command line, login there.  Then type:
```
rm -rf ~/.config
```

Hopefully that'll work for you.

---

### Post by juanfran27 on 2008-03-23
I had the same problem... I think. 

[http://ubuntuforums.org/showthread.php?t=733295](http://ubuntuforums.org/showthread.php?t=733295)

This link takes you to my problem. If someone is willing to help me, please do (and perhaps post an answer there).

---

