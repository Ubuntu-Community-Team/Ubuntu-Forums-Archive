---
title: "Wall of text when booting."
date: 2013-03-13
forum: General Help
---

### Post by Silky Jackson on 2013-03-13
This just started a few days ago, but when I boot my computer in place of the purple ubuntu screen I get a scrolling wall of text. It seems to take longer but it eventually goes to the login screen and everything else seems to work fine.

---

### Post by Bashing-om on 2013-03-13
Silky Jackson; Hi !

What pops into my mind is a change had been made to the /etc/default/grub file (???)
Post the output of terminal code:
```
cat /etc/default/grub
```
and we will see what it looks like.[INDENT]try'n to help

[/INDENT]

---

### Post by Silky Jackson on 2013-03-13
OK so this is what I got.

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="vesafb.invalid=1 drm.debug=0xe nopat plymouth:debug"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXPAYLOAD_LINUX="text"


export GRUB_MENU_PICTURE="/home/chris/Pictures/Backgrounds/darkmint.jpg"
export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="light-blue/black"
GRUB_FONT="/boot/grub/unicode.pf2"

---

### Post by schragge on 2013-03-13
> **Silky Jackson said:**
> ```
GRUB_CMDLINE_LINUX_DEFAULT="vesafb.invalid=1 drm.debug=0xe nopat plymouth:debug"
...
GRUB_GFXPAYLOAD_LINUX="text"
```Where did you get these lines from? Have you edited /etc/default/grub manually? Or used [Grub Customizer](https://launchpad.net/grub-customizer)?

---

### Post by oldos2er on 2013-03-13
> **Silky Jackson said:**
> This just started a few days ago, but when I boot my computer in place of the purple ubuntu screen I get a scrolling wall of text. It seems to take longer but it eventually goes to the login screen and everything else seems to work fine.

Which version of Ubuntu are you running?

---

### Post by Silky Jackson on 2013-03-13
I am running 12.10

---

### Post by Silky Jackson on 2013-03-13
> **schragge said:**
> Where did you get these lines from? Have you edited /etc/default/grub manually? Or used [Grub Customizer]("https://launchpad.net/grub-customizer")?

I don't think I did but I downloaded KDE the other day and thats when my problems started. I am still new to Linux and did try to fix things myself by using Google search as much as I could. Everything else seems back to normal except for this wall of text.

---

### Post by Bashing-om on 2013-03-13
Silky Jackson     ;
In accordance with your grub, your system is doing what you have told it to do. If You want to, we can work with you to get you back to a GUI login.
But, not knowing the source of the changes to the grub file or why they were made - it may be a trial and error kind of thing. We can start by seeing if there exist a backup copy of the old grub file.
terminal code:
```
ls -la /etc/default/g*
```[INDENT=3]
try'n to help

[/INDENT]

---

### Post by Silky Jackson on 2013-03-13
> **Bashing-om said:**
> Silky Jackson     ;
In accordance with your grub, your system is doing what you have told it to do. If You want to, we can work with you to get you back to a GUI login.
But, not knowing the source of the changes to the grub file or why they were made - it may be a trial and error kind of thing. We can start by seeing if there exist a backup copy of the old grub file.
terminal code:
```
ls-la /etc/default/g*
```[INDENT=3]
try'n to help

[/INDENT]

  
Trial and error is a good way for me to learn. Terminal came back with command not found.

---

### Post by schragge on 2013-03-13
Okay, let's change you /etc/default/grub a bit. First, make a copy of it:
```
sudo cp /etc/default/grub{,.save}
```
Then try this
```

sudo sed -i '/^GRUB_CMDLINE_LINUX_DEFAULT=/s/=.*/="quiet splash"/;/^GRUB_GFXPAYLOAD/s/=.*/="auto"/' /etc/default/grub

```
Then
```
sudo update-grub
``` and reboot.

---

### Post by schragge on 2013-03-13
> **Silky Jackson said:**
> Trial and error is a good way for me to learn. Terminal came back with command not found.There should be a space between ls and -la ```
ls -la /etc/default/g*
```

---

### Post by Silky Jackson on 2013-03-13
So I noticed the scrolling text while logging off. (short amount of time) I still had the text after reboot but it was pretty quick before it went to the login screen.

I am at work so if I don't respond for a little while its just because I got busy.

---

### Post by Bashing-om on 2013-03-13
Silky Jackson;
Sorry bout the "bad"code. Do not know why that a space is lost in a "coded" command sequence on occasion. Paddy has remarked that it happens. We will have to pay greater attention to our post, huh ! Fixed in that post for others reference.

---

### Post by Silky Jackson on 2013-03-13
> **schragge said:**
> There should be a space between ls and -la ```
ls -la /etc/default/g*
```

-rw-r--r-- 1 root root   58 Dec 13 00:07 /etc/default/google-chrome
-rw-r--r-- 1 root root 1521 Mar 13 03:49 /etc/default/grub
-rw-r--r-- 1 root root 1238 Jan 23 20:39 /etc/default/grub.bak
-rw-r--r-- 1 root root 1265 Mar 12 03:49 /etc/default/grub.bak.0
-rw-r--r-- 1 root root 1281 Mar 12 03:49 /etc/default/grub.bak.1
-rw-r--r-- 1 root root 1281 Mar 12 03:50 /etc/default/grub.bak.2
-rw-r--r-- 1 root root 1521 Mar 13 18:10 /etc/default/grub.save

This came back.

---

### Post by Silky Jackson on 2013-03-13
> **Bashing-om said:**
> Silky Jackson;
Sorry bout the "bad"code. Do not know why that a space is lost in a "coded" command sequence on occasion. Paddy has remarked that it happens. We will have to pay greater attention to our post, huh ! Fixed in that post for others reference.

It happens. When I ran the new code it looks like I did something last night to the grub. Not real sure what it was. I was up late trying to fix it while taking care of our newborn.

---

### Post by Bashing-om on 2013-03-13
Silky Jackson     ; 
A new Born will certainly re direct one's thoughts.
Ok we will want to see what the updated grub looks like now. So again:
```
cat /etc/default/grub
```
to looksee what else requires changing.

---

### Post by Silky Jackson on 2013-03-13
Yeah the days of getting more than a few hours of sleep have gone away. Here is after the update.


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="vesafb.invalid=1 drm.debug=0xe nopat plymouth:debug"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXPAYLOAD_LINUX="text"


export GRUB_MENU_PICTURE="/home/chris/Pictures/Backgrounds/darkmint.jpg"
export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="light-blue/black"
GRUB_FONT="/boot/grub/unicode.pf2"

---

### Post by Bashing-om on 2013-03-13
Silky Jackson;

???? I do not perceive a change in your grub file in respect to schragge's advise from post #10. Am I being dense or has the code not been run ?

then do:
```
sudo update-grub
```
[INDENT=2]
try'n to help

     
[/INDENT]

---

### Post by Silky Jackson on 2013-03-13
after running the update

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="vesafb.invalid=1 drm.debug=0xe nopat plymouth:debug"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXPAYLOAD_LINUX="text"


export GRUB_MENU_PICTURE="/home/chris/Pictures/Backgrounds/darkmint.jpg"
export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="light-blue/black"
GRUB_FONT="/boot/grub/unicode.pf2"

---

### Post by Bashing-om on 2013-03-13
Silky Jackson;
I do not have the skills to question schragge's code. But "sed" = Streamline EDitor, and should have inserted "quiet splash" in the appropriate place as well as "keep". His code is very efficient and as affective as the longer method I employ. At this time - as this situation does not hamper your operating system - I want to await schragge for enlightenment on my part why the code is not performing.
Rest assured in the event that schragge's fingers become broken or other mishaps prevent a timely response, I can laborously guide you through editing that grub file.[INDENT=3]it is all a learning experience

[/INDENT]

---

### Post by Silky Jackson on 2013-03-13
That's fine, it is starting to get hectic at work so I will check the thread later.

---

### Post by Silky Jackson on 2013-03-14
What if I change GRUB_GFXPAYLOAD_LINUX="text" to[COLOR=#000000] [/COLOR]GRUB_GFXPAYLOAD_LINUX="auto".

---

### Post by schragge on 2013-03-14
Yes, by all means. "auto" is even better than "keep" I suggested. I've edited [post=12556355]my post[/post] accordingly. You don't have to run that cryptic sed sequence if you feel more comfortable editing the file manually. Don't forget to change  GRUB_CMDLINE_LINUX_DEFAULT line, too:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` These are Ubuntu defaults. I think we should try them before anything else.

[highlight]Update.[/highlight]
:oops: Oh now I see why that sed line didn't worked. Fixed.

---

### Post by Bashing-om on 2013-03-14
Guys,
Situation is well in hand. I have a doctor's appointment to keep and will not return 'till late in my afternoon (GMT-6). I play catch up.[INDENT=3]
it's all good
[/INDENT]

---

### Post by Silky Jackson on 2013-03-14
That worked guys. Thanks for all the help.

---

