---
title: "What Makes A Computer Slow?"
date: 2014-04-12
forum: General Help
---

### Post by Smallwheels on 2014-04-12
Years ago I experienced my 2003 Gateway computer getting slow because the 40 GB HDD was 75% full. The closer it got to full the slower it got. I read in many places that this is a normal occurrence. Eventually it had about 35 GB of data on it. 

A couple of years ago my 2008 Mac Book seemed to be much slower than it was when new. It had a 160 GB HDD. The most that drive ever held was 88 GB. Yet why was it getting slow? Programs seemed to be taking longer to load. Eventually I did some testing and cleaning with programs designed to put everything back in order as they should be. With a clean bill of health I was glad to know everything was working properly. The machine was not much faster. Most of the time it still seemed slow, much slower than when new.

On forums I was told that having a drive with only about 55% in use shouldn't have any effect on the speed of the machine. 

In 2010 I loaded Ubuntu 10.04 LTS. It was my first experience with GNU/Linux. I liked it. It was much faster than the Vista OS on the same machine. It took a long time to get it working but eventually I liked it enough to make Ubuntu my main OS. 

Last year while learning about different operating systems on Youtube I came across Joli OS. The concept was about using the cloud. It was very lightweight and would make any machine run fast because one would keep files stored on the internet instead of on the HDD. By the time I discovered it the project had ceased as an OS. It transformed into a web location that connected to all of the same sources for internet products. It isn't working that well yet. I tried it last year. It is called Jollicloud. 

My point is coming soon. 

Ubuntu 13.04 was running great but it was time to update to 13.10 so I could make the switch to 14.04 using updates. I put everything on an external HDD. Ubuntu 13.10 wasn't working so well. It was crashing a lot with Firefox and Chrome. Most of the time it seemed video was part of it but not always. I didn't load my files back to the HDD. I kept them on the external HDD. 

I decided to do a fresh installation using a Live USB. It worked. I still have crashes but fewer of them. The thing is, after two weeks the machine seems slow. Not slow like a clogged HDD but definitely not snappy. This despite not having more than 2.3 GB of data on the HDD! This afternoon my machine froze. I had four browser windows open. Three of them had one window with no tabs. One of them had three tabs. The Thunderbird mail program was running in the background but its window wasn't open. I wasn't watching any videos at the time. Two of those windows were Google Drive. The others were related to news stories, text with links and ads. 

The machine got slow and slower and eventually the cursor was just barely moving. Nothing would respond to clicks. Why would my machine be acting so slowly with so little going on? The HDD is nearly empty. You may be wondering what the specifications of this machine are. It is an HP tower with a 2.3 GHz AMD Sempron LE 1300 with 2 GB RAM. The HDD is 320 GB. When I was using 10.04 LTS the machine was much snappier and could handle much more than it is now. 

I mostly use Firefox. It has AdBlocker Plus, DoNotTrackMe, and Video Download Helper as add-ons. I have the same ones on Chrome. GNU/Linux is supposed to be lightweight compared to the other two big boys. Shouldn't I be having a great experience with a quick running machine? Back when I learned of Joli OS I was considering moving everything into the cloud and just having a light and fast OS running on my machine. It would make my computer last a really long time because the HDD would only have the programs on it and nothing more. It should run like new all of the time. Yet it doesn't. 

With almost all of my files on an external HDD my machine will still get slow. Are browsers taking up so much RAM and CPU that they alone with their plug-ins are ruining my computing experience? I loaded this OS last week and I remember just how quickly programs loaded on the first day. 

I thought that a machine with just the OS and programs, with nothing stored on the HDD, would run as fast as new. It seems that I was wrong about that. There needs to be a RAM dump button so that I can just instantly empty it and begin the next process without the previous process' stuff clogging the memory. Maybe that would be a solution. 

Chrome OS people with very low power processors are having a blast with their fast machines. I know that SSDs do a good job of speeding things up but that wouldn't explain their wonderful video playback and browsing experiences. I'm keeping my machine as is until 14.04 comes out. I don't want to fiddle with reloading the OS again. I'll deal with the pain for another week. If I experience the same thing then I'll hunt for a new OS. If that doesn't fix it then I'll suck it up and buy a Chrome OS machine. They seem to be great for their users. I fit the profile of somebody who could do just fine with Chrome OS. 
 
So what do you think is causing my machine and all machines to run so slowly? What makes a computer slow?

---

### Post by mörgæs on 2014-04-12
I have to admit that I didn't get all details in your long post, but a good first try is installing something lighter than Ubuntu, say X/Lubuntu.
More advice in the link in my signature.

---

### Post by buzzingrobot on 2014-04-12
Systems can slow down as disk space becomes less available.  Empty space needs to be searched for, and the less that is available, the longer that search can take.  Much depends, though, on the file system in use.

The number of services, daemons, and startup applications executed when you boot up consume memory and can slow response time.  Often, especially on Windows, apps will add these applications without informing the user.

Making things easy to use consumes resources, in Windows or OS X or Linux.  Contemporary Linux interfaces like Unity, Gnome and KDE are very functional but do not sacrifice usability for lightness. Meanwhile, an application is an application. I.e., whatever interface you run Firefox on, it's still Firefox.

External drives are usually slower than internal drives because data need to be fed down the attaching cable, and that pathway is typically not as broad or as fast as what's available on the motherboard.. Thunderbolt devices can be fast, but USB devices are not, comparitively. Applications, Windows or Linux, are typically made up of many individually executable files that are loaded into memory as needed.  If those files are on an external drive, they're probably going to take longer to load.

Video capabilities have a lot to do with subjective impressions of speed and responsiveness. Regardless of how fast or slow the CPU or takes to accomplish a task, if the video takes too long pushing the results to the screen, the user will be annoyed.

---

### Post by oldos2er on 2014-04-12
> **Smallwheels said:**
>  GNU/Linux is supposed to be lightweight compared to the other two big boys. 

Not all Linux distros are created equal in their default installations, some are much lighter than others.

What are your hardware specs?

---

### Post by Double.J on 2014-04-12
> **Smallwheels said:**
> So what do you think is causing my machine and all machines to run so slowly? What makes a computer slow?

A great many things can slow down performance. based upon your description that a clean install was snappy, it sounds less likely to be hardware, but it is an option. I would recommend finding out what is running software wise first. Try opening up system monitor and noting what the CPU usage is, the RAM usage and SWAP usage (along the bottom of the window)

You have already encountered one type of slowdown - low disk space. You absolutely correct that as a disk becomes full, performance is reduced.

If you're RAM is full, performance will also slow down as the computer must more frequently move things it needs from the hard drive swap space to the RAM (Even with an SSD, the hard drive is just a fraction of the speed of the RAM.)

If your SWAP space is running out of space, then again the CPU must move things around when it wants to write data from RAM and read data to RAM. Both This and lack of space in RAM will increase CPU activity as it spends more of it's time moving data where it wants it rather than doing what you've asked.

non-optimum graphics drivers can cause the display to become laggy and prone to image distortion.

If your CPU usage is high, that means that there already a lot of ongoing system processes, so when you ask the CPU to do something, that is just added to the list. 

In terms of hardware, RAM and HDD are the most likely suspects. Grub has memtest built into it's boot select, and check out this [ask ubuntu]("http://askubuntu.com/questions/59064/how-to-run-a-checkdisk") regarding checking your disk.


Finally, you say you've moved a lot of data to an external Hdd. is there anything on there that the system needs? judgin by your specs, I'm assuming it's a USB 2.0 so this could be another bottleneck. 


But for now, lets start at the beginning; and have a look in system monitor.

if the user interface has slowed so much as to not be practical, enter the terminal prompt by pressing
```
ctrl+alt+F1
```(ctrl+alt+F7 to get back)
Then log in and install htop
```
sudo apt-get install htop
htop
```(if you have no internet connection, you can just use 'top' but htop is easier to understand imho.)

All the best, 

Jj

---

### Post by Smallwheels on 2014-04-12
It is good to learn a bit more about this situation. To be clear, all programs are loaded onto the HDD. Only my saved files and images are stored on the external drive. Requesting stuff from the external drive via USB 2 doesn't really take much time. 

The graphical display of the System Monitor is almost never lower than 50% for the CPU and the slightest thing takes it to 100%. The RAM indicator varies a lot. It is often at maximum. The little circular displays in the System Monitor usually stay the same until I restart the machine. Then they will register something different. The RAM usually says 1.5 GB or higher and the swap is always at 700+ megabytes. 

In the process list the names of things are so unrelated to the things I have running that I don't know which ones I could end and which ones I can't end. The programs that are running usually have icons that turn on in one column in the process list. That makes it easy to turn off a frozen process. When the whole machine freezes I can't access anything. 

Why do computers freeze? Windoz will do it all of the time. It seems that 13.10 for me got so bad that I did a fresh installation to try to fix it. Why can't the processes that slowed the machine just catch up and run properly after a little while instead of just locking up? There needs to be instructions in these programs that allows this to happen. I've heard of sandboxing in the Chrome browser and then the Firefox browser. Something like that needs to be incorporated into the computer operating systems too. Maybe it already exists but just doesn't work. It certainly isn't working on my machine.

---

### Post by Double.J on 2014-04-13
Hi,

ah so it does sound like software - likely that RAM is running out of space, having to swap often and using the cpu.

could you post what is using the most resources?

Jj

---

### Post by buzzingrobot on 2014-04-13
> **Smallwheels said:**
> Requesting stuff from the external drive via USB 2 doesn't really take much time. 

Yes, subjectively.  But, it is, in fact, significantly slower.

> The graphical display of the System Monitor is almost never lower than 50% for the CPU and the slightest thing takes it to 100%. The RAM indicator varies a lot. It is often at maximum. The little circular displays in the System Monitor usually stay the same until I restart the machine. Then they will register something different. The RAM usually says 1.5 GB or higher and the swap is always at 700+ megabytes. 

One thing to do is to look at RAM use immediately after a reboot, with no programs launched.  (If it's 1.5 GB, that's high.) Then, launch the usual programs one at a time and see how RAM use changes. 

Swap shouldn't be used until RAM is full. 

> In the process list the names of things are so unrelated to the things I have running that I don't know which ones I could end and which ones I can't end...

The OS uses many processes. All but the simplest programs spawn a variety of processes. Killing a process is temporary.  if a process is actually unnecessary, then it needs to be disabled so it is not activated at boot.
 
> Why do computers freeze? 

Hardware faults. Overheating. Bad drivers.  Wrong drivers. Forgetting to update, leaving buggy software in place. Faulty software. An errant program or process gobbling up memory until none is left. An errant program or process overwriting the wrong data in just the right place. 

Whatever it is, there is a cause.  If hardware isn't it, then you're left to methodically check the impact of suspect software.

---

### Post by mörgæs on 2014-04-13
> **buzzingrobot said:**
> 
Swap shouldn't be used until RAM is full. 


That what one would expect, but reality is different. Please see the swappiness section in the link below and try changing the setting.

---

### Post by buzzingrobot on 2014-04-13
> **mörgæs said:**
> That what one would expect, but reality is different. Please see the swappiness section in the link below and try changing the setting.

I've never seen that happen on any machine I've used Linux/BSD/OS X on for the last 15 years or so.

---

### Post by Double.J on 2014-04-13
Many things can be put in swap that aren't needed after loading an app. My current machine has 2gb ram, using 619mb RAM, sawp at 91MB

---

### Post by mörgæs on 2014-04-13
> **buzzingrobot said:**
> I've never seen that happen on any machine I've used Linux/BSD/OS X on for the last 15 years or so.

I have seen a significant improvement in speed by setting swappiness low, but of course it depends on the hard disk used and the type of workload. Don't let long experience get in the way of experimenting.

---

### Post by buzzingrobot on 2014-04-13
> **mörgæs said:**
> I have seen a significant improvement in speed by setting swappiness low, but of course it depends on the hard disk used and the type of workload. Don't let long experience get in the way of experimenting.

My 8-gig Macbook would swap if I loaded enough 100-150 meg image files into Photoshop.  Doesn't take many to add up to several gigs when they are that fat.

This ThinkPad has 32 gigs and I've yet to see it swap, no matter how many fat image files I feed it at one time. (Which is why I sprung for the memory.) I could deliberatly force it to swap, of course.

Memory use is a moment to moment thing.  If a process makes a memory request that pushes the total above available RAM, swap can be used. If the memory is freed one second later, the code/data pushed out to the swap partition will likely stay there until it's needed again. So, if a user checks swap usage at that point, it can show some non-zero amount in use, even while RAM use is below maximum. Whether that tool reflects real-time swap use or periodically polls for it also needs to be considered.

In general, I think if something was wrong with the swap algorithm or code, that would be a very visible kernel bug. If I did see myself constantly using swap, I'd probably check out that swappiness setting.  But, actually, I'd just probably look for a way to squeeze in more RAM chips.

---

### Post by Double.J on 2014-04-13
> **mörgæs said:**
>  Don't let long experience get in the way of experimenting.
This is so true; I first used linux around 2001/2. My initial learning curve was mount everest, but then I just learned to do the things I needed. I've honestly learnt more in my 4 years of helping out in online forums than I did in the 8/9 years previously! 

Plus, you know, it helps that nowadays installing a release and getting all your features working is relatively straight forward -Affords a lot more time for tinkering ;)

Jj

---

