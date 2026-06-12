---
title: "[SOLVED] WARNING: Nautilus may contain strobe effects!"
date: 2008-05-14
forum: General Help
---

### Post by itsjustarumour on 2008-05-14
OK, heres how it happened (Hardy 8.04 32-bit btw)

I wanted to create a link on my Desktop for a web site I visit frequently, so I could just click on an icon and launch the site in Firefox.

Nothing out of the ordinary.  Right mouse click, select "Create Launcher", fill in details, select icon I want to use, hit "OK" - and ***BAM***! :frown:

Nautilus suddenly opens up, almost gets there but fails and closes again... and again... and again - this flashes backwards and forwards about 10 times in about 10 seconds.  Then my machine locks up completely. I reboot, and when my desktop loads, I get the same Nautilus window flashing up and and closing again rapidly several times, and then finally my Desktop appears.  But all my icons and files I had on my Desktop have disappeared!!

So I go to the "Places" menu, select "Home", and I can navigate around in Nautilus fine until I click on the /home/(username)/Desktop folder - and straight away, Nautilus starts flashing on and off several times, and shuts itself down, leaving me staring at a blank Desktop again.

So where are all my files???

Opening a terminal and doing

> cd /home/(username)/Desktop

and then

> ls

tells me that all my files are still there.

Trying to open Nautilus in a terminal won't work though - I just get the Nautilus window flashing on and off about 10 times, and then it closes again - and then I get:

> Segmentation fault

HELP! How do I fix this???  :confused:


EDIT: If I try

> sudo nautilus

I get:

> Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I have no idea what net usershare is, and I've never done anything with Samba, so this message is a complete mystery to me.

If I then try and click on my "Desktop" folder in Nautilus, I just get:

> Segmentation fault

Anyone got any ideas?  :rolleyes:

itsjustarumour

---

### Post by itsjustarumour on 2008-05-14
Bump - anyone? :rolleyes:

---

### Post by chrisccoulson on 2008-05-14
The message from nautilus-share is nothing to worry about - you probably don't have Samba installed.

As for your Nautilus problems, can you try with a fresh profile? Try creating a new user first. If that works, then try removing your own Nautilus profile:
```
mv .nautilus .nautilus_old
killall nautilus
```

---

### Post by itsjustarumour on 2008-05-14
> **chrisccoulson said:**
> The message from nautilus-share is nothing to worry about - you probably don't have Samba installed.

As for your Nautilus problems, can you try with a fresh profile? Try creating a new user first. If that works, then try removing your own Nautilus profile:
```
mv .nautilus .nautilus_old
killall nautilus
```

Hi Chris,

OK, well I already had a "guest" account set up so I tried that and everything went fine.  If I browsed using Nautilus to /home/(my username)/Desktop and clicked on that folder, it triggered the freaky Nautilus behaviour...

But this where I misunderstood your instructions, and now I'm in big trouble due to foolishly acting in the "MS Windows" way.  I renamed my home directory (thats what I thought you meant by "Profile") to ianBACKUP, and logged out and in again thinking that a new Home directory would be created.  Oops - except I couldn't log in again because it doesn't work like that, and now I can't log in as either "ian" or "ian BACKUP".  And I can't use the sudo command in the "guest" account as I'm "not in the sudoer's file", and although I can look at all the files in ianBACKUP I can't move them because of course I don't have permissions. Also, I can't rename my home folder from "ianBACKUP" back to "ian".  

Heeeeeeeeeeeeeeeeelllllllllllpppppppppppp!!

EDIT - sorry, reading your instructions again its as plain as daylight now what I SHOULD have done...  ](*,)

---

### Post by chrisccoulson on 2008-05-14
Should be easy to fix. If you have another user on the system who can use sudo, then log in as them and do:
```
sudo mv /home/ianBACKUP /home/ian
```
If you don't, then you can boot to recovery mode. To do this, you need to select the recovery mode option from the GRUB menu. When GRUB loads (just before the Ubuntu splash screen appears), press [ESC]. Then use the arrow keys to select the recovery mode option and press [ENTER]

Once in recovery mode, do:
```
mv /home/ianBACKUP /home/ian
```

---

### Post by itsjustarumour on 2008-05-14
> **chrisccoulson said:**
> Should be easy to fix. If you have another user on the system who can use sudo, then log in as them and do:
```
sudo mv /home/ianBACKUP /home/ian
```
If you don't, then you can boot to recovery mode. To do this, you need to select the recovery mode option from the GRUB menu. When GRUB loads (just before the Ubuntu splash screen appears), press [ESC]. Then use the arrow keys to select the recovery mode option and press [ENTER]

Once in recovery mode, do:
```
mv /home/ianBACKUP /home/ian
```

Hi again Chris,

I've just been diving around in "init 1" giving myself a crash-course in system admin from the command line :lolflag:  

I can't do your first suggestion, I'll just go try the second before I try anything else... deep breath before I dive under the GUI again...

---

### Post by itsjustarumour on 2008-05-14
> **chrisccoulson said:**
> Should be easy to fix. If you have another user on the system who can use sudo, then log in as them and do:
```
sudo mv /home/ianBACKUP /home/ian
```
If you don't, then you can boot to recovery mode. To do this, you need to select the recovery mode option from the GRUB menu. When GRUB loads (just before the Ubuntu splash screen appears), press [ESC]. Then use the arrow keys to select the recovery mode option and press [ENTER]

Once in recovery mode, do:
```
mv /home/ianBACKUP /home/ian
```


OK, worked like a charm and all back up and running now. Its given me a sense of enormous well-being... in my panic I'd completely forgotten about pressing Esc at bootup.  Thanks again!  :-)

Now to go and try that original fix for the "flashing" Nautilus...

---

### Post by itsjustarumour on 2008-05-14
Well, after all that I still have my flashing Nautilus, no desktop icons, and on the majority of boots, no desktop wallpaper...

:rolleyes:

---

### Post by ibuclaw on 2008-05-14
Out of curiosity, have you removed this file that caused it all yet?

The proper way to create a shortcut (for future reference) would be to:
[LIST]
[*]Right-Click on Desktop, select "**Create Launcher**", choose "**Application**" and type in "**firefox [http://ubuntuforums.org](http://ubuntuforums.org)**". Where the site is the place you want to go to.
[/LIST]

As for Nautilus, does this happen for all users, or just you?

Have you considered resetting everything to it's default factory settings? (removing all hidden folders in your home directory, with the slight exception of those that you would **need** to keep, ie: ".evolution", ".mozilla", etc.).

It's a bit extreme, but if you don't mind having to enter all information again (Router Password, Email Accounts, etc). It's a small price to pay.

Regards
Iain

---

### Post by itsjustarumour on 2008-05-15
OK, I fixed it! (Iain - thanks for your post - this happened to only my own account, "guest" account etc all worked fine).

In Nautilus, I created a copy of my "Desktop" folder and called it "DesktopNEW".  I found I was able to open this folder and check its contents, without Nautilus flashing and closing itself down (OK, I know I could have done this at the command line, I just found it easier at this point).

Apart from a couple of desktop shortcuts, the "DesktopNEW" folder contained the following:

"Bumf" - a folder containing 425.9MB of files
"Tunes!" - a small text document
"Work Rota 050508.doc"
"Ubuntu804Issues.doc"
"Ubuntu804Issues.doc.bak~"
"Ubuntu 8.04 Fixes and Tips.doc"
"Ubuntu 8.04 Fixes and Tips.doc.bak~"

The two files ending in ".bak~" were the obviously strange ones - I have no idea why they were there, so I deleted them.  I also renamed "Tunes!" to "Tunes", just in case there was a problem with the exclamation mark, and also moved the "Bumf" folder to /home/(Username) just in case having such a large folder on the Desktop had caused Nautilus to crash (I see no reason why these last two things should cause problems, I was just making sure!)

I then deleted my "Desktop" folder, and renamed "DesktopNEW" to "Desktop".  Et voila, all sorted...

Weird!  :)

---

### Post by niteshifter on 2008-05-15
Hi,

> I wanted to create a link on my Desktop for a web site I visit frequently, so I could just click on an icon and launch the site in Firefox.

A quick, no-typing way to do this is with the site you wish to make a link for open in FF, move the mouse cursor over the icon in the address bar (just to the left of where "http://" is), click and drag it to your desktop or a folder.

The one thing you can't do (I think) is change the icon. But you can "emblemize" it: right click on the icon, click Properties, click the Emblems tab.

---

### Post by TenPlus1 on 2008-05-15
The same thing happened to me after an update and all I did to fix the problem was to pop into Synaptic and re-install nautilus and nautilus-data again...

---

