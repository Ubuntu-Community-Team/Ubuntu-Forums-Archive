---
title: "suspend"
date: 2022-09-17
forum: General Help
---

### Post by davidwillis on 2022-09-17
when I suspend my computer, it comes back with just text on the screen (what shows on the screen before the graphical display.  However it is frozen, and I can't even ctl+alt+f1 does not work.   I just have to restart the computer.  I didn't think to take a picture of the screen.  I am not sure how to figure out why that is happening.

---

### Post by TheFu on 2022-09-20
Look at the system logs.  Some hardware needs to be told, explicitly how to handle power going away and power coming back.  The system logs probably will have the hardware listed.  

It has been some time since I had to do this.  I use a USB3 to GigE adapter for my laptop, so the solution at suspend was to tell the adapter to behave like it was unplugged and at power up from suspend, act like it was inserted.    That handled it.  I think all the internal hardware on the laptop that already worked (i.e. not the fingerprint reader), handled standby correctly.

BTW, the exact release and DE used could matter, but I don't know. I run a Frankenstein install (yes, I know Frankenstein was the Doctor's name, not the monster's). ;)

Another option is to run inxi -F before and after the standby. Save the result for both to text files and compare those results.  inxi is a console tool, so at standby, you can hopefully switch to a different console, login, and run the command.  If not, you could try using ssh from another system that almost always works, since it isn't tied to any graphics at all.  The key point is to get a list of hardware before and after standby so it can be compared.

There are lots of comparison tools. I like 'meld', if I have a GUI, but will use 'sdiff' if I don't.  Use any tool you like ... or do it manually, if you like punishment.  If the inxi output isn't different and you are 100% positive you have different saved files, then you'll want to go into commands that do more details for the hardware reports, like 'lspci -vvv' and 'lshw' and perhaps 'lsusb -v'.  Comparing those will probably be painful. IDK, I've avoided it.

---

### Post by davidwillis on 2022-09-21
> **TheFu said:**
> Look at the system logs.  Some hardware needs to be told, explicitly how to handle power going away and power coming back.  The system logs probably will have the hardware listed.  

It has been some time since I had to do this.  I use a USB3 to GigE adapter for my laptop, so the solution at suspend was to tell the adapter to behave like it was unplugged and at power up from suspend, act like it was inserted.    That handled it.  I think all the internal hardware on the laptop that already worked (i.e. not the fingerprint reader), handled standby correctly.

BTW, the exact release and DE used could matter, but I don't know. I run a Frankenstein install (yes, I know Frankenstein was the Doctor's name, not the monster's). ;)

Another option is to run inxi -F before and after the standby. Save the result for both to text files and compare those results.  inxi is a console tool, so at standby, you can hopefully switch to a different console, login, and run the command.  If not, you could try using ssh from another system that almost always works, since it isn't tied to any graphics at all.  The key point is to get a list of hardware before and after standby so it can be compared.

There are lots of comparison tools. I like 'meld', if I have a GUI, but will use 'sdiff' if I don't.  Use any tool you like ... or do it manually, if you like punishment.  If the inxi output isn't different and you are 100% positive you have different saved files, then you'll want to go into commands that do more details for the hardware reports, like 'lspci -vvv' and 'lshw' and perhaps 'lsusb -v'.  Comparing those will probably be painful. IDK, I've avoided it.

Thank you for your reply.  Do you know what logs to look at specifically?  I can't switch to a console after I suspend, I tried, but it did not work.

---

### Post by TheFu on 2022-09-22
> **davidwillis said:**
> Thank you for your reply.  Do you know what logs to look at specifically?  I can't switch to a console after I suspend, I tried, but it did not work.

Then you'll have to look at them after a reboot. I'd use 'journalctl' to specify the time period, say 2 minutes before the lockup. Does ssh not work? That would be easier.

When looking at log files, I search them all. To get started:
```
$ sudo egrep -i 'err|warn' /var/log/*og | less -X
```
That will show the filenames with errors and warnings.  Note the timestamp, so when you go into the specific files, you can get to those lines quickly.

Finding and reviewing logs is a basic skill.  You can google for more tips.

---

### Post by davidwillis on 2022-09-22
It sounds like it is more work than it is worth to figure out.   It seems like ubuntu worked better years ago than it does now.  I am not sure if it is ubuntu, or hardware is harder to work with, but things used to work, without so much effort.

---

### Post by TheFu on 2022-09-23
> **davidwillis said:**
> It sounds like it is more work than it is worth to figure out.   It seems like ubuntu worked better years ago than it does now.  I am not sure if it is ubuntu, or hardware is harder to work with, but things used to work, without so much effort.

Could be a 3 minute fix. Depends on YOUR hardware, as always.  If you don't look, you'll never know that 1 setting is the issue on your system. If you want things to just work, buy hardware that comes with Linux already installed.   System76 and Dell sell some. There must be others.

---

