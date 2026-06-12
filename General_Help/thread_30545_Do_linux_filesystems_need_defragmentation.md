---
title: "Do linux filesystems need defragmentation ?"
date: 2005-04-29
forum: General Help
---

### Post by davegahan on 2005-04-29
In windows one can get a speed improvement by regulary defragmenting the harddrive. Do Linux filesystems fragment ? If so, are there programs or utilities one can use to defragment ?

---

### Post by nocturn on 2005-04-29
[QUOTE=davegahan]In windows one can get a speed improvement by regulary defragmenting the harddrive. Do Linux filesystems fragment ? If so, are there programs or utilities one can use to defragment ?[/QUOTE]

Well, first off, you have to split the answer over available filesystems.  But in general it is no.

Ext2/3 do have some fragmentation, but even after long use it is very low (0.2-2%).
Unless you partition filled up completely, then it can increase to 5% or more.

Reiser does not fragment AFAIK.

---

### Post by Juergen on 2005-04-29
> Reiser does not fragment AFAIK.All filesystems fragment :-) (unless you do some automatic background defrag - freeBSD has this AFAIK)

But Linux fs have a better strategy to place new or growing files and so they fragment less than the windows ones.

And Linux fs sort read/write requests so that you have a lot less head-movements and get only a small time-penalty for having a fragmented fs.

So all in all nobody cares to write defraggers because they are not needed :-)
There is an old ext2defrag around, but it's use was AFAIR never recommended...

---

### Post by shakin on 2005-04-29
O & O has a beta Linux defragger, which I've never used. It looks like it's a free download.

[http://www.oo-software.com/en/products/oodlinux/](http://www.oo-software.com/en/products/oodlinux/)

---

### Post by az on 2005-04-29
[QUOTE=davegahan]In windows one can get a speed improvement by regulary defragmenting the harddrive. [/QUOTE]


You can also get a bit speed inprovement in windows by
1. Rebooting very very often
2. Reinstalling your os regularly to wipe out your registry
3. Not being connected to the internet so as to not have your computer secretly keep tabs with microsoft or another source of spyware.
4. Regularly buy hew hardware with windows preinstalled.
5. Do a virus scan every hour.
6. Install linux.

---

### Post by slux on 2005-04-29
Separate partition for swap also tremendously helps GNU/Linux stay unfragmented. Making other system dirs separate partitions probably also helps a bit as some of them are written to frequently (/var for one) and similar type of data (app binaries, user's personal files) will be located closer together on the drive.

---

### Post by cutOff on 2005-04-29
[QUOTE=azz]You can also get a bit speed inprovement in windows by
1. Rebooting very very often
2. Reinstalling your os regularly to wipe out your registry
3. Not being connected to the internet so as to not have your computer secretly keep tabs with microsoft or another source of spyware.
4. Regularly buy hew hardware with windows preinstalled.
5. Do a virus scan every hour.
6. Install linux.[/QUOTE]
Nice one!! :wink: 


Regards

---

### Post by darkcoder on 2005-04-29
[QUOTE=davegahan]In windows one can get a speed improvement by regulary defragmenting the harddrive. Do Linux filesystems fragment ? If so, are there programs or utilities one can use to defragment ?[/QUOTE]
 NTFS is not as bad as FAT is on fragmentation.  There was a review some months ago  on one of the mayor Windows Magazines (sorry cannot find it now), that they compare many Defragment software like Diskkeeper, even the XP own Defragmenter and no defragment at all.  And found that no matter the defragment program used, the advantage of it was a mere 2% or something like that.  So their conclusion was that fragmentation was not as bad as with FAT filesystems.

---

### Post by brk3 on 2005-04-29
To make a long story short: The answer is no  ;-) 
Just one of the benefits of using linux  :)

---

### Post by DutchLau on 2005-04-29
[QUOTE=darkcoder]NTFS is not as bad as FAT is on fragmentation.  There was a review some months ago on one of the mayor Windows Magazines.[/QUOTE]

That's the biggest bunch of .. I've ever read. I remember once defragmenting my own winblows xp and the defrag log showed that my NTFS HDD was 17.4% fragmented!! Although it was on a 40 GB HDD which was about 70% full, 17.4% fragmentation is NO excuse!!

That software review, coming from a "winblows magazine," (note that winblows magazines are *usually* pro-winblows) was *probably* especially written to convince all the sheep out there that winblows is better than *any other* O/S.  :-P We all know that that's true right?  :) 

DutchLau

---

### Post by tread on 2005-04-29
I have definitely needed to defrag my ntfs file system .. I havent read the article yet but if it says ntfs doesnt need defrag ..  not true! [-X

---

### Post by Stormy Eyes on 2005-04-29
[QUOTE=davegahan]In windows one can get a speed improvement by regulary defragmenting the harddrive. Do Linux filesystems fragment ? If so, are there programs or utilities one can use to defragment ?[/QUOTE]

You don't have to worry about fragmentation on Linux.

---

### Post by rothbart on 2005-04-29
[QUOTE=azz]You can also get a bit speed inprovement in windows by
1. Rebooting very very often
2. Reinstalling your os regularly to wipe out your registry
3. Not being connected to the internet so as to not have your computer secretly keep tabs with microsoft or another source of spyware.
4. Regularly buy hew hardware with windows preinstalled.
5. Do a virus scan every hour.
6. Install linux.[/QUOTE]
 Now *that* was hilarious!  :)

---

### Post by MetalMusicAddict on 2005-04-29
[QUOTE=azz]You can also get a bit speed inprovement in windows by
1. Rebooting very very often
2. Reinstalling your os regularly to wipe out your registry
3. Not being connected to the internet so as to not have your computer secretly keep tabs with microsoft or another source of spyware.
4. Regularly buy new hardware with windows preinstalled.
5. Do a virus scan every hour.
6. Install linux.[/QUOTE]
Why do people bash?

People seem to bash M$ and windows because they are the big dogs. Its eaiser. Linux boards look just like XP boards. People tryin to solve problems. Both of which have 'em.

---

### Post by az on 2005-04-29
I guess you are right.

I think I gave five very prominent problems with the Microsoft company's products.

It would seem to me that these issues are very hard to ignore for a multi-million dollar company.  It is ridiculous to think that they are unable to fix them.

It is obvious that Microsoft spies on it's users and obliges them to upgrade both their hardware and software to please the technology economy's beneficiaries (them).

I think that there is a difference in what I wrote and some jerk saying "I hate M$, KILL BILL!"

It is tougue-in-cheek, as well as preaching to the converted.  But I think it is much more linux advocacy than bashing.  

I am respectful your opinion, though, and will be more careful in the future.

---

### Post by Turin Turambar on 2005-04-29
Azz, you are right.... not to mention that it took M$ more than 6 years to actually make a fairly stable desktop OS (XP). That's inexcusable for a multi-billion company.
But we'll not talk about HIM here? No. :-\"

---

### Post by darkcoder on 2005-05-02
[QUOTE=DutchLau]That's the biggest bunch of .. I've ever read. I remember once defragmenting my own winblows xp and the defrag log showed that my NTFS HDD was 17.4% fragmented!! Although it was on a 40 GB HDD which was about 70% full, 17.4% fragmentation is NO excuse!!DutchLau[/QUOTE]

Yes, Windows Defrag said that your HD is X percent fragmented. After defrag, if you run Norton Speed Disk it would say that still the HD is Y percent fragmented and so on.  Each program has it's own way of organizing files, even analyzing the disk only will give different fragmentation percents when you compare the defrag programs.  But at the end, no matter the program, if you do a **loading time test** the results will be very similar, pointing that a defrag program is not the big deal anyway.

[QUOTE=DutchLau]That software review, coming from a "winblows magazine," (note that winblows magazines are *usually* pro-winblows) was *probably* especially written to convince all the sheep out there that winblows is better than *any other* O/S.  :-P We all know that that's true right?  :) 
DutchLau[/QUOTE]
<Sarcasm>No... I found it on Linux Weekly News... ](*,) <Sarcasm off> Of course if it was a review of Windows Defrag software, it should come from a Windows magazine.

---

### Post by nocturn on 2005-05-02
[QUOTE=MetalMusicAddict]Why do people bash?

People seem to bash M$ and windows because they are the big dogs. Its eaiser. Linux boards look just like XP boards. People tryin to solve problems. Both of which have 'em.[/QUOTE]

Good question.  If MS just made bad products, I wouldn't worry to much.
But it is their agressive artificial domination of the market that worries me.  One easy example is that I want to  buy a laptop soon.  Every single model I can find has Win XP on it, but I will install ubuntu on it.  So, I have to pay the MS tax, >100 € for the most expensive coaster I'll ever buy.

That in combination with them making the crappiest software I have ever witnessed makes me very unhappy about them.

---

### Post by MetalMusicAddict on 2005-05-02
[QUOTE=nocturn]But it is their agressive artificial domination of the market that worries me.  One easy example is that I want to  buy a laptop soon.  Every single model I can find has Win XP on it, but I will install ubuntu on it.  So, I have to pay the MS tax, >100 € for the most expensive coaster I'll ever buy.[/QUOTE]
This I do agree with. I dont mind their products just their tactics are what scare me.

---

### Post by wasynyt on 2005-05-02
i dont know that much about linux to answer that.. but i think the answer is no
yet its possible to fragment whole disk in winxp home (80gig in this case) into state where over 50% of space is fragmented in just few days.. simply by moving big ( over 600 mt) files around...
thats a sertain sign of poor file system for me

---

### Post by slux on 2005-05-02
[QUOTE=nocturn]So, I have to pay the MS tax, >100 € for the most [/QUOTE]

If you're in the US, you could get the HP NX5000, it can be bought with SuSe installed. The Linspire laptop is another possibility and if you're just not charmed with the idea of paying MS tax you could even get an Apple laptop. :)

As a bonus for the first two, they work very well with GNU/Linux since that's what they're sold with.

---

### Post by nocturn on 2005-05-02
[QUOTE=slux]If you're in the US, you could get the HP NX5000, it can be bought with SuSe installed. The Linspire laptop is another possibility and if you're just not charmed with the idea of paying MS tax you could even get an Apple laptop. :)

As a bonus for the first two, they work very well with GNU/Linux since that's what they're sold with.[/QUOTE]

Unfortunately, I'm in the EU, Belgium.
A laptop without an MS OS here is very rare...  Ditto for desktop PC's, but you can get arround that buy a) making your own, b) buying an assembled one (house brand).

---

### Post by Bagboy23 on 2006-10-12
> **azz said:**
> You can also get a bit speed inprovement in windows by
1. Rebooting very very often
2. Reinstalling your os regularly to wipe out your registry
3. Not being connected to the internet so as to not have your computer secretly keep tabs with microsoft or another source of spyware.
4. Regularly buy hew hardware with windows preinstalled.
5. Do a virus scan every hour.
6. Install linux.

^ Obviously this person understand nothing about computers.

---

### Post by Magnes on 2006-10-12
Bagboy23, why do you say that? Point 1-4 are true - I know that from my own (and my friends) experience. 5&6 are added for fun I suppose.

---

### Post by doowgof on 2007-11-24
This post is so useful to me!
+ I love the joke from az  lol

---

### Post by doowgof on 2007-11-24
> **Bagboy23 said:**
> ^ Obviously this person understand nothing about computers.

I agree loving linux does not require hating windows, but obviously az was just trying to make some fun, no need to be serious Bagboy :)

---

### Post by rune0077 on 2007-11-24
I agree no need to take it too seriously, but frankly, that whole Linux is faster than Windows is a bit dated, and not so true anymore. My Gutsy, for instance, boots sligthly slower than my Vista partition. My Vista-partition takes longer to load in all the applications after bootup. But once both are up and running, I notice very little different in the speed-factor. Both systems seems rather fast to me. Granted, Gutsy uses only 1/3 or 1/4 the resources to get that speed, but hey, I bought all that extra RAM and those dual processors for a reason you know. Might as well use 'em.

And wauw, that was so off topic, but worth mentioning.

---

### Post by doowgof on 2007-11-24
> **rune0077 said:**
> I agree no need to take it too seriously, but frankly, that whole Linux is faster than Windows is a bit dated, and not so true anymore. My Gutsy, for instance, boots sligthly slower than my Vista partition. My Vista-partition takes longer to load in all the applications after bootup. But once both are up and running, I notice very little different in the speed-factor. Both systems seems rather fast to me. Granted, Gutsy uses only 1/3 or 1/4 the resources to get that speed, but hey, I bought all that extra RAM and those dual processors for a reason you know. Might as well use 'em.

And wauw, that was so off topic, but worth mentioning.

You know it will be only a little bit faster when you update to more than 1Gb ram from 512Mb in XP? The effectualness isn't that great compare with updating from a 256Mb ram to a 512Mb? Cos XP's default settings don't work very efficiently with large rams and you have to configure them yourself.

---

### Post by rune0077 on 2007-11-24
> **doowgof said:**
> You know it will be only a little bit faster when you update to more than 1Gb ram from 512Mb in XP? The effectualness isn't that great compare with updating from a 256Mb ram to a 512Mb? 

Yeah, but Vista uses RAM much better than XP (and it needs it to, considering how much it requires to run the darn thing).

---

### Post by doowgof on 2007-11-24
> **rune0077 said:**
> Yeah, but Vista uses RAM much better than XP (and it needs it to, considering how much it requires to run the darn thing).

Yes, but Vista isn't very good, it supports no software~ And Microsoft isn't happy about the number of Vista sold. My friend has one but he prefers XP.

I just reallised the word Microsoft looks so nice. I mean the order and combination of the letters.

---

