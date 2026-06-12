---
title: "Dual boot advice"
date: 2006-09-19
forum: General Help
---

### Post by ClarkePeters on 2006-09-19
This is my experience. 

It's amazing how "dual boot" often becomes "duel boot" when it comes to windows and any other system. :)

I used to program years ago, but I'm not a new age techie here, but I've never failed at putting together my own hardware and setting up a system.

First, the problem that I had and then fixed, then, the solution.

I had installed Ubuntu on a spare hard drive, all things went fine (a 20 gig drive completely dedicated to Ubuntu OS). I decided, therefore, to try Xubuntu on another spare hard disk I had lying around in order to compare Xubuntu to my Ubuntu experience (which, btw, is wonderful!).

The spare drive had two partitions, one dedicated to my Windows Me OS, and the other was just spare use for my data (so basically, in Windows file manager, C: drive was my Windows system, and D: drive was folders for saving data, documents etc.. I used to have some programs on the D: drive in the past but had since uninstalled all of them to dedicate that partition to data only).  

So I got the idea that rather than reformat the whole disk I'd give the "dual boot" setup a try by adding Xubuntu to that extra data space (D: drive) that I no longer needed (leaving Windows in its natural C: drive partition)

I downloaded the ISO install CD for Xubuntu, and did a flawless installation (the process, not the results). During install I manually chose the old D:\ partition (it's easy to tell which partition is which, because Xubuntu Install marks the system partition with a big red warning sign)

FYI: Xubuntu and Ubuntu will recognize windows and then setup a dual boot for you in the background so that you'll always have a choice of systems at start up--you don't have to do a thing (the install will not even ask you anything about dual boot, it just works)

The problem: I booted into Xubuntu just fine but when I went to boot Windows I got the infamous blue screen (and now I even forgot what the error message was). I could still get into Windows via safe mode or the Option 4), but that's big trouble. 

Solution: 

Here's my thinking, Xubuntu on this rare occasion overlayed something in my Windows System files or swap files or something. I think Window's System had planted something in that old D:\ space even though I had a dedicated C: partition solely for Windows. 

So how can we prevent this? 

I started from ground zero with the troubled disk drive. Since no data or program loss/worry was involved. I did a re-install for both systems in the following manner:

I ran Xubuntu install CD  and started the gnome partition editor.  I made a partition for my Windows (I prefer fat32), using about 1/3 of the drive space. _**Now this is important**_, I left the rest of the disk unformated (no ext3 nor fat32 nor anykind of system format at all). Then I installed Windows and checked that it was working fine, which it was. At this point, if you look at the disk properties for C: drive while your in Windows you'll notice that it doesn't recognize the unused space.

After the successful Windows install, I installed Xubuntu, letting it format automatically for itself the other 2/3 of the disk's unused space (it will automatically chose the largest continuous unused space to format and install itself on.) It worked like a charm.

My thinking is this. In the first instance windows had slipped some important data outside of the C: drive, (swap?, old program bit? not sure), so Xubuntu inadvertenly overwrote something important. 

But in the second instance, by partitioning only part of the drive for Windows, and leaving the rest unformatted, you are locking Windows completely into it's own partition because Windows will not recognise unpartitioned/unformatted space--therefore it won't write anything important there, hence, nothing important can be overwritten with the Ubuntu/Xubuntu install. Windows will make any swap space or system files completely within its partition. 

In this case, this leaves Xubuntu free to do whatever it likes on the unused/unformated space; no harm, no foul. 

Both my systems have been working just dandy ever since.

Respond if you think this is useful advice. 

P.S.  the Xubuntu experience was not too great, only because I didn't have time to fool around with setups. Xubuntu didn't automatically mount and give access to my secondary hard drive and my sound didn't work. With Ubuntu, all that was done automatically.

---

