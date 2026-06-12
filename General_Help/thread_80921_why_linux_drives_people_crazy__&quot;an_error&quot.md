---
title: "why linux drives people crazy / &quot;an error&quot;"
date: 2005-10-23
forum: General Help
---

### Post by lance_delacroix on 2005-10-23
Pardon the rant, but Linux _does_ drive me nuts.  I just installed the latest Kubuntu release on my laptop.  When I log on, I see a removable disk on the desktop.  That must be my 80-gig USB IDE disk.  When I try to open it I get a message that says that the file system type is unknown.  Well, it has at least two different FSs on it, so maybe that is the problem. 

I can't make any progress fooling around with it, so I go to the start menu / system settings / Disk & File systems, and here's where the fun begins, which to me is typical of Linux:  I click on Administrator Mode and immediately get a message that says, "SU returned with an error".  

Huh?  What the heck does THAT mean?  More to the point, what am I now supposed to do?

I had something similar with my last install of Kubuntu, which is why I finally gave up on it.  The kdesu or sudo or whatever it was broke, and I had no clue where to go from there.

"Oh, you just need to get off your butt and read... everything."  I.e., read EVERYTHING...  Come on!  

This is about my fifteenth Linux system over a period of three years.  I've gotten a couple of Mandrake installations to work well enough to get me online, and I've had very good luck with live disks (Mepis and Kubuntu).  But I've never gotten EVERYTHING working at once in a real installation, and what really kills me are these OOB errors that give me no clue as to where to go next. 

Funny thing about Windoze: I can always manage to cobble it together well enough so that it works better for me than Linux.

---

### Post by mostwanted on 2005-10-23
K. Linux does drive me crazy, but only in the positive, open source evangelist way ;)

I never experience a problem I can't solve by googling or asking on the forums. And I rarely encounter problems.

---

### Post by Iandefor on 2005-10-23
I can totally understand your frustration, but this is a Kubuntu support forum... If you want help with some of the issues you mentioned in Kubuntu, we're gonna need a little more information; What were the filesystems on the hard disk that Kubuntu failed to recognize? Did you open a terminal and run su in isolation? What did it do?
I'm sorry if you've been switching between distros at a rate of five per year; What kind of hardware are you using?
Funny thing about Windows: It tends to spit BSODs at me, whereas Linux has never even frozen; Linux works well for some people, and not for others. Who knows why?

---

### Post by lance_delacroix on 2005-10-23
[QUOTE=Iandefor]What were the filesystems on the hard disk that Kubuntu failed to recognize? [/quote]

FAT, NT, and EXT3

> Did you open a terminal and run su in isolation? 

Nope.  I just clicked on the "administrator mode" button.  

>  What kind of hardware are you using?

A two-year-old Toshiba laptop, a four-year-old Compac laptop, a new, up-to-date desktop, and an older desktop.  Different functions in different distros fail on different computers, which suggests hardware issues, but what I don't understand is why the live disks work flawlessly while the permanent installs are hit-and-miss. 

> Funny thing about Windows: It tends to spit BSODs at me, whereas Linux has never even frozen; Linux works well for some people, and not for others. Who knows why?

My best guess is that various combinations of hardware have more of an effect than people generally like to think. 

Thanks for your interest.

---

### Post by leo898@gmail.com on 2005-10-23
Hey,

Okay, i totally understand that your stressing out. I would recomend you to use gnome with breezy. Its not as graphical and does not have as much as cool softwaree and takes a bit to get used to, but its really stable of first instal. 

About your HD not mounting, you can access it in your master HD go to your media folder and find the usb device. I am currently trying to mount it with the faq i got from the wiki but i dont nkow if it will work. From what i got of the forums, it is a error.

Second of all, if you want to config your system, the current setting folder admin priv you talked about does not work. You will to open the comand prompt and type in "sudo kcontrol" , this will give you access to edit w/e you need. Dont try to add the file system to your HD because it wont help.

I think this is it for now, i will get back to you on the mounting issue, if it works.
Regards, 
Leo

---

### Post by Digitallysick on 2005-10-23
I understand how hard linux can be at times, i dont think i will ever learn it all, and when need to accomplish a task i end up back at this board, trying to to read and edit files, etc, but i feel that in time it will be great, i have tried linux since "zip slack" back in the day when i had to download packages on the 56k modem, and then put them tg, only for it to never work!! it has came along way

---

### Post by lance_delacroix on 2005-10-24
[QUOTE=leo898@gmail.com]
Second of all, if you want to config your system, the current setting folder admin priv you talked about does not work.[/quote]

Then why is it there?  (Question for anyone.)  

>  You will to open the comand prompt and type in "sudo kcontrol" , this will give you access to edit w/e you need.

Something about that sentence suggests that I will need to know much more than I already do in order to make any progress.  :-)  I think it's the "give you access to edit", which seems to imply that I will know how and what to edit, which I don't.  But I'll try it.

Anyway, thanks for your help.

---

### Post by Jengu on 2005-10-24
[QUOTE=lance_delacroix]My best guess is that various combinations of hardware have more of an effect than people generally like to think. [/QUOTE]

I have to disagree. I have only been using linux for just over a year, so I haven't been around for the early horrors, but my experience with hardware support has generally been good. The first thing to realize is that generally laptops have more customized hardware than desktops, so you're more likely to have compatibility issues with them. The second thing to notice is that to complain about hardware support in 'linux' is too general. In my experience the quality of hardware support has varied wildly across distributions. The kernel may have support for a particular piece of hardware, but the distro may not be setup to detect it properly and make it useful.

I have had the highest success rate hardware wise with SuSe, you may want to give it a shot, they just released 10.0 ([www.opensuse.org)](www.opensuse.org)). Hardware support in Ubuntu/Kubuntu is improving rapidly, but as of the last version still didn't setup suspend automagically on my laptop (haven't tried with Breezy yet though). To be honest, Kubuntu is very good but not nearly as polished yet. Kubuntu-desktop is younger than Ubuntu-desktop and in some places it shows.

Your familiarity with windows is subjecting you to a bit of bias. The su error seems so confounding because you haven't seen it before. But is it any more or less intuitive than a blue screen of death or a general protection fault message? Computer errors in general are too vague, and this is pretty true across all operating systems. Even on the much touted as user friendly Mac OS X users are treated to little pictures of bombs with obscure error numbers.

You say on windows you always manage to hobble things together. Presumably you install adaware and a virus scanner, to compensate for Windows lack of a good permissions system. Then you may go into control panel and futz around to make it harder for people to break in. Before connecting to the internet, you download a half dozen service packs. To get rid of annoying startup apps, you edit the registry with regedit. To further prevent malware, you download firefox. Then it's 'usable.' The only reason that seems like an improvement over linux is that you already know how to do all that.

su is the utility used to switch users. Presumably kdesu (the program that comes up to ask for your password when you click administrator mode) doesn't actually perform the user switching itself. Rather, it probably just calls the terminal command su with the appropriate parameters. But when it does, su is giving an error. BUT, this is odd, because Kubuntu/Ubuntu don't use su, they use another command called sudo (see the Ubuntu FAQ to learn the distinction). Are you sure the error didn't say sudo returned an error?

To see what the error is, open up Konsole (K-menu -> System -> Konsole) and type this:

sudo echo test!

"echo test!" is just a nonsense command to print out the word test, but the sudo part will make linux try and do the command as root (Administrator). It should prompt you for a password. If it gives an error, copy and paste it back here.

P.S. To copy and paste from Konsole, highlight the text in the Konsole and then middle click where you want to paste it. If you don't have a middle mouse button pressing the right and left mouse buttons at the same time is the same as middle click.

---

### Post by odrop on 2005-10-24
[QUOTE=Jengu]
Your familiarity with windows is subjecting you to a bit of bias. The su error seems so confounding because you haven't seen it before. But is it any more or less intuitive than a blue screen of death or a general protection fault message? Computer errors in general are too vague, and this is pretty true across all operating systems. Even on the much touted as user friendly Mac OS X users are treated to little pictures of bombs with obscure error numbers.

You say on windows you always manage to hobble things together. Presumably you install adaware and a virus scanner, to compensate for Windows lack of a good permissions system. Then you may go into control panel and futz around to make it harder for people to break in. Before connecting to the internet, you download a half dozen service packs. To get rid of annoying startup apps, you edit the registry with regedit. To further prevent malware, you download firefox. Then it's 'usable.' The only reason that seems like an improvement over linux is that you already know how to do all that.
[/QUOTE]
I would just like to say thank you for this beautiful and eloquent synthesis of many problems that face new users to linux today.  The same can be said for those who were trained and only used Unix and then wanted to try out Windows.  Frustrations and problems exist when learning something new and different.

I've been using Linux for about 10 years now and it's come a long way from the days when x11 would warn you about blowing up your monitor if you configured it wrong.  The learning curve is still very high and many old problems still exist that every new user has to overcome, but I think the rewards you receive with hard work and perseverance far outweigh just sticking with Windows.

One thing that shines above all else is the Ubuntu community.  So many people here give their time and expertise and are willing to help out anyone and everyone, its a great community.

---

### Post by lance_delacroix on 2005-10-25
[QUOTE=Jengu]
To see what the error is, open up Konsole (K-menu -> System -> Konsole) and type this:

sudo echo test!

"echo test!" is just a nonsense command to print out the word test, but the sudo part will make linux try and do the command as root (Administrator). It should prompt you for a password. If it gives an error, copy and paste it back here.[/QUOTE]

Here you go:

sudo: unable to lookup ubuntu via gethostbyname()

---

### Post by cus on 2005-10-26
[QUOTE=lance_delacroix]Here you go:

sudo: unable to lookup ubuntu via gethostbyname()[/QUOTE]

Hi there, Lance.

Linux uses a 'hosts' file to look up its network details - Windows does something similar. Could you post the contents of your hosts file? It should be located in '/etc/hosts'

I suspect that the host 'ubuntu' which is what you've called your machine does not have an entry in there, though this is normally done automatically on install.

Mine looks like this: ('jaka' is my machine name)

127.0.0.1 localhost.localdomain localhost jaka

---

### Post by lance_delacroix on 2005-10-27
The only entry in the HOSTS file is 127.0.0.1 localhost.  

And I can't edit the file, of course.

---

### Post by Jengu on 2005-10-27
Edit it to look like CUS's and see if that helps, or try a reinstall (I suspect something went funky with the install, /etc/hosts should be setup automatically). To edit it, use one of the many live CDs you have lying around, preferably one like knoppix that will automatically mount your drives. Then edit the file (you won't need your root password). I've installed Ubuntu on 3 systems and never seen this problem, and it doesn't look like any sort of driver issue. Are you sure you weren't fiddling with system files by hand at some point? It doesn't seem like the sort of bug that would happen because of weird hardware. Maybe an untested install option, but Ubuntu/Kubuntu doesn't have any :P

---

### Post by lerrup on 2005-11-01
But call it ubuntu to make sure everything matches...

---

### Post by shinygerbil on 2005-11-01
Are you able to log in as root?

Try the command-line login (Ctrl-N at the normal login screen i think it is, otherwise just click on the button).

Then you could try either startx or, if that doesn't work, use nano to edit the file.

It's a fairly long shot, but I've done similar things on mine (damn forgetting to backup xorg.conf...)

Steve

---

### Post by dtfinch on 2005-11-01
I had an exact opposite experience. I had a 20gb NTFS formatted USB drive that no Windows system would mount (I tried 2000, XP Home, XP Pro). Eventually I plugged it into a Warty system and it "just worked". I rarely see Windows BSOD's, but I see a lot of "unexpected error", "undefined error", "unknown error", "unspecified error", etc. It took over 2 days to xcopy 200gb to a Windows system, because it would randomly bail with an error like "insufficient system resources" and I'd have to resume it manually. But then a lot of Linux GUI programs write their errors to stdout or stderr before they bail, which more often than not happens to be pointed to /dev/null.

Something I always do on an Ubuntu system is set the root password (sudo passwd) so that I can log in as root by methods other than sudo, like with the su command.

---

