---
title: "New user.  New to Linux.  Horribly painful experience so far."
date: 2007-03-01
forum: General Help
---

### Post by MrDetermination on 2007-03-01
Hi.  I **really** like the concept and the feeling and the excitement!  Wow!  Very appealing to the idealogical side of me.  Really, I appreciate the work and initiative and to put it bluntly, this community this community doesn't owe me anything.  I just don't like the over-optimism/false advertising I read and hear on some podcasts & in the press.

Practically speaking, this is ridiculous.  I'm a power Windows user (don't write code but I end up fixing everyone else's machines and I've build my computers for years).  I've been in ubuntu for several days now and idled/participated in the chat rooms, posted on various forums,  scoured google, listened to a dozen podcast episodes.  I keep hearing how ready this is for prime time, but it ain't.

I've had to boot to live CDs to restore xorg files and create a shortcut to the terminal window I've been using it so much.  That's cool, if troubleshooting is your thing, but don't tell me anything that requires you to have a shortcut to the command line is everyday user ready.

Here are some basic things I can not get done.  Things that I can do in 60 seconds or less in Windows, except maybe the last one.  I have, at least, 10 hours invested in trying to accomplish the following with no success.   At least three of those hours are working with folks at irc.arstechnica.com #linux and on the ubuntu irc servers.
[B]
#1 Bind the side buttons my my Logitech mouse to Ctrl and Shift[/B]

Well, I think I actually do have them bound but there is no way to keep them "held" in Linux while I hold them on the device.

.imwheelrc
```
".*"
None, Thumb1, Control_L, 1, 150, 0
None, Thumb2, Shift_L, 1, 150, 0
```
imwheel -kb '0 0 0 0 8 9'

[pastebin](http://pastebin.arslinux.com/4470)

That is the result of working with a seasoned Linux user for half an hour or more in IRC, and it still doesn't work.  And if you expect the average user to sink the kind of time I did in to something like that, forget it.

**#2 Map network drives to where they stay across reboots.**  Also, I'd rather they not stay connected if I'm not using them, that is simply wasteful.

I installed autofs. Made the auto.master and auto.smb files in /etc (both required sudo to "save" changes). auto.master looks like:

```
/var/autofs/smb	/etc/auto.smb	--timeout=60
```

auto.smb looks like

```
purgatory  -fstype=smbfs,username=USER,password=PASS,uid=1000,gid=1000	://192.168.0.X/runt/purgatory
backup  -fstype=smbfs,username=USER,password=PASS,uid=1000,gid=1000	://192.168.0.X/backup
```

I tried to restart autofs, then restarted the machine. ls /var/autofs/smb and ls /var/autofs/smb/backup still don't get me anywhere.

If I: 
```
ls: /var/autofs/smb/purgatory
```
then:
```
No such file or directory
```

I thought this thing called Linux had a network OS heritage... I'd expect this to be a cinch.

**#3 Launch [JavaFIBS]("http://www.fibs.com/~cthulhu/") from a program launcher.**

I can navigate to it in a file manager, right click and then select "open w/Sun 6" and that works.  I can navigate to it in the Terminal and launch it fine that way.  But I've tried at least 12 different variants on the launcher file and none of them work without making the program error out about a missing board.  Here is the current iteration of the launcher from a text editor.
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=JavaFIBS
Comment=FIBS
Categories=Application;
Exec=java -jar /home/chip/Apps/JavaFIBS/JavaFIBS.jar
Icon=user-info
Terminal=false
StartupNotify=false
Path=/home/chip/Apps/JavaFIBS
```

How can it be that much harder than "Send to desktop as shortcut"?  Why have I even put this much time in to making a shortcut...
[B]
#4 Sound.  Sometimes it works.  Sometimes the right channel works.  Sometimes it doesn't work at all.  Sometimes it causes this error message to come up repeatedly:[/B]
```

Error-artsmessage

Sound server fatal error:

cpu overload, aborting

[Ok]

```

The longer I leave a music player running, the more frequent these errors.  M Audio Revolution 7.1 sound card, comes up in the mixer appropriately.  Here is the kicker... those different results... they happen on different reboots without me touching anything at all having to do with sound.  The first time it worked right after a fresh reboot I was all like "EUREKA, FINALLY I have fixed something in Linux!"  Then on the next boot I had those hopes deflated.

---

### Post by bpmorris on 2007-03-02
I think MrDetermination has a couple of valid points. I find my self in a similar situation in that I too am a support/consulting role for a very large organization mainly having to deal MS products and just into my first month of learning Linux. I too heard the reviews and that is what initially got me curious but I certainly didn’t take it as gospel. I too had problems such as video and Mythtv issues and spent significant amounts of time in resolving them which at times was very frustrating. Where I personally place Linux right now is now that it ready for any given user once configured and setup correctly so in that sense it is definitely Desktop ready. However in saying that in comparison to my usual experience with a windows install Linux has been a very complicated and time consuming exercise when having to find obscure fixes and work arounds. But in that respect I do have to say it has an excellent community, so much so I am almost addicted to reading all the posts in the various sections of this forum. I am not trying to bash either OS the only point I wish to make it don’t always dismiss someone who has a differing opinion at very least some it may very well be valid. I personally am extremely happy to run Ubuntu at home as its free and to invest my time to learn to support it as I can easily see it really taking off on the Desktop very soon and so easily exposure early for me would be of great help professionally.  Either way these were just my thoughts... have a great weekend every body!

---

### Post by DagMan on 2007-03-02
I honestly thought you were just trying to say that Ubuntu sucks and that the bolded bits were reasons why, and not things that you actually wanted help with.  When you come in and say "here are some things that I can't get working and could do it in less than 60 seconds in Windows" it doesn't look like a support question but like a complaint.  I was responding to your complaint and Linux is not for everyone.  Windows is a better suited operating system for many people and despite what a lot of Linux lovers here would say, it's the plain truth, that Linux isn't always better... it depends upon the user.

I apologise for gotten started off like this, but at the same time you went about asking for help in such a way that implied my way of doing things is inferior to your "Windows Poweruser" ways. 

To bind your mouse buttons, the fastest way I can think of is to install xbindkeys, xbindkeys.config, then look into the keymapings and whatnot.  this seems hard.  There's also a program called joy2key that will let you do this sort of thing.  In both cases there are further things to work out that I don't know the answers to without looking more into it and since it isn't my machine...
You might find some way of mapping mouse things in the tips and tutorial section by looking for how to get snazzy mice like the Mac one for example, working.  Those are all directions to persue.  When running Xbindkeys-config, you need to save an empty file first or it will crash btw.

I don't know anything about autofilesystem but I know a small amount about sshfs and sambafs.  From my experience with these, you would need to have a script run it at startup.  You can edit your sudoers file to add commands that will run sudo without a password prompt if you need it.  Search the forums for 'firestarter sudo visudo nopasswd' on bypassing the sudo command
Startup commands go in preferences->sessions->startup and scripts can be dropped into /usr/local/bin to keep track of them, when they are your own, more easily.
I think some network filesystems can take an fstab entry, but I don't really see them mounting at boot time.  I could be wrong.


With the launcher, try right clicking on the desktop if you want it to be there and select to make a launcher.  on the panel, add an item and select 'custom launcer' at the top.  In the Menu right click on the ubuntu icon and select Edit Menus, or navagate into preferences->menu layout.  be careful to make a new item and not a new menu.  
Also, sometimes it's helpful to specify the program that will be launching the prgram as well as the full path, for example, 'python /path/to/file/something.py' instead of just 'something.py'

For your sound, try going to preferences->sound and see what you have there.


That's pretty general and I wouldn't really have responded usually since I don't in fact know all that well but considering the misunderstanding I thought I'de throw out my thoughts for you and you might find them useful.

---

### Post by Boomy on 2007-03-02
It looks like Mr. Determination is making a valid effort at learning Linux. Sure you can have the typical holier than thou attitude and tell him to stick to windows. That really makes people want to cross over to linux. Or you could try to help the guy out, instead of being a smug I know it all and implying you should just stick to windowz because you don't worship linux. I can't really help you with your problems, but I think you can map a network drive by clicking places>connect to server>windows share and entering in the info. This will place a shortcut on your desktop. I map ftp servers like this and the shortcut stays there through reboots. I have mapped shares by ip address this way, I think it just requires forward slashes instead of backslashes like in windows. I hope you get your problems sorted out. I have been  using Ubuntu for about a year, and it looks like you are diving into configuration deeper than I ever have. Good luck. :)

---

### Post by goatflyer on 2007-03-02
Hey all,

Give the guy the benefit of the doubt.  Yes he whines but he's a newbie who's still at the stage of trying to understand why Linux isn't more like Windows...

MrDetermination: note for future reference -- whining is a major turnoff around here, people generally don't bother to offer help to people who are more interested in moaning and complaining than actually getting down to the nitty gritty.

To be constructive, I can see two major problems with your post.

The biggest problem is that you have 4 questions/troubles, instead of 4 posts with 1 question each.  Your odds of finding one person who can answer all four is slim indeed.  That is, unless the point of your post was just to rant and let off steam (thanks but keep your steam to yourself, we got plenty of our own).  Although I understand how hard it can be to write a good rant when there is only one point in a post, but I digress...

Secondly, most people who do want to help scan the titles of messages looking for topics they've seen or feel they have some experience or expertise in.  Your topic title is way too vague to be useful.  I mean just read it, it only draws curious onlookers like me who sometimes gawk at train wrecks to see how bad they really are...  Dividing into 4 separate posts will make it easier to come up with a winning subtitle for each that will attract the attention of the real helper who knows something about your problem(s).

Sorry I can't be more helpful, but I've read your 4 points and have no specific experience to offer.  But I do know how to ask for help, so I thought I would share that...

Welcome to Linux.  Sink or swim as you see fit, but do try to keep the pool clear for the next guy.

---

### Post by aysiu on 2007-03-02
I've removed the off-topic responses (including my own). I agree that the thread should be focused on helping the OP. Let's keep that the focus.

---

### Post by MrDetermination on 2007-03-02
Eep!

aysiu, you're threatening to move my thread and talking to cocoAUS like he was me.  We != the same guy.

Sorry for my tone.  I'm at my wits end on these issues.  If I was just here to bitch I wouldn't have posted all the detail and I wouldn't have posted in the help forum.  I'm just saying I was lured here under false pretenses.  Now that I'm here, and I'm already heavily time invested, maybe you guys can help get me over the hill.  Look at my name.  Think I'm going to sink that kind of time in to something and not see it thru?  Heh :)

Boomy, thanks.  I can do the legacy samba share thing, but I'm losing the mount after reboot.  Also, I'd much rather figure it out the autofs way if I can... I don't like the idea of maintaining that connection when not used.

DagMan, seems you and I had a misunderstanding.  Peace.  Thanks for the xbindkeys and joy2key tips, I'll follow both those roads tomorrow (getting late here).  The launcher I've created about as many ways as I can come at it.  And sound wise, everything looks fine in the mixer and it looks like I have the proper driver loaded.  *shrug*

---

### Post by MrDetermination on 2007-03-02
Just let this die (edit: or lock it)  Goatflyer's points are well taken.  I got a couple new leads out of this anyway.  I'll take a one per day approach from here on out, or at a minimum, isolate the threads to unique issues and try not to spam the fora.

---

### Post by aysiu on 2007-03-02
Closing the thread then.

I think that's for the best. Take it one issue at a time in their own threads. Don't make comparisons to Windows or declare Ubuntu not ready for prime time or whatnot. Those assertions, however true you may believe them to be, simply distract from the main issue--getting help for problems that need solving.

Best of luck.

---

