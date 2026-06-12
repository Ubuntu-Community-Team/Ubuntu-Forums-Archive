---
title: "Launcher to Terminal command?"
date: 2007-02-11
forum: General Help
---

### Post by Gibbs on 2007-02-11
I have created a launcher on my desktop that I want to connect to the net.

The command is sudo ./dial. 

How can I add this command to the launcher so that the terminal opens and executes it?

---

### Post by laidback on 2007-02-11
Right click launcher (by which I assume you mean icon), select Properties, then select Launcher tab. Put your command in the command line. Don't think I've ever added a sudo here but it has to be worth a try.

P.S. No I do have one with sudo. but I haven't put ./ just the command, e.g. sudo lshw-gtk or in your case sudo dial. You'll be asked for the password.

---

### Post by Gibbs on 2007-02-11
dial isn't a global command, it's a file. I need to change to the /etc/init.d directory. If I enter "cd /etc/init.d sudo dial" it says "cd" is an unknown command...

Is there a way to make dial a "global command" (not sure if that's the right word)?

---

### Post by laidback on 2007-02-11
Don't think lshw-gtk is a global,  it's just an apps that I installed via synatptic.
How about sudo /etc/init.d/dial then?

---

### Post by Gibbs on 2007-02-11
Thanks for your help so far. Haven't got anything working yet though. I've used a lot of variations, I either get "Permission Denied" with things like ```
sudo "/etc/init.d/dial"
``` or it simply won't do anything...

---

### Post by laidback on 2007-02-11
Oh dear, never mind.
echo $PATH will probably show you that /etc/init.d is not in you path, so I guess it's not searched when you issue the command dial, unless you're in the directory itself.

I'm not that familiar with all this but could you:-

add /etc/init.d to your path?
copy dial to the usr area, /usr/local/..., or your own area.

sorry I cannot be more help, i'm still learning too.

---

### Post by koenn on 2007-02-11
try

```
gksu /etc/init.d/dial
```
gksu is the GUI equivalent of sudo - it's the thing that gives you the "enter password for admin task" dialog 

is 'dial' a script, something you made ? 
if so, you need to make it executable : 
```
chmod 775  /etc/init.d/dial
``` (or file properties : permissions)

---

### Post by koenn on 2007-02-11
or if you want to see what's happening, try a launcher that does
```
xterm -e 'sudo /etc/init.d/dial'
```

---

### Post by Gibbs on 2007-02-11
Brilliant thank you! :)

---

