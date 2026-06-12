---
title: "Why isn't Chrome getting killed?"
date: 2015-03-04
forum: General Help
---

### Post by Sunsawe on 2015-03-04
Hi everyone,

I'm facing a problem which is rather annoying now.
First, I have to confess being that guy who always has at least three browser windows opened with multiple tabs in them (dozens) ):P
I'm used to my Linux box being able to handle it \\:D/ . At worst, the browser would just be killed by the system when it would consume too much memory. Sometimes, the operation could be painful, taking like 10 to 15 seconds of total freeze and the browser would die, leaving me free to close few things before restarting it.

But since I upgraded from 12.04 32bits to 14.10 64bits (home preserved, system mount replaced), it is not the case anymore. Now, when the system runs out of memory (I guess it is what is happening) it slows down to a point of non usability and... that's it :confused: . The mouse pointer starts to move at about 3px/min speed, the rest of the display is never updated. When I switch to the terminal (ctrl-alt-f1), it takes time, prompts me for the user name but then times out before even prompting me for the password. Once, I left it like that for 30 min and nothing changed. Needless to say that going back to the UI is impossible. ](*,)

As a consequence, I have been hard rebooting my box in the past month more than regular reboots in the past year or something. Before launching anything, I need to think about if there is enough memory left or it might force me to reboot. I almost started to have nightmares about blue screens... :frown:

So why is this happening now? Is there any settings built in which I can modify to instruct the system to sacrifice the browser first in case of memory need?
Maybe an additional package? Anything...

For indication, my system runs on 4 GB of Ram and 4 GB of swap on SSD.

Cheers!

---

### Post by Al1000 on 2015-03-04
Conky system monitor is a great way of keeping an eye on how much RAM and swap your system is using.

I suspect that as you were previously able to close Chrome, your system hadn't run out of memory, as there was evidently enough available for it to run the command to close Chrome. I once ran out of memory on a laptop with 768MB of RAM and a 1GiB swap partition, and I wasn't able to close anything.

But now that you have an operating system that uses more memory than the one you had before, perhaps it is now running out of memory, and that is why you are unable to close Chrome.

To be able to continue to use internet browsers with your new operating system, in the way that you did with the old one, it looks like you need more memory.

---

### Post by meanmrmustard on 2015-03-04
I've had similar issues with my box with 14.04 on an AMD Phenom X4 965 and an OCZ Vertex4 SSD with 8 GB of ram and like the OP I'm usually using at least two browsers with multiple tabs.
I recently discovered [zram-config]("http://www.webupd8.org/2011/10/increased-performance-in-linux-with.html") (available in repos).
It's too early to say if it's resolved the issue completely but it has made a big difference at least.
Might be worth a try.

---

### Post by Sunsawe on 2015-03-04
Thank you for the answer.
@Al1000 I didn't close Chrome myself. It would get killed by the system. That's what I'm talking about. I would want the system to automatically kill processes when they consume too much ram.

I'll check the zram even if it is somewhat different to what I wanted.

---

### Post by raptir on 2015-03-04
I'm very surprised you run out of RAM with 4GB + 4GB Swap. I think the first step would be to confirm that's actually what's happening. Run a system monitor (weather it's conky, top in a virtual console, gnome system monitor itself) and see if you are indeed running out of memory at the that you experience the slowdown. The base system should be using less than 1GB so your browser tabs would need to be taking up 7GB of memory to cause a real out of memory scenario.

Edit: Also, I don't think I would recommend zram in this situation. Zram is really beneficial if you do not have a swap partition or if your swap partition is on a slow HDD. Since you have a SSD and a good bit of RAM I don't think you'd see much improvement. You could try zswap but I still thing 8GB of total memory + swap should be plenty without resorting to that.

---

### Post by v3.xx on 2015-03-04
I think 'raptir' is on to something.  Where is that 4G going to?  Does the system see 4G?
```
free -m
```

---

### Post by Sunsawe on 2015-03-10
Hello guys,

Sorry for the delay, I have been very busy. While we were talking last time, I was as well in the process of moving partitions to increase the swap to 6Gb. Since then, I have had no issues with the system anymore. But for the sake of testing, this is the output of ```
free -mh
``` when I boot up:
```

             total       used       free     shared    buffers     cached
Mem:          3.8G       1.0G       2.8G        18M        43M       395M
-/+ buffers/cache:       564M       3.2G
Swap:         6.1G         0B       6.1G

```
after launching the browser (and the tabs in it):
```

             total       used       free     shared    buffers     cached
Mem:          3.8G       3.3G       515M        54M       8.3M       200M
-/+ buffers/cache:       3.1G       724M
Swap:         6.1G       826M       5.3G

```
and in usual use:
```

             total       used       free     shared    buffers     cached
Mem:          3.8G       3.7G       103M        95M       9.9M       270M
-/+ buffers/cache:       3.4G       383M
Swap:         6.1G       2.2G       3.9G

```

I guess it says that there is still some swap left and still more than the 2Gb I added but then... what was the issue if it wasn't that?

---

### Post by v3.xx on 2015-03-10
You still have something eating up your ram.  Take a look at system processes.

Open your 'System Monitor' and click on Processes.  Then click on Memory to bring up the top users.

What ya got?

---

### Post by Sunsawe on 2015-03-12
I'm actually starting to think that you are seriously right.
I looked at the processes and was surprised to see that even with all my tabs, there is 1 chrome process which eats less than 350 Mb, then VirtualBox with less than 300 Mb!
So this is the list about in count of process:
1 at less than 350
1 at less than 300
3 at less than 200
5 at less than 150
12 at less than 100
20 at less than 50
20 at less than 25
And some under 1

That's a top max of 4.7Gb and with a very large margin as when I say less than 100 for example, that includes many at 52 and counted 100. 4.7Gb Absolute top while the resources tab reports... 8.6 Gb Ram + Swap!!!
Where is my memory going? Nothing listed in the System Monitor justifies that.

---

### Post by v3.xx on 2015-03-12
Wow, you used up your 4G.

I have a lot going on too, but not getting anywhere near 4G.
[ATTACH=CONFIG]260585[/ATTACH]
Why do you have so many processes running?

Could you post a pic of the processes?

Also, try chrome with extensions disabled.
```
google-chrome --disable-extensions
```

---

### Post by Sunsawe on 2015-03-13
I'm going to try to do that, but I can already tell you that I have MANY more chrome processes then you do....
38 to be exact...

---

### Post by buzzingrobot on 2015-03-13
> **Sunsawe said:**
> 
38 to be exact...

That's a lot of processes, although I recall that a single instance of Chrome with no tabs open shows up in system monitor as several separate processes. 

In any case, it's the memory in use, not the number of processes, that's the issue for you.

As suggested, run Chrome with no extensions, addon, apps, etc., to try to determine of the browser itself or something added to it is the problem.  If there's an improvement, re-enable them, one at a time, looking for one that triggers this excessive memory use.  

Just to be sure, since you updated from a 32-bit release to a 64-bit release, did that go well?  Are you sure you're running a 64-bit kernel? ("uname -a" in a terminal). Was 32-bit Chrome replaced by 64-bit Chrome? Presumably the memory management in the two different versions is different.

[EDIT:  Very roughly speaking, swap works by moving a chunk of code from RAM to the swap partition in order to free a bit of RAM space for a process that's made a memory request that cannot be fulfilled. When the chunk of code that's written to the swap partition is needed by the process that owns it, it's read from the partition and moved back into memory.  If memory needs to be freed to make room for *that* chunk, then something else is written from RAM to the swap partition.

So, when RAM is full and swap is full or nearly full, it's normal for the system to become dramatically slower because it is spending most of its time writing and reading data to and from the swap partition.  That accounts for slow video, slow mouse, etc., because their support code gets swapped, too.  E.g., you move the mouse and the code to respond to it needs to be read from the swap partition.]

---

### Post by Sunsawe on 2015-03-13
well... This is the output of free -mh right after boot and launching:
```
google-chrome --disable-extensions
```
```
             total       used       free     shared    buffers     cached
Mem:          3.8G       3.7G       114M        61M       1.8M       152M
-/+ buffers/cache:       3.5G       268M
Swap:         6.1G       578M       5.5G

```

And the output of uname -a:
```
Linux uHP 3.16.0-31-generic #43-Ubuntu SMP Tue Mar 10 17:37:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

The "migration" was made by erasing the / partition, keeping only the /home partition so I would expect it to be fully 64bits.
So why is chrome eating up so much memory if it isn't extensions?

---

### Post by v3.xx on 2015-03-13
```
killall chrome
```
Should clean out all chrome processes and clear the memory.

As for whats going on, I'm not sure.  If not already tried, I would reinstall chrome, but maybe buzzingrobot has some ideas.

---

### Post by buzzingrobot on 2015-03-13
> **v3.xx said:**
> ```
killall chrome
```
Should clean out all chrome processes and clear the memory.

...maybe buzzingrobot has some ideas.

Sorry.  Fresh out. :( 

If Chrome with no extensions, plugin, etc. enabled gobbled up almost all of RAM, it would be a popular topic.

(BTW, to address the question in the title of the thread, apps don't "get killed" when swap is used. They might crash, possibly for a related reason, but the purpose of swap is to keep things working when RAM is insufficient.)

---

### Post by v3.xx on 2015-03-13
Found this

[https://code.google.com/p/chromium/issues/detail?id=393395](https://code.google.com/p/chromium/issues/detail?id=393395)

---

### Post by Sunsawe on 2015-03-16
Well,
It seems that this is what my computer is suffering from... The solutions proposed didn't workout in my case. So I went for the final one... I was thinking about doing that already but..after so many years..
Well I migrated my opened tabs to Firefox, one by one. Then rebooted and launched Firefox only. The result is a "no contest": 1.6Gb of Ram used. That's it.

So, unless you guys have other suggestions, I guess it will be time to say bye to Chrome.

---

### Post by v3.xx on 2015-03-16
Maybe try chrome beta, but other than that ??

---

### Post by Sunsawe on 2015-03-19
I think I'll just confirm my migration to Firefox for the moment. Apart from some flickering, it seems to be working well.
Thank you all for your help :)

---

### Post by monkeybrain20122 on 2015-03-19
Chrome's tabs use a lot of ram. Firefox can handle 200+ tabs easily but in Chrome it is struggling with around 20+. However if you like Chrome you can try this extension [https://chrome.google.com/webstore/detail/footab/anbodogikfbehidmmjdokehphginagbb](https://chrome.google.com/webstore/detail/footab/anbodogikfbehidmmjdokehphginagbb) It prevents tabs from loading on start until you actually clicks it, it is not as good as Firefox's built in feature but still would save you a lot of ram.

---

### Post by mattharris4 on 2015-03-20
^ 200 tabs -- that is more than I could even keep track of!  For the record no web browser should be eating 4-5 GB of RAM even in this day and age.

Also, you may wish to set your swappiness factor to 0 or 10.  That will keep your computer from going into swap until you are just about out of RAM and speed it up considerably when you start getting into you RAM heavily as swap slows down a computer horribly.  Here is a link that shows how to do this:  [https://sites.google.com/site/tipsandtricksforubuntu/system-tips/swappiness](https://sites.google.com/site/tipsandtricksforubuntu/system-tips/swappiness) .

---

### Post by monkeybrain20122 on 2015-03-20
I have 200 tabs in FF but most of them are not loaded so it doesn't use any more ram then you would have only a few open. Chrome on the other hand doesn't have this featute so it uses up your ram pretty fast as soon as you start if you have ~ 20 (I have 4 G of rams) Using foo tab improves it somehow but still very far from Firefox.

---

### Post by vasa1 on 2015-03-20
> **mattharris4 said:**
> ^ 200 tabs -- that is more than I could even keep track of!  For the record no web browser should be eating 4-5 GB of RAM even in this day and age.

Also, you may wish to set your swappiness factor to 0 or 10.  That will keep your computer from going into swap until you are just about out of RAM and speed it up considerably when you start getting into you RAM heavily as swap slows down a computer horribly.  Here is a link that shows how to do this:  [https://sites.google.com/site/tipsandtricksforubuntu/system-tips/swappiness](https://sites.google.com/site/tipsandtricksforubuntu/system-tips/swappiness) .

[LIST]
[*]I wouldn't fiddle with the swap unless really, really necessary.
[*]Avoid links to random tips-and-trick sites. Stay with Ubuntu Forums or Ask Ubuntu or the wikis at ubuntu.com. The home page of the link recommended above has this image in part. Enough said ...
[/LIST]

---

