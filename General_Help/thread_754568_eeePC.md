---
title: "eeePC?"
date: 2008-04-13
forum: General Help
---

### Post by sekinto on 2008-04-13
**So, I'm thinking about buying an eeePC, but I have some questions.**

Things I've decided on:
Getting the 4GB non-surf.
Buying 2GB of RAM for it.
OS: Minimal Debian install, or posibly eeeBuntu.

**Edit: I deleted old questions that have been solved, everything below this is a question that hasn't been answered yet.**

**Questions**
_External Storage_
How long will a USB flash drive last when used every day with no read-write saving feautres turned on?
How long will a USB flash drive last when used every day with read-write saving features turned on?

---

### Post by Islington on 2008-04-13
> 1 ) Are there any variations in the hardware between the 2, 4 and 8 GB versions?
If there are variations, what are they.
If there aren't variations wouldn't it be a good idea just to get the 2 GB one for a cheap price and buy an 8-16 GB USB flash drive?

I believe there is an embedded video cam in select 4 and 8 gb models.
If you dont use the webcam, then yes I suppose.

---

### Post by aysiu on 2008-04-13
I think you'll find these two links helpful:
[http://wiki.eeeuser.com/eee_pc_701#models](http://wiki.eeeuser.com/eee_pc_701#models)
[http://wiki.eeeuser.com/ubuntu:eeexubuntu:home?s=eeexubuntu](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home?s=eeexubuntu)

---

### Post by sekinto on 2008-04-14
I don't really care about the internal space since I'll be mostly be using external drives,
Is the carrying case, mouse, extra battery life, extra RAM, built in webcam, and slightly better processor worth $200?
I really don't need the webcam, it would be nice, but I've never needed one before. I won't need the carrying case since it is small and should fit in my backpack just fine. The mouse and extra RAM would be big pluses for me. The extra batter life and processor are also nice enhancements. But are they worth the money?

I heard about eeeXubuntu already, it sounds very interesting, I think I'll go with that.

If anyone can answer my other questions that would be very helpful.

---

### Post by aysiu on 2008-04-14
I went with the 4 Gb non-surf for several reasons: [list][*]It actually allows you to upgrade the RAM, unlike the surf versions [*]It has a slightly faster processor, and I don't think you'll be manually upgrading the processor [*]2 GB is a pittance of disk space, and they take out a lot of programs in order to fit Xandros on there. Yes, I know you're going with *buntu instead of Xandros anyway and also using external storage, but it's nice to have that little bit of storage. [*]Considering that even on the upper-level models the battery life is wanting (okay but not impressive), I can't imagine having it even worse (which is what the surf models offer). [*]The non-surf model comes with a neat little carrying case for the Eee[/list]

---

### Post by sekinto on 2008-04-14
After looking at all of the models again that does appear to be the best deal. What is the RAM upgrade limit, how many sticks of RAM can you have, and what number of pins does it require the RAM to have... oh, also how fast of RAM can it utilize to its full potential.

---

### Post by aysiu on 2008-04-14
There is only one slot (so you are replacing the default 512 MB, not adding to it), and it's 200 pins. The Xandros installation will recognize only up to 1 GB of RAM (unless you recompile the kernel), but I think if you use eeeXubuntu or another Ubuntu derivative, you can use more than that (2 GB, for example).

I got a 1 GB stick from NewEgg for US$18.

---

### Post by sekinto on 2008-04-14
Yeah, I was going to buy all my **** from NewEgg, I love them. Anyway, could you recomend a really tiny mouse? PS/2 is preferred if the eeePC supports it, if not, USB.

---

### Post by aysiu on 2008-04-14
I can't recommend a mouse, but i can tell you Eee does not support PS/2. It should be a USB mouse.

---

### Post by sekinto on 2008-04-14
Updated!

---

### Post by fragos on 2008-04-14
You can buy more powerful entry level laptops for little more than the eeePC. Buy the eeePC because of it's size and portability, not because of it's price.

---

### Post by sekinto on 2008-04-14
Who said I was buying it because of the price?

---

### Post by sekinto on 2008-04-15
Bump.

---

### Post by sekinto on 2008-04-15
Bump.

---

### Post by ronacc on 2008-04-16
I got this mouse for my HP laptop and will migrate it yo my eee which arrives tomorrow .
[http://www.geeks.com/details.asp?invtid=BEI-FDM-G51-USB&cat=MOU](http://www.geeks.com/details.asp?invtid=BEI-FDM-G51-USB&cat=MOU)
I am not recomending necessarily that you buy it from them I just included the liknk so you could see what I am talking about . it is really a finger grip trackball and needs no surface which is handy if you will be using your eee where flat surfaces are hard to come by. It takes a little getting used to but works quite well . I got mine at walmart . 
 I also ordered my eee from newegg and got a 2gb memory stick because I want to run with no swap . I am going to try to get ubuntu to boot off of an sd card, what I would like to do is leave xandros on the ssd and have ubuntu on an 8gb flash card and puppyeee on another so I can just plug in the os I want ;)

---

### Post by sekinto on 2008-04-16
I already found the mouse I'm going to get with it, but if you can answer any of my other questions I would apreciate it greatly.

---

### Post by ibuclaw on 2008-04-16
You can install Ubuntu on an EeePC.
There's [EeeBuntu]("http://www.eeebuntu.org/").

Or if you want the original Ubuntu, [you can do that too]("http://ubuntu-eee.tuxfamily.org/index.php5?title=Quick_Start").

On the questions you asked:
a) External Storage.
Hardware lasts the same amount of time, no matter what file format you have it in.
I think one flat 8GB Pocket Hard-drive should really do (3.14"). I doubt you're gonna do anything that will require alot of Hard Drive storage with the EeePC.
I recommend Ext3 or ReiserFS. They are more optimal formats.

b) The Screen.
This is a 7" screen, with an around 800x480 pixels fitted across. When using the internet, you'll have a scroll bar to view from left to right as well as up and down.
So we are talking about a pretty small screen. When compared to some large scaled programs built for 1024x768 monitors. Though if you dig around, you'll start to find special made apps for the EeePC due to its popularity.

c) Power.
It's not slow, but not excitingly quick. Though you can put in loads of optimisations such as reducing swappiness (the amount of data stored on swap during runtime), overclocking it's CPU to 900Mhz (If you get the EeePC 800MHz version) and optimising how the filesystem reads/writes to the hard-drive (an added function such as "noatime" put in the /etc/fstab file.)

I think Video-Editing is a bit out of the EeePC's league. Unless you have a load old PCs of lying around that can act as an AmpFarm for it. All what the webcam is for, is for apps such as Skype for internet chats with your mates.
Else, everything else should be just about doable.

I don't think that the onboard graphics card supports OpenGL 3D stuff, so no (or very little) compiz.
That said, you can get other neat little dekstop apps that improve the flashy-ness of the Desktop.
One would be Enlightenment, as found in OpenGEU.
Another would be the AWN Desktop Bar (Bit Like an Apple Mac Look).

d) Wireless
EeePC has a builtin Atheros chip. It's wireless, and WEP/WAP/WPA2 capabilities all depend on what software you use. Hardware will do as you tell it to, no probs.

e) Webcam
Erm... Skype.
It's what the EeePC was built for.
But anything else should work with it too.

f) Heat
Given that you can overclock it without too much hassle or effect to the hardware.
If you feel that paranoid. You can [clean the Laptop HeatSink]("http://icrontic.com/articles/clean_laptop_heatsink") and reapply some heatsink paste once every year and a half or two years.
Though I'm not too sure whether or not the EeePC is locked up more than normal laptops.

You can also get external [Cooling Mats]("http://images.google.co.uk/images?hl=en&q=Laptop+Cooling+Mat&um=1&ie=UTF-8&sa=N&tab=wi").
Comes in both metall and soft cushion. Take your pick.

>  You can buy more powerful entry level laptops for little more than the eeePC. Buy the eeePC because of it's size and portability, not because of it's price.
The EeePC is more than a Laptop. It's turning into a wonderful accessory, like the iPOD, for example.
If someone really wanted to get a Laptop Cheap. They might as well go and buy a [Zepto Znote.]("http://uk.zepto.com/Shop/Notebooks.aspx") Though, the reason why they are so cheap is because they don't come packaged with an OS.

Anyway, I hope that I've given you alot of food for thought on the matter.

Regards
Iain

---

### Post by aidanr on 2008-04-16
The [900]("http://jkkmobile.blogspot.com/2008/04/asus-eee-pc-900-retail-version-video.html") is far better and should be out soon, I'd wait for that instead of the 701.

---

### Post by sekinto on 2008-04-16
Thanks, you answered almost all of my questions.

The reason I asked about the XFS vs EXT2 thing is because I heard somewhere that journaliing file systems write more (don't they make a log of changes preformed or something like that). If jounaling file systems don't shorten the life any more than non-journaling ones I'm going to go with XFS, I prefer it over the two you mentioned (ResierFS and EXT3).

I still need to know the speed limitations of the RAM it can use are, and also what kind of storage I should use.

---

### Post by SnappyU on 2008-04-17
> **fragos said:**
> You can buy more powerful entry level laptops for little more than the eeePC. Buy the eeePC because of it's size and portability, not because of it's price.

Au contraire!  I got the eeepc mainly because of its size, portability *and* price!  If price was not a concern, I would have gotten a Sony vaio subnotebook or a fujitsu ... many on eeeuser.com and forum.vr-zone.com.sg would agree as well.

Think about it, if the Sony vaio picturebooks were priced at US$399 and not US$1999 or more back in 2001, they would have sold like hotcakes! :)

---

### Post by SnappyU on 2008-04-17
> **tinivole said:**
> 

The EeePC is more than a Laptop. It's turning into a wonderful accessory, like the iPOD, for example.
If someone really wanted to get a Laptop Cheap. They might as well go and buy a [Zepto Znote.]("http://uk.zepto.com/Shop/Notebooks.aspx") Though, the reason why they are so cheap is because they don't come packaged with an OS.

Anyway, I hope that I've given you alot of food for thought on the matter.

Regards
Iain

The reason they are so cheap is only in part because they don't come packaged with an OS.  At OEM price, Windows XP Home Edition comes at less than US$100.  At larger volume, it can go to $50~$70.

Perceptions, perceptions!

---

### Post by ronacc on 2008-04-17
to your question about memory , the eee memory bus runs at about 400 mhz so in that respect there is no advantage to 800mhz ram , however most laptop ram is rated at cl5 latency and will actualy work at cl4 or 3 at the lower speed so if the 800 stick you are looking at is better than the 667 there would be an advantage , check the specific manufacturer's specs . as to the usb stick I would go with one 16gb and partition it .you only have 3 external usb ports and need one for the mouse , if you use 2 usb sticks as / and /home you can't plug anything else in without disconnecting your mouse since you can't remove  either / or /home  . also I am going with an sd card rather than a usb stick because I am primairily looking at ultra portable use an a usb stick poking out the side probably wouldnt last one day.

---

### Post by ibuclaw on 2008-04-17
> **sekinto said:**
> Thanks, you answered almost all of my questions.

The reason I asked about the XFS vs EXT2 thing is because I heard somewhere that journaliing file systems write more (don't they make a log of changes preformed or something like that). If jounaling file systems don't shorten the life any more than non-journaling ones I'm going to go with XFS, I prefer it over the two you mentioned (ResierFS and EXT3).

I still need to know the speed limitations of the RAM it can use are, and also what kind of storage I should use.

Journaling systems are harder to defrag, from my knowledge. I think the only trouble with them is that they require more space to host them.
ie:
if I were to format my 982Mb Flash Stick to Ext3, I would loose around 80-100Mb.
Re-Format it to Ext2, I would loose around 20Mb.
But format it back to Fat32 I would loose 8Mb, (but it would be back to 982Mb again.)

Subsequently, I think that booting and shutting down is the only loss you have using those types of filesystems. Though that isn't to say that using Ext2 is far quicker to load Programs than Ext3.
I should really lookup a few tests before I start speculating something I know little about.

I'm reading that the RAM is 1Gb or 512Mb DDR2 sticks. Off the top of my head, DDR2 is usually 400MHz, is it not? I'd take the CPU speed more into consideration.

For example, I have 1GB of DDR2 RAM, but a 2GHz Processor, this speed allows me to hold alot of apps with little speed loss. Okay, maybe the fair amount of RAM has its part, as I use less of the swap and more of the RAM. But with the speed of the CPU, it allows quick read/write access to the swap while as the same time seamless handling of the primary memory too..
A slower CPU, despite having a large RAM, just wouldn't be as smooth when running multiple apps.

But back to the EeePC. As I said, it's speeds aren't slow, but aren't spectacular.
I think it has a 12 second load for the first time you run OpenOffice. 5-7 seconds everytime after.

As to how much it can hold.I wouldn't push it.
Say, give it a max pointscore of 8.
Where Heavy apps (OpenOffice) equal 4 points for each app running.
Medium (Firefox) equal 2 and Light apps (Calculator) equal 1 point.

I may be underestimating the power/potential of the EeePC, but I wouldn't go absolutely silly with it. But this isn't far off from the limit I have on my PC (but I have compiz, so it probably balances itself out to equal the same effect).

USB storage drives. It's all down to personal preference, and how much you want it to get in the way.
As I mentioned in my previous post, 8/16GB drives are around the size of a 3.14" floppy disk.
So its all down to personal preferences on which one you want.
ie, do you want an 8GB pen stick sticking out, but gives you great portability. Or an 16GB pocket drive hidden away, but restricts you to a table?)

Regards
Iain

---

### Post by sekinto on 2008-04-17
Thanks for your help guys, I'm only down to one question now.
Do read/write saving features (no-swap, no-indexing, et cetera) really help prolong a flash drives life by a lot, or is the difference not very noticable?

---

### Post by ibuclaw on 2008-04-17
Have a swap.
Even if it is, say 512MB. I recommend that you have it. This is especially true with the newer Linux kernels, if you boot into Linux without a swap, the memory handling and speed can get very disasterous very quickly.

Once installed with swap, you can tinker the config files to reduce the swappiness of Linux, so more memory is kept in the RAM.
```
 gksudo gedit /etc/sysctl.conf 
```
And add this line at the bottom of the file...
```
 vm.swappiness=0 
```

Regards
Iain

---

### Post by dcstar on 2008-04-18
> **tinivole said:**
> 
.......
As I mentioned in my previous post, 8/16GB drives are around the size of a 3.14" floppy disk.
So its all down to personal preferences on which one you want.
ie, do you want an 8GB pen stick sticking out, but gives you great portability. Or an 16GB pocket drive hidden away, but restricts you to a table?)


I have a Lacie 8GB USB hard drive which is the dimensions of a (very) thick credit card - and because it is a physical hard drive it has none of the limitations of flash storage.

Not as small as a USB stick, but not too bad at all. Good for the top pocket but not the wallet - because you don't want to sit on it too often!

---

