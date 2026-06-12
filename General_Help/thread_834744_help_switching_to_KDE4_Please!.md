---
title: "help switching to KDE4 Please!"
date: 2008-06-19
forum: General Help
---

### Post by Redrazor39 on 2008-06-19
Ok. I wanted KDE4 since it looked so much cooler than the older version so I enabled all the repos and then installed kubuntu-kde4-desktop. I then clicked on "Full Upgrade" and installed all of that stuff, too. However, when I log in, the login screen looks nice and new, but everything else is the same.

I'm very new to kubuntu, but I have used ubuntu a bit. Please help.

[B]*EDIT* I forgot, when I look in the K menu, I have two versions for almost all of the applications, except one says "(KDE4)" by it. How can I make it so the older ones don't show up/aren't there?

*EDIT 2* Also, the GRUB menu now shows Ubuntu 8.04 and Ubuntu 8.04 recovery for two kernels. Is there a way to get rid of the old kernel version and keep the new one?[/B]

---

### Post by cacycleworks on 2008-06-19
Hi! 

KDE4 is quite attractive. I haven't made the switch yet, but will once it's stable.

> **Redrazor39 said:**
> Ok. I wanted KDE4 since it looked so much cooler than the older version so I enabled all the repos and then installed kubuntu-kde4-desktop. I then clicked on "Full Upgrade" and installed all of that stuff, too. However, when I log in, the login screen looks nice and new, but everything else is the same.

I'm very new to kubuntu, but I have used ubuntu a bit. Please help.

***EDIT* I forgot, when I look in the K menu, I have two versions for almost all of the applications, except one says "(KDE4)" by it. How can I make it so the older ones don't show up/aren't there?**

If I were to try it, I'd create another user on the computer, and give it full admin access. 

Now, backup your ~/.kde folder and burn it to a CD. If you can, actually, back up all of your ~/.* hidden folders... you can copy these to the new user account and the settings will transfer over.

For experimenting, I like to use sudo aptitude from the terminal rather than synaptic. (Synaptic is better at searching, though) And then install the kde4 metapackage. Then check to ensure that the other ones are also installed... kde4-amusements, etc.

I recall that 3.x and 4 can reside side by side, but a lot of the developers and early adopters were suggesting a separate user account. I recall the rc directory is .kde4. Make sure that you save this folder frequently. When I was mucking about with kde4, much of the GUI wasn't sorted out and hand tweaking of the rc files was needed. Sometimes, entirely deleting .kde4 was required for the kde4 xsession to work.

> **Redrazor39 said:**
> ***EDIT 2* Also, the GRUB menu now shows Ubuntu 8.04 and Ubuntu 8.04 recovery for two kernels. Is there a way to get rid of the old kernel version and keep the new one?**

You back up /boot/grub/menu.lst then edit it as superuser to change the default options. Then run update-grub and grub will rewrite the menu.lst file.

:) Chris

---

### Post by Redrazor39 on 2008-06-19
Thanks for replying.

I think I'm gonna clean install Kubuntu again because I really mucked it up.

Wait, you said KDE wasn't stable... is it? I'm going back to Ubuntu if it's not! I don't want a dead computer-- it took me two days to recover Windows and reinstall linux (tried KDE instead of GNOME this time though) and it was SO BORING. I had to babysit it the whole time, too!

How stable is it, really?


Also, I see in your sig that it has tripled your productivity. How exactly has it done that?

---

### Post by cacycleworks on 2008-06-19
> **Redrazor39 said:**
> Thanks for replying.

I think I'm gonna clean install Kubuntu again because I really mucked it up.

Wait, you said KDE wasn't stable... is it? I'm going back to Ubuntu if it's not! I don't want a dead computer-- it took me two days to recover Windows and reinstall linux (tried KDE instead of GNOME this time though) and it was SO BORING. I had to babysit it the whole time, too!

How stable is it, really?


Also, I see in your sig that it has tripled your productivity. How exactly has it done that?

No, that's kde4. 4 is definitely interesting. I think you'd be fine to install kubuntu, then apt-get install kde4, create another user account, and use that other account for testing.

3.x is totally awesome. I use it as my desktop at work and always have 3 different firefox profiles open (different cookies for my 3 gmail accounts, etc), a terminal, and will open/close ooo, gimp, qcad, and gwenview as needed. :)

As far as my sig, I found that the ubuntu install CD works better on my finicky Dell notebook. Then I did apt-get to install kubuntu. 

Personally, I never did figure out gnome. And KDE's hotkeys and the ability to put in huge text macros totally eliminate repetitive typing in all my e-mail. 

:) Chris

---

### Post by cacycleworks on 2008-06-20
Oh, by the way, it was the kde4 visual desktop manager that was flakey, not kubuntu or the OS itself.

---

### Post by cacycleworks on 2008-06-20
> **Redrazor39 said:**
> Also, I see in your sig that it has tripled your productivity. How exactly has it done that?


Oh! Sorry, didn't fully read this. 

Specifically, the steps I've taken to increase my productivity are:
- Using ssh and sshfs (fusermount) together to allow "local" editing of files on my live website, where on windows, one normally has a local copy, edits, saves, and ftp's the files. Yes, some editors can use ftp to appear transparent, but my experience in Quanta and the sshfs mounted remote volume, I just ctrl-s and the result is close enough to that if it were a local file.

- I do research development from a server at my office and ssh in to it from my desk or from home. In linux, I created a "move_home" script that swaps in and out /etc/hosts as well as the .ssh/knownhosts files so that the move from home to work is seamless. Basically, it mimics some of the ease of work that VPN creates. And the firewall at the office allows the internet in to said office server on various ports. Since port 80 is so common, I put a virtual host on the IP address that points to a blank page saying "go away" and then another virtual host looks at what I call the hostname on the incoming connection. If I alias "goaway" to the office IP address, the apache server looks for that and points me to my special area. 

- KDE also has integral samba access via konqueror, so accessing my windows shares are as easy as typing smb://winhost/share/directory and I can browse with ease. Here again, I made a script to automate mounting certain win shares as local directories.
So I've got ~/winhost/blah/file.txt to access files on the win share and then ~/officeserver/dir/index.php to access the files on the office dev webserver. Oh, and ~/livesite/dir/index.php for our live site.

- And then the hotkey macros!! Win+k opens konsole, win+w opens kwrite, win/shft+w is open office writer.

I set up win+t to do this....
Before:
```
Bill(cursor is here)
```

perform the keystroke win+t and it becomes:
```
Hi Bill,

Thanks for writing!

(cursor is here)

Thanks,
Chris
```

This alone almost doubled my e-mail productivity!

Watching the occasional thread here on the forums has taught me so much!

:) Chris

---

### Post by cacycleworks on 2008-06-20
here is the text of that thank you macro as typed into the hotkey interface:
```
home:shift+h:i:space:end:,:return:return:shift+t:h:a:n:k:s:space:f:o:r:space:w:r:i:t:i:n:g:shift+1:return:return:return:return:shift+t:h:a:n:k:s:,:return:shift+c:h:r:i:s:return:up:up:up:up
```

And I mapped win+h to launch the hotkey applet... but it took me forever to learn that to get it, I had to run the command ```
kcmshell khotkeys
```

---

### Post by Zorael on 2008-06-20
The KDE 4.1b1 build seems to have a lot of improvements over the older 4.0.x builds available from the official repositories, such as 4.0.5 from hardy-backports. Installation instructions over at [http://kubuntu.org/announcements/kde-4.1beta1.php](http://kubuntu.org/announcements/kde-4.1beta1.php).

Basically:
```
$ sudo su
# echo "deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main" > /etc/apt/sources.list.d/kde4.1b1-ppa.list
# aptitude update
```
At this point, if you already have kubuntu-kde4-desktop installed:
```
# aptitude full-upgrade
```
If not:
```
# aptitude install kubuntu-kde4-desktop
```


If you install Startup Manager (package name **startupmanager**), you'll have a GUI way of making simple and common modifications to your grub menu.lst. What you're describing - getting several kernel entries - can either be solved by removing those kernel images (will spawn endless 'updates available' messages), or limiting the number of kernels displayed in grub.

While at it, it's also technically possible to disable the recovery mode showing up, but not recommended. If done, to boot into recovery mode, you'd have to edit the normal kernel entry by hitting E, then editing the kernel line by hitting E again, and appending **single** to the argument line. If that sounds complex and difficult to understand, *don't do it*.

You can also disable the memtest entry, which is seldom used anyway. If you need to memtest, keep a live cd around.


Relevant menu.lst sections (if not using Startup Manager):
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```
```
## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true
```
```

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true
```
Once you make changes, have grub itself update the menu.lst file to make it apply them to the kernel entries.
```
$ sudo update-grub
```

---

### Post by Redrazor39 on 2008-06-20
Thanks for all the help! What exactly does the memtest option do? Is it that useful or even necessary?

---

### Post by Redrazor39 on 2008-06-20
Also, I'm considering trying kubuntu again because I'm getting a bit sick of GNOME. It's pretty intuitive, but so inefficient. I like intuitive, efficient, and reasonable as well as beautiful. KDE seems to do that; I just need to figure it out :)


If I install kubuntu again and figure out KDE 3.5.9, then would you guys or anyone else help me get through creating a new user account and installing KDE4?

The main problem I had last time was that when I installed kubuntu-kde4-desktop and did a full upgrade, my K menu showed applications for KDE3 as well as a double of those applications for KDE4. It was incredibly annoying and cluttered up my menu beyond reasonable use. Would you or anyone be willing to help me get through this without having that problem?

Is it possible to have KDE4 and completely get rid of KDE3 and the KDE3 versions of all the apps? I have Windows on the other partition so it's not like I depend on Linux for work or anything and I'm basically exploring it now.

Thank you everyone! The ubuntu forums are amazing! People actually help you when you need it :)

---

### Post by Zorael on 2008-06-20
memtest checks your RAM memory, reading and writing to it to make sure that your RAM sticks aren't failing. You can use it if you suspect that they're broken; this can be the cause of sudden and unexplainable hangs and reboots.

Having KDE3 and KDE4 alongside eachother *will* give you several entries of applications in the kmenu. This is not a bug: the applications you're seeing "duplicates" of aren't duplicates, but KDE3 and KDE4 variants of the same program. konsole and konsole-kde4. systemsettings and systemsettings-kde4. dolphin and dolphin-kde4. The only way to avoid it is to manually remove their entries.

I've never done this, but I *think* you can get rid of KDE3 and all its apps by removing one of the KDE3 core libraries. Since other apps depend on them, their packages will become "broken" and uninstalled automatically. KDE4 is made to be independent of KDE3, so this just might work. If it does pull KDE4 down along with it, it's no trouble reinstalling KDE4 from - say - a recovery session. Actually, I recommend doing it from there.

```
$ sudo aptitude remove kubuntu-desktop kde-core
```
And, if necessary:
```
$ sudo aptitude install kubuntu-kde4-desktop
```
This will remove KDE3, leaving you with only KDE4.

---

### Post by Redrazor39 on 2008-06-20
Are you sure I should do it in that order? I mean, wouldn't that kill my kubuntu before I get the chance to install kde4?

---

### Post by Zorael on 2008-06-20
Do it from a recovery session, or at the very least outside of any graphical interface. Such as by logging out, doing Ctrl+Alt+F1, logging in, then 'sudo /etc/init.d/kdm stop'. If it puts you at the usplash screen, just hit Ctrl+Alt+F1 again. Then enter those commands.

It's much easier to just boot up into a recovery session.

---

### Post by Redrazor39 on 2008-06-20
Ok, so what you're saying is install kubuntu from the live cd, then from GRUB do Ubuntu 8.04 recovery, then enter the commands:

Code:
$ sudo aptitude remove kubuntu-desktop kde-core
And, if necessary:
 
Code:
$ sudo aptitude install kubuntu-kde4-desktop

Right?

I just want to be 100% sure because I've screwed up my computer from missing one step and reinstalling is NOT FUN

---

### Post by Zorael on 2008-06-20
Yep, go ahead.

Even if the first command doesn't remove KDE4, entering the second when it's already installed won't mess up anything.

Remember that if you want to try the 4.1b1 build, you have to do those steps I posted earlier.

---

### Post by Redrazor39 on 2008-06-20
Ok I'm going to do that. Then, when I boot into kubuntu, should I do a full upgrade from adept or should I only do fetch updates? Should I do both (full upgrade first then fetch updates)?

Will I even be able to update after I do this?

---

### Post by Zorael on 2008-06-20
You shouldn't need to do any upgrades if you don't wish, but you might as well. Upgrading upgrades packages you have installed, so you will naturally be able to continue to do so even without using KDE3.

---

### Post by Redrazor39 on 2008-06-20
aw man, I did all that and when I get to the login screen only KDE shows up, so I log in with that and it's still KDE3 :(

That's disappointing, considering I did all that with the root terminal...

Wait, maybe I need to enable the backport repos in order to install kde4 properly... I'll try again, or maybe you or someone could reply explaining this?

---

### Post by Redrazor39 on 2008-06-20
Nope, didn't work.

Do you think it would work if I installed kde4 and removed kde-core straight from adept when logged in normally? Wouldn't it do that once I reboot?

---

### Post by Redrazor39 on 2008-06-20
Hey I just found that at this site [http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04/release/](http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04/release/)

there's a kde4 version of kubuntu. I have all my ubuntus on CD-RWs. Would it work if I blanked one of them in k3b and burned the .iso on that?

---

### Post by Zorael on 2008-06-20
Oh, kde-core won't do, I see. Sec.

edit: Try this instead.
```
$ sudo aptitude remove kdebase-bin-kde3 kubuntu-desktop kubuntu-kde4-desktop+
```
Don't forget the + at the end of kubuntu-kde4-desktop. That command will remove the first two packages and install that one.

---

### Post by Zorael on 2008-06-20
> **Redrazor39 said:**
> Hey I just found that at this site [http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04/release/](http://cdimage.ubuntu.com/kubuntu-kde4/releases/8.04/release/)

there's a kde4 version of kubuntu. I have all my ubuntus on CD-RWs. Would it work if I blanked one of them in k3b and burned the .iso on that?
Sure. You'd get the one on the official repos (4.0.5), but then you could just add the other one and upgrade to get 4.1b1. You'd be doing a complete reinstallation, though, so it's completely up to you to decide whether that's a good or a bad thing.

---

### Post by Redrazor39 on 2008-06-20
I did that and it totally **bleep**ed up my Kubuntu installation. Now I have to fixmbr and reinstall kubuntu...

ok, new plan. I'm just gonna install the kde-4 version, but would it work if I blanked a CD-RW and burned the .iso to that? If I did a check of the CD integrity, then what do I do if it finds errors?

---

### Post by Zorael on 2008-06-20
:> I'm not sure what you mean with it being bleeped up; it should still leave the important bits, like the kernel and boot procedure tidbits.

Well, sure, burn your cdrw from the .iso image, that ways it's guaranteed to work.

---

### Post by Redrazor39 on 2008-06-20
Ok, thanks. I meant that from Vista can see, it killed that partition and made it "unallocated". Also, when I try to boot from GRUB, the login screen doesn't come up and all I get is a command line to log in. It's like the whole GUI died.

downloading the kde4 version via bittorrent as I type-- 90.5% there.

I hope I don't get a bad burn from a blanked CD-RW.

---

### Post by cacycleworks on 2008-06-20
+1 ... if you don't want kde 3x and only the 4.1, then here's what I would do if my machine...

I would use the ubuntu 8.04 ALT cd appropriate for my architecture (i386 or x86_64) and install ubuntu. This should get the most possible hardware recognition on your installation.

I always format the drives so there is a separate space for /boot, /, and /home. (obviously, there's also a swap partition)

Here's my usual layout:
primary partition: /dev/sda1   197.41 on /boot type ext3 (bootable)
primary partition: /dev/sda3  9829.21 on / type ext3
primary partition: /dev/sda2 86003.53 on /home type ext3
primary partition: /dev/sda4  3997.49 swap

And here's how I have been formatting my work computer's drive:
primary partition: /dev/sda1 on /boot type ext3 (bootable) 200M
primary partition: /dev/sda2 on / type ext3  15GB for root
primary partition: /dev/sda3 on /usr type ext3 14.8 GB for /usr
Extended partition: /dev/sda4 (which doesn't show up)
Logical Drive in extended partition: /dev/sda5 on /tmp type ext3  8GB
Logical Drive in extended partition: /dev/sda6 on /home type ext3  80GB  (never ever format this!)
Logical Drive in extended partition: /dev/sda7 is swap 2GB


Note that if you leave /home there and never format it, a reinstall can be quite the painless and fast process.


THEN do the apt-get steps as pointed out above to get KDE 4.1, totally bypassing KDE3.


(I think this isn't needed, but I'll answer the question)
If you want make another user, Ubuntu has a user management tool in the menu. KDE3 has Kmenu -> system settings -> User Management Just be sure to tick the boxes indicating your new user is admin. That way you have sudo privilege on both.

Also, remember that you can edit the k-menu ... though I'm not sure if that's a user level setting or admin setting affecting all user accounts. The unix/linux part of my brain wants to think that it's user level.

I really like seeing people so interested in and passionate about kde. 

:) Chris

---

### Post by cacycleworks on 2008-06-20
> **Zorael said:**
> 
If you install Startup Manager (package name **startupmanager**), you'll have a GUI way of making simple and common modifications to your grub menu.lst.

THANKS!! I'll make notes about this in my "install recipe" document. I always mess around with grub to remove "quiet" and splash and all that... I like to see the info scroll by as well as the fsck when it runs. :)

*Oh-- eta: use the command sudo apt-get install startupmanager to install. There isn't a space in the package name. *

Thanks also for the kde4 info. That's the best install info I have seen yet about how to get KDE4! It will likely be in the repos by the time I'm ready to experiment with it again.

:) Chris

---

### Post by Zorael on 2008-06-20
> **Redrazor39 said:**
> Ok, thanks. I meant that from Vista can see, it killed that partition and made it "unallocated". Also, when I try to boot from GRUB, the login screen doesn't come up and all I get is a command line to log in. It's like the whole GUI died.
Well, yes. From that command line, do the second command to install KDE4 again.
```
$ sudo aptitude install kubuntu-kde4-desktop
```
May as well do this for good measure, too:
```
$ sudo dpkg-reconfigure kdm-kde4
```

---

### Post by Redrazor39 on 2008-06-20
Wow, thanks for the help! You guys are so amazingly helpful! It looks like KDE users are friendlier to new users than GNOME users (lol).

Well, I found the download on kubuntu.org for a kubuntu-kde4-8.04 iso image. I went to the store just now and bought some CD-Rs (I've been using CD-RWs and keep getting bad burns when I blank them) so now I bittorrented that iso and I'm burning it as we speak. I'm going to keep this thread in mind and bookmark it somewhere for reference to some of these commands and also to know your usernames :)

If I have any more problems with kubuntu, you guys wouldn't mind answering if you see any of my threads about it or the occasional PM, right?

---

