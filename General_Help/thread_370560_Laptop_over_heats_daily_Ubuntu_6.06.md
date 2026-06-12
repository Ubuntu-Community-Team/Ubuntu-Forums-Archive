---
title: "Laptop over heats daily Ubuntu 6.06"
date: 2007-02-25
forum: General Help
---

### Post by jrattner on 2007-02-25
At first it was just occasional, but now it seems like my laptop overheats everyday.  What happens is all of sudden X goes down, and I brought the terminal and greeted by the wonderful phrase:  System has reached critical temperature (X degrees) shutting down now.  How can I diagnose this problem, and see where the problem is coming from?  This did not happen to me until I started using 6.06. :(

---

### Post by IcemanV9 on 2007-02-25
It could be related to the kernel. My HP laptop (686 kernel) used to be overheated every single day. -27 is the best stable one. -28 is the newest one and it seem to be stable (so far).

---

### Post by nanotube on 2007-02-26
you should install some temperature monitoring utilities, to see how your temperature behaves. also put up the cpu usage applet in your panel, so you can notice when something is eating your CPU.

for a tutorial on how to monitor temperature on a dell, check out my customization guide in the sig (go to the temp and fan sensors page). if you have a non-dell, you can do very similar things, but with some variations. generally, check out the 'sensors-applet' package and website.

i'd generally say that maybe it's some runaway process that keeps eating 100% of cpu. check your process list ('top' from commandline, or just use the gnome system monitor for a gui version).

---

### Post by h0bbe on 2007-05-12
I had the same problem several times on my HP omnibook xe4500 in Xubuntu Feisty Fawn 7.04 a couple of days ago, luckily it hasn't happen again since then. But I haven't change a thing though...

The solution cant just be to monitor the problem (which I so far haven't managed to do yet: [http://ubuntuforums.org/showthread.php?p=2641192#post2641192](http://ubuntuforums.org/showthread.php?p=2641192#post2641192))!? Is there something you can to do really avoid it? It never happened to me before in Suse 9.2 or Ubuntu 5.04-6.10.

---

### Post by Brucevdk on 2007-05-12
I apologize if I'm echoing what others have said (such as nanotube) but I wanted to share my personal experience related to the issue at hand.

Even though my CPU hasn't reached critical temperature (97C) it has certainly reached high levels when a process utilizes the CPU intensively for longer periods. I don't consider this abnormal behavior, the situation isn't any different when using Windows XP.

I personally disabled/removed Beagle since every time it started indexing it utilized 99% of the CPU for quite a while and would bring the temperature up to 85C >. I also noticed an Amarok plugin written in Python which was causing havok. To see which process is using the CPU the most use the command "*top*" in the terminal or use the *gnome-system-monitor*. You can also use *ps auxwww --sort %cpu* which will immediately tell you the full path to the executable.

You can monitor the CPU temperature using the command "*acpi -t*" in the terminal or install the *sensors-applet* (sudo apt-get install sensors-applet) to get [a little icon on your panel]("http://sensors-applet.sourceforge.net/images/screenshots/001-icon-with-notification.jpg"). 

You can also use the [GNOME Frequency Scaling Monitor applet]("http://lgo.0d.be/cpufreq-applet/2.18/cpufreq-applet-introduction.html.en") to scale the CPU frequency manually (so you can for example turn it down a notch when you start gaming). You can allow any user to scale the frequency using this applet by setting the SUID bit on cpufreq-selector (use *sudo dpkg-reconfigure gnome-applets* to do this).

Use the "Add to Panel" functionality to add these applets.

Hopefully this will help you find the culprit or at least prevent it from occurring too often, if not then as others have pointed out this might be caused by something a little bit deeper.

---

### Post by robin.w on 2007-05-19
But what if the critical temperature has occurred directly after switch-on my laptop? I couldn't boot Kubuntu 7.04 so I was running Windows and everything was fine there (actually just Win sucks :) ). After few minutes I tried reboot my laptop and no problem. Strange, isn't it? 
My laptop - Compaq Presario M2000, CPU AMD Turion, running temperature is approx. 48-50C.

---

### Post by ozorba on 2007-05-19
You need to check which process causes the CPU to run at full speed continiously.

You can use top command from a shell window. 

I have had a similar problem and discovered that gnome-cups-icon was the culprit. I renamed it in /usr/bin/ directory and it all went cool.

---

