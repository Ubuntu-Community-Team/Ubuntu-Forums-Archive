---
title: "Using LKL - have I got it wrong?"
date: 2007-08-02
forum: General Help
---

### Post by tim356 on 2007-08-02
I've been launching LKL by the following:
sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o /path/to/log.file

but the log file doesn't seem to get created - am I doing something wrong? No errors are presented.  

Also, is there a way to launch LKL wihtout having to leave the terminal open?  Kinda defeats the purpose of a keylogger.

No flaming about the use of a keylogger please - I have a legitimate need for it that I don't feel I need to explain but am happy to if it will ease your minds...

---

### Post by gentine on 2007-08-02
there's a way to make ther terminal invisable, using beryl.

---

### Post by Tiekyl on 2007-08-02
I don't know how much help it would be in your situation, but I've opened up lkl in one of the other displays (Ctrl-alt-f1 things). It stays pretty well hidden.

I'd be interested in figuring out why its not creating the log files though.

---

### Post by tim356 on 2007-08-02
> **Tiekyl said:**
> I don't know how much help it would be in your situation, but I've opened up lkl in one of the other displays (Ctrl-alt-f1 things). It stays pretty well hidden.

I'd be interested in figuring out why its not creating the log files though.

Ah, that will probably be sufficient - I'll just hide it that way.

I have no idea why the log file isn't being created - I've tried a few different locations and extensions but it never appears.  I wonder if it is because the keyboard is usb?  I read somewhere that LKL doesn't log keystrokes from a usb keyboard - does anyone know if this is true?

---

### Post by Tiekyl on 2007-08-02
I have a USB keyboard, I've been having trouble with the keymap, but I got it to output into a file when i saved it as .txt file. Maybe that would help?

---

### Post by tim356 on 2007-08-02
Hmm, tried to save it as a txt file but have the same problem.  It's funny - I rebuilt another machine I have with Feisty last night and installed LKL - works fine.  I thought it was perhaps the p/s2 keyboard but the log file gets created on the new box as soon as I run the command.

This has really got me buggered. For now I have resorted to using the box I built last night, however this is a lower spec machine (IDE drives, slower processor) and my good spec'd box is just sitting there... :(

Any ideas anyone??

---

### Post by stepluvx on 2007-09-18
I've installed LKL from the repos on my son's feisty machine. I can't seem to find any "how to's" on LKL, is their anything special I need to do after installing it & how do I set it up to auto run on startup?

---

### Post by Tiekyl on 2007-09-18
You can try checking the man page. I had a little bit of trouble setting it up for the proper keyset, but just read the man page, it gives a decent idea of how to get it started at least. Are you worried about hiding the LKL window? I've been trying to figure out a way to send a command to open up the display in another display..thing..but I haven't figured it out yet.

---

### Post by Greevous on 2008-01-21
Tiekyl, where did you find a man page for lkl?

---

### Post by Tiekyl on 2008-01-21
Hmm,

I could have swore I saw a man page for it before, but I guess it's not there is it. Theres some basic commands if you just type in sudo lkl though, if that helps.

---

### Post by twizler on 2008-01-25
Ultimate Linux Keylogger - Uberkey

A while ago I wrote a post about a Linux keylogger called lkl. It’s a decent program but it’s rather hard to manage at times and had some configuration bugs. Even once I got it running I’d find that many of the characters were off from what they should have been.

Luckily a reader used the comment form on that post to point out a much better program called uberkey.

Uberkey is awesome because of it’s simplicity. When you download it from the link above (or this link) you’ll be amazed at just how simple the install package is. There are three files:

makefile
uberkey.8
uberkey.c

Installing Uberkey
To install the uberkey keylogger on Linux simply compile the uberkey binary by typing # make. Really, it’s that simple. You’ll now have a fourth file in the current directory named uberkey. Copy this to some executable directory like so:

# cp uberkey /usr/bin/

Uberkey is now installed.

Running Uberkey

Uberkey does not handle log files on it’s own, what it does is when it’s running it will print out the names or values of the keys being hit to the standard output. This is not very useful if you just type it in a terminal straight, but with two very simple changes to the way the program is called it becomes an excellent system keylogger. First, we’ll use the greater-than symbol to direct the standard output to a text file:
# uberkey > /home/myname/.keylogfile

Second, we’ll use the ampersand symbol at the end of the program call to allow this to run in the background and give us our terminal prompt back:
# uberkey > /home/myname/.keylogfile &

If you want this to start at boot, all you need to do is add the last line of code above to one of your init scripts. If this doesn’t seem easy to do, I’ve included a script that you can make into a file and drop into /etc/init.d. Make sure it is executable (# chmod +x filename)

Sample Init Script for Uberkey
(Note: you should have runscript installed to do this)


###############
#!/sbin/runscript

start() {
        ebegin "Starting Uberkey keylogger"

        uberkey > /home/myname/.keylogfile

        eend $?
}
###############

Update: Wicher has told me that sometimes uberkey can mess up X. If anybody knows something about this, I’d love to hear it. So far it’s been working fine for me. Also, has anybody tried uberkey on a non en-us keyboard layout?

---

### Post by twizler on 2008-01-25
@#

---

### Post by cbarboza on 2008-01-25
I have seen this information posted before on another site for Uberkey.  I've had problems running it.  When I've looked at the log file, it said I had to be root.  I don't know if I installed in in the wrong place or what?  I've seen different start up scripts for Uberkey and for LKL.  I still haven't been able to get either to work.  I use Ubuntu 7.04 and would love some help getting it up and running.  What I'm looking for is either LKL or Uberkey to start at boot up without the need of inputting a password and have it log to a file.

---

### Post by cbarboza on 2008-01-30
I am using LKL right now, but I have to manually start it after boot up, then at some point it screws up the logging with odd letters and what not.  Below is a sample of what I enter into terminal to get it logging, what I would like to know is how to set it up so that it starts up automatically at boot up without me having to do it manually.  Can anyone tell me how to do this?

Here is what I use to get it going, manually:

sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/.cart/log.log -l

Then:

sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/.cart/log.log -l &

How can I make this initialize at startup automatically?

---

