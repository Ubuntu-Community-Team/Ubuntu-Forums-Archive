---
title: "Need a good GUI-based FTP server"
date: 2007-02-13
forum: General Help
---

### Post by mjpatey on 2007-02-13
Hi, Group-

I'm trying to create a way for my business clients to be able to download large files from me, upwards of 600MB each.  The best way I can think of to do this (aside from hosting my own website) is through FTP.

What I'm looking for is something that will let me set up usernames and passwords, so I can email my clients a link to the folder they're approved to download files from.  They should be able to just click the link in the email, and have it open in their browser (which may be IE, Safari, Firefox), asking them for a username and password.  Once they enter the required info, they'd be presented with a standard folder tree showing what they have permission to download.

I understand there are probably ways of doing this via the command line, but I'd love a GUI-based program.  Sound like anything I can get in Linux?

I hope so!  I just read another thread which didn't look too promising on this subject.  Thanks for any help you can provide!

-Mark

---

### Post by Jussi Kukkonen on 2007-02-13
A graphical ftp server? don't think you'll find one -- there's not much point.

Whatever solution you end up with, read up on ftp security: it's not the most secure protocol on the net... Actually some experts have called ftp a "security disaster". On the other hand, if you aren't allowing uploads it should be manageable. Personally I'd probably setup a web server.

EDIT: I just realised **webmin** would do it... It's a web-based server admining tool that probably works with at least one ftp server. Read the docs, maybe it's your tool.

---

### Post by mjpatey on 2007-02-13
OK... I want to serve files to my clients via FTP and I would like to do it (set it up, create user accounts, select files to upload, etc.) via a GUI rather than a command line.  I'm not sure why it's hard to see the point of that, but OK.

Not too worried about security; I'll likely just be running the server for a few hours at a time a few times per month, and hopefully my choice of passwords will stymie the baddies.

Looking at Webmin online right now; it looks like it does a lot more than I'd need, but that may be OK, too.  Thanks for the info.

[EDIT] Any ideas for a simple Web server?  That would be fine, too, if I can use .htaccess for permissions, etc.

---

### Post by Soulxlight on 2007-02-13
pure-ftp server with pureadmin ^_^ That shoud do it...

---

### Post by localzuk on 2007-02-13
I think the problem you'll have is that most linux developers don't see gui server apps as useful - it is usally seen as the following:

1. Set up server
2. Leave server running
Occasionally: Edit config file to add new user/use command line tool to add new user.

The idea of running an entire graphical environment in which to do that just seems like a waste of resources.

However, I would recommend using Webmin with one of the supported FTP servers. It is modular, so you only need to enable the modules you want + it doesn't require you to be running an entire graphical front end (saving a huge amount of resources).

The servers you could choose from are proftpd, wuftpd, pure-ftpd, pyftpd and many more.

However, if you already have a graphical environment on your computer you may want to look at proftpd and gproftpd (which is a graphical front end to it).

I can't give advice specifically on which software is best as I steer clear of ftp.

---

### Post by mjpatey on 2007-02-13
localzuk,

Thanks for the insight, and for the FTP server info.  I've installed gproftpd, and when I try to run it, it says I have to be root.  As I understand it, Ubuntu doesn't let us be root, is that right?  I've tried "sudo gproftpd", knowing that probably wouldn't be good enough, and I was right.

Any idea how to tell it I'm root?

-Mark

---

### Post by Soulxlight on 2007-02-13
```
su
```

Though you might not have a password set, if that is the case type in 

```
sudo passwd
```

and set it.

---

### Post by localzuk on 2007-02-13
Use sudo -s, don't use su. You shouldn't need to set a root password.

EDIT: Oops, I should read before I type...

You should run gksudo rather than sudo to run it.

---

### Post by frup on 2007-02-13
Why ftp and not http?

install a lamp get something of hotscripts and make the accounts... you might have to make calls to your ip forward through your router to your computers localhost but that you would need to do for ftp to i think... i'm not to experienced with all that though

---

### Post by mjpatey on 2007-02-13
Hmmm... I am familiar with port forwarding, so that's not an issue.  I'll look into Apache in all its hugeness, and see if I can wrap my brain around it.  :-)

-Mark

---

### Post by nix4me on 2007-02-13
gproftpd is a front end for proftpd.  try that.

you could also install proftpd-mysql and use phpmyadmin to addmin the authenitcation via apache.

nix4me

---

### Post by dafacct on 2008-01-19
:guitar:I too am slowly making the switch from Windows to Ubuntu 7.10. I also need an ftp server that supports file tranfers to/from my clients that will interface with most ftp clients. My problem (to date) with the Linux environment is that while it boasts of security, reliability and speed, it lacks in a gui for most programs that run under it.

I am not a programmer and do not have the skills in the Linux environment to get pgms up & running without much trial & error. Trial & error (and following documentation from the software vendor or online forum) is time consuming...........and time that I don't have. I shouldn't have to be a programmer or an expert to be able to administer the server.

In the windows environment, getting programs to install and run without much effort is how the Linux programmers must start developing software to be utilized by users who are not Linux experts. In order for Linux to become a mainstay, this issue must be overcome. 

I too need an ftp server that can be installed and administered through a gui. The ones that I have reviewed for the Linux platform boast of security, speed, etc, but lack in an easy install and admin. All that I've seen require command line install & administration.

Come on folks, understand that most new users that are making their way to the Linux platform want the ability to have a gui and not have to learn or use the command line language for all installs & administration.

---

### Post by lespaul_rentals on 2008-01-19
Hey Mark, did you install this is a daemon?  If so, you can usually start, stop, and restart the daemon as follows:
```
sudo /etc/init.d/<name of service> {stop|start|restart}
```

Example to restart proftpd:

```
sudo /etc/init.d/proftpd restart
```

This may be what you have to do to get the proftpd daemon up and running.  I am not sure, as I choose vsftpd for FTP purposes.

[quote=dafacct]I too am slowly making the switch from Windows to Ubuntu 7.10. I also need an ftp server that supports file tranfers to/from my clients that will interface with most ftp clients. My problem (to date) with the Linux environment is that while it boasts of security, reliability and speed, it lacks in a gui for most programs that run under it.

I am not a programmer and do not have the skills in the Linux environment to get pgms up & running without much trial & error. Trial & error (and following documentation from the software vendor or online forum) is time consuming...........and time that I don't have. I shouldn't have to be a programmer or an expert to be able to administer the server.

In the windows environment, getting programs to install and run without much effort is how the Linux programmers must start developing software to be utilized by users who are not Linux experts. In order for Linux to become a mainstay, this issue must be overcome. 

I too need an ftp server that can be installed and administered through a gui. The ones that I have reviewed for the Linux platform boast of security, speed, etc, but lack in an easy install and admin. All that I've seen require command line install & administration.

Come on folks, understand that most new users that are making their way to the Linux platform want the ability to have a gui and not have to learn or use the command line language for all installs & administration.[/quote]

Not trying to sound like an elitist jerk or anything, but Linux is not made for the point-and-click people.  It's really not that hard to go through a simple configuration file and change some settings.  I use vsftpd and the first time I edited the configuration file it took me about 15 minutes, not much more.  Most of that was reading through some of the great documentation.  If you can edit it, you can probably find it on Google.  Configuration files usually allow for a lot more customability than GUI's, so I'd strongly recommend getting accustomed to them.  It's not like we're asking you to host your server on Gentoo or anything, it can't get much easier than "sudo gedit /etc/service/service.conf."

Also remember that running a background daemon versus a GUI is a huge difference when it comes to memory footprint.  Whoops, you accidentally closed the GUI, now everyone got kicked.  Get what I'm saying?  Get accustomed to the advanced Linux way of doing things and I think you will be happier.

---

### Post by mjpatey on 2008-01-19
Hello, all-

It's interesting to see the progress of this thread over the months!  As time has gone by, I've become more accustomed to doing a lot of things without a GUI, plus my original need has been filled.

What I did end up doing to solve the original problem was to install apache, and simply run my own web server to give files to my clients.  I do use Kftpgrabber as a graphical ftp client when I need it, though I'm not running an ftp server, which is what I originally inquired about here.

Regarding the posts that address the issue of GUI vs. command line, my current perspective is the following:  by and large, command line interfaces (as well as manual editing of config files) offer more *flexibility *than most GUIs.  And GUIs offer quicker *accessibility*, at least initially.  If I'm new to something (and I'm new to a lot of things), a well-designed GUI gives me clues not only about *how* to do something, but about what a program can do, in a single glance.

Most of us Ubuntu users are former or current Windows/Mac users, and it's hard to do without the  GUI when that's all we know.  In Ubuntu, you can go forever and never use the Terminal, never edit a config file, if you're a casual user (just make sure your friendly neighborhood geek is well-fed in case things break!)  But if you're setting up an FTP server on your machine, you've probably got the skills to figure out how to do it via command line.  It just takes some getting used to, and some reading of "man" pages or help files.

It's definitely an adjustment, but it works.

Sorry to ramble on here, but as an off-topic aside... we have 3 computers at home, 2 running Windows and 1 (mine) running Ubuntu 7.10.  In my latest install, I neglected to include Tux Racer, Neverball, and a couple of other kid favorites that I also have installed on the Windows boxes for my kids.  The two Win machines were being used, and my son wanted to play his games, and I told my wife I didn't have them installed on my computer yet.  She told our son, "Sorry, honey, those programs aren't on Daddy's computer."  During his 30 seconds or so of fretting, I had typed:

```
sudo apt-get install tuxkart tuxtype neverball tuxracer pingus
```

...and all his games were installed and ready to play in the blink of an eye.  My wife was astonished!  She's a dyed-in-the-wool Windows user, but is coming along slowly... she actually may be ordering an EeePC soon, which we'll convert over to EeeXubuntu.  :-)

-Mark

---

### Post by lespaul_rentals on 2008-01-19
> **mjpatey said:**
> Regarding the posts that address the issue of GUI vs. command line, my current perspective is the following:  by and large, command line interfaces (as well as manual editing of config files) offer more *flexibility *than most GUIs.  And GUIs offer quicker *accessibility*, at least initially.  If I'm new to something (and I'm new to a lot of things), a well-designed GUI gives me clues not only about *how* to do something, but about what a program can do, in a single glance.

Most of us Ubuntu users are former or current Windows/Mac users, and it's hard to do without the GUI when that's all we know. In Ubuntu, you can go forever and never use the Terminal, never edit a config file, if you're a casual user (just make sure your friendly neighborhood geek is well-fed in case things break!) But if you're setting up an FTP server on your machine, you've probably got the skills to figure out how to do it via command line. It just takes some getting used to, and some reading of "man" pages or help files.

You summed it up perfectly.

Sorry I posted in reply to something a year old!  I didn't even think to look at the date.  :(  Hope you are enjoying your stay on the forums and in the Linux world.

---

### Post by mjpatey on 2008-01-19
> **lespaul_rentals said:**
> You summed it up perfectly.

Sorry I posted in reply to something a year old!  I didn't even think to look at the date.  :(  Hope you are enjoying your stay on the forums and in the Linux world.

Thanks, you too!  I've done the same thing before, when somebody replies to something from a long time ago and it gets bumped to the top.

---

