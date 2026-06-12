---
title: "My First Time"
date: 2008-06-19
forum: General Help
---

### Post by MooreUser21 on 2008-06-19
OK I have wanted to give Linux a go for a long time, not because its different, but I want to learn to write code and computer language like C++ and others, but I am having a huge problem. People don't give you guys enough credit on how much you know, its crazy. I am a complete and total beginner and as Virgin as it gets in learning to use the terminal. I have two main problems: 
  One I need someone to speak english in telling me how to install an ATI driver so I can get a nice graphic desktop with Beryl. I am used to the windows just click download and click install and bam its done so writing and typing in the terminal I dont know what to do.
  Also is there anyone out there than can explain to me how the whole terminal code thing works? How do u guys know what to write for what function? I though something as simple as installing a driver would be easier. I mean I don't know how to explain my confusion other than I am completely in the dark here. I have know idea what each symbol means or whats going on I understand. Even the most basic function of installing software from a CD I have no idea how to do. 

Any Help would be so very useful, unfortunately I am not in an area where friends or family use Linux so it is a lonely struggle.

---

### Post by joekidston on 2008-06-19
Yes, I was in this position a few weeks ago!

I use ubuntu, which comes with a nice click and point interface (Graphical User Interface), but am trying to do everything from the terminal.

I think that installing something from a CD you might have to "mount" it, so that your computer thinks it's a regular harddrive.  Somewhere on the disk there will be an executable file, and you just type the full path (location) of the file, and it will execute.

Read the basics about navigating with the terminal.  It's mainly using 

cd (current directory, where the terminal can "see")
ls -l (list all files in a directory)

---

### Post by Hunkadoodledoo on 2008-06-19
Well, you came to the right place!  I'm not all keen on ATI graphics cards, but Ubuntu uses the Restricted Drivers Manager (I think it has been renamed to something different in Hardy), and once opened, it will be able to detect if there are available commercial drivers for your graphics cards/wireless cards/etc.  I know it detects nVidia cards, but I'm not sure about ATI.  If you're using Hardy, go to "System - Administration - Hardware Drivers" and see if it detects your ATI card.  Back in the day, you'd have to install a package that contained the driver, and then reconfigure your XServer to use the new driver...That was fun!  So, try the Hardware Drivers route and let us know what happens.

As far as the terminal goes, I think the command "help" without the quotes may list a fair amount of built-in commands, but I'm not able to check right now...If you ever want to know how a command works, just type "man *command*" without the quotes - where *command* is the command you want to know about.  This brings up the manual pages for that command and tells you what it does and any possible options/switches available.

Here are a few commands to get you started:
cd [*dir*](change current directory to *dir* - contrary to what was put in the previous post.
pwd (This prints the current working directory back to you.)
sudo *command* (Gives temporary Super User authority to execute the *command*. Requires the root password.)

And here is a link to About.com's Linux Command Library:
[http://linux.about.com/od/commands/l/blcmdl.htm](http://linux.about.com/od/commands/l/blcmdl.htm)

I would recommend getting familiar with the Synaptic Package Manager ("System - Administration - Synaptic Package Manager").  For the most part, any application you are going to want to install can be found there.  Synaptic is a front end to the apt-get package management system, and it contains links to repositories of programs that have been compiled and tested against your version of Linux and are, to an extent, guaranteed to work.  It also automatically resolves dependencies that certain programs require to be installed before they can run.  By default, I think only the most restrictive repositories are enabled by default, but you can add more to allow you access to more, possibly less tested or stable, possibly newer versions of software.

As far as installing software from a CD, I would guess you have software that is written for Microsoft Windows, and you would like to install it in Ubuntu.  Well, there is no direct way to do that.  There are many differences between Linux and Windows, and the short answer is that Windows programs aren't made to run in Linux.  Bummer, right?  Well, there is good news!  The Wine Project (Wine is a recursive acronym that means "Wine Is Not an Emulator") was created for just such an occasion.  Here's a description from the Wine webpage:
> Wine is a translation layer (a program loader) capable of running Windows applications on Linux and other POSIX compatible operating systems. Windows programs running in Wine act as native programs would, running without the performance or memory usage penalties of an emulator, with a similar look and feel to other applications on your desktop.
So, using Wine, you should be able to install Windows programs on Linux, but I would recommend looking in Synaptic for a suitable alternative.  Many free programs exist that are as good or better than their Windows counterparts.

Well, I've definitely typed long enough.  Let us know if you have any luck, and welcome to Linux!

---

### Post by MooreUser21 on 2008-06-19
Thank you so much for the replies they were helpful. I spent the morning tinkering with terminal and desktop trying to understand other posts on the forums with little to no success at one point I made things worse when I tried to enable my graphics card with the hardware drivers tool in system >administration. I restarted my computer and loaded up ubuntu after I got past the part where I enter my user name and password the moniter flickered and then no picture so I assume the driver or w/e I did to the GPU didnt work and I had to restart in restore mode and change things. After that I tried to enable desktop effects to try and get a 3d Desktop that looks good like I see in so many youtube videos but once again after I enable it it goes to a blank white screen. I tried many things including restarting in restore mode which all ended up with me repartitioning my hard drive and reinstalling ubuntu all over again. 

I am deeply sorry but I grew up in a time where no one used DOS anymore and Command lines were never heard of it was all click and drag kinda thing. I went to a local Book Store to try and find books on learning to use the Command line terminal again but no luck as of yet.

any thoughts?

---

### Post by Zenze on 2008-06-19
Hey, I was in the same boat as you are a couple weeks ago. I found this in the beginner guide, and it was a great introduction to the terminal.

Check it out: [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by jakupl on 2008-06-19
> **joekidston said:**
> 
I think that installing something from a CD you might have to "mount" it, so that your computer thinks it's a regular harddrive.  Somewhere on the disk there will be an executable file, and you just type the full path (location) of the file, and it will execute.



huh? what where? no!

the cd will ofcourse automount.
You do not need to worry about manually mounting the cd.
This should work exactly like in windows and mac, if not - then tell us.

---

### Post by Nameless_one on 2008-06-19
As for the ATi driver, check this out: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by Hunkadoodledoo on 2008-06-19
Well, if you don't want to worry about messing your settings up to the point where you have to re-partition, just boot into Ubuntu using the Live CD option.  Sure, you won't have hardware accelerated graphics, but you won't change anything on the computer that can't be fixed by just rebooting.

My first computer was a 33Mhz 486DX with 4 (maybe 8 ) MB of RAM.  I do believe that Windows 3.1 ran on top of MS DOS 5.0, and you had to edit your Autoexec.bat file to run win.exe after it had loaded all the other junk the computer needed.  I grew up with DOS commands like: cd, dir, mem, deltree, xcopy, etc.

There are definitely many advantages to a Graphical User Interface, and I think they are just getting more and more user-friendly.  From your original post, you mentioned you wanted to learn to program using C++.  Knowledge of Terminal commands are probably not going to help you learn that.  You'll probably want to check out a book from the library or find some beginning programming tutorials on the internet for that.  You'll also probably want to get familiar with an IDE (Integrated Devolopment Environment), which will help you use correct syntax (and some can integrate a compiler, if I remember correctly).  I've heard good things about Eclipse, but I've never used it.  gedit does syntax highlighting for Python, and that is the only language I know that much about.

I do hope you are eager to learn and are patient with Ubuntu.  I was frustrated when I first started using Linux because it challenged me to not be a complacent computer user - just accepting the MS way as the only way.  I had to learn new things, and I think I'm better for it.  I don't know how old you are, but I'm glad you are already learning about Linux at a young age.  Keep asking questions, and we'll keep giving answers.

I didn't mean for this to be a "pearls of wisdom" post.  I do hope you figure out your graphics card issue.  I looked at the ATI driver link that Nameless_one posted.  Doing those things should get you up and running, but remembering back when I was new to Linux, and I really wished I knew what the cryptic commands I was typing into the Terminal was doing.  They usually fixed the problem I had, but I didn't know why I was typing what I was typing or what it actually did behind the scenes.  I guess some of that will come with time.  So, again, best of luck, and let us know if it works for you!

---

