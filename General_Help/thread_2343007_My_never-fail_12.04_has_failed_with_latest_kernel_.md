---
title: "My never-fail 12.04 has failed with latest kernel - can't get past grub prompt"
date: 2016-11-12
forum: General Help
---

### Post by crazybear on 2016-11-12
While I have disks of 14.04 and 16.04, they all have very limited function compared to my 12.04 which can do anything I ask of it [unlike the others given my hardware or abilities]. So, my trusted 12.04 was my workhorse and used most of the time. It has been been down a few times, but I was always able to find some fix. After the most recent update which I didn't [foolish me!] carefully look at what was being installed - but must have included a new kernel as I was prompted for my password - it no longer boots up. I get through the password prompt and see the desktop image, but there is only [in letters so tiny I must put on my reading glasses and put my face up against the monitor] the words: 
[COLOR=#0000ff]"Minimal Bash-like Editing is supported' [/COLOR][then mention that hitting Tab will give choices - none of which work and all which need file names, commands, or or other information I don't know nor have]
[COLOR=#0000ff]Grub > _

[/COLOR][COLOR=#000000]I have seen some webpages on searching "Minimal Bash-like Editing is supported' and most simply say to use Boot Repair. I tried, but the usually helpful Boot Repair stopped midway and won't complete. I tried over 20 times using all combinations of things.

Help, please! Thanks for any suggestions, work arounds, fixes, ideas, etc.
I have the output of the Boot Repair, which I can post. It can be found here [/COLOR]http://pastebin.ubuntu.com/23461581/ 
I have NO idea why it lists both yesterday and 2014.

---

### Post by mörgæs on 2016-11-12
What can 12.04 do that 16.04 can't?

---

### Post by crazybear on 2016-11-12
> **mörgæs said:**
> What can 12.04 do that 16.04 can't?

On my system, and with my intermediate skills, my 12.04 can do EVERYTHING, 16.04 only runs a few of the programs I need, all with difficulty and with some annoying predetermined flourishes I hate. Everytime I have struggled to make my 16.04 be as good as my 12.04, I give up...I'd say it is only about 20% as functional [for me] as my 12.04. It could be hardware, my abilities or 16.04 on my system - I don't know and until I'm forced to abandon 12.04 in about half a year, I need it to do my WORK and JOB. For example, I can not [have spent about 100 hours or more] get the item on desktop to display on desktop...not do I get my image - only a black screen. I have several flavors of 16.04 I can boot into and ALL have different limitations - none of these limitations are on 12.04. I can see that 16.04 has better sound and video - but that of both on 12.04 is fine and everything works - something I can NOT say for 16.04 ON MY system! I don't doubt that likely a Ubuntu Geek could get my 16.04 to operate well, but I have none as a friend and my attempts on forums have not produced much help toward that goal. If it works, don't abandon it is my motto. I will be sad to see 12.04 go. A lot of the changes that I believe can NOT be modified are for the worse in the newer versions. IMHO.

....but this is a pointless discussion and does nothing for me now.

---

### Post by crazybear on 2016-11-12
I saw this, below:

 > 
[LIST]
[*][LEFT]    [COLOR=#111111][FONT=Times New Roman]First    type [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]ls[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman] command    and Press [/FONT][/COLOR][COLOR=#242729][FONT=Times New Roman]Enter[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman] to    see all the available partitions. The entries will be shown    as [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman](hd0,msdos1)    (hd0,msdos2) (hd0,msdos5)[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman] etc.[/FONT][/COLOR][/LEFT]

[*][LEFT]    [COLOR=#111111][FONT=Times New Roman]Then    type [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]ls    (hd0,msdos1)/[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman] to    see the content of the drive. if you see entries    like [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]vmliuz[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]or [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]initrd[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman],    it is your Linux partition. If you fail with (hd0,msdos1), try with    (hd0,msdos2) and so on, until you recognize your Ubuntu partition.[/FONT][/COLOR][/LEFT]

[*][LEFT]    [COLOR=#111111][FONT=Times New Roman]When    you correctly identify your Ubuntu partition,    type [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]root=(hdX,msdosX)[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman] ,    replace the [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]X[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]with    correct identified number. For example, if you    see [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]vmlinuz[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman] and [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]initrd[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman] entries    by entering [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]ls    (hd0,msdos5)[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman],    the command will be [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]root=(hd0,msdos5)[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman].[/FONT][/COLOR][/LEFT]

[*][LEFT]    [COLOR=#111111][FONT=Times New Roman]then    type [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]configfile    /boot/grub/grub.cfg[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman] and    type [/FONT][/COLOR][COLOR=#242729][FONT=Times New Roman]Enter[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman].    This will bring you Previous Ubuntu grub menu.[/FONT][/COLOR][/LEFT]

[*][LEFT]    [COLOR=#111111][FONT=Times New Roman]Then    choose the entry to boot Ubuntu.[/FONT][/COLOR][/LEFT]

[*][LEFT]    [COLOR=#111111][FONT=Times New Roman]After    you booted up, Open a terminal and type [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]sudo    update-grub[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman] and    press [/FONT][/COLOR][COLOR=#242729][FONT=Times New Roman]Enter[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman].    This will update the grub menu and prevent future problems.[/FONT][/COLOR][/LEFT]
[/LIST]

I followed the instructions [though they are not totally clear]. My root=(hd0,msdos2). I didn't know if I should then hit enter or also add the configfile line. I tried both ways several times and all it did was clear the screen and give me a new grub > _ prompt
So, was back to the start, with nothing accomplished. Is the above missing something? None of them had [COLOR=#111111][FONT=Times New Roman] [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]vmliuz[/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]or [/FONT][/COLOR][COLOR=#111111][FONT=Times New Roman]initrd , but the one I chose had the correct disk size and the correct Label name.[/FONT][/COLOR]

Help! Please! Prosim! S'il vous plait! Por favor!

---

### Post by mörgæs on 2016-11-12
> **crazybear said:**
> 
....but this is a pointless discussion and does nothing for me now.

I wouldn't think so. If you post some exact questions about what you want to accomplish in 16.04 there is a chance that people will post the solution. 

People here in Ubuntuforum hardly ever discuss 12.04-specific problems and I doubt that many are able to help you.

---

### Post by Impavidus on 2016-11-12
It seems there's something wrong with your grub.cfg. It doesn't contain any menu entry to boot Ubuntu. These entries should be located in a section between```
### BEGIN /etc/grub.d/10_linux ###

### END /etc/grub.d/10_linux ### 
```which is missing and part of the package grub-common. At least, I think so, but I've ditched 12.04 myself years ago. The recommended repair of boot-repair is supposed to purge and reinstall grub, which should fix the problem. Have you tried running the recommended repair?

The differences between 12.04 and 16.04 are, or at least should be, fairly minimal from the user's point of view. How did you try 16.04? Have you tried a live session or have you tried to upgrade your 12.04 to 16.04 and, after finding it unsatisfactory, installed 12.04 again? Upgrading can be problematic. There could also be a problem with your hardware that doesn't show up on 12.04.

Your hard drive is only half full. I suggest that, after you manage to fix 12.04, you make a separate partition for 16.04 (about 30 GB) and dual boot both systems. Take your time to get 16.04 running properly. Then make it your main system and ditch 12.04.

---

