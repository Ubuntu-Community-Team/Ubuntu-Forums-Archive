---
title: "Super Noob Question - where do the files go?"
date: 2006-12-09
forum: General Help
---

### Post by randalotto on 2006-12-09
Well, I'm brand new to Ubuntu (and Linux), and I'm trying to get accustomed to all the new things... 

I cannot, for the life of me, figure out where the files i need are...

I installed on a Dell Laptop, and everything is working straight out of the box, but i want to change the cpufreqd settings so that the CPU runs full speed when hooked up to AC power.

Where the heck is the config file? i've found some documentation showing what changes i need to make to the cpufreqd.conf file, but i can't find the damn thing.

(and if i need to create the file, how and where do i do so?)

thanks in advance

---

### Post by pay on 2006-12-09
Try using the find command```
sudo find / -iname cpufreqd.conf
```All that means is find the file "cpufreqd.conf" in the directory /

---

### Post by randalotto on 2006-12-09
I got nothing... 

went through a bunch of /proc/xxxx/ directories and said "no such file or directory"

---

### Post by randalotto on 2006-12-09
A further part of this question:

i was just looking at something, and it gave me a choice to "pick the program blah blah blah" and had the explorer-type window...

WHERE ARE THE PROGRAMS???

---

### Post by K.Mandla on 2006-12-09
Sometimes configuration files are inside your home directory, but they're hidden -- they start with a dot (.). If you use a file manager you can usually tell it to view hidden files. From the terminal

```
ls -la
```
will show all the files, hidden or not, in the directory you're in.

---

### Post by drphilngood on 2006-12-09
Enter this in a terminal and you can control your cpu speed from a gnome applet:
 
```
sudo chmod +s /usr/bin/cpufreq-selector
```

Just see here:

[cpufreq scaling applet: manual scaling]("http://ubuntuforums.org/showthread.php?t=214007")

Hope this helps!

---

### Post by po0f on 2006-12-09
randalotto,

I'm pretty sure cpufreqd.conf lies somewhere under /etc.  Try running this command from a terminal:
```
[FONT="Courier New"]$ locate cpufreqd.conf[/FONT]
```

---

### Post by pay on 2006-12-09
From here [http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml) it says 
> cpufreqd can be configured by editing /etc/cpufreqd.conf. The default one that ships with cpufreqd may look a bit confusing. I recommend replacing it with the one from former Gentoo developer Henrik Brix Andersen (see below). Please notice that you need cpufreqd-2.0.0 or later. Earlier versions have a different syntax for the config file.

Code Listing 3.4: /etc/cpufreqd.conf (cpufreqd-2.0.0 and later)

[General]
pidfile=/var/run/cpufreqd.pid
poll_interval=3
enable_plugins=acpi_ac, acpi_battery
enable_remote=1
remote_group=wheel
verbosity=5
[/General]

[Profile]
name=ondemand
minfreq=0%
maxfreq=100%
policy=ondemand
[/Profile]

[Profile]
name=conservative
minfreq=0%
maxfreq=100%
policy=conservative
[/Profile]

[Profile]
name=powersave
minfreq=0%
maxfreq=100%
policy=powersave
[/Profile]

[Profile]
name=performance
minfreq=0%
maxfreq=100%
policy=performance
[/Profile]

[Rule]
name=battery
ac=off
profile=conservative
[/Rule]

[Rule]
name=battery_low
ac=off
battery_interval=0-10
profile=powersave
[/Rule]

[Rule]
name=ac
ac=on
profile=ondemand
[/Rule]

Now you can start the cpufreqd daemon. Add it to the default and battery runlevel as well. So to edit that file execute ```
sudo nano /etc/cpufreqd.conf
```

---

### Post by randalotto on 2006-12-09
Wow. You guys are awesome. Thanks for all of the quick responses. 

I used drphilngood's solution, which is actually perfect - control of the speed plus the ability to change the active profile. 

I think in general, i need to get more comfortable with all of the terminal commands. Is it normal to just type stuff in like "nano" or "get-apt" without understanding precisely what it means or does? 

anyway, i'm still not quite sure about where files go - for example, i downloaded k3b, a cd burning tool - where is the actual program file?

Like I said, a "choose the program..." thing came up, and I have no idea where the file would be.

---

### Post by HereInOz on 2006-12-09
You get a lot of the basic utility files in /bin - things like gzip and other basic linux files.

You will then find the higher level utilities in /usr/bin, and programs usually (I emphasize usually, as it is not always the case), reside in /usr/share.

Plugins and library files usually (there's that word again) find their way to /usr/lib whereas the basic system libraries live in /lib.

Program configuration files usually (damn!!) live in your home folder in a hidden folder starting with a dot.  Open your Home Folder and then do Ctrl-H and it will show you the hidden files.

Not the full bucket by any means, but I hope it helps in some way.

---

### Post by drphilngood on 2006-12-09
This should answer most of your questions:

[CommandLineBeginners]("http://doc.gwos.org/index.php/CommandLineBeginners")

but post back if you still have questions.

Please edit the thread title with the word ¨resolved¨ when joy is achieved.;)

---

### Post by 3rdalbum on 2006-12-09
With the majority of programs, there's no need to specify an actual path. In your case, you don't need to try navigating the filesystem, looking for the actual k3b executable - in the "command" field, just type:

```
k3b
```

K3B has been installed into a directory where the system knows where to find it. That's how this magic works.

---

### Post by pay on 2006-12-09
The executables for programs go into```
/usr/bin
```

---

