---
title: "Internet Traffic Meter"
date: 2014-06-20
forum: General Help
---

### Post by david228 on 2014-06-20
Is there an app that would do roughly the same as the Windows versions of DU Meter or Network Traffic widgets? I'd like a programme that gave me a graphical representation of data coming and going over the internet (or a Network if I get around to figuring out how).

I did look at Wireshark and Etherape but neither seemed to do this, or if they can, then i didn't figure it out.

---

### Post by slickymaster on 2014-06-20
[ipac-ng]("https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals") is aimed at people with a small home network, who want to monitor the amount uploaded / download from the internet but not the local traffic on the LAN.

---

### Post by ajgreeny on 2014-06-20
It may not do exactly what you want, but I use vnstat and output the data from that to my conky window on the desktop.

It monitors only this one machine, not the whole network, but that is all that I personally need.

See screenshot for what I see on my desktop (alongside a lot of other data as in second screenshot)

---

### Post by david228 on 2014-06-22
> **ajgreeny said:**
> It may not do exactly what you want, but I use** vnstat **and output the data from that to my **conky window **on the desktop.

It monitors only this one machine, not the whole network, but that is all that I personally need.

See screenshot for what I see on my desktop (alongside a lot of other data as in second screenshot)


Thanks **ajgreeny**, it does look the sort of thing I am after, however, I am left a little confused. I am very new to Linux, and am still working my around the Unity Desktop, and yet to venture into the CLI world. I don't actually understand what you replied. 

Do I download both Vnstat and Conky from the Ubuntu Software Centre and run them on the desktop? Or this something that requires the CLI? Or does it look like I don't know enough yet if I don't fully understand you, and therefore should be avoiding this project at present.

---

### Post by deadflowr on 2014-06-22
As far as I can tell both conky and vnstat are cli.
Though I guess there are attempts to get a gui for conky, like conky manager.
Basically you install the packages conky-all, and vnstat.
Then what you would need to do is create a basic conkyrc file and add vnstat to it.

Beware, though, conky is a giant rabbit-hole.
It's highly customizable and you can tweak to your hearts content.
[here's some more on conky]("http://conky.sourceforge.net/documentation.html")

And here are a couple super long conky threads
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
and
[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)
Hopefully this will give you some tips and tricks on what you need to do to set up a conky to your liking.
Best of luck.

---

### Post by ajgreeny on 2014-06-23
Yes, deadflower is correct, once you start playing with conky, you will either get terribly frustrated and give up quickly, or as in my situation, begin simply and then over the years add more and more code to the configuration file used to get the full display you see in my screenshot.
Mine is still relatively simple compared to some others I have seen, and you may find the two large threads linked to rather too large and unsearchable to be very useful.  They are, nevertheless, a handy reference to have available and look through, and then copy parts of the config files relative to what you want to show.

Just in case you find it useful I have added my own .conkyrc file to this post which you are welcome to use,though some parts of it may not be appropriate for your setup.  Just open the attachment and save it in your home as a hidden file named .conkyrc

The network monitor package I use, vnstat, is basically a command-line application, but I use other command-line variables in the .conkyrc file to take the vnstat output and show it on my screen. See the lower part of the file beneath the word TEXT for the details of what shows in the window on screen.

Good luck!

---

### Post by LastDino on 2014-06-23
I use ''system load indicator''. It puts nifty little graph window of resource usage in top bar (Dunno what to call it, its name changes from DE to DE) and if you click on it, you will see net upload and download in live.

It is available in Ubuntu software centre. Just install and no need to do anything else.

---

### Post by Habitual on 2014-06-23
> **david228 said:**
> Do I download both Vnstat and Conky from the Ubuntu Software Centre and run them on the desktop? Or this something that requires the CLI? 
Have a look at [https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals#vnstat](https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals#vnstat)

---

### Post by david228 on 2014-06-23
Thank you all. It both gives me leads to try and leaves me terrified. Clearly I need to start some serious reading and research, but the whole concept sounds like it could be a worthwhile project to play with. Alas, I am at work right now but will make a start from home tomorrow night. In the meantime I'll try some reading between work tasks.

---

### Post by sandyd on 2014-06-23
Also check ntop (the version in the repos). You can access it from a browser which is a plus

---

### Post by col48 on 2015-02-15
I haven't got conky, but have created a tiny shell script run manually from time to time which uses vnstat to tell me how much traffic there has been today (and each day over the last month) and a total for the last month (and monthly over the last year).  No fancy graphics, and the window closes after 30 seconds, enough time for me to see what I want to see.

```
vnstat -d ;sleep 2
vnstat -m ;sleep 30
```

This lives in an executable shell file netmon.sh which is run from a panel icon with the launcher property "Application in Terminal".

This tells me about 
A. traffic to/from the computer to the internet
B. traffic to/from the computer to other network devices
without separating the two.

It does *not* tell me about
C. traffic to/from other network devices and the internet
D. traffic between other network devices.

What I'd really like to know is A+C, which is my internet usage - what my ISP may be bothered about.  **Is there anything which will do that for me?**  Icing on the cake would be something which would break this down by target website, but that may be too much to hope for!  As far as I can see from the brief descriptions, neither ntop nor darkstar will distinguish between A and B above, never mind C or D!

---

