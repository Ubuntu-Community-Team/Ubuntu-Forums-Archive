---
title: "Data recovery"
date: 2014-03-26
forum: General Help
---

### Post by GSD4ME on 2014-03-26
Dear all

I am in a panic here as I desperately require some detailed knowledge and help to assist me

Last week I copied some files to a USB stick and went to power down my laptop, which 'hung', so I "5-seconded" the power button and shut the machine down.
When I booted it up the next day, there was an error "Could not update .ICEauthority file /home/<my name>/.ICEauthority" and the only thing that I was allowed to do was log off.
I did some research and recreated the file which others have done to cure this problem, done via terminal interface at the log on screen at bootup
However, I still cannot login after doing what the advise told me to do.
I have looked at the files under my account using terminal and there are only about 3/4 files, with *no* Documents/music/pictures/download/etc structures present.
Therefore I seemed to have lost eveything.
90% of my files are backed up on a cloud but I need to retrieve the 10% plus my email settings - address book, emails etc. (For this I am using Thunderbird so should easily be accessible)
The other accounts on the laptop are fine.
Q: Is there a utility that I can use to access the files that are hopefully still on the HDD, just not being able to be seen currently? Something like a disk analysis/retrieval program?
I don't mind how tedious and time-consuming it is - I just want all my files back. The trouble is that my account was the "super user" one on the machine and the others are not.
Or does anyone else have any suggestion or mthods to help retrieve my data
I would rather not install new packages big time as I am unsure whether the lack of 'structure'means that my files would be regarded as being 'free space'on the HDD and therefor be overwritten.
I have tried my local repair shop but they admitted that their knowledge of Ubuntu was minimal, as well of their contacts, and rather than do something that would destroy the data, they quite correctly declined to try. They suggested that I contact a professional data recovery organisation but I simply do not have the money to use them - but it may come to that if nothing else works
Any guidance would be deeply appreciated as I am approaching near panic with this problem.

---

### Post by grahammechanical on 2014-03-26
As an inhabitant of Hampshire, UK you must have heard the expression: "Don't panic Mr Mainwarring." Think before you really mess things up. Please clarify. Does Ubuntu load? Can you log in? Can other users log in? I am not clear about this.

You can try loading a Ubuntu Live session and access your files from there to back up. Perhaps you can copy your home directory/folder. I found this

[http://askubuntu.com/questions/58877/error-saying-unable-to-update-ice-authority-while-booting](http://askubuntu.com/questions/58877/error-saying-unable-to-update-ice-authority-while-booting)

[http://ubuntuforums.org/showthread.php?t=1841457](http://ubuntuforums.org/showthread.php?t=1841457)

[http://askubuntu.com/questions/356284/cannot-login-after-update-ubuntu-12-04-iceauthority-error-message](http://askubuntu.com/questions/356284/cannot-login-after-update-ubuntu-12-04-iceauthority-error-message)

Regards.

---

### Post by Navneet_Kumar on 2014-03-27
Perhaps you can use usb backup tools such as gParted live iso,and some others.....they will help you to rescue your data from your previous BackUps.............:D

---

### Post by GSD4ME on 2014-03-27
A couple of statements:

As per my posting, the machine boots up so Ubuntu sort of works.
It is only my account that is playing up.
I wish to find files that are on my machine that are *not* backed up - most of my data is but some items (eg recent photographs have not been). Hence I want to access them.

Been doing some research.
The .ICEauthority file seems to be a misleading area here.
It seems that the system "recognised" that there was a fault and has 'locked' out my account

See these postings, as it mimics what is happening to me
[http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/](http://goshawknest.wordpress.com/2010/04/16/how-to-recover-crypted-home-directory-in-ubuntu/)
and
[http://www.lainoox.com/recover-encrypted-home-ubuntu/#How_To_Access_Your_Encrypted_Drive_from_a_Live_CD](http://www.lainoox.com/recover-encrypted-home-ubuntu/#How_To_Access_Your_Encrypted_Drive_from_a_Live_CD)
and
[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

So what I need to do is try and carry out the actions specified in these articles.

I therefore seemingly need a 'live' version of Ubuntu 12.04 (the one that I am running) in a CD
Q: How do I do this? IE how do I create this CD?
The Ubuntu version I have is 10.10 on CD, and I upgraded online so I do not have a CD version.
My machine's setup will not let me boot from a USB stick so I don't want to start playing in that area.

The blogs also talk about mounting my home partition - how do I do that? ie what commands do I need to do?
I have the encryptin key so hopefully that will work

Sorry to be such a pain but Linux/Ubuntu does not come naturally to me. I switched from WIndows as everyne said how easy Linux was. It *is* if you want to do something straightforward with files etc but if anything goes wrong, it seems to be as bad as Microsoft's products.

---

### Post by oldfred on 2014-03-27
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

If you are not logging in as you, then you cannot see another user. That is normal. Plus if encrypted it is even more difficult to mount and see data. 

 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)
chroot & reinstall grub encrypted LVM
[http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/](http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/)

      
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Do not force shutdown. best to remember the Elephants
       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by dragonfly41 on 2014-03-27
Taking one step at a time .. what do you see in command terminal when you run this command  ..

[COLOR=#696969]**ls -al .ICEauthority**[/COLOR]

---

### Post by GSD4ME on 2014-03-28
(dragonfly41) - Have got past that part I think and I believe so am progressing beyond that. Hope you can help me here though as I progress this, as you said, one step at a a time.

I am looking at being able to 'unlock/unblock' my user account and retrieve the data that the system has (sort of) hidden. It seems that I need to enter the encryption code applicable to my account (which I have).

As per the other stated posts above, I have now got a bootable 12.04 image that will boot up from my CD drive.
With it I get the options of "try Ubuntu" and "install ubuntu". I take it I want to do the first rather than the second - or even neither?

According to the blogs above, I want to somehow mount my home drive (the locked one on my laptop) by doing ... what?
OR - according to another of the blogs, I want to create another account with the same name as my old one without creating a "home" directory by using one of the options (--make-nohome or something- aplogies, done from memory at the moment)

Basically, having got my bootable CD, what is the next step?
Please provide an idiot's guide in simple, single steps as I am a bear of little brain (copyright Winnie The Pooh) and don't wish to screw this up! (I will also store it in a file for later use if this ever happens again)

---

### Post by GSD4ME on 2014-03-28
(dragonfly41) - Have got past that part I think and I believe so am progressing beyond that. There only seems to be two files in my home directory and they seem to point to telling me that things have been locked away for safe keeping. A propos the .ICEauthority file, I have tried recreating it and changing the permissions on it but nothing seems to help there.
 
Hope you can help me here though as I progress this, as you said, one step at a a time.

I am looking at being able to 'unlock/unblock' my user account and retrieve the data that the system has (sort of) hidden. It seems that I need to enter the encryption code applicable to my account (which I have).

As per the other stated posts above, I have now got a bootable 12.04 image that will boot up from my CD drive.
With it I get the options of "try Ubuntu" and "install ubuntu". I take it I want to do the first rather than the second - or even neither?

According to the blogs above, I want to somehow mount my home drive (the locked one on my laptop) by doing ... what?
OR - according to another of the blogs, I want to create another account with the same name as my old one without creating a "home" directory by using one of the options (--make-nohome or something- aplogies, done from memory at the moment)

Basically, having got my bootable CD, what is the next step?
Please provide an idiot's guide in simple, single steps as I am a bear of little brain (copyright Winnie The Pooh) and don't wish to screw this up! (I will also store it in a file for later use if this ever happens again)

---

### Post by GSD4ME on 2014-03-28
(dragonfly41 - as per your request)
The files shown on an "ls -al" are:
.cache
.ecryptfs -> /home/.ecryptfs/adb/.ecryptfs
.ICEauthority
.Private -> /home/.ecryptfs/adb/.Private
README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
Access-Your-Private-Data.desktop

I *have* tried deleting the .ICEauthority file and recreating it and changing the permissions but nothing seems to work

interestingly, when I am doing nothing in the "terminal" login area, two messages keep coming up:
<stuff, stuff>[sdb]Asking for caxhe data failed
<stuff, stuff>[sdb]Assuming drive cache:write through

---

### Post by dragonfly41 on 2014-03-28
**Step 2** .. now .. can you do this .. as in this thread posted by OldFred

[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

run command in terminal ...

```
sudo chown username:username /home/username/.ICEauthority 
```

substituting "username" (three patterns above) with your actual account **username**

You say you have tried "changing permissions" but the above is to change ownership of your user home directory

e.g. /home/gsd4me/  .. or whatever is your user account path where .ICEauthority is located.

This may be repeating what you've already tried .. but we need to explore one step at a time.

---

### Post by Navneet_Kumar on 2014-03-28
And notify what you see as output in each step so that we can assist further..........

---

### Post by GSD4ME on 2014-03-29
dragonfly41 Logged in as me via terminal. did sudo chown -R : /home//.*  machine did things - i got a coupleof refusals for a couple of files down in my file structure. Tried to log in-still get: "Could not update ICEauthority file /home//.ICEauthority"  Interestingly - one of the "refusals" to change the permissions was a file in a directory that was "down" in my file structure. So the system is somehow recognising the file structure, and being able to access it, but I as the user cannot.  Some small progress?

---

### Post by steeldriver on 2014-03-29
I've been following this thread but I'm finding it very hard to understand what state your system is in, and what you've done so far to try to recover it. In particular:
 
[LIST]
[*]is your home directory encrypted, and if so did you perform a manual ecryptfs recovery to unlock it? 
[*]did you actually fire up the live CD ("Try Ubuntu") and mount the hard drive, or did you back out and reboot into the text login? 
[/LIST]
If there is **any** suspicion that your hard drive is failing (the "cache write through" error messages are concerning) then the sooner you get the data off the better - and you want to minimize the number of reboots and general poking about in the meantime

---

### Post by dragonfly41 on 2014-03-29
Before you follow the "try Ubuntu" option (certainly** do not** use the "install Ubuntu" option since this might cause loss of your data) perhaps you can try just one more "poking around" ..

cd /home/yourname/

sudo chown yourname:yourname .ICEauthority 


Can you try this ...

sudo nautilus

If Nautilus launches .. navigate to FileSystem > home > yourname folder

View (in Nautilus menubar) "Show Hidden Files" and "List" files

look for .ICEauthority and right click on this

Look at "Permissions" tab


Owner should be "yourname" with access "read & write"
Group should be "yourname" with access "none"
(these are my default permissions in .ICEauthority)

If that hits a dead end then try the Live CD route (**Try Ubuntu**) to inspect your current Ubuntu installation
and look for your important data.

p.s. have a USB flash drive at hand so that you can copy your found data.

---

### Post by GSD4ME on 2014-03-29
Dragonfly41

Did all the things you sgguested - nautilus would not boot up.Gave error: "Could not parse argument: Cannot open display"

Did an "ls"on the files - I do have the correct permissions "r+w", with group = "none"

Steeldriver:

Booted up the live CD but chickened out of doing anything beyond that at the moment as I wasn't completely sure as to what I should be doing.
CAnnot honestly remember if I have run the "Access-Your-Private-Data.desktop" file or not.
(Is it simply a metter of typing that file name at the prompt? with nothing else in the command line?)
I shall try that next and see what happens - I have the encryption key to hand!

Found this on the web as well:
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

I'm not 100% sure that this applies to 12.04 LTS (My version) but am open to correction
Also - Nautilus will not start upon my machine remember

---

### Post by dragonfly41 on 2014-03-29
So you got this when trying to launch Nautilus ..

[http://askubuntu.com/questions/156998/how-do-i-start-nautilus-as-root](http://askubuntu.com/questions/156998/how-do-i-start-nautilus-as-root)

Try again booting into recovery mode as explained here ..

[http://askubuntu.com/questions/356284/cannot-login-after-update-ubuntu-12-04-iceauthority-error-message](http://askubuntu.com/questions/356284/cannot-login-after-update-ubuntu-12-04-iceauthority-error-message)

...

If that does not help ...

Provided that you only use "Try Ubuntu" you need not be too concerned since Ubuntu is not running in your PC but is running in your CD.

If you can run your Live CD you should be able to inspect your files in your resident Ubuntu on your hard drive and we can point you to how to copy your non backed up files into say a USB flash drive.

...

To answer your question on desktop file ..

From your post #9 this appears to be in /home/yourname/Access-Your-Private-Data.desktop

So in terminal you can try ...

sudo [COLOR=red]xdg-open[/COLOR] /home/yourusername/Access-Your-Private-Data.desktop  ...  [[COLOR=red]incorrect command later corrected to add "xdg-open" - see post #14 below[/COLOR]]

...

[COLOR=maroon][later edit]

the link you posted

[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

 explains how to use Live CD to recover

> Next, fire up a terminal and run the following command to search your mounted file systems for encrypted private directories[INDENT]sudo ecryptfs-recover-private

[/INDENT]
[/COLOR]

---

### Post by GSD4ME on 2014-03-30
Looks like progress here...

Tried (as typed here)
Sudo /home/<me>/Access-Your-Private-Data.desktop
gave:
sudo: Access-Your-Private-Data.desktop: "command Not Found"

OK - can live with that for the time being

did
sudo ecryptfs-recover-private

gave:
Searching for encrypted Private directories (this mighttake a while)

Came back with my directory as found (!!!)
I entered the passphrase

It seemed todo something and then said that the 'data' was in a folder:
/tmp/ecryptfs.<some numbers>

Now stuck again.
Permissions on this directory (?) are
drwx------

Chmod says that:
chmod changing permissions of file : read only file system

How do I progress now?

Things seem to be getting closer to a solution

I have tried this a couple of times now and get the /tmp/ecryptfs.<some numbers> directory(?) created each time. When I log out, this disappears - because it is in th e/tmp directory? 
So the question is: how do I access what is in that directory? Is it my files? 
Also gksu Nautilus still does not work from the command line saying cannot open display so that doesn't help me here!

---

### Post by westie457 on 2014-03-30
Most of what is happening in this thread is so far over my head I am in fear of drowning.

However it might be a good idea to copy > [COLOR=#000000]It seemed todo something and then said that the 'data' was in a folder:[/COLOR]
[COLOR=#ff0000]/tmp/ecryptfs.<some numbers>[/COLOR] to a USB drive so it can be worked on.

---

### Post by dragonfly41 on 2014-03-30
Sorry .. I misinformed you .. with incorrect command syntax to run your .desktop file

[http://askubuntu.com/questions/5172/running-a-desktop-file-in-the-terminal](http://askubuntu.com/questions/5172/running-a-desktop-file-in-the-terminal)

Try some of the options in above thread .. (I believe you have ubuntu 12.04 installed so some options may not apply such as gtk-launch which is not found in my ubuntu 12.04)

```
sudo xdg-open /home/<me>/Access-Your-Private-Data.desktop
```

You have not yet tried the ubuntu recovery route (at initial logon) or Live CD route (Try Ubuntu)?

[COLOR=maroon][later edit]

I find that in my ubuntu 12.04 when I try xdg-open to run a desktop file I get this message ...

error
Failed to add a plugin to the panel
No running instance of xfce4-panel was found

...

However you should be able to read contents of your desktop file by ...
```
sudo gedit /home/<me>/Access-Your-Private-Data.desktop
```



**Note: **your desktop file [COLOR=maroon]Access-Your-Private-Data.desktop should have **executable** permissions and you may have inadvertently changed this permission when dabbling with permissions in your /home/<me>/ directory.[/COLOR][/COLOR]

In general **do not** blanket change permissions on folders such as /home/<me>/ .. but **only** on selected individual files.

---

### Post by GSD4ME on 2014-04-02
Have tried the Live CD" recovery route - managed to extract something into the /tmp directory but the files extracted are seemingly still encrypted - they are all called ECRYPTS-something with -FNEK in all the file names as well, which seemingly is yet another area to be explored if FNEK searches in the technical forums are true.

Anyone got any further ideas? I will try it again to see what everything comes up with

---

### Post by dragonfly41 on 2014-04-02
So finally you got around to running Live CD.

I have had no need to encrypt my local data so I don't write from personal experience.

But see links below explaining how to decrypt.

In your Live CD you will need to install ecryptfs-utils

```
sudo apt-get install ecryptfs-utils
```

Then you should be able to decrypt your already recovered data using your private keys you have.


[http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)


[color=maroon][later edit]

If you look back in this thread to read OldFred's contribution in post #5 you will see this link which is relevant ...

[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

[/color]

---

