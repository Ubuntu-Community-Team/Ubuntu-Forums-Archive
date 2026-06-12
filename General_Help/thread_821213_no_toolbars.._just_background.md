---
title: "no toolbars.. just background"
date: 2008-06-07
forum: General Help
---

### Post by badgethefarmer on 2008-06-07
- i am using hardy.
- i restarted and i was directed to my background image/wallpaper without my toolbars. the ones on top and bottom.
- i managed to fire up this browser thru the use of help
- how do i fix
- help is highly apprecited
- thank you

---

### Post by iaculallad on 2008-06-07
Drop to your terminal by pressing Ctrl+Alt+F1, then issue the command:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

and press Ctrl+Alt+F7 to get back to your GUI.

---

### Post by badgethefarmer on 2008-06-07
thank yo for the imediate reply

- when i load up the terminal, i cant type the code
- the last line says something like 'kinit no resume image, doing normal boot

---

### Post by oldsoundguy on 2008-06-07
Not saying this is your issue, but I had the same thing happen and found I had installed the wrong video driver.  Once the correct driver was installed, all was OK.

---

### Post by badgethefarmer on 2008-06-07
oldsoundguy

ok. thanks.
if so, how to install the correct video driver?

---

### Post by iaculallad on 2008-06-07
> **badgethefarmer said:**
> thank yo for the imediate reply

- when i load up the terminal, i cant type the code
- the last line says something like 'kinit no resume image, doing normal boot

What about pressing the "ESC" or "Enter" key? Will it not bring you to a terminal where you can login?

---

### Post by damis648 on 2008-06-07
Let me try this again:
Alt+F2 and type gnome-terminal and run it.
In the terminal, type:
```
gconftool-2 --recursive-unset /apps/panel
```
then
```
gconftool-2 --shutdown
```
then
```
rm -rf ~/.gconf/apps/panel
```
then
```
pkill gnome-panel
```
then
```
sudo dpkg-reconfigure gnome-panel
```
and finally
```
sudo reboot
```
and you should be good to go :)

---

### Post by badgethefarmer on 2008-06-07
What about pressing the "ESC" or "Enter" key? Will it not bring you to a terminal where you can login?

- it worked. i got in to terminal
- i typed your code and pressed enter
- i did 'ctrl atl f7 to go back to gui
- it's still the same
- tried typing in the 'rm -r~/.gconf...' code' but there was an error
- but i did manage to go to terminal.
- i am learning as i troubleshoot this

---

### Post by iaculallad on 2008-06-07
> **badgethefarmer said:**
> What about pressing the "ESC" or "Enter" key? Will it not bring you to a terminal where you can login?

- it worked. i got in to terminal
- i typed your code and pressed enter
- i did 'ctrl atl f7 to go back to gui
- it's still the same
- tried typing in the 'rm -r~/.gconf...' code' but there was an error
- but i did manage to go to terminal.
- i am learning as i troubleshoot this

On your terminal:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/panel
sudo pkill gnome-panel
sudo shutdown -r now

```

It would be much easier if you copy and paste commands on your terminal.

---

### Post by oldsoundguy on 2008-06-07
you have failed to mentioned your video card set up and whether you have standard or restricted drivers.

I have nVidia cards and used the third party program, Envy, to install them.  AFTER I had let Ubuntu install the generic drivers.  Three machines, three cards, all worked using the program.

---

### Post by badgethefarmer on 2008-06-08
i got it restarted, i had the default walpapaer back but still no toolbars, above and bottom.

- is there a way to restart my system ? it's all right because i had my files backed up.
- i dont want to resort to re-installing the OS
- TY for all the help i got.

---

### Post by badgethefarmer on 2008-06-08
> **oldsoundguy said:**
> you have failed to mentioned your video card set up and whether you have standard or restricted drivers.

I have nVidia cards and used the third party program, Envy, to install them.  AFTER I had let Ubuntu install the generic drivers.  Three machines, three cards, all worked using the program.

i do not have any video card. just defaults.
- before this happened, i installed my webcam.
- then i installed this program called "motion"
- in the process of installation things got weird and stuff just did not respond so i decided to hit the restart button thinking it would bring things back to normal.

---

### Post by oldsoundguy on 2008-06-08
try going back into Synaptic Package Manager and unchecking motion (that will uninstall it.)  You may have to re-boot or at least use ctrl/alt/backspace.
If that does not do it, you may have to uninstall the web cam.

As with any operating system, if it works properly and you install something and it no longer works as it should, the obvious culprit is what you just installed.

---

### Post by badgethefarmer on 2008-06-09
- i have installed hardy again
- thinking that it will solve the issue once and for all
- it did
- but the problem happened again. 
- i would like to know the reason why this problem happens
- thanks

---

### Post by bminy1 on 2009-08-24
How can we solve this problem?

---

### Post by burton1064 on 2009-09-18
I have the same problem as this guy, no toolbars - just background.  

I ran all the commands in the terminal and got it to the point where the ubuntu symbol on the tool bar appears (but doesn't respond to clicks) and the battery, internet connection, volume & date appear but nothing else.

I can't access any programs or anything.  I just installed Ubuntu 9.04 Netbook Remix on my Dell Mini 9.  Was working fine for about 2 days until I got a "windows manager unknown" error or something of the like.

I'd highly appreciate any help.

---

### Post by Flyers2391 on 2009-10-05
> **burton1064 said:**
> I have the same problem as this guy, no toolbars - just background.  

I ran all the commands in the terminal and got it to the point where the ubuntu symbol on the tool bar appears (but doesn't respond to clicks) and the battery, internet connection, volume & date appear but nothing else.

I can't access any programs or anything.  I just installed Ubuntu 9.04 Netbook Remix on my Dell Mini 9.  Was working fine for about 2 days until I got a "windows manager unknown" error or something of the like.

I'd highly appreciate any help.

Having this problem as well.  A coworker had XP on this Dell mini 10 and it was unbelievably slow.  I thought it was Windows so I put the remix on and the standard interface would be a few seconds behind clicks, practically unusable.  I switched the desktop mode to standard, which was a little better but that is when the "only background" problem started.  

I just installed so I'm trying again to see if it's better but maybe it is a problem with this mini 10 build (model PP19S) and the standard desktop or video card?

---

### Post by Flyers2391 on 2009-10-05
I was continuing my searching and found this:

[http://ubuntuforums.org/showthread.php?t=1272071&highlight=mini+background](http://ubuntuforums.org/showthread.php?t=1272071&highlight=mini+background) 
which links to 
[https://bugs.launchpad.net/desktop-switcher/+bug/349519](https://bugs.launchpad.net/desktop-switcher/+bug/349519)


I just read through (so others in this tread hopefully won't have to) and it appears from everything (specifically here - [https://bugs.launchpad.net/desktop-switcher/+bug/349519/comments/59](https://bugs.launchpad.net/desktop-switcher/+bug/349519/comments/59)) that you can download [http://launchpadlibrarian.net/26020903/desktop-switcher_0.4.6_i386.deb](http://launchpadlibrarian.net/26020903/desktop-switcher_0.4.6_i386.deb), dkpg it and you should be good ... if that doesn't work, I'd go through the link on launchpad and check out what others have to say there

---

