---
title: "Process Quits When Logging Out"
date: 2008-02-14
forum: General Help
---

### Post by MacAnthony on 2008-02-14
I have a script that is running on a desktop machine I don't use much. I would ssh to the box and run the script calling it with 'scriptname &' to get it to run in the background and then would log out. The script would remain running until the machine would shut off. I've since updated the machine to 7.10 and now I do the same process, but it seems that the script exits when I log out. How can I keep it running in the background after logout?

---

### Post by pointone on 2008-02-14
Just add the command you want to run at the end of the line when you start SSH.

```
ssh [user@]hostname [command]
```

```
man ssh
```

---

### Post by astrotech226 on 2008-02-14
Try using the "nohup" command.  It means it doesn't respond to the hangup signal.  I agree with you.  I've used different versions of Linux and sometimes I need it and other times I don't.  Here's an example of what you would run:

```
nohup scriptname &
```

---

### Post by MacAnthony on 2008-02-15
Thanks for the tips. I'm going to try both out since I wasn't aware of either feature, but the nohup sounds like it will be more what I'm looking for.

I'll try it out this weekend. Right now, I've been getting by with just leaving the ssh connection open, so I've been working around it.

---

### Post by Sokertes on 2008-02-17
You could also use screen

After you ssh into the machine type "screen"

Then run you command

kill the ssh connection

at any time if you want to ssh into the machine again to check your running script you just ssh into the machine and type "screen -r" which will reconnect to the last screen you ran the command.

I use it all the time and it works like a charm.


Sokertes

---

