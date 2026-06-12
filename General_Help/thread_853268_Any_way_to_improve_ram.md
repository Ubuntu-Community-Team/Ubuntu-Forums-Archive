---
title: "Any way to improve ram?"
date: 2008-07-08
forum: General Help
---

### Post by wbutchart on 2008-07-08
Hi i noticed on my system monitor thing that my RAM doesnt drop below 90%.  I think this is what is slowing my system down.  No matter what request i make the cpu doesnt go above 50% it seems that the RAM is so poor the cpu speed is effected.

Is there any programs i can add to make the ram more efficient or to disable some of the things that are taking it all up?

Thanks :)

---

### Post by snowpine on 2008-07-08
> **wbutchart said:**
> Hi i noticed on my system monitor thing that my RAM doesnt drop below 90%.  I think this is what is slowing my system down.  No matter what request i make the cpu doesnt go above 50% it seems that the RAM is so poor the cpu speed is effected.

Is there any programs i can add to make the ram more efficient or to disable some of the things that are taking it all up?

Thanks :)

Yes, but we can help you better if we know how much RAM you have, which OS you're running, etc. :)

Going into the System Monitor will give you a good idea of which processes are using the most RAM.

Also, buying more RAM is relatively inexpensive and a great way to boost your performance.

---

### Post by Elfy on 2008-07-08
> Hi i noticed on my system monitor thing that my RAM doesnt drop below 90%. Do you know that linux uses ram differently than win - it uses it up - mine rarely drops below the same unless I look just after I've booted.

Run free -m in a terminal and see what that says.

             total       used       free     shared    buffers     cached
Mem:          1265       1197         67          0         54        888
-/+ buffers/cache:        255       1009
Swap:          956          0        956

---

### Post by wbutchart on 2008-07-08
> **snowpine said:**
> Yes, but we can help you better if we know how much RAM you have, which OS you're running, etc. :)

Going into the System Monitor will give you a good idea of which processes are using the most RAM.

Also, buying more RAM is relatively inexpensive and a great way to boost your performance.
I think i have 256 mb ram, but the swap thing is 700ish....?

I am running the latest ubuntu version 8.04.1.

I have noticed that my girlfriend (i installed ubuntu on her computer last night) her computer runs ubuntu super quick, her computer is pretty old and im sure my laptop at least matches it but my laptop runs quite slow.

---

### Post by snowpine on 2008-07-08
> **wbutchart said:**
> I think i have 256 mb ram, but the swap thing is 700ish....?

I am running the latest ubuntu version 8.04.1.

I have noticed that my girlfriend (i installed ubuntu on her computer last night) her computer runs ubuntu super quick, her computer is pretty old and im sure my laptop at least matches it but my laptop runs quite slow.

Ubuntu will never run *quickly *on 256mb ram; I would upgrade to 512mb or give Xubuntu a try.

The only suggestion I can give is to go to System > Sessions and disable any sessions you don't need, like the Tracker search history and Bluetooth for my needs (yours may vary). 

Also you can try lighter weight applications (Abiword instead of OpenOffice, Epiphany or Kazehakase instead of Firefox, etc.) and try not to have too many applications running at once.

But again, you are using the bare minimum of RAM for Ubuntu and it is never going to be "speedy."

---

### Post by wbutchart on 2008-07-08
Can i add more ram to a laptop?.  If i could i would happly add more, i would like to see the system run quicker :)

---

### Post by Titan8990 on 2008-07-08
You can add RAM to all laptops but the ease differs. Look at the bottom and see if there is a spot to open up an insert new RAM.

Older laptops can require that you remove the keyboard which can be more trouble than it is worth.

---

### Post by Topsiho on 2008-07-08
I put more ram into one of my laptops once, and found that ram in a laptop is not the same as you put into a desktop. That's point one. I forgot how to call it, the form factor is different. Second: what precise type of ram you need depends on the laptop. What I am saying is that you can not put any ram into any laptop. Probably you should have a look in the manual.

It is true that 256 MB is the bare minimum, 512 is what I have, and 1024 is far better.

The reason that your laptop is slow is also possibly that your mere 256 KB of ram is ***shared with your video card***, 48 MB or so, and then you have a problem indeed running Gnome or KDE at all.

Topsiho

---

### Post by Herman on 2008-07-08
:) It's a good idea to google for the owner's manual for your brand and model of computer. The manual will probably have some useful instructions about how to upgrade your RAM modules. You might already have a manual somewhere if you can find it. Likely it's a .pfd file.
Your motherboard manual will tell you what kind of RAM modules you can use and what is the maximum amount of RAM your motherboard can handle. If you are already running the maximum that the motherboard was designed for, adding more RAM won't help. If you can add more RAM though, it will probably help a lot. It's about the best way to improve your computer's performance.

Generally, if it's a notebook or laptop that's relatively modern, when you turn the laptop upside down, there will probably be a hatch on the bottom you can open to see your RAM modules. 
You may not need to touch anything yet, but you might need to copy down the part numbers on the stickers on your existing RAM modules to help get the right new modules to put in. Or, your computer store man can look it up based on your make and model number, but it's often helpful if you know what kind of RAM you have already.

Once you're home again with the right RAM module, placing it in isn't all that much harder than changing a light bulb. 
You should not touch them without removing the laptop's battery first, of course you would already have unplugged the laptop too. and wait a minute for the residual power in the motherboard to dissipate.
You should use an ESD wrist strap if you have one, or if you haven't got one, at least touch some metal part of the laptop's frame to equalize your body's static electricity with the laptop before touching any parts connected to the laptop's innards.
Then when you are ready, place your new RAM module in it's slot.  Your manual is worth referring to if you can, it may be that the RAM module needs to be placed in at an angle and then pressed down to clip it in or something like that. 

When you're finished, close the hatch, put your battery back and boot your laptop, it should automatically detect the extra RAM and use it. :)

---

### Post by stek79 on 2008-07-08
> **wbutchart said:**
> Hi i noticed on my system monitor thing that my RAM doesnt drop below 90%.  I think this is what is slowing my system down.  No matter what request i make the cpu doesnt go above 50% it seems that the RAM is so poor the cpu speed is effected.

Is there any programs i can add to make the ram more efficient or to disable some of the things that are taking it all up?

Thanks :)

Hi,
  the counter Memory Utilization is not a useful one to establish if you're suffering a memory shortage.

For example, take a look at my mem util:

Linux 2.6.24-19-generic 
  
 
10:35:01 AM %memused
10:45:01 AM 97.93
10:55:01 AM 89.26
11:05:01 AM 96.86
11:15:02 AM 97.02
11:25:01 AM 96.48
11:35:01 AM 95.74
11:45:01 AM 96.15
11:55:01 AM 95.48
12:05:01 PM 96.81
12:15:01 PM 95.05
12:25:01 PM 95.07
Average: 22567 24718
  
09:45:03 PM %memused
09:55:01 PM 97.86
10:05:01 PM 97.62
10:15:01 PM 96.55
10:25:01 PM 98.26
10:35:01 PM 95.24
10:45:01 PM 95.66
10:55:01 PM 96.26
11:05:02 PM 96.91
11:15:01 PM 97.62
11:25:01 PM 88.45
11:35:01 PM 90.32
11:45:01 PM 92.22
11:55:02 PM 97.26
11:59:01 PM 97.56

As you can see it is far over 90% but the system is no way slow. This is because this counter consider all RAM contributions, not only the applications. Don't worry about that.

So you should NOT use it to identify memory shortage. Actually 256MB of RAM can be a small quantity, but I think with a bit of tuning you can actually have a usable system.

From my experience the most memory hog app is firefox. To do a nice list of the most demanding apps, you can use System Monitor. Open the Processes tab. Then Edit -> Precerences and from the metric list add Writable Memory. Then sort the processes according to this counter, which is a REAL measure of memory utilization. 

Once you have this ranking, start from the top and try to eliminate every app you don't need. The place to start, as others have suggested, is your Preferences->Sessions. Then the unneeded services (Admin-> Services).

If you post a screenshot of your memory ranking, along with a 'free -m' output as suggested, we can help you more.

---

### Post by sayakb on 2008-07-08
@wbutchart
You may install openbox (window manager)
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/) (what i used)
[http://ubuntuforums.org/showthread.php?t=192106](http://ubuntuforums.org/showthread.php?t=192106)

Openbox is **much** liter than gnome and you can add only the things you need to startup. I got an old rig working fairly fast with just 76MB of RAM usage :)

---

