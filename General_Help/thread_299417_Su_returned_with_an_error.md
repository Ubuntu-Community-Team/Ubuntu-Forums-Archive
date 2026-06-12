---
title: "Su returned with an error"
date: 2006-11-14
forum: General Help
---

### Post by liveN4HIM on 2006-11-14
Been with Kubuntu since Feb 2006, updated my computer about a month ago.  (I don't use it every day/week)

Since I've updated no matter which program I run that I want to click on admin mode i get the same message. Also when I click on package managers in menu/system/ (adept,kynaptic,synaptic package manager, adept updater, and even Kuser) I get the same message "Su returned with an error." Though if I su or su - in a konsole I'm prompted for pswd which I give for root and I'm in. Yet in the konsole# to run the command like # adept   I get the message  "adept: cannot connect to X server" and the like for other similar commands. One out of every 10 attempts for adept in $ will yield a read only with no write or execute. 

All I was originally trying to do is set my pc for a new printer "Epson Stylus C88+" I down loaded 'gutenprint 5.0.0'  but am not quite sure what to do with gutenprint now that I've downloaded it.

If anyone can help, I've been away from linux for several years ( since RH 7.2) and have forgotten a lot.

Additionally I've visited sites listing "su returned with an error" that I've found via google including here @ ubuntuforums.org and I've tried what has been suggested to no avail. even added me to etc/sudoers under root.

---

### Post by taurus on 2006-11-14
Can you still use sudo like

```
gksudo synaptic
```

---

### Post by liveN4HIM on 2006-11-14
taurus: Can you still use sudo like 

code
gksudo synaptic

Honestly, I don't know what gksudo is though I did type it on the command line  
:~# gksudo synaptic
-su: gksudo: command not found

I believe this whole problem started when I changed my user passwd. All those programs I mentioned above would prompt for su passwd but would be accessed by my user passwd and not su passwd.

Honestly, haven't got a clue...

---

### Post by maestrobwh1 on 2006-11-14
The same thing has happened to me and I could not figure out how to work around it.  Actually, I did not do anything other than the ususal, then all things that revoled around the sudo command returned "su returned with an error"  I just became really annoyed at the lack of answers (I never posted here, to be honest) on the net and reinstalled kubuntu.  I recently put Edgy alongside Dapper, and everything worked great for a long time and now my Edgy install is doing the same thing.  I did use the recovery mode to go into root but from there, I am not sure what to do.  I keep my Dapper backed up with Norton Ghost so now I can just overwrite things when such things happen:-)

---

### Post by igknighted on 2006-11-14
> **liveN4HIM said:**
> taurus: Can you still use sudo like 

code
gksudo synaptic

Honestly, I don't know what gksudo is though I did type it on the command line  
:~# gksudo synaptic
-su: gksudo: command not found

I believe this whole problem started when I changed my user passwd. All those programs I mentioned above would prompt for su passwd but would be accessed by my user passwd and not su passwd.

Honestly, haven't got a clue...

if you have the # prompt are you not root already?  When I am on as a user I get :~$ as my prompt, but when root I get :~#

---

### Post by liveN4HIM on 2006-11-15
igknighted: if you have the # prompt are you not root already? When I am on as a user I get :~$ as my prompt, but when root I get :~#

Yes, igknighted when I'm :~# I'm root (or su) and when :~$ I'm user. For some reason when I want to open the programs mentioned in my initial string it will not let me. 

Example:
   command

:~$ adept
This command yields the following applet "Su returned with an error."

and

:~# adept 
adept: cannot connect to X server

Also when in any GUI clicking on Admin Mode button returns the same  applet "Su returned with an error."

---

### Post by liveN4HIM on 2006-11-15
maestrobwh1 thanks for sharing my pain. It's nice to know I'm not the only one out here who's clueless at times.:-k

---

### Post by taurus on 2006-11-15
Okay, what is the output of this command from a terminal?

```
id
```
You need to belong to groups adm & admin to be able to use sudo/gksudo...

---

### Post by adewale on 2006-11-17
am a newbie 2linux and also having the same problem even when i click on root shell it doesn't  come up. am getting a bit fed up 

does anyone know where i can select themes from i use kde

---

### Post by liveN4HIM on 2006-11-18
taurus  	Okay, what is the output of this command from a terminal?
  id

uid=1000(mark) gid=1000(mark) groups=4(adm),20(dialout),24(cdrom),25(floppy),
29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),106(admin),
1000(mark),1001(root)

Thanks again Taurus for taking the time to keep up with me and help.

---

### Post by liveN4HIM on 2006-11-27
To All:

Installed a newer version of kubuntu on a diff partition on my sys. Still kept the old one and am getting around to copying home over, then I'll probably erase the old sys and use the space for storage. New sys runs fine, no ru error mesgs, can even print with now hastles and I don't have to totally rely on scripting. Boy when you are out of habit with scripts and command line, you're outta luck...

Thanks again everyone who contributed.

---

### Post by kheaver on 2007-10-16
Hi all,

I'll tack my problem onto the end of this thread as I've got the same error message.

I use playing with virtualbox and used the command
sudo chown kim:kim /sda3/

sda3 is a partition that just has data on it.

Anyway now the wheels have fallen off and I get the error
**su returned with an error**
whenever I try anything that requires admin rights.
Also when I start up knetwork manager is not running, if I try manual config I get the su error, if I try to run Virtualbox I get a "Virtualbox kernal driver not installed" message.

If I start a terminal and type su, I get "Authenitcation failure", if I type 'Visudo" I get permission denied.

I'm guessing its a rights issue but have not idea what to do from here.

 I've used windows for 20yrs  but ubuntu for only a few weeks so if anyone can tell me what to type and where to type it, I'd be most grateful.

Regards,
Kim Heaver

---

